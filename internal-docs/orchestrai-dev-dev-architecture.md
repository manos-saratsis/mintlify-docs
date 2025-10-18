# orchestrai-dev - Architecture Documentation

## Overview

OrchestrAI-dev is a React-based web application that provides AI-powered code quality, testing, compliance, and documentation capabilities for software development teams. The application is built with TypeScript, React, and integrates with Supabase for backend services, GitHub for repository management, and various AI services for intelligent code analysis and documentation generation.

The architecture follows a modern component-based approach with clear separation of concerns, utilizing React Context for state management, React Query for data fetching, and React Router for navigation.

## Project Structure

### Root Configuration Files

**`eslint.config.js`** - ESLint configuration using flat config format:
- Uses `@eslint/js`, `typescript-eslint`, and React plugins
- Configures browser globals with ECMAScript 2020
- Disables `@typescript-eslint/no-unused-vars` rule
- Ignores `dist` directory
- Includes React Hooks and React Refresh plugins for development

**`postcss.config.js`** - PostCSS configuration:
- Integrates TailwindCSS for utility-first styling
- Includes Autoprefixer for cross-browser CSS compatibility

### Application Entry Point

**`src/App.tsx`** - Main application component that orchestrates the entire application:

```typescript
function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <TooltipProvider>
        <Toaster />
        <Sonner />
        <BrowserRouter>
          <AuthProvider>
            <WorkspaceProvider>
              <AppContent />
            </WorkspaceProvider>
          </AuthProvider>
        </BrowserRouter>
      </TooltipProvider>
    </QueryClientProvider>
  );
}
```

**Key architectural patterns implemented:**
1. **Provider Hierarchy**: Wraps application in QueryClientProvider → BrowserRouter → AuthProvider → WorkspaceProvider
2. **Toast Notifications**: Dual toast system using both Toaster and Sonner components
3. **Tooltip System**: Global TooltipProvider for consistent tooltip behavior
4. **Welcome Modal**: Implements first-time user onboarding with `useWelcomeModal` hook

### Routing Architecture

**Route Structure** (`src/App.tsx` lines 42-73):

```typescript
<Routes>
  {/* Landing & Enterprise */}
  <Route path="/" element={<Index />} />
  <Route path="/enterprise" element={<Enterprise />} />
  
  {/* Mission & Organization */}
  <Route path="/mission" element={<Mission />} />
  <Route path="/organization-mission" element={<OrganizationMission />} />
  
  {/* Product Pages */}
  <Route path="/product" element={<Product />} />
  <Route path="/product/code" element={<ProductCode />} />
  <Route path="/product/code-connected" element={<ProductCodeConnected />} />
  <Route path="/product/testing" element={<ProductTesting />} />
  <Route path="/product/code-quality" element={<ProductCodeQuality />} />
  <Route path="/product/code-quality/results" element={<ProductCodeQualityResults />} />
  <Route path="/product/workflow" element={<ProductWorkflow />} />
  <Route path="/product/documentation" element={<ProductDocumentation />} />
  <Route path="/product/compliance" element={<ProductCompliance />} />
  <Route path="/product/compliance/results" element={<ProductComplianceResults />} />
  <Route path="/product/workspace-management" element={<ProductWorkspaceManagement />} />
  <Route path="/product/permissions" element={<ProductPermissions />} />
  
  {/* Functional Pages */}
  <Route path="/code-analysis" element={<CodeAnalysis />} />
  <Route path="/testing" element={<Testing />} />
  <Route path="/workspace-management" element={<WorkspaceManagement />} />
  <Route path="/account" element={<Account />} />
  <Route path="/cost-analysis/:workspaceId" element={<CostAnalysis />} />
  
  {/* OAuth & Legal */}
  <Route path="/github-success" element={<GitHubSuccess />} />
  <Route path="/github-error" element={<GitHubError />} />
  <Route path="/privacy" element={<PrivacyPolicy />} />
  <Route path="/terms" element={<TermsOfService />} />
  
  {/* Fallback */}
  <Route path="*" element={<NotFound />} />
</Routes>
```

**Route Categories:**
1. **Landing Pages**: `/`, `/enterprise`, `/pricing`
2. **Product Feature Routes**: `/product/*` - Main application features
3. **Functional Routes**: `/code-analysis`, `/testing`, `/workspace-management`
4. **Account Management**: `/account`, `/cost-analysis/:workspaceId`
5. **OAuth Callbacks**: `/github-success`, `/github-error`
6. **Legal**: `/privacy`, `/terms`

### State Management Architecture

**1. Authentication Context** (`AuthProvider` in `src/contexts/AuthContext`):
- Manages user authentication state
- Wraps entire application after routing setup
- Provides authentication methods and user data to all components

**2. Workspace Context** (`WorkspaceProvider` in `src/contexts/WorkspaceContext`):
- Located at `src/contexts/WorkspaceContext.tsx`
- Manages current workspace selection and workspace-related data
- Nested within AuthProvider for access to user authentication
- Provides `currentWorkspace` state used throughout the application

**3. React Query Client** (lines 29):
```typescript
const queryClient = new QueryClient();
```
- Manages server state and caching
- Used for data fetching and mutations
- Configured at application root level

### Key Component Patterns

**1. AI Compliance Analyst Panel** (`src/components/AIComplianceAnalystPanel.tsx`):

**Purpose**: Provides interface for running compliance analysis on repositories

**Key Features**:
- Permission-based access control using `useWorkspaceFunctionPermissions` hook
- Workflow configuration checking via `workflowService.getWorkflowConfiguration`
- Integration with Supabase edge function `code-compliance-analyzer`
- Progress tracking with `ComplianceProgressDialog`
- Checkpoint/resume capability for long-running analyses

**Implementation Details**:
```typescript
interface AIComplianceAnalystPanelProps {
  repository: Repository;
  isOpen: boolean;
  onClose: () => void;
  onAnalysisComplete?: (analysisId: string) => void;
}
```

**State Management** (lines 23-35):
- `isComplianceAllowed`: Workflow configuration check
- `analysisInProgress`: Tracks analysis execution state
- `analysisProgress`: Numeric progress (0-100)
- `showProgressDialog`: Controls progress dialog visibility
- Permission checking with `hasPermission` and `isFreePlan` flags

**Workflow Configuration Check** (lines 37-51):
```typescript
const checkWorkflowConfiguration = async () => {
  const config = await workflowService.getWorkflowConfiguration(
    currentWorkspace.id, 
    'Compliance'
  );
  const isAllowed = config && 
    (config.enablement === 'analysis_only' || 
     config.enablement === 'analysis_and_fix');
  setIsComplianceAllowed(isAllowed);
};
```

**Analysis Execution** (lines 53-75):
```typescript
const handleStartAnalysis = async () => {
  const { data, error } = await supabase.functions.invoke(
    'code-compliance-analyzer', 
    {
      body: {
        repository_id: repository.id,
        repository_name: repository.name,
        workspaceId: currentWorkspace.id,
        instructions: instructions
      }
    }
  );
  return { success: data?.success, analysisId: data?.analysis_id };
};
```

**2. AI Documentation Specialist Panel** (`src/components/AIDocumentationSpecialistPanel.tsx`):

**Purpose**: Manages documentation generation and migration with granular control over scope and content structure

**Key Features**:
- Dual mode operation: 'migrate' (restructure existing) or 'create' (generate new)
- Advanced scope selection: User-facing, Internal developer, SBOM
- Content structure customization with 7 content types
- Repository scope selection (full repo or specific commit)
- Checkpoint/resume support for interrupted executions
- Real-time commit fetching from GitHub API

**Implementation Details**:
```typescript
interface AIDocumentationSpecialistPanelProps {
  isOpen: boolean;
  onClose: () => void;
  action: 'migrate' | 'create';
  hasDocumentationUrl: boolean;
  resumeExecution?: any;
  onComplete?: (result: { success: boolean; error?: string }) => void;
}
```

**State Management** (lines 24-53):
```typescript
const [selectedScopes, setSelectedScopes] = useState({
  userFacing: true,
  internal: true,
  sbom: true,
});

const [selectedContentStructure, setSelectedContentStructure] = useState({
  intro: true,
  tutorials: true,
  howTo: false,
  reference: true,
  concepts: false,
  troubleshooting: false,
  releaseNotes: false,
});

const [repositoryScopes, setRepositoryScopes] = useState<
  Record<string, { scope: 'full' | 'commit'; commitSha?: string }>
>({});
```

**Checkpoint Data Loading** (lines 61-100):
```typescript
const loadCheckpointData = async () => {
  const { data: checkpoint } = await supabase
    .from('function_checkpoints')
    .select('checkpoint_data')
    .eq('execution_id', resumeExecution.id)
    .eq('execution_type', 'documentation')
    .single();
    
  if (checkpoint?.checkpoint_data) {
    // Restore scope configuration
    setSelectedScopes({
      userFacing: scopes.includes('user_facing'),
      internal: scopes.includes('internal_developer'),
      sbom: scopes.includes('sbom'),
    });
    
    // Restore repository selection
    setSelectedRepositories(repos.map(r => r.fullName));
    setRepositoryScopes(/* ... */);
  }
};
```

**Repository & Commit Management** (lines 135-195):
```typescript
const loadCommitsForRepository = async (repoFullName: string) => {
  // Fetch GitHub access token
  const { data: connection } = await supabase
    .from('git_connections')
    .select('access_token, vault_secret_id')
    .eq('id', repo.git_connection_id)
    .single();

  // Fetch commits from GitHub API
  const response = await fetch(
    `https://api.github.com/repos/${repoFullName}/commits?per_page=20`,
    {
      headers: {
        'Authorization': `token ${accessToken}`,
        'Accept': 'application/vnd.github.v3+json',
      }
    }
  );
  
  const commits = await response.json();
  setRepositoryCommits(prev => ({ 
    ...prev, 
    [repoFullName]: formattedCommits 
  }));
};
```

**UI Components Hierarchy**:

1. **Header** (lines 232-246):
   - Bot icon with purple theme (`text-purple-600`)
   - "AI Documentation Specialist" title
   - Close button

2. **Alert Sections** (lines 250-268):
   - Resume checkpoint indicator (green theme)
   - Action type info card (purple theme)
   - Migration warning (amber theme when no URL)
   - Configuration required alert (amber theme)

3. **Instructions Section** (lines 299-313):
   - Priority badge indicating override behavior
   - Textarea for custom instructions
   - Default: "Analyze existing documentation..." or "Create comprehensive documentation..."
   - Muted text explaining priority over default config

4. **Advanced Options - Collapsible** (lines 316-464):
   - **Scope Selection**:
     - User Facing (checkbox)
       - Nested Content Structure (7 sub-options):
         - `/intro` (positioned Quickstart)
         - `/tutorials` (end-to-end, outcome-driven)
         - `/how-to` (task-centric, short)
         - `/reference` (API/SDK; autogenerated)
         - `/concepts` (architecture, models, quotas)
         - `/troubleshooting` (error catalog, logs)
         - `/release-notes` (automated)
     - Internal Developer (checkbox)
     - SBOM - Software Bill of Materials (checkbox)

5. **Repository Selector - Collapsible** (lines 467-600):
   - Lists OrchestrAI-enabled repositories
   - Select All / Deselect All button
   - Per-repository options:
     - Checkbox for selection
     - "Whole Repo" vs "Specific Commit" buttons
     - Commit list with selection (when "Specific Commit" chosen)
   - Commit details: message, SHA (7 chars), date

6. **Configuration Display** (lines 603-634):
   - Shows workspace documentation settings
   - Repository name (handles old string format and new object format)
   - Folder path
   - Content structure name

7. **How It Works Card** (lines 637-651):
   - Blue-themed informational card
   - Steps: Product Analysis → Documentation Review (migrate only) → Structured Generation → Code Deployment

8. **Footer Button** (lines 656-687):
   - Purple "Generate Documentation" button
   - Disabled states:
     - No configuration
     - No scope selected
     - Migration without URL
     - Loading states
   - Play icon on active state
   - Spinner animation during execution

**Collapsible Patterns** (lines 316-464, 467-600):
```typescript
<Collapsible open={isAdvancedExpanded} onOpenChange={setIsAdvancedExpanded}>
  <CollapsibleTrigger asChild>
    <div className="flex items-center justify-between cursor-pointer">
      <CardTitle>
        <Settings className="h-4 w-4" />
        <span>Customize Scope & Content Structure</span>
      </CardTitle>
      {isAdvancedExpanded ? <ChevronDown /> : <ChevronRight />}
    </div>
  </CollapsibleTrigger>
  <CollapsibleContent>
    {/* Content here */}
  </CollapsibleContent>
</Collapsible>
```

**Badge Usage** (line 477):
```typescript
{selectedRepositories.length > 0 && (
  <Badge variant="secondary">{selectedRepositories.length} selected</Badge>
)}
```

**Validation Logic** (lines 198-210):
```typescript
const startDocumentation = () => {
  if (selectedRepositories.length === 0 && availableRepositories.length > 0) {
    toast({
      title: "Repository Selection Required",
      description: "Please select at least one repository...",
      variant: "destructive",
    });
    return;
  }
  setShowProgressDialog(true);
};
```

### Hooks Architecture

**1. useWelcomeModal** (`src/hooks/useWelcomeModal`):
- Manages first-time user experience
- Returns `{ showWelcomeModal, handleWelcomeComplete }`
- Used in AppContent component (lines 32-34)

**2. useWorkspaceFunctionPermissions** (AIComplianceAnalystPanel.tsx line 21):
```typescript
const { 
  hasPermission, 
  isLoading: permissionLoading, 
  isFreePlan 
} = useWorkspaceFunctionPermissions('Compliance');
```
- Checks user permissions for specific workspace functions
- Returns loading state and plan type
- Function-specific permission checking ('Compliance', 'Documentation', etc.)

### Service Layer Architecture

**1. workflowService** (`src/services/workflowService`):

Used in AIComplianceAnalystPanel.tsx (line 44):
```typescript
const config = await workflowService.getWorkflowConfiguration(
  currentWorkspace.id, 
  'Compliance'
);
```

Used in AIDocumentationSpecialistPanel.tsx (lines 106-108):
```typescript
const configs = await workflowService.getWorkflowConfigurations(
  currentWorkspace.id
);
const config = configs.find(c => c.function_name === 'Documentation');
```

**Methods:**
- `getWorkflowConfiguration(workspaceId, functionName)`: Fetches single function config
- `getWorkflowConfigurations(workspaceId)`: Fetches all workflow configs for workspace

**Configuration Structure:**
```typescript
{
  function_name: 'Compliance' | 'Documentation',
  enablement: 'analysis_only' | 'analysis_and_fix' | 'disabled',
  configuration: {
    repo?: { name: string, full_name: string, id: number },
    folder?: string,
    contentStructure?: { name: string }
  }
}
```

### Supabase Integration

**Edge Function Invocation Pattern** (AIComplianceAnalystPanel.tsx lines 60-72):
```typescript
const { data, error } = await supabase.functions.invoke(
  'code-compliance-analyzer',
  {
    body: {
      repository_id: repository.id,
      repository_name: repository.name,
      repository_full_name: repository.full_name,
      repository_url: repository.html_url,
      workspaceId: currentWorkspace.id,
      instructions: instructions
    }
  }
);
```

**Database Query Pattern** (AIDocumentationSpecialistPanel.tsx lines 66-75):
```typescript
const { data: checkpoint, error } = await supabase
  .from('function_checkpoints')
  .select('checkpoint_data')
  .eq('execution_id', resumeExecution.id)
  .eq('execution_type', 'documentation')
  .order('created_at', { ascending: false })
  .limit(1)
  .single();
```

**Tables Referenced:**
1. `function_checkpoints`: Stores execution state for resume capability
2. `repository_settings`: Stores repository configuration and enablement flags
3. `git_connections`: Stores GitHub OAuth tokens and workspace associations

### UI Component Library

**shadcn/ui Components Used:**

1. **Toast System**:
   - `Toaster` from `@/components/ui/toaster`
   - `Sonner` from `@/components/ui/sonner`
   - `useToast` hook for programmatic toasts

2. **Form Components**:
   - `Button` with variants: default, ghost, outline
   - `Label` for form labels
   - `Textarea` for multi-line input
   - `Checkbox` for boolean selections

3. **Layout Components**:
   - `Card`, `CardContent`, `CardHeader`, `CardTitle`
   - `Alert`, `AlertDescription`
   - `Progress` for progress bars
   - `Badge` for status indicators
   - `Collapsible`, `CollapsibleContent`, `CollapsibleTrigger`

4. **Utility Components**:
   - `TooltipProvider` for global tooltip support

### Icon System

**Lucide React Icons Used:**
- `X`: Close buttons
- `Bot`: AI feature indicators
- `FileText`: Documentation-related features
- `AlertCircle`: Warning messages
- `ExternalLink`: External navigation
- `Settings`: Configuration sections
- `Shield`: Permission/security indicators
- `CheckCircle`: Success states
- `Clock`: In-progress states
- `Play`: Action initiation
- `ChevronDown`, `ChevronRight`: Collapsible indicators
- `GitBranch`: Repository-related features

### CSS Architecture

**Tailwind CSS Utility Patterns:**

1. **Layout**:
   - `fixed inset-y-0 right-0`: Slide-in panels
   - `flex flex-col`: Vertical flex containers
   - `space-y-N`: Vertical spacing
   - `border-N`: Border styling

2. **Color System**:
   - Purple theme: `bg-purple-600`, `text-purple-600`, `border-purple-200`
   - Amber theme: `bg-amber-50`, `text-amber-700`, `border-amber-200`
   - Green theme: `bg-green-50`, `text-green-700`, `border-green-200`
   - Red theme: `bg-red-50`, `text-red-700`, `border-red-200`
   - Blue theme: `bg-blue-50`, `text-blue-900`, `border-blue-200`

3. **Responsive Design**:
   - `w-96`: Fixed width panels
   - `min-h-[100px]`: Minimum heights
   - `max-h-96`: Maximum heights with overflow
   - `overflow-y-auto`: Scrollable areas

4. **Interactive States**:
   - `hover:bg-purple-700`: Hover effects
   - `cursor-not-allowed`: Disabled states
   - `cursor-pointer`: Clickable elements

### Testing Infrastructure

**Test Files Located in `orchestrai_tests/` Directory:**

**1. Configuration Tests:**
- `eslint.config.test.js`: Validates ESLint configuration structure
- `postcss.config.test.js`: Validates PostCSS plugin configuration

**2. Component Tests:**
- `App.test.tsx`: Tests main App component rendering and navigation
- `AIQualityEngineerPanel.test.tsx`: Tests AI quality analysis panel
- `AITestEngineerPanel.test.tsx`: Tests AI test generation panel
- `CodePageContent.test.tsx`: Tests code page content rendering

**Test Patterns Used:**
```typescript
// Mock child components
jest.mock('../../src/components/AIQualityEngineerPanel', () => {
  return function MockAIQualityEngineerPanel() {
    return <div data-testid="ai-quality-engineer-panel">
      AI Quality Engineer Panel
    </div>;
  };
});

// Render with BrowserRouter
const renderApp = () => {
  return render(
    <BrowserRouter>
      <App />
    </BrowserRouter>
  );
};
```

**Test Coverage Areas:**
1. Component rendering without crashes
2. Navigation functionality
3. Theme switching
4. Responsive layout
5. Error boundary handling
6. Loading states
7. User interactions (button clicks, form inputs)
8. API call mocking

### TypeScript Configuration

**Type Definitions Used:**

1. **Repository Type** (AIComplianceAnalystPanel.tsx line 12):
```typescript
import type { Repository } from "@/types/github";

interface AIComplianceAnalystPanelProps {
  repository: Repository;
  // ...
}
```

2. **Component Props Interfaces**:
- Explicit props interfaces for all major components
- Optional props marked with `?`
- Callback function type definitions

### Permission System

**Permission Check Pattern** (AIComplianceAnalystPanel.tsx lines 19-21, 121-125):
```typescript
const { hasPermission, isLoading, isFreePlan } = 
  useWorkspaceFunctionPermissions('Compliance');

const showPermissionRestriction = 
  !isFreePlan && !hasPermission && !isLoading;
```

**Permission-Based UI:**
1. Alert shown for restricted paid users (lines 135-143)
2. Button disabled when no permission (lines 264-265)
3. Different behavior for free plan users (full access)

### Error Handling Patterns

**1. Try-Catch with Toast Notifications:**
```typescript
try {
  const result = await someDatabaseOperation();
  // Success handling
} catch (error) {
  console.error('Operation failed:', error);
  toast({
    title: "Operation Failed",
    description: error.message,
    variant: "destructive",
  });
}
```

**2. Supabase Error Handling:**
```typescript
const { data, error } = await supabase.functions.invoke('function-name', {
  body: { /* ... */ }
});

if (error) {
  console.error('Error:', error);
  return { success: false, error: error.message };
}
```

**3. Error State Management:**
```typescript
const [hasError, setHasError] = useState(false);

if (result.error) {
  setHasError(true);
  // Show error UI
}
```

### Progress Tracking Pattern

**Used in both Compliance and Documentation panels:**

1. **Progress Dialog Component:**
   - `ComplianceProgressDialog` (AIComplianceAnalystPanel.tsx line 163)
   - `DocumentationProgressDialog` (AIDocumentationSpecialistPanel.tsx line 689)

2. **Progress States:**
```typescript
const [analysisInProgress, setAnalysisInProgress] = useState(false);
const [analysisProgress, setAnalysisProgress] = useState(0);
const [analysisComplete, setAnalysisComplete] = useState(false);
const [showProgressDialog, setShowProgressDialog] = useState(false);
```

3. **Completion Handler:**
```typescript
const handleProgressComplete = (result: { 
  success: boolean; 
  analysisId?: string; 
  error?: string 
}) => {
  setShowProgressDialog(false);
  
  if (result.success) {
    setAnalysisComplete(true);
    // Success handling
  } else {
    setHasError(true);
    // Error handling
  }
};
```

### Data Flow Architecture

**1. Top-Down Data Flow:**
```
App (QueryClient, Auth, Workspace)
  ↓
Pages (Route Components)
  ↓
Feature Panels (AIComplianceAnalystPanel, AIDocumentationSpecialistPanel)
  ↓
Progress Dialogs
  ↓
Edge Functions (Supabase)
```

**2. Context Consumer Pattern:**
```typescript
const { currentWorkspace } = useWorkspace();
const { toast } = useToast();
```

Components consume context at any level without prop drilling.

**3. Callback Pattern:**
```typescript
interface PanelProps {
  onAnalysisComplete?: (analysisId: string) => void;
  onComplete?: (result: { success: boolean; error?: string }) => void;
}
```

Parent components receive results through callback functions.

### Deployment Configuration

**Build Output:**
- Target directory: `dist/` (ignored in ESLint config)
- Build tool: Vite (inferred from React + TypeScript setup)

**Browser Targets:**
- ECMAScript 2020 (from eslint.config.js line 10)
- Modern browser features expected

### Security Considerations

**1. Token Management:**
- GitHub tokens stored in Supabase `git_connections` table
- Vault integration for sensitive data (`vault_secret_id` field)
- Access tokens retrieved via Supabase function `vault-retrieve`

**2. Workspace Isolation:**
- All operations scoped to `currentWorkspace.id`
- Permission checks before operations
- Repository settings per workspace

**3. Environment Separation:**
- Production/development configuration through environment variables
- Separate OAuth flows (github-success/github-error routes)

## Key Architectural Decisions

1. **Supabase Edge Functions**: Server-side operations for AI analysis and code manipulation
2. **Context-Based State**: Auth and Workspace contexts for global state
3. **React Query**: Efficient data fetching and caching
4. **Component Composition**: Small, reusable components with clear responsibilities
5. **Type Safety**: TypeScript throughout for compile-time error detection
6. **Permission-Based Features**: Granular access control per workspace function
7. **Checkpoint/Resume**: Long-running operations can be resumed after interruption
8. **Progressive Disclosure**: Collapsible sections for advanced options
9. **Toast Notifications**: Consistent user feedback pattern
10. **Repository Scoping**: Flexible code analysis scope (full repo vs. specific commits)

## Navigation Flow

**Primary User Journeys:**

1. **New User**:
   - Land on `/` → WelcomeModal shown
   - Complete onboarding
   - Navigate to `/product` or `/workspace-management`

2. **Compliance Analysis**:
   - Navigate to `/product/compliance`
   - Select repository
   - Open AIComplianceAnalystPanel
   - Start analysis
   - View results at `/product/compliance/results`

3. **Documentation Generation**:
   - Navigate to `/product/documentation`
   - Configure workflow settings
   - Open AIDocumentationSpecialistPanel
   - Select action (migrate/create)
   - Configure scope and content structure
   - Generate documentation

4. **GitHub Integration**:
   - Connect GitHub account
   - OAuth flow redirects to `/github-success` or `/github-error`
   - Repository settings managed in workspace

## Development Workflow

**Running Tests:**
```bash
# Test files organized by date in orchestrai_tests/
# Example: orchestrai_tests/2025-08-24_08-38-11/
npm test  # or yarn test
```

**Linting:**
```bash
npm run lint  # Uses eslint.config.js
```

**Building:**
```bash
npm run build  # Outputs to dist/
```

## Dependencies Summary

**Core Libraries:**
- React + React DOM
- TypeScript
- React Router DOM
- TanStack React Query
- Supabase Client
- Lucide React (icons)
- shadcn/ui components

**Styling:**
- TailwindCSS
- PostCSS + Autoprefixer

**Development:**
- ESLint + TypeScript ESLint
- React Hooks linting
- React Refresh for HMR