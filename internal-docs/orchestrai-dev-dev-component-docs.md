# orchestrai-dev - Component Documentation

## Overview

This document provides comprehensive documentation for the major React components in the orchestrai-dev project. The application is built with React, TypeScript, and uses modern UI libraries including Radix UI components, TanStack Query for data fetching, and Supabase for backend services. The components follow a modular architecture with clear separation of concerns between presentation, business logic, and data management.

## Implementation

### Core Application Structure

The application is structured around a central `App.tsx` component that provides routing, context providers, and global UI elements. The implementation can be found in `src/App.tsx`.

**Key Features:**
- **Routing:** Uses `react-router-dom` with `BrowserRouter` for client-side routing
- **Context Providers:** Wraps the application with `AuthProvider` and `WorkspaceProvider` for global state management
- **Query Client:** Implements TanStack Query with a `QueryClient` instance for data fetching and caching
- **Toast Notifications:** Integrates both standard `Toaster` and `Sonner` for user notifications
- **Welcome Modal:** Displays a welcome modal for new users controlled by `useWelcomeModal` hook

**Component Structure:**
```tsx
// From src/App.tsx
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

### AI-Powered Component Panels

The application includes specialized AI-powered panels for different engineering tasks. These panels follow a consistent pattern and are located in `src/components/`.

#### AIComplianceAnalystPanel

**Location:** `src/components/AIComplianceAnalystPanel.tsx`

**Purpose:** Provides an interface for running AI-powered compliance analysis on GitHub repositories.

**Props Interface:**
```typescript
interface AIComplianceAnalystPanelProps {
  repository: Repository;
  isOpen: boolean;
  onClose: () => void;
  onAnalysisComplete?: (analysisId: string) => void;
}
```

**Key Implementation Details:**

1. **Permission Checking:**
   - Uses `useWorkspaceFunctionPermissions('Compliance')` hook to verify user permissions
   - Distinguishes between free plan users and paid plan permission restrictions
   - Checks workflow configuration to ensure compliance analysis is enabled

2. **Workflow Configuration:**
   ```typescript
   const checkWorkflowConfiguration = async () => {
     if (!currentWorkspace) return;
     
     const config = await workflowService.getWorkflowConfiguration(
       currentWorkspace.id, 
       'Compliance'
     );
     
     const isAllowed = config && (
       config.enablement === 'analysis_only' || 
       config.enablement === 'analysis_and_fix'
     );
     setIsComplianceAllowed(isAllowed);
   };
   ```

3. **Analysis Execution:**
   - Calls the `code-compliance-analyzer` Supabase edge function
   - Passes repository metadata, workspace ID, and user instructions
   - Returns analysis ID upon successful execution

4. **State Management:**
   - `isStarting`: Controls button loading state
   - `isComplianceAllowed`: Tracks if compliance is enabled in workspace settings
   - `analysisInProgress`: Monitors ongoing analysis
   - `analysisComplete`: Tracks completion status
   - `showProgressDialog`: Controls visibility of progress dialog

**Usage Example:**
```tsx
<AIComplianceAnalystPanel
  repository={{
    id: 123,
    name: "my-repo",
    full_name: "owner/my-repo",
    html_url: "https://github.com/owner/my-repo",
    private: false
  }}
  isOpen={isPanelOpen}
  onClose={() => setIsPanelOpen(false)}
  onAnalysisComplete={(analysisId) => {
    console.log('Analysis completed:', analysisId);
  }}
/>
```

**UI Components Used:**
- `Button` from `@/components/ui/button`
- `Card`, `CardContent`, `CardHeader`, `CardTitle` from `@/components/ui/card`
- `Alert`, `AlertDescription` from `@/components/ui/alert`
- `Progress` from `@/components/ui/progress`
- `Textarea` from `@/components/ui/textarea`
- `Label` from `@/components/ui/label`

**Key Features:**
- Fixed position side panel (right: 0, width: 384px)
- Permission-based access control with visual indicators
- Integration with ComplianceProgressDialog for real-time progress tracking
- Workflow configuration validation
- Toast notifications for user feedback
- Repository information display

#### AIDocumentationSpecialistPanel

**Location:** `src/components/AIDocumentationSpecialistPanel.tsx`

**Purpose:** Provides an interface for AI-powered documentation generation, supporting both migration of existing documentation and creation of new documentation.

**Props Interface:**
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

**Key Implementation Details:**

1. **Documentation Scope Selection:**
   ```typescript
   const [selectedScopes, setSelectedScopes] = useState({
     userFacing: true,
     internal: true,
     sbom: true,
   });
   ```

2. **Content Structure Customization:**
   ```typescript
   const [selectedContentStructure, setSelectedContentStructure] = useState({
     intro: true,
     tutorials: true,
     howTo: false,
     reference: true,
     concepts: false,
     troubleshooting: false,
     releaseNotes: false,
   });
   ```

3. **Repository Scope Management:**
   - Loads OrchestrAI-enabled repositories from the workspace
   - Supports full repository analysis or specific commit documentation
   - Implements commit selection UI with GitHub API integration

   ```typescript
   const [repositoryScopes, setRepositoryScopes] = useState<
     Record<string, { 
       scope: 'full' | 'commit'; 
       commitSha?: string; 
       commitMessage?: string 
     }>
   >({});
   ```

4. **Checkpoint/Resume Support:**
   - Loads previous execution state from `function_checkpoints` table
   - Restores user selections, instructions, and repository configurations
   - Indicated via `resumeExecution` prop with checkpoint data

5. **Configuration Loading:**
   ```typescript
   const loadDocumentationConfig = async () => {
     const configs = await workflowService.getWorkflowConfigurations(
       currentWorkspace.id
     );
     const config = configs.find(c => c.function_name === 'Documentation');
     setDocConfig(config);
   };
   ```

**Usage Example:**
```tsx
<AIDocumentationSpecialistPanel
  isOpen={isPanelOpen}
  onClose={() => setIsPanelOpen(false)}
  action="create"
  hasDocumentationUrl={true}
  resumeExecution={previousExecution}
  onComplete={(result) => {
    if (result.success) {
      console.log('Documentation generated successfully');
    }
  }}
/>
```

**Advanced Features:**

1. **Collapsible Advanced Options:**
   - Uses `Collapsible` component from Radix UI
   - Allows customization of scope and content structure
   - Nested checkbox structure for content types under user-facing scope

2. **Repository Commit Selector:**
   - Fetches last 20 commits from GitHub API
   - Displays commit SHA, message, and date
   - Supports selection of specific commits for documentation updates
   - Handles GitHub authentication via vault secrets

3. **Priority Instructions:**
   - User-provided instructions override default workspace configuration
   - Clearly labeled with priority badge to indicate override behavior

**State Validation:**
- Requires at least one repository selected when repositories are available
- Requires at least one scope selected (userFacing, internal, or sbom)
- For migration action, requires `hasDocumentationUrl` to be true
- Validates that workflow configuration includes repository and folder settings

**UI Structure:**
```
Fixed Right Panel (width: 384px)
├── Header (title + close button)
├── Scrollable Content Area
│   ├── Resume Checkpoint Alert (conditional)
│   ├── Action Type Card (migrate/create)
│   ├── Configuration Required Alert (conditional)
│   ├── Instructions TextArea (priority)
│   ├── Advanced Options (Collapsible)
│   │   ├── Scope Selection
│   │   └── Content Structure (nested under userFacing)
│   ├── Code Scope Selection (Collapsible)
│   │   └── Repository List with Scope Options
│   ├── Configuration Info Card
│   └── How It Works Card
└── Footer (Generate Documentation button)
```

**Integration Points:**
- `DocumentationProgressDialog`: Handles the generation progress and execution
- `workflowService.getWorkflowConfigurations()`: Retrieves workspace documentation settings
- Supabase `repository_settings` table: Loads OrchestrAI-enabled repositories
- Supabase `function_checkpoints` table: Loads/saves execution state for resume functionality
- GitHub API: Fetches commits for specific commit documentation

## Component Styling

All components use a consistent styling approach:

**Styling Framework:**
- Tailwind CSS utility classes for layout and basic styling
- Custom component library in `@/components/ui/` built on Radix UI primitives
- Consistent color scheme: violet/purple for compliance, emerald/green for success, amber/yellow for warnings

**Common CSS Classes:**
- Fixed panels: `fixed inset-y-0 right-0 w-96 bg-white shadow-xl border-l border-gray-200 z-50 flex flex-col`
- Card borders: `border-{color}-200 bg-{color}-50`
- Text colors: `text-{color}-700` for headings, `text-{color}-600` for body text
- Spacing: consistent `space-y-{n}` for vertical spacing, `p-6` for padding

## Testing

The codebase includes comprehensive test files located in `orchestrai_tests/` directory with multiple test runs dating from July 2025 through October 2025.

**Test Structure:**

1. **JavaScript Configuration Tests:**
   - `eslint.config.test.js`: Validates ESLint configuration structure
   - `postcss.config.test.js`: Validates PostCSS plugin configuration

2. **TypeScript Component Tests:**
   - `App.test.tsx`: Tests main application component rendering and routing
   - `AIQualityEngineerPanel.test.tsx`: Tests quality engineer panel functionality
   - `AITestEngineerPanel.test.tsx`: Tests test engineer panel functionality (partial implementation)
   - `CodePageContent.test.tsx`: Tests code page content component (partial implementation)

**Testing Patterns Used:**

1. **Component Mocking:**
   ```typescript
   jest.mock('../../src/components/AIQualityEngineerPanel', () => {
     return function MockAIQualityEngineerPanel() {
       return <div data-testid="ai-quality-engineer-panel">
         AI Quality Engineer Panel
       </div>;
     };
   });
   ```

2. **Service Mocking:**
   ```typescript
   const mockApiCall = jest.fn();
   jest.mock('../../../src/services/api', () => ({
     generateTests: mockApiCall,
     analyzeCode: mockApiCall,
   }));
   ```

3. **Async Operations:**
   ```typescript
   await waitFor(() => {
     expect(mockApiCall).toHaveBeenCalledWith(codeContent);
   });
   ```

**Test Files Location:**
- Latest test run: `orchestrai_tests/2025-10-09_17-31-41/`
- TypeScript tests: `orchestrai_tests/{date}/typescript/tests/`
- JavaScript tests: `orchestrai_tests/{date}/javascript/tests/`

## Dependencies

**Core Libraries:**
- `react`: ^18.x (React framework)
- `react-router-dom`: Client-side routing
- `@tanstack/react-query`: Data fetching and state management
- `lucide-react`: Icon library
- `@radix-ui/*`: Headless UI components

**UI Components:**
- All custom UI components are located in `@/components/ui/`
- Built on top of Radix UI primitives
- Includes: Button, Card, Alert, Progress, Textarea, Label, Checkbox, Badge, Collapsible, Dialog

**Backend Integration:**
- `@supabase/supabase-js`: Supabase client for backend communication
- Custom service layer in `@/services/` for business logic
- Integration with Supabase edge functions for AI operations

**State Management:**
- Context API: `AuthContext` and `WorkspaceContext` in `@/contexts/`
- Custom hooks: `useWelcomeModal`, `useWorkspaceFunctionPermissions`
- React Query for server state management

## File Organization

```
src/
├── App.tsx                           # Main application component
├── components/
│   ├── ui/                          # Reusable UI components (Radix-based)
│   ├── AIComplianceAnalystPanel.tsx # Compliance analysis panel
│   ├── AIDocumentationSpecialistPanel.tsx # Documentation generation panel
│   ├── ComplianceProgressDialog.tsx # Progress dialog for compliance
│   ├── DocumentationProgressDialog.tsx # Progress dialog for documentation
│   └── WelcomeModal.tsx             # Welcome modal for new users
├── contexts/
│   ├── AuthContext.tsx              # Authentication state management
│   └── WorkspaceContext.tsx         # Workspace state management
├── hooks/
│   ├── useWelcomeModal.ts           # Welcome modal state hook
│   ├── useWorkspaceFunctionPermissions.ts # Permission checking hook
│   └── use-toast.ts                 # Toast notification hook
├── services/
│   └── workflowService.ts           # Workflow configuration service
├── integrations/
│   └── supabase/
│       └── client.ts                # Supabase client configuration
├── pages/                           # Route components
└── types/
    └── github.ts                    # TypeScript type definitions
```

## Configuration Files

**ESLint Configuration** (`eslint.config.js`):
- Uses `@eslint/js` recommended configuration
- Extends TypeScript ESLint recommended rules
- Configures React hooks and React refresh plugins
- Disables `@typescript-eslint/no-unused-vars` rule
- Ignores `dist` directory
- Targets `**/*.{ts,tsx}` files

**PostCSS Configuration** (`postcss.config.js`):
- Integrates Tailwind CSS via `tailwindcss` plugin
- Adds vendor prefixes via `autoprefixer` plugin
- Simple plugin-only configuration structure

## Best Practices

**Component Patterns:**

1. **Side Panel Pattern:**
   - Fixed positioning with consistent width (384px)
   - Flexbox layout with scrollable content area
   - Sticky header and footer sections
   - Close handler with state reset

2. **Permission Checking:**
   - Use `useWorkspaceFunctionPermissions` hook
   - Display permission alerts before disabled functionality
   - Distinguish between free plan and paid plan restrictions
   - Check workflow configuration enablement settings

3. **State Management:**
   - Local state for UI interactions
   - Context providers for global state
   - React Query for server state
   - Custom hooks for reusable logic

4. **Error Handling:**
   - Try-catch blocks around async operations
   - Toast notifications for user feedback
   - Error state variables for UI error display
   - Graceful degradation when services unavailable

5. **Async Operations:**
   - Loading states for user feedback
   - Disabled buttons during operations
   - Progress dialogs for long-running tasks
   - Error recovery mechanisms

**Code Organization:**
- Separate concerns: presentation, business logic, data fetching
- Reusable UI components in dedicated directory
- Service layer for API interactions
- Custom hooks for stateful logic
- Type definitions in dedicated types directory

This documentation reflects the actual implementation found in the source code and provides accurate references to file paths, component structures, and implementation patterns used throughout the orchestrai-dev application.