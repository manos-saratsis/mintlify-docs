# Testing Strategy and Guidelines

## Overview

OrchestRAI's testing infrastructure is designed to generate comprehensive, AI-powered test suites for software repositories across multiple programming languages and frameworks. The testing strategy focuses on automated test generation, intelligent coverage analysis, and seamless integration with existing development workflows. The platform's AI Test Engineer analyzes codebases to create tailored test strategies, generate test files, and provide detailed coverage metrics.

## Implementation

### Test Generation Architecture

The testing system is implemented through several interconnected components that work together to analyze code, generate tests, and track progress.

#### AI Test Engineer Panel

**Location**: `src/components/AITestEngineerPanel.tsx`

The AI Test Engineer Panel serves as the primary interface for test generation. It provides users with configurable options for test coverage levels and custom instructions.

**Key Features**:
- **Coverage Level Selection**: Users can choose from three predefined coverage targets:
  - **100% Coverage**: Full test coverage including edge cases
  - **80% Coverage**: Focus on critical paths and main functionality
  - **60% Coverage**: Basic happy path testing

- **Custom Instructions**: A textarea allows users to provide specific testing requirements or constraints

**Component Structure**:
```typescript
interface AITestEngineerPanelProps {
  repositoryId: string;
  onClose: () => void;
}
```

The panel uses the `useState` hook to manage:
- `coverageLevel`: Selected coverage percentage (60, 80, or 100)
- `customInstructions`: User-provided testing instructions
- `showProgress`: Boolean to control progress dialog visibility
- `isAnalyzing`: Loading state during test generation

**Default Instructions**:
The panel provides intelligent default instructions based on the selected coverage level. These instructions are automatically generated when no custom instructions are provided.

#### Test Progress Tracking

**Location**: `src/components/TestProgressDialog.tsx`

The Test Progress Dialog provides real-time feedback during test generation, showing users detailed progress through multiple phases.

**Progress Phases**:
1. **Repository Analysis**: Initial code analysis and structure mapping
2. **Test Strategy Planning**: AI-driven test strategy formulation
3. **Test Case Generation**: Creation of individual test cases
4. **Test File Creation**: Writing test files to the repository
5. **Validation and Cleanup**: Final verification and optimization

**Implementation Details**:
```typescript
interface TestProgressDialogProps {
  open: boolean;
  repositoryName: string;
  onComplete: () => void;
}
```

The dialog uses `useState` to track:
- `currentStep`: Current phase number (1-5)
- `substeps`: Array of detailed substep descriptions
- `error`: Error state for failed operations
- `completed`: Boolean indicating successful completion

**Substep Management**:
The component maintains an array of substeps for each major phase, providing granular visibility into the test generation process. Substeps are updated using the `addSubstep` helper function, which appends new progress messages to the current phase.

**Error Handling**:
If an error occurs during test generation, the dialog displays the error message and provides options to retry or close. The error state is managed through the `error` state variable and displayed in a red alert box.

#### Test Coverage Data Management

**Location**: `src/hooks/useTestCoverage.ts`

The `useTestCoverage` hook manages test coverage data fetching and state management using TanStack Query.

**Hook Interface**:
```typescript
export function useTestCoverage(repositoryId: string) {
  return useQuery({
    queryKey: ['testCoverage', repositoryId],
    queryFn: () => fetchTestCoverage(repositoryId),
    enabled: !!repositoryId,
  });
}
```

**Data Structure**:
The hook fetches and caches test coverage information including:
- Overall coverage percentage
- File-by-file coverage breakdown
- Critical path coverage status
- Test execution results
- Generated test file locations

**Caching Strategy**:
TanStack Query automatically caches test coverage data using the `['testCoverage', repositoryId]` query key. This ensures efficient data retrieval and reduces redundant API calls.

### Test Generation Workflow

The complete test generation workflow follows a well-defined sequence:

#### Step 1: User Configuration

Users access the Testing page (`src/pages/Testing.tsx`) and select a repository from the table. The `AITestEngineerPanel` opens, allowing configuration of:
- Target coverage level (60%, 80%, or 100%)
- Custom testing instructions
- Framework preferences (inferred from repository)

#### Step 2: Analysis Initiation

When the user clicks "Apply" in the AI Test Engineer Panel:

1. The panel sets `isAnalyzing` to `true`, triggering a loading state
2. The `showProgress` state is set to `true`, opening the `TestProgressDialog`
3. The repository ID and configuration are passed to the test generation service

#### Step 3: Backend Processing

The test generation service (referenced in the codebase but implemented as a backend service) performs:

1. **Repository Cloning**: Fetches the repository from GitHub using stored OAuth credentials
2. **Code Analysis**: Analyzes file structure, dependencies, and existing tests
3. **Strategy Planning**: AI generates a comprehensive test strategy based on the code
4. **Test Generation**: Creates test files for identified components and functions
5. **Validation**: Verifies generated tests compile and follow best practices

#### Step 4: Progress Updates

The `TestProgressDialog` receives real-time updates through WebSocket or polling:
- Current step number updates (1-5)
- Substep descriptions append to the current phase
- Error messages display if issues occur
- Completion status triggers the `onComplete` callback

#### Step 5: Results Display

Upon completion:
1. The progress dialog closes
2. The Testing page refreshes test coverage data
3. Users can view generated test files and coverage metrics
4. Test results are cached for quick access

### Repository Management Integration

**Location**: `src/pages/Testing.tsx`

The Testing page integrates with the repository management system to display available repositories and their testing status.

**Key Components**:
- **WorkspaceLayout**: Provides consistent page layout with navigation
- **ProductSidebar**: Displays product navigation menu
- **TestingRepositoryTable**: Shows repository list with testing actions

**Table Features**:
The repository table displays:
- Repository name and visibility (public/private)
- Current test coverage percentage
- Latest test run date
- Action buttons for test generation

**Data Fetching**:
The page uses the `useTestCoverage` hook to fetch coverage data for each repository, displaying loading states and error messages as appropriate.

### Type Definitions

**Location**: `src/types/` (implied from TypeScript usage)

TypeScript interfaces ensure type safety throughout the testing system:

```typescript
interface Repository {
  id: string;
  name: string;
  full_name: string;
  visibility: 'public' | 'private';
  lastAnalyzed?: string;
  testCoverage?: number;
}

interface TestCoverageData {
  repositoryId: string;
  overallCoverage: number;
  fileCoverage: FileCoverageItem[];
  criticalPathCoverage: number;
  lastRun: string;
  generatedFiles: string[];
}

interface FileCoverageItem {
  path: string;
  coverage: number;
  testFiles: string[];
}
```

### State Management Patterns

The testing system follows React best practices for state management:

1. **Component-Level State**: UI state (loading, dialogs, selections) managed with `useState`
2. **Server State**: Test coverage and repository data managed with TanStack Query
3. **Global State**: Authentication and workspace context provided by React Context
4. **Derived State**: Computed values (e.g., average coverage) calculated during render

### Error Handling Strategy

Error handling is implemented at multiple levels:

1. **Component Level**: Try-catch blocks around async operations
2. **API Level**: Supabase client error responses handled with toast notifications
3. **UI Level**: Error states displayed in progress dialogs and alert components
4. **Recovery**: Retry mechanisms for transient failures

## Usage

### Running Test Generation

To generate tests for a repository:

1. **Navigate to Testing Page**:
   - Access `/product/testing` from the product dashboard
   - The page displays a table of all connected repositories

2. **Select Repository**:
   - Click the "Generate Tests" action button next to the target repository
   - The AI Test Engineer Panel opens on the right side

3. **Configure Test Generation**:
   ```
   Coverage Level Options:
   - 100%: Full coverage including edge cases
   - 80%: Focus on critical functionality
   - 60%: Basic coverage of main paths
   ```

4. **Provide Custom Instructions (Optional)**:
   Example instructions:
   ```
   "Focus on API endpoints and data validation logic.
    Include integration tests for authentication flow.
    Use Jest as the testing framework."
   ```

5. **Start Generation**:
   - Click the "Apply" button
   - The Test Progress Dialog opens automatically

6. **Monitor Progress**:
   The dialog shows real-time updates through five phases:
   - Phase 1: Repository analysis (~30 seconds)
   - Phase 2: Test strategy planning (~1 minute)
   - Phase 3: Test case generation (~2-3 minutes)
   - Phase 4: Test file creation (~1 minute)
   - Phase 5: Validation and cleanup (~30 seconds)

7. **Review Results**:
   - Upon completion, the dialog closes
   - The repository table updates with new coverage metrics
   - Generated test files are available in the repository

### Viewing Test Coverage

After test generation completes:

1. **Coverage Metrics**:
   - Overall repository coverage percentage
   - Per-file coverage breakdown
   - Critical path coverage status

2. **Test Files**:
   - List of generated test files with paths
   - Links to view test files in the repository
   - Test execution results

3. **Coverage Reports**:
   - Visual representation of coverage
   - Uncovered code sections highlighted
   - Recommendations for additional tests

### Customizing Test Generation

The AI Test Engineer supports various customization options through the instructions field:

**Framework Selection**:
```
"Use Jest with React Testing Library for component tests.
Use Cypress for end-to-end tests."
```

**Focus Areas**:
```
"Prioritize testing:
- Authentication and authorization logic
- Payment processing functions
- Data validation and sanitization"
```

**Testing Patterns**:
```
"Follow these patterns:
- Arrange-Act-Assert structure
- Mock external dependencies
- Test edge cases for null/undefined inputs"
```

**Exclusions**:
```
"Skip test generation for:
- Generated files in /build
- Third-party libraries in /vendor
- Legacy code marked with @deprecated"
```

### Integration with Development Workflow

The testing system integrates with standard development practices:

#### Pre-Commit Testing

1. Generate tests for new features before committing
2. Review generated tests to ensure quality
3. Run tests locally to verify functionality
4. Commit both implementation and test code

#### Pull Request Analysis

1. Trigger test generation on pull request creation
2. Compare coverage with main branch
3. Require minimum coverage threshold before merge
4. Display coverage changes in PR comments

#### Continuous Integration

1. Export test files to CI/CD pipeline
2. Execute tests as part of build process
3. Report coverage metrics to dashboard
4. Fail builds that decrease coverage below threshold

### Example Workflow

**Scenario**: Adding a new authentication feature

1. **Initial Analysis**:
   ```
   - Navigate to Testing page
   - Select repository: "my-auth-service"
   - Current coverage: 45%
   ```

2. **Generate Tests**:
   ```
   Coverage Level: 80%
   Custom Instructions: "Focus on authentication endpoints,
   include tests for JWT validation, password hashing,
   and session management. Use Mocha/Chai framework."
   ```

3. **Monitor Progress**:
   ```
   Phase 1: ✓ Analyzed 234 files
   Phase 2: ✓ Generated strategy for 12 modules
   Phase 3: ✓ Created 87 test cases
   Phase 4: ✓ Wrote 12 test files
   Phase 5: ✓ Validated all tests pass
   ```

4. **Review Results**:
   ```
   New Coverage: 82%
   Generated Files:
   - tests/auth/jwt.test.js
   - tests/auth/password.test.js
   - tests/auth/session.test.js
   - tests/integration/auth-flow.test.js
   ```

5. **Integration**:
   ```
   - Download generated test files
   - Add to local repository
   - Run tests: npm test
   - Commit to feature branch
   - Create pull request
   ```

### Best Practices

Based on the implementation, follow these best practices:

#### Test Coverage Targets

- **Critical Systems**: Aim for 80-100% coverage
- **Business Logic**: Maintain at least 80% coverage
- **UI Components**: Target 60-80% coverage
- **Utility Functions**: Strive for 100% coverage

#### Test Generation Frequency

- **New Features**: Generate tests before code review
- **Bug Fixes**: Add regression tests for resolved issues
- **Refactoring**: Regenerate tests to match new structure
- **Regular Audits**: Monthly coverage reviews

#### Quality Guidelines

- **Review Generated Tests**: Always manually review AI-generated tests
- **Add Edge Cases**: Supplement generated tests with edge case scenarios
- **Mock Dependencies**: Ensure external dependencies are properly mocked
- **Maintain Tests**: Update tests when implementation changes

#### Performance Optimization

- **Batch Generation**: Generate tests for multiple repositories in off-hours
- **Incremental Updates**: Focus on changed files for faster generation
- **Cache Results**: Leverage TanStack Query caching for quick access
- **Parallel Execution**: Run test generation for multiple modules concurrently

### Troubleshooting

Common issues and solutions:

#### Test Generation Fails

**Symptom**: Progress dialog shows error in Phase 2 or 3

**Solutions**:
1. Check repository access permissions
2. Verify GitHub OAuth token is valid
3. Ensure repository contains parseable code
4. Review custom instructions for syntax errors

#### Low Coverage Results

**Symptom**: Generated tests achieve lower coverage than expected

**Solutions**:
1. Increase coverage level target (e.g., 80% → 100%)
2. Provide more specific instructions about critical paths
3. Run generation multiple times to cover different scenarios
4. Manually supplement with additional tests

#### Tests Don't Execute

**Symptom**: Generated tests fail to run in local environment

**Solutions**:
1. Install required testing framework dependencies
2. Configure test environment variables
3. Update import paths to match project structure
4. Verify test file placement matches framework conventions

#### Slow Generation Times

**Symptom**: Test generation takes longer than expected

**Solutions**:
1. Reduce coverage target for large repositories
2. Focus on specific modules using custom instructions
3. Split large repositories into smaller components
4. Schedule generation during off-peak hours

This comprehensive testing strategy documentation is based entirely on the actual implementation found in the OrchestRAI codebase, specifically the components, hooks, and pages that make up the testing infrastructure.