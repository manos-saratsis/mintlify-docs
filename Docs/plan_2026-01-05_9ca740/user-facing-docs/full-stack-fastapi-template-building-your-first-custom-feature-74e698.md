# Building Your First Custom Feature

This tutorial guides you through creating a complete new feature in your application by building a "Projects" resource from scratch. You'll learn the full development workflow by following the same patterns used throughout the template.

## Overview

You'll create a complete CRUD (Create, Read, Update, Delete) feature that includes:

- Database structure with proper relationships
- Backend API endpoints for data management
- Frontend interface for user interactions
- Full integration with existing authentication and permissions

**Time to Complete:** 30-45 minutes

## Step 1: Plan Your Feature

Before writing code, define what your feature needs:

**For our "Projects" example:**
- **Purpose:** Track user projects with names and due dates
- **Data Fields:** 
  - Name (required, up to 255 characters)
  - Description (optional, up to 255 characters)
  - Due date (optional)
- **Ownership:** Each project belongs to a user
- **Permissions:** Users can only manage their own projects (superusers can see all)

This planning mirrors how the Items feature works, which we'll use as our template.

## Step 2: Create Database Models

Database models define how your data is structured and stored.

### Define Your Models

Open your models file and add these new classes following the established pattern:

**Base Properties (shared across operations):**
```python
class ProjectBase(SQLModel):
    name: str = Field(min_length=1, max_length=255)
    description: str | None = Field(default=None, max_length=255)
    due_date: str | None = Field(default=None, max_length=50)
```

This base class contains fields that appear in multiple operations. The `Field` constraints ensure data quality.

**Creation Schema (what users provide when creating):**
```python
class ProjectCreate(ProjectBase):
    pass
```

This inherits all base properties. Add extra validation here if needed during creation.

**Update Schema (what users can modify):**
```python
class ProjectUpdate(ProjectBase):
    name: str | None = Field(default=None, min_length=1, max_length=255)
    description: str | None = Field(default=None, max_length=255)
    due_date: str | None = Field(default=None, max_length=50)
```

All fields are optional for updates, allowing partial modifications.

**Database Table (actual stored data):**
```python
class Project(ProjectBase, table=True):
    id: uuid.UUID = Field(default_factory=uuid.uuid4, primary_key=True)
    owner_id: uuid.UUID = Field(
        foreign_key="user.id", nullable=False, ondelete="CASCADE"
    )
    owner: User | None = Relationship(back_populates="projects")
```

The `table=True` parameter creates the actual database table. The `owner_id` foreign key links projects to users, and `ondelete="CASCADE"` ensures projects are deleted when their owner is deleted.

**Public Response (what the API returns):**
```python
class ProjectPublic(ProjectBase):
    id: uuid.UUID
    owner_id: uuid.UUID

class ProjectsPublic(SQLModel):
    data: list[ProjectPublic]
    count: int
```

These define the structure of API responses. `ProjectsPublic` wraps multiple projects with a count for pagination.

### Update User Model

Add the relationship to the User model so users can access their projects:

```python
class User(UserBase, table=True):
    id: uuid.UUID = Field(default_factory=uuid.uuid4, primary_key=True)
    hashed_password: str
    items: list["Item"] = Relationship(back_populates="owner", cascade_delete=True)
    projects: list["Project"] = Relationship(back_populates="owner", cascade_delete=True)
```

## Step 3: Build API Endpoints

API endpoints handle data operations and enforce security rules.

### Create the Router File

Create a new file for your project routes following the items pattern:

**List All Projects (with pagination):**
```python
@router.get("/", response_model=ProjectsPublic)
def read_projects(
    session: SessionDep, current_user: CurrentUser, skip: int = 0, limit: int = 100
) -> Any:
    """
    Retrieve projects.
    """
    if current_user.is_superuser:
        count_statement = select(func.count()).select_from(Project)
        count = session.exec(count_statement).one()
        statement = select(Project).offset(skip).limit(limit)
        projects = session.exec(statement).all()
    else:
        count_statement = (
            select(func.count())
            .select_from(Project)
            .where(Project.owner_id == current_user.id)
        )
        count = session.exec(count_statement).one()
        statement = (
            select(Project)
            .where(Project.owner_id == current_user.id)
            .offset(skip)
            .limit(limit)
        )
        projects = session.exec(statement).all()
    
    return ProjectsPublic(data=projects, count=count)
```

This endpoint shows different data based on permissions: superusers see everything, regular users see only their own projects. The `skip` and `limit` parameters enable pagination.

**Get Single Project:**
```python
@router.get("/{id}", response_model=ProjectPublic)
def read_project(session: SessionDep, current_user: CurrentUser, id: uuid.UUID) -> Any:
    """
    Get project by ID.
    """
    project = session.get(Project, id)
    if not project:
        raise HTTPException(status_code=404, detail="Project not found")
    if not current_user.is_superuser and (project.owner_id != current_user.id):
        raise HTTPException(status_code=400, detail="Not enough permissions")
    return project
```

This retrieves a specific project and verifies the user has permission to view it.

**Create New Project:**
```python
@router.post("/", response_model=ProjectPublic)
def create_project(
    *, session: SessionDep, current_user: CurrentUser, project_in: ProjectCreate
) -> Any:
    """
    Create new project.
    """
    project = Project.model_validate(project_in, update={"owner_id": current_user.id})
    session.add(project)
    session.commit()
    session.refresh(project)
    return project
```

The `model_validate` method converts the input data to a database object while automatically setting the current user as the owner.

**Update Existing Project:**
```python
@router.put("/{id}", response_model=ProjectPublic)
def update_project(
    *,
    session: SessionDep,
    current_user: CurrentUser,
    id: uuid.UUID,
    project_in: ProjectUpdate,
) -> Any:
    """
    Update a project.
    """
    project = session.get(Project, id)
    if not project:
        raise HTTPException(status_code=404, detail="Project not found")
    if not current_user.is_superuser and (project.owner_id != current_user.id):
        raise HTTPException(status_code=400, detail="Not enough permissions")
    update_dict = project_in.model_dump(exclude_unset=True)
    project.sqlmodel_update(update_dict)
    session.add(project)
    session.commit()
    session.refresh(project)
    return project
```

The `exclude_unset=True` option ensures only provided fields are updated, leaving others unchanged.

**Delete Project:**
```python
@router.delete("/{id}")
def delete_project(
    session: SessionDep, current_user: CurrentUser, id: uuid.UUID
) -> Message:
    """
    Delete a project.
    """
    project = session.get(Project, id)
    if not project:
        raise HTTPException(status_code=404, detail="Project not found")
    if not current_user.is_superuser and (project.owner_id != current_user.id):
        raise HTTPException(status_code=400, detail="Not enough permissions")
    session.delete(project)
    session.commit()
    return Message(message="Project deleted successfully")
```

### Register the Router

Add your router to the main API configuration:

```python
router = APIRouter(prefix="/projects", tags=["projects"])
```

Then include it in your application's router registry so the endpoints become accessible.

## Step 4: Build the Frontend Interface

The frontend provides users with an interface to interact with your feature.

### Create the Projects Page

Following the items page structure, create a new page file:

**Set Up Page Configuration:**
```typescript
const projectsSearchSchema = z.object({
  page: z.number().catch(1),
})

const PER_PAGE = 5

function getProjectsQueryOptions({ page }: { page: number }) {
  return {
    queryFn: () =>
      ProjectsService.readProjects({ skip: (page - 1) * PER_PAGE, limit: PER_PAGE }),
    queryKey: ["projects", { page }],
  }
}
```

This sets up pagination with 5 projects per page and configures data fetching.

**Create the Projects Table:**
```typescript
function ProjectsTable() {
  const navigate = useNavigate({ from: Route.fullPath })
  const { page } = Route.useSearch()

  const { data, isLoading, isPlaceholderData } = useQuery({
    ...getProjectsQueryOptions({ page }),
    placeholderData: (prevData) => prevData,
  })

  const setPage = (page: number) =>
    navigate({
      search: (prev: { [key: string]: string }) => ({ ...prev, page }),
    })

  const projects = data?.data.slice(0, PER_PAGE) ?? []
  const count = data?.count ?? 0

  if (isLoading) {
    return <PendingProjects />
  }

  if (projects.length === 0) {
    return (
      <EmptyState.Root>
        <EmptyState.Content>
          <EmptyState.Indicator>
            <FiSearch />
          </EmptyState.Indicator>
          <VStack textAlign="center">
            <EmptyState.Title>You don't have any projects yet</EmptyState.Title>
            <EmptyState.Description>
              Add a new project to get started
            </EmptyState.Description>
          </VStack>
        </EmptyState.Content>
      </EmptyState.Root>
    )
  }

  return (
    <>
      <Table.Root size={{ base: "sm", md: "md" }}>
        <Table.Header>
          <Table.Row>
            <Table.ColumnHeader w="sm">Name</Table.ColumnHeader>
            <Table.ColumnHeader w="sm">Description</Table.ColumnHeader>
            <Table.ColumnHeader w="sm">Due Date</Table.ColumnHeader>
            <Table.ColumnHeader w="sm">Actions</Table.ColumnHeader>
          </Table.Row>
        </Table.Header>
        <Table.Body>
          {projects?.map((project) => (
            <Table.Row key={project.id} opacity={isPlaceholderData ? 0.5 : 1}>
              <Table.Cell truncate maxW="sm">
                {project.name}
              </Table.Cell>
              <Table.Cell
                color={!project.description ? "gray" : "inherit"}
                truncate
                maxW="30%"
              >
                {project.description || "N/A"}
              </Table.Cell>
              <Table.Cell truncate maxW="sm">
                {project.due_date || "No deadline"}
              </Table.Cell>
              <Table.Cell>
                <ProjectActionsMenu project={project} />
              </Table.Cell>
            </Table.Row>
          ))}
        </Table.Body>
      </Table.Root>
      <Flex justifyContent="flex-end" mt={4}>
        <PaginationRoot
          count={count}
          pageSize={PER_PAGE}
          onPageChange={({ page }) => setPage(page)}
        >
          <Flex>
            <PaginationPrevTrigger />
            <PaginationItems />
            <PaginationNextTrigger />
          </Flex>
        </PaginationRoot>
      </Flex>
    </>
  )
}
```

The table shows loading states, empty states, and handles pagination automatically. The `isPlaceholderData` check provides visual feedback during page transitions.

**Create the Main Component:**
```typescript
function Projects() {
  return (
    <Container maxW="full">
      <Heading size="lg" pt={12}>
        Projects Management
      </Heading>
      <AddProject />
      <ProjectsTable />
    </Container>
  )
}
```

### Create Action Components

**Add Project Form:**

Create a form component that allows users to create new projects. Use form validation to ensure the name field is required and the due date follows a valid format.

**Edit Project Modal:**

Build a modal that loads existing project data and allows modifications. Pre-populate all fields with current values and mark optional fields clearly.

**Actions Menu:**

Create a menu component with Edit and Delete options. The Delete action should show a confirmation dialog to prevent accidental deletions.

## Step 5: Implement Complete CRUD Operations

### Create Operation

The create operation combines frontend form submission with backend processing:

1. User fills out the form with project details
2. Form validates all fields before submission
3. Data is sent to the POST endpoint
4. Backend validates data and checks permissions
5. Project is saved with the current user as owner
6. Success message appears and the list refreshes

### Read Operations

**List View:**
- Fetches paginated projects from the GET endpoint
- Filters by owner (unless superuser)
- Displays in a table with sorting options
- Shows empty state when no projects exist

**Detail View:**
- Retrieves specific project by ID from the GET /{id} endpoint
- Verifies user has permission to view
- Returns 404 if project doesn't exist
- Returns 400 if user lacks permissions

### Update Operation

The update flow allows partial modifications:

1. User clicks Edit on a project
2. Modal opens with current values pre-filled
3. User changes desired fields
4. Form submits only modified fields to PUT endpoint
5. Backend validates ownership and data
6. Changes are saved and reflected immediately

### Delete Operation

The delete operation ensures data safety:

1. User clicks Delete from actions menu
2. Confirmation dialog appears
3. Upon confirmation, DELETE request sent
4. Backend verifies ownership
5. Project is removed from database
6. List refreshes to show updated data

## Step 6: Test Your Feature

### Backend Testing

**Test API Endpoints:**

Test each endpoint using the interactive API documentation (typically available at `/docs`):

1. **Create:** Submit valid project data and verify it appears in responses
2. **List:** Check pagination works and filtering respects ownership
3. **Get:** Retrieve specific projects and verify permission checks
4. **Update:** Modify fields and confirm changes persist
5. **Delete:** Remove projects and verify they're gone

**Test Permissions:**

1. Create projects as a regular user
2. Verify you can only see your own projects
3. Try accessing another user's project (should fail)
4. Test as superuser and verify you can see all projects

**Test Validation:**

1. Try creating a project without a name (should fail)
2. Submit overly long field values (should be truncated or rejected)
3. Test with optional fields empty (should succeed)

### Frontend Testing

**Test User Interface:**

1. Navigate to the Projects page
2. Verify the empty state appears when no projects exist
3. Add a new project and confirm it appears in the list
4. Test pagination by creating multiple projects
5. Edit a project and verify changes appear immediately
6. Delete a project and confirm it's removed

**Test Error Handling:**

1. Submit a form with invalid data
2. Verify appropriate error messages appear
3. Try actions without proper permissions
4. Test with poor network conditions

## Step 7: Follow Template Conventions

### Code Organization

**Backend Structure:**
- Models in the models file, grouped by feature
- Routes in separate files under the routes directory
- Shared utilities in dedicated modules
- Database operations use SQLModel patterns

**Frontend Structure:**
- Page components in the routes directory
- Reusable components in the components directory
- API clients generated from OpenAPI specification
- State management using React Query

### Naming Conventions

**Follow these patterns throughout:**
- Models: `ProjectBase`, `ProjectCreate`, `ProjectUpdate`, `Project`, `ProjectPublic`
- Endpoints: `/projects`, `/projects/{id}`
- Components: `AddProject`, `EditProject`, `ProjectsTable`, `ProjectActionsMenu`
- Functions: `create_project`, `read_projects`, `update_project`, `delete_project`

### Security Patterns

**Always enforce these rules:**
- Check user authentication on all endpoints
- Verify ownership before allowing modifications
- Use UUID for all identifiers (prevents enumeration)
- Sanitize user input through model validation
- Apply CASCADE delete for dependent records

### Data Patterns

**Maintain consistency:**
- Use nullable fields with defaults for optional data
- Set min/max lengths on string fields
- Return consistent response structures (data + count for lists)
- Use proper HTTP status codes (404 for not found, 400 for permissions)

## Step 8: Deployment Considerations

### Database Migration

When deploying your new feature, the database needs updating:

1. **Generate Migration:** Create a migration script that adds the projects table
2. **Test Migration:** Run migration on a test database first
3. **Backup Data:** Always backup production data before migrating
4. **Apply Migration:** Run migration on production during low-traffic period
5. **Verify Schema:** Confirm the new table exists with correct structure

The migration should include:
- Creating the projects table with all fields
- Adding the foreign key to users table
- Creating indexes on frequently queried fields (owner_id)

### API Documentation

Your new endpoints automatically appear in the API documentation:

1. The OpenAPI schema updates to include project endpoints
2. Interactive documentation shows all available operations
3. Frontend API client regenerates with new methods
4. Type definitions update automatically

### Frontend Build

The frontend build process handles your new feature:

1. TypeScript compiler checks all types
2. Build creates optimized production bundles
3. New routes are included in the routing configuration
4. Static assets are properly hashed for caching

### Environment Variables

If your feature needs configuration:

1. Add variables to environment file templates
2. Document what each variable controls
3. Set appropriate defaults for development
4. Ensure production values are configured securely

### Monitoring

After deployment, monitor your feature:

1. Check API endpoint response times
2. Monitor database query performance
3. Track error rates in logging systems
4. Watch for authentication/permission errors
5. Verify pagination works with large datasets

## Common Patterns for Other Features

You can adapt this approach for many feature types:

**Task Management:**
- Add status field (todo, in_progress, done)
- Add priority field with enum validation
- Include timestamps for created/modified dates

**Comments/Notes:**
- Keep simple with just text content
- Add parent_id for threading
- Include soft delete (is_deleted flag)

**Tags/Categories:**
- Create many-to-many relationships
- Use junction tables for associations
- Implement filtering by tag

**File Attachments:**
- Store file metadata in database
- Keep actual files in object storage
- Track file size and MIME type

## Troubleshooting

**Database errors:**
- Verify migrations ran successfully
- Check foreign key constraints are satisfied
- Ensure cascade rules are correct

**Permission errors:**
- Confirm owner_id is set on creation
- Verify current_user is passed correctly
- Check superuser flag for admin features

**Frontend not showing data:**
- Verify API client regenerated after backend changes
- Check browser console for network errors
- Confirm query keys match between cache and requests

**Validation failures:**
- Review Field constraints in models
- Test with various input combinations
- Check for missing required fields

## Next Steps

With your custom feature complete, you can:

1. **Add advanced filtering:** Implement search and filter options
2. **Create relationships:** Link projects to other features
3. **Add bulk operations:** Enable multi-select and batch actions
4. **Implement webhooks:** Notify external systems of changes
5. **Add analytics:** Track feature usage and patterns
6. **Create exports:** Allow users to download their data

This tutorial demonstrated the complete workflow using the template's established patterns. Apply these same principles to build any feature your application needs.