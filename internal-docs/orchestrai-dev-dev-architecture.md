# orchestrai-dev - Architecture Documentation

## Overview

OrchestrAI is a web-based platform for automating software development workflows, including code analysis, testing, documentation generation, and compliance checking. The application is built using React with TypeScript, leveraging Vite as the build tool, and integrates with Supabase for backend services and authentication.

The architecture follows a component-based approach with context providers for state management, a service layer for API interactions, and custom hooks for shared functionality. The application supports multi-workspace functionality and integrates with GitHub for repository management.

## Project Structure

### Root Directory Organization

```
orchestrai-dev/
├── src/                          # Source code directory
│   ├── components/               # React components
│   ├── contexts/                 # React context providers
│   ├── hooks/                    # Custom React hooks
│   ├── integrations/             # External service integrations
│   ├── pages/                    # Page components for routing
│   ├── services/                 # Business logic and API services
│   ├── types/                    # TypeScript type definitions
│   ├── App.tsx                   # Root application component
│   └── main.tsx                  # Application entry point
├── orchestrai_tests/             # Generated test files
├── eslint.config.js              # ESLint configuration
├── postcss.config.js             # PostCSS configuration
├── tailwind.config.ts            # Tailwind CSS configuration
├── tsconfig.json                 # TypeScript configuration
└── vite.config.ts                # Vite build configuration
```

### Source Code Organization (`src/`)

The source code is organized into distinct directories based on functionality:

- **components/** - Reusable UI components and feature-specific panels
- **contexts/** - React Context providers for global state management
- **hooks/** - Custom React hooks for shared logic
- **integrations/** - External service integration code (Supabase client)
- **pages/** - Top-level page components mapped to routes
- **services/** - Business logic and API communication layer
- **types/** - TypeScript interfaces and type definitions

## Technology Stack

### Frontend Framework

- **React 18+** - Component-based UI library
- **TypeScript** - Static type checking
- **Vite** - Fast build tool and development server
- **React Router** - Client-side routing (`react-router-dom`)

### State Management

- **React Context API** - Global state management
  - `AuthContext` - User authentication state
  - `WorkspaceContext` - Current workspace and workspace-related data

### UI Components

- **Custom Component Library** - Located in `src/components/ui/`
- **Radix UI Primitives** - Accessible component primitives
- **Tailwind CSS** - Utility-first CSS framework
- **Lucide React** - Icon library

### Backend Integration

- **Supabase** - Backend as a Service
  - Authentication
  - PostgreSQL database
  - Edge functions
  - Real-time subscriptions
  - Vault for secrets management

### Data Fetching

- **@tanstack/react-query** (v5) - Server state management and caching

### Form Handling

- **React Hook Form** - Form validation and state management

## Configuration Files

### ESLint Configuration (`eslint.config.js`)

The project uses ESLint v9+ flat config format with TypeScript support.

```javascript
import js from "@eslint/js";
import globals from "globals";
import reactHooks from "eslint-plugin-react-hooks";
import reactRefresh from "eslint-plugin-react-refresh";
import tseslint from "typescript-eslint";

export default tseslint.config(
  { ignores: ["dist"] },
  {
    extends: [js.configs.recommended, ...tseslint.configs.recommended],
    files: ["**/*.{ts,tsx}"],
    languageOptions: {
      ecmaVersion: 2020,
      globals: globals.browser,
    },
    plugins: {
      "react-hooks": reactHooks,
      "react-refresh": reactRefresh,
    },
    rules: {
      ...reactHooks.configs.recommended.rules,
      "react-refresh/only-export-components": [
        "warn",
        { allowConstantExport: true },
      ],
      "@typescript-eslint/no-unused-vars": "off",
    },
  }
);
```

**Key Configuration Details:**
- Extends recommended TypeScript and JavaScript configs
- Ignores `dist` directory
- Targets ECMAScript 2020
- Includes React Hooks and React Refresh plugins
- Disables `no-unused-vars` TypeScript rule
- Warns on non-component exports that break fast refresh

### PostCSS Configuration (`postcss.config.js`)

Minimal PostCSS setup for Tailwind CSS processing.

```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

**Key Configuration Details:**
- Integrates Tailwind CSS plugin
- Includes Autoprefixer for cross-browser compatibility

## Application Architecture

### Entry Point (`src/App.tsx`)

The root component sets up the application's core infrastructure:

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

**Architecture Layers (from outer to inner):**

1. **QueryClientProvider** - React Query for server state management
2. **TooltipProvider** - Global tooltip context from Radix UI
3. **Toaster/Sonner** - Toast notification systems
4. **BrowserRouter** - React Router for client-side routing
5. **AuthProvider** - Authentication context wrapper
6. **WorkspaceProvider** - Workspace management context wrapper
7. **AppContent** - Main application routes and content

### Routing Structure

The application uses React Router v6 with the following route configuration in `AppContent` component:

```typescript
<Routes>
  <Route path="/" element={<Index />} />
  <Route path="/enterprise" element={<Enterprise />} />
  <Route path="/mission" element={<Mission />} />
  <Route path="/organization-mission" element={<OrganizationMission />} />
  <Route path="/organization-information" element={<ProductInformation />} />
  <Route path="/product/org-information" element={<ProductInformation />} />
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
  <Route path="/pricing" element={<Pricing />} />
  <Route path="/code-analysis" element={<CodeAnalysis />} />
  <Route path="/testing" element={<Testing />} />
  <Route path="/workspace-management" element={<WorkspaceManagement />} />
  <Route path="/account" element={<Account />} />
  <Route path="/cost-analysis/:workspaceId" element={<CostAnalysis />} />
  <Route path="/github-success" element={<GitHubSuccess />} />
  <Route path="/github-error" element={<GitHubError />} />
  <Route path="/privacy" element={<PrivacyPolicy />} />
  <Route path="/terms" element={<TermsOfService />} />
  <Route path="*" element={<NotFound />} />
</Routes>
```

**Route Categories:**

1. **Marketing/Public Routes**
   - `/` - Landing page (Index)
   - `/enterprise` - Enterprise information
   - `/pricing` - Pricing information
   - `/privacy` - Privacy policy
   - `/terms` - Terms of service

2. **Product Setup Routes**
   - `/mission` - Mission definition
   - `/organization-mission` - Organization-level mission
   - `/organization-information` - Organization details
   - `/product/org-information` - Product organization info (duplicate route)

3. **Product Feature Routes** (under `/product`)
   - `/product` - Main product dashboard
   - `/product/code` - Code repository management
   - `/product/code-connected` - Connected code view
   - `/product/testing` - Testing features
   - `/product/code-quality` - Code quality analysis
   - `/product/code-quality/results` - Quality results
   - `/product/workflow` - Workflow configuration
   - `/product/documentation` - Documentation management
   - `/product/compliance` - Compliance checking
   - `/product/compliance/results` - Compliance results
   - `/product/workspace-management` - Workspace settings
   - `/product/permissions` - Permission management

4. **Analysis Routes**
   - `/code-analysis` - Code analysis page
   - `/testing` - Testing page
   - `/workspace-management` - Workspace management
   - `/cost-analysis/:workspaceId` - Cost analysis with workspace parameter

5. **OAuth Callback Routes**
   - `/github-success` - Successful GitHub OAuth
   - `/github-error` - Failed GitHub OAuth

6. **Fallback Route**
   - `*` - 404 Not Found page

### Context Providers

#### AuthProvider

Located in `src/contexts/AuthContext.tsx` (inferred from usage in `App.tsx`), this provider manages:
- User authentication state
- Login/logout functionality
- Session management
- User profile data

#### WorkspaceProvider

Located in `src/contexts/WorkspaceContext.tsx` (inferred from usage in `App.tsx`), this provider manages:
- Current workspace selection
- Workspace data
- Workspace-related operations

**Usage Example from `AIComplianceAnalystPanel.tsx`:**

```typescript
import { useWorkspace } from "@/contexts/WorkspaceContext";

const { currentWorkspace } = useWorkspace();
```

### Welcome Modal System

The application includes a first-run welcome modal system:

```typescript
function AppContent() {
  const { showWelcomeModal, handleWelcomeComplete } = useWelcomeModal();

  return (
    <>
      <Routes>
        {/* ... routes ... */}
      </Routes>
      
      <WelcomeModal 
        isOpen={showWelcomeModal} 
        onComplete={handleWelcomeComplete} 
      />
    </>
  );
}
```

**Components:**
- `useWelcomeModal` hook - Manages modal state
- `WelcomeModal` component - Renders the welcome flow

## Component Architecture

### AI Feature Panels

The application includes specialized AI-powered panels for different workflows:

#### AIComplianceAnalystPanel

**Location:** `src/components/AIComplianceAnalystPanel.tsx`

**Purpose:** Manages compliance analysis for GitHub repositories with configurable workflow settings.

**Props Interface:**
```typescript
interface AIComplianceAnalystPanelProps {
  repository: Repository;
  isOpen: boolean;
  onClose: () => void;
  onAnalysisComplete?: (analysisId: string) => void;
}
```

**Key Features:**
- Permission checking via `useWorkspaceFunctionPermissions` hook
- Workflow configuration validation
- Progress tracking via `ComplianceProgressDialog`
- Integration with Supabase edge function `code-compliance-analyzer`
- Checkpoint-based resume capability

**State Management:**
```typescript
const [instructions, setInstructions] = useState(string);
const [isStarting, setIsStarting] = useState(boolean);
const [isComplianceAllowed, setIsComplianceAllowed] = useState(boolean);
const [loadingWorkflowConfig, setLoadingWorkflowConfig] = useState(boolean);
const [hasError, setHasError] = useState(boolean);
const [analysisInProgress, setAnalysisInProgress] = useState(boolean);
const [analysisProgress, setAnalysisProgress] = useState(number);
const [analysisComplete, setAnalysisComplete] = useState(boolean);
const [showProgressDialog, setShowProgressDialog] = useState(boolean);
```

**Workflow Integration:**
```typescript
const checkWorkflowConfiguration = async () => {
  if (!currentWorkspace) return;

  setLoadingWorkflowConfig(true);
  try {
    const config = await workflowService.getWorkflowConfiguration(
      currentWorkspace.id, 
      'Compliance'
    );
    
    const isAllowed = config && (
      config.enablement === 'analysis_only' || 
      config.enablement === 'analysis_and_fix'
    );
    setIsComplianceAllowed(isAllowed);
  } catch (error) {
    console.error('Error checking workflow configuration:', error);
    setIsComplianceAllowed(false);
  } finally {
    setLoadingWorkflowConfig(false);
  }
};
```

**Analysis Execution:**
```typescript
const handleStartAnalysis = async () => {
  if (!currentWorkspace) {
    return { success: false, error: "No workspace selected" };
  }

  try {
    const { data, error } = await supabase.functions.invoke(
      'code-compliance-analyzer', 
      {
        body: {
          repository_id: repository.id,
          repository_name: repository.name,
          repository_full_name: repository.full_name,
          repository_url: repository.html_url,
          workspaceId: currentWorkspace.id,
          instructions: instructions || "Perform a comprehensive compliance analysis..."
        }
      }
    );

    if (error) {
      return { success: false, error: error.message };
    }

    if (data?.success && data?.analysis_id) {
      return { success: true, analysisId: data.analysis_id };
    } else {
      return { success: false, error: data?.error || 'Analysis failed' };
    }
  } catch (err) {
    return { 
      success: false, 
      error: err instanceof Error ? err.message : 'Unknown error occurred' 
    };
  }
};
```

**UI Structure:**
- Fixed right-side panel (396px wide)
- Permission restriction alerts
- Workflow configuration status
- Analysis progress indicators
- Repository information display
- Action buttons with state-based disabling

#### AIDocumentationSpecialistPanel

**Location:** `src/components/AIDocumentationSpecialistPanel.tsx`

**Purpose:** Manages documentation generation and migration workflows with advanced scope and content structure configuration.

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

**Key Features:**
- Documentation scope selection (User Facing, Internal Developer, SBOM)
- Content structure customization (/intro, /tutorials, /how-to, /reference, /concepts, /troubleshooting, /release-notes)
- Repository selection with full repo or specific commit scope
- Checkpoint-based execution resume
- Workflow configuration integration
- Progress tracking via `DocumentationProgressDialog`

**State Management:**
```typescript
const [instructions, setInstructions] = useState(string);
const [isStarting, setIsStarting] = useState(boolean);
const [loadingWorkflowConfig, setLoadingWorkflowConfig] = useState(boolean);
const [showProgressDialog, setShowProgressDialog] = useState(boolean);
const [docConfig, setDocConfig] = useState(any);
const [isAdvancedExpanded, setIsAdvancedExpanded] = useState(boolean);
const [selectedScopes, setSelectedScopes] = useState({
  userFacing: boolean,
  internal: boolean,
  sbom: boolean,
});
const [selectedContentStructure, setSelectedContentStructure] = useState({
  intro: boolean,
  tutorials: boolean,
  howTo: boolean,
  reference: boolean,
  concepts: boolean,
  troubleshooting: boolean,
  releaseNotes: boolean,
});
const [selectedRepositories, setSelectedRepositories] = useState(string[]);
const [availableRepositories, setAvailableRepositories] = useState(any[]);
const [isRepositorySelectorExpanded, setIsRepositorySelectorExpanded] = useState(boolean);
const [repositoryScopes, setRepositoryScopes] = useState(Record<string, { 
  scope: 'full' | 'commit'; 
  commitSha?: string; 
  commitMessage?: string 
}>);
const [repositoryCommits, setRepositoryCommits] = useState(Record<string, Array<{
  sha: string;
  message: string;
  date: string;
}>>);
const [loadingCommits, setLoadingCommits] = useState(Record<string, boolean>);
```

**Checkpoint Resume Logic:**
```typescript
const loadCheckpointData = async () => {
  if (!resumeExecution?.id) return;
  
  try {
    const { data: checkpoint, error } = await supabase
      .from('function_checkpoints')
      .select('checkpoint_data')
      .eq('execution_id', resumeExecution.id)
      .eq('execution_type', 'documentation')
      .order('created_at', { ascending: false })
      .limit(1)
      .single();

    if (error) throw error;
    
    if (checkpoint?.checkpoint_data) {
      const checkpointData = checkpoint.checkpoint_data as any;
      
      // Restore configuration
      if (checkpointData.scopesToGenerate) {
        const scopes = checkpointData.scopesToGenerate;
        setSelectedScopes({
          userFacing: scopes.includes('user_facing'),
          internal: scopes.includes('internal_developer'),
          sbom: scopes.includes('sbom'),
        });
      }
      
      if (checkpointData.userInstructions) {
        setInstructions(checkpointData.userInstructions);
      }
      
      if (checkpointData.sourceRepositories) {
        const repos = checkpointData.sourceRepositories;
        setSelectedRepositories(repos.map((r: any) => r.fullName));
        
        const scopes: Record<string, { 
          scope: 'full' | 'commit'; 
          commitSha?: string 
        }> = {};
        repos.forEach((repo: any) => {
          scopes[repo.fullName] = {
            scope: repo.scope,
            commitSha: repo.commitSha
          };
        });
        setRepositoryScopes(scopes);
      }
    }
  } catch (error) {
    console.error('Error loading checkpoint:', error);
  }
};
```

**Repository Loading:**
```typescript
const loadEnabledRepositories = async () => {
  if (!currentWorkspace) return;

  try {
    const { data: repos, error } = await supabase
      .from('repository_settings')
      .select(`
        id,
        repo_id,
        name,
        full_name,
        orchestrai_enabled,
        git_connection_id,
        git_connections!inner(workspace_id)
      `)
      .eq('git_connections.workspace_id', currentWorkspace.id)
      .eq('orchestrai_enabled', true);

    if (error) throw error;

    setAvailableRepositories(repos || []);
    
    // Auto-select all repositories by default
    if (repos && repos.length > 0) {
      const repoNames = repos.map(r => r.full_name);
      setSelectedRepositories(repoNames);
      
      const initialScopes: Record<string, { scope: 'full' | 'commit' }> = {};
      repoNames.forEach(name => {
        initialScopes[name] = { scope: 'full' };
      });
      setRepositoryScopes(initialScopes);
    }
  } catch (error) {
    console.error('Error loading enabled repositories:', error);
  }
};
```

**Commit Loading for Specific Commit Documentation:**
```typescript
const loadCommitsForRepository = async (repoFullName: string) => {
  if (!currentWorkspace || repositoryCommits[repoFullName]) return;

  setLoadingCommits(prev => ({ ...prev, [repoFullName]: true }));

  try {
    const repo = availableRepositories.find(r => r.full_name === repoFullName);
    if (!repo) return;

    const { data: connection, error: connError } = await supabase
      .from('git_connections')
      .select('access_token, vault_secret_id')
      .eq('id', repo.git_connection_id)
      .single();

    if (connError) throw connError;

    let accessToken = connection.access_token;
    
    // Retrieve from vault if needed
    if (!accessToken && connection.vault_secret_id) {
      const { data: vaultData } = await supabase.functions.invoke('vault-retrieve', {
        body: { secret_id: connection.vault_secret_id }
      });
      accessToken = vaultData?.secret_value;
    }

    if (!accessToken) throw new Error('No access token available');

    const response = await fetch(
      `https://api.github.com/repos/${repoFullName}/commits?per_page=20`,
      {
        headers: {
          'Authorization': `token ${accessToken}`,
          'Accept': 'application/vnd.github.v3+json',
        }
      }
    );

    if (!response.ok) throw new Error('Failed to fetch commits');

    const commits = await response.json();
    const formattedCommits = commits.map((commit: any) => ({
      sha: commit.sha,
      message: commit.commit.message.split('\n')[0],
      date: new Date(commit.commit.author.date).toLocaleDateString()
    }));

    setRepositoryCommits(prev => ({ ...prev, [repoFullName]: formattedCommits }));
  } catch (error) {
    console.error('Error loading commits:', error);
  } finally {
    setLoadingCommits(prev => ({ ...prev, [repoFullName]: false }));
  }
};
```

**UI Structure:**
- Fixed right-side panel (396px wide)
- Action type indicator (migrate vs create)
- Checkpoint resume indicator
- Collapsible advanced options for scope and content structure
- Repository selector with commit-level granularity
- Configuration display
- Progress dialog integration

### Progress Dialogs

#### ComplianceProgressDialog

**Location:** `src/components/ComplianceProgressDialog.tsx` (inferred from usage)

**Purpose:** Displays real-time progress for compliance analysis execution.

**Props:**
```typescript
interface ComplianceProgressDialogProps {
  isOpen: boolean;
  onClose: () => void;
  repositoryName: string;
  onComplete: (result: { success: boolean; analysisId?: string; error?: string }) => void;
  onStartAnalysis: () => Promise<{ success: boolean; analysisId?: string; error?: string }>;
}
```

#### DocumentationProgressDialog

**Location:** `src/components/DocumentationProgressDialog.tsx` (inferred from usage)

**Purpose:** Displays real-time progress for documentation generation execution.

**Props:**
```typescript
interface DocumentationProgressDialogProps {
  isOpen: boolean;
  onClose: () => void;
  action: 'migrate' | 'create';
  docConfig: any;
  repositoryName: string | null;
  instructions: string;
  selectedScopes: {
    userFacing: boolean;
    internal: boolean;
    sbom: boolean;
  };
  selectedContentStructure: {
    intro: boolean;
    tutorials: boolean;
    howTo: boolean;
    reference: boolean;
    concepts: boolean;
    troubleshooting: boolean;
    releaseNotes: boolean;
  };
  selectedRepositories: string[];
  repositoryScopes: Record<string, { 
    scope: 'full' | 'commit'; 
    commitSha?: string; 
    commitMessage?: string 
  }>;
  resumeExecutionId: string | null;
  onComplete: (result: { success: boolean; error?: string }) => void;
}
```

### UI Component Library

The application uses a custom component library built on Radix UI primitives with Tailwind CSS styling.

**Component Location:** `src/components/ui/`

**Key Components Used:**

1. **Button** (`@/components/ui/button`)
   - Variants: default, ghost, outline
   - Sizes: icon, sm, default

2. **Card** (`@/components/ui/card`)
   - CardHeader, CardTitle, CardContent subcomponents
   - Used for sectioned content display

3. **Label** (`@/components/ui/label`)
   - Form input labels

4. **Textarea** (`@/components/ui/textarea`)
   - Multi-line text input

5. **Alert** (`@/components/ui/alert`)
   - AlertDescription subcomponent
   - Used for notification-style messages

6. **Progress** (`@/components/ui/progress`)
   - Linear progress indicator

7. **Checkbox** (`@/components/ui/checkbox`)
   - Boolean selection input

8. **Badge** (`@/components/ui/badge`)
   - Small status/count indicators

9. **Collapsible** (`@/components/ui/collapsible`)
   - CollapsibleTrigger, CollapsibleContent subcomponents
   - Used for expandable sections

10. **Toast** (`@/components/ui/toaster`, `@/components/ui/sonner`)
    - Toast notification system
    - Hook: `useToast` from `@/hooks/use-toast`

## Service Layer

### Workflow Service

**Location:** `src/services/workflowService.ts` (inferred from usage)

**Purpose:** Manages workflow configuration for different AI functions.

**Methods:**

```typescript
workflowService.getWorkflowConfiguration(
  workspaceId: string, 
  functionName: string
): Promise<WorkflowConfig>

workflowService.getWorkflowConfigurations(
  workspaceId: string
): Promise<WorkflowConfig[]>
```

**Usage Example from `AIComplianceAnalystPanel`:**
```typescript
const config = await workflowService.getWorkflowConfiguration(
  currentWorkspace.id, 
  'Compliance'
);
```

**Usage Example from `AIDocumentationSpecialistPanel`:**
```typescript
const configs = await workflowService.getWorkflowConfigurations(
  currentWorkspace.id
);
const config = configs.find(c => c.function_name === 'Documentation');
```

## Custom Hooks

### useWorkspace

**Location:** `src/contexts/WorkspaceContext.tsx` (exported hook)

**Purpose:** Provides access to current workspace data and operations.

**Return Value:**
```typescript
{
  currentWorkspace: Workspace | null;
  // Additional workspace-related properties and methods
}
```

### useWelcomeModal

**Location:** `src/hooks/useWelcomeModal.tsx` (inferred)

**Purpose:** Manages welcome modal state for first-time users.

**Return Value:**
```typescript
{
  showWelcomeModal: boolean;
  handleWelcomeComplete: () => void;
}
```

### useWorkspaceFunctionPermissions

**Location:** `src/hooks/useWorkspaceFunctionPermissions.ts` (inferred from usage)

**Purpose:** Checks user permissions for specific workspace functions.

**Parameters:**
```typescript
functionName: string  // e.g., 'Compliance'
```

**Return Value:**
```typescript
{
  hasPermission: boolean;
  isLoading: boolean;
  isFreePlan: boolean;
}
```

**Usage Example:**
```typescript
const { hasPermission, isLoading, isFreePlan } = 
  useWorkspaceFunctionPermissions('Compliance');
```

### useToast

**Location:** `src/hooks/use-toast.ts` (inferred)

**Purpose:** Provides toast notification functionality.

**Return Value:**
```typescript
{
  toast: (options: ToastOptions) => void;
}
```

**Toast Options:**
```typescript
interface ToastOptions {
  title: string;
  description?: string;
  variant?: "default" | "destructive";
}
```

**Usage Example:**
```typescript
const { toast } = useToast();

toast({
  title: "Analysis Complete",
  description: `Compliance analysis completed for ${repository.name}`,
});

toast({
  title: "Analysis Failed",
  description: "Failed to analyze repository",
  variant: "destructive",
});
```

## Supabase Integration

### Client Setup

**Location:** `src/integrations/supabase/client.ts` (inferred from import)

```typescript
import { supabase } from "@/integrations/supabase/client";
```

### Edge Functions

The application invokes Supabase Edge Functions for backend operations:

#### code-compliance-analyzer

**Purpose:** Performs compliance analysis on a repository.

**Invocation:**
```typescript
const { data, error } = await supabase.functions.invoke(
  'code-compliance-analyzer', 
  {
    body: {
      repository_id: string,
      repository_name: string,
      repository_full_name: string,
      repository_url: string,
      workspaceId: string,
      instructions: string
    }
  }
);
```

**Response:**
```typescript
{
  success: boolean;
  analysis_id?: string;
  error?: string;
}
```

#### vault-retrieve

**Purpose:** Retrieves secrets from Supabase Vault.

**Invocation:**
```typescript
const { data: vaultData } = await supabase.functions.invoke('vault-retrieve', {
  body: { secret_id: string }
});
```

**Response:**
```typescript
{
  secret_value?: string;
}
```

### Database Tables

Based on queries in the code, the following tables are used:

#### function_checkpoints

**Purpose:** Stores execution checkpoints for resumable operations.

**Columns:**
- `execution_id` (string)
- `execution_type` (string) - e.g., 'documentation'
- `checkpoint_data` (JSONB)
- `created_at` (timestamp)

**Query Example:**
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

#### repository_settings

**Purpose:** Stores repository configuration and enablement settings.

**Columns:**
- `id`
- `repo_id`
- `name`
- `full_name`
- `orchestrai_enabled` (boolean)
- `git_connection_id`

**Relationships:**
- `git_connections` (foreign key)

**Query Example:**
```typescript
const { data: repos, error } = await supabase
  .from('repository_settings')
  .select(`
    id,
    repo_id,
    