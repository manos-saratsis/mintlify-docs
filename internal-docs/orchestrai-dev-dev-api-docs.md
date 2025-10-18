# orchestrai-dev - API Documentation

## Overview

The OrchestrAI application provides a comprehensive API infrastructure built on Supabase edge functions and React Query for managing code analysis, testing, compliance, and documentation workflows. The API layer consists of:

- **Edge Functions**: Serverless functions deployed on Supabase for backend processing
- **React Query Integration**: Client-side data fetching and state management
- **Supabase Client**: Database and authentication operations
- **Service Layer**: TypeScript services that abstract API interactions

The application uses a workspace-based permission model where users interact with repositories and AI-powered features through various panels and dialogs.

---

## Implementation

### Supabase Client Configuration

**Location**: `src/integrations/supabase/client.ts` (referenced throughout components)

The application initializes a Supabase client using environment variables for the project URL and anonymous key:

```typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

**Required Environment Variables**:
- `VITE_SUPABASE_URL`: Your Supabase project URL
- `VITE_SUPABASE_ANON_KEY`: Your Supabase anonymous/public API key

### React Query Setup

**Location**: `src/App.tsx` (lines 48-63)

The application wraps all components in a `QueryClientProvider` to enable React Query functionality:

```typescript
const queryClient = new QueryClient();

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

This setup enables:
- Automatic request deduplication
- Background refetching
- Caching and invalidation
- Loading and error states

---

## API Endpoints

### Edge Functions

The application interacts with Supabase Edge Functions for AI-powered operations. Edge functions are invoked using the `supabase.functions.invoke()` method.

#### 1. Compliance Analysis

**Function**: `code-compliance-analyzer`

**Location**: Referenced in `src/components/AIComplianceAnalystPanel.tsx` (lines 83-108)

**Purpose**: Performs compliance analysis on repository code to check for regulatory requirements and security standards.

**Request Body**:
```typescript
{
  repository_id: string;           // Repository identifier
  repository_name: string;         // Repository name
  repository_full_name: string;    // Full repository name (owner/repo)
  repository_url: string;          // GitHub repository URL
  workspaceId: string;             // Current workspace ID
  instructions: string;            // User-provided analysis instructions
}
```

**Implementation Example** (`src/components/AIComplianceAnalystPanel.tsx`, lines 83-108):
```typescript
const handleStartAnalysis = async (): Promise<{ success: boolean; analysisId?: string; error?: string }> => {
  if (!currentWorkspace) {
    return { success: false, error: "No workspace selected" };
  }

  try {
    const { data, error } = await supabase.functions.invoke('code-compliance-analyzer', {
      body: {
        repository_id: repository.id,
        repository_name: repository.name,
        repository_full_name: repository.full_name,
        repository_url: repository.html_url,
        workspaceId: currentWorkspace.id,
        instructions: instructions || "Perform a comprehensive compliance analysis..."
      }
    });

    if (error) {
      return { success: false, error: error.message };
    }

    if (data?.success && data?.analysis_id) {
      return { success: true, analysisId: data.analysis_id };
    } else {
      return { success: false, error: data?.error || 'Analysis failed' };
    }
  } catch (err) {
    return { success: false, error: err instanceof Error ? err.message : 'Unknown error occurred' };
  }
};
```

**Response Format**:
```typescript
{
  success: boolean;
  analysis_id?: string;  // Unique analysis identifier
  error?: string;        // Error message if failed
}
```

**Usage Pattern** (`src/components/AIComplianceAnalystPanel.tsx`, lines 249-274):
```typescript
const startAnalysis = async () => {
  if (!isComplianceAllowed) {
    toast({
      title: "Compliance Disabled",
      description: "Please enable Compliance in Workflow settings to perform analysis.",
      variant: "destructive",
    });
    return;
  }

  if (!hasPermission && !isFreePlan) {
    toast({
      title: "Permission Denied", 
      description: "You do not have permission to run compliance analysis.",
      variant: "destructive",
    });
    return;
  }

  setShowProgressDialog(true);
};
```

**Authentication**: Uses Supabase session authentication automatically through the configured client.

**Error Handling**: All errors are caught and returned in a standardized format with `{ success: false, error: string }`.

#### 2. Vault Secret Retrieval

**Function**: `vault-retrieve`

**Location**: Referenced in `src/components/AIDocumentationSpecialistPanel.tsx` (lines 194-198)

**Purpose**: Retrieves sensitive credentials (like GitHub access tokens) from a secure vault.

**Request Body**:
```typescript
{
  secret_id: string;  // Vault secret identifier
}
```

**Implementation Example** (`src/components/AIDocumentationSpecialistPanel.tsx`, lines 194-198):
```typescript
if (!accessToken && connection.vault_secret_id) {
  const { data: vaultData } = await supabase.functions.invoke('vault-retrieve', {
    body: { secret_id: connection.vault_secret_id }
  });
  accessToken = vaultData?.secret_value;
}
```

**Response Format**:
```typescript
{
  secret_value: string;  // The decrypted secret
}
```

**Use Case**: Used when GitHub access tokens are not stored directly in the database but referenced by a vault secret ID.

---

### Database Operations

#### Repository Settings

**Table**: `repository_settings`

**Location**: Referenced in `src/components/AIDocumentationSpecialistPanel.tsx` (lines 152-170)

**Purpose**: Manages repository configurations and OrchestrAI enablement status.

**Query Example** (lines 152-170):
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
  } catch (error) {
    console.error('Error loading enabled repositories:', error);
  }
};
```

**Schema**:
- `id`: string - Unique identifier
- `repo_id`: string - GitHub repository ID
- `name`: string - Repository name
- `full_name`: string - Full repository name (owner/repo)
- `orchestrai_enabled`: boolean - Whether OrchestrAI features are enabled
- `git_connection_id`: string - Foreign key to git_connections
- `git_connections`: Related git connection data with workspace_id

**Filters**:
- `workspace_id`: Filters repositories by workspace
- `orchestrai_enabled`: Only returns enabled repositories

#### Git Connections

**Table**: `git_connections`

**Location**: Referenced in `src/components/AIDocumentationSpecialistPanel.tsx` (lines 180-187)

**Purpose**: Stores GitHub integration credentials and configuration.

**Query Example** (lines 180-187):
```typescript
const { data: connection, error: connError } = await supabase
  .from('git_connections')
  .select('access_token, vault_secret_id')
  .eq('id', repo.git_connection_id)
  .single();

if (connError) throw connError;
```

**Schema**:
- `id`: string - Unique identifier
- `access_token`: string (nullable) - GitHub access token
- `vault_secret_id`: string (nullable) - Reference to vault secret
- `workspace_id`: string - Associated workspace

**Security Note**: Access tokens may be stored directly or referenced via `vault_secret_id` for enhanced security.

#### Function Checkpoints

**Table**: `function_checkpoints`

**Location**: Referenced in `src/components/AIDocumentationSpecialistPanel.tsx` (lines 55-92)

**Purpose**: Stores checkpoint data for resumable AI operations.

**Query Example** (lines 55-92):
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
      
      // Restore configuration from checkpoint
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
    }
  } catch (error) {
    console.error('[RESUME] Error loading checkpoint:', error);
  }
};
```

**Schema**:
- `execution_id`: string - Associated execution identifier
- `execution_type`: string - Type of operation ('documentation', 'compliance', etc.)
- `checkpoint_data`: JSON - Serialized checkpoint state
- `created_at`: timestamp - Checkpoint creation time

**Checkpoint Data Structure** (for documentation):
```typescript
{
  scopesToGenerate: string[];        // e.g., ['user_facing', 'internal_developer']
  userInstructions: string;          // User-provided instructions
  sourceRepositories: Array<{
    fullName: string;
    scope: 'full' | 'commit';
    commitSha?: string;
  }>;
}
```

---

### Service Layer

#### Workflow Service

**Location**: `src/services/workflowService.ts` (referenced in components)

**Purpose**: Manages workflow configurations for different AI functions.

**Methods**:

##### getWorkflowConfiguration

**Referenced in**: `src/components/AIComplianceAnalystPanel.tsx` (line 48)

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

**Parameters**:
- `workspaceId`: string - Current workspace identifier
- `functionName`: string - Function name ('Compliance', 'Documentation', etc.)

**Returns**:
```typescript
{
  enablement: 'disabled' | 'analysis_only' | 'analysis_and_fix';
  configuration?: {
    // Function-specific configuration
  };
}
```

##### getWorkflowConfigurations

**Referenced in**: `src/components/AIDocumentationSpecialistPanel.tsx` (line 97)

```typescript
const loadDocumentationConfig = async () => {
  if (!currentWorkspace) return;
  
  setLoadingWorkflowConfig(true);
  try {
    const configs = await workflowService.getWorkflowConfigurations(currentWorkspace.id);
    const config = configs.find(c => c.function_name === 'Documentation');
    setDocConfig(config);
  } catch (error) {
    console.error('Error loading documentation config:', error);
  } finally {
    setLoadingWorkflowConfig(false);
  }
};
```

**Parameters**:
- `workspaceId`: string - Current workspace identifier

**Returns**: Array of workflow configurations for all functions in the workspace.

---

## External API Integrations

### GitHub API

**Location**: `src/components/AIDocumentationSpecialistPanel.tsx` (lines 200-216)

**Purpose**: Fetches commit history and repository information from GitHub.

**Authentication**: Uses GitHub personal access token from git_connections table or vault.

**Endpoint**: `https://api.github.com/repos/{owner}/{repo}/commits`

**Implementation Example** (lines 200-216):
```typescript
const loadCommitsForRepository = async (repoFullName: string) => {
  // ... token retrieval logic ...

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
};
```

**Response Format**:
```typescript
Array<{
  sha: string;           // Commit SHA hash
  message: string;       // First line of commit message
  date: string;          // Formatted commit date
}>
```

**Rate Limiting**: GitHub API has rate limits (5,000 requests/hour for authenticated requests). The application does not currently implement rate limit handling beyond error catching.

**Error Handling** (lines 217-223):
```typescript
catch (error) {
  console.error('Error loading commits:', error);
  toast({
    title: "Failed to Load Commits",
    description: "Could not fetch commits for this repository",
    variant: "destructive",
  });
}
```

---

## Usage

### Setting Up API Client

The Supabase client is automatically configured in the application. Ensure environment variables are set:

**`.env.local`** (create this file in project root):
```env
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### Making API Calls

#### Example 1: Invoking an Edge Function

```typescript
import { supabase } from "@/integrations/supabase/client";

const analyzeCompliance = async (repository: Repository) => {
  const { data, error } = await supabase.functions.invoke('code-compliance-analyzer', {
    body: {
      repository_id: repository.id,
      repository_name: repository.name,
      repository_full_name: repository.full_name,
      repository_url: repository.html_url,
      workspaceId: currentWorkspace.id,
      instructions: "Focus on GDPR compliance"
    }
  });

  if (error) {
    console.error('Analysis failed:', error);
    return { success: false, error: error.message };
  }

  return data;
};
```

#### Example 2: Querying Database

```typescript
import { supabase } from "@/integrations/supabase/client";

const fetchEnabledRepos = async (workspaceId: string) => {
  const { data, error } = await supabase
    .from('repository_settings')
    .select(`
      id,
      name,
      full_name,
      orchestrai_enabled,
      git_connections!inner(workspace_id)
    `)
    .eq('git_connections.workspace_id', workspaceId)
    .eq('orchestrai_enabled', true);

  if (error) throw error;
  return data;
};
```

#### Example 3: Using Workflow Service

```typescript
import { workflowService } from "@/services/workflowService";

const checkPermissions = async (workspaceId: string) => {
  const config = await workflowService.getWorkflowConfiguration(
    workspaceId,
    'Compliance'
  );

  const isEnabled = config && (
    config.enablement === 'analysis_only' || 
    config.enablement === 'analysis_and_fix'
  );

  return isEnabled;
};
```

### Handling Responses

#### Success Handling

All API responses follow a consistent pattern. Check for the `success` field or handle the `data` object:

```typescript
const { data, error } = await supabase.functions.invoke('function-name', {
  body: { /* request body */ }
});

if (error) {
  // Handle error case
  console.error('API error:', error);
  return;
}

if (data?.success) {
  // Handle success case
  console.log('Analysis ID:', data.analysis_id);
}
```

#### Error Handling

Standard error handling pattern used throughout the application:

```typescript
try {
  const { data, error } = await supabase.functions.invoke('function-name', {
    body: { /* request body */ }
  });

  if (error) {
    throw new Error(error.message);
  }

  // Process data
  return { success: true, data };
} catch (err) {
  console.error('Operation failed:', err);
  return { 
    success: false, 
    error: err instanceof Error ? err.message : 'Unknown error'
  };
}
```

#### Toast Notifications

The application uses toast notifications for user feedback (`src/components/AIComplianceAnalystPanel.tsx`, lines 249-260):

```typescript
import { useToast } from "@/hooks/use-toast";

const { toast } = useToast();

// Success notification
toast({
  title: "Analysis Complete",
  description: `Compliance analysis completed for ${repository.name}`,
});

// Error notification
toast({
  title: "Analysis Failed",
  description: result.error || "Failed to analyze repository",
  variant: "destructive",
});
```

### Permission Checks

Before making API calls, components check for workspace permissions using the `useWorkspaceFunctionPermissions` hook:

**Example from** `src/components/AIComplianceAnalystPanel.tsx` (lines 38-39):

```typescript
const { hasPermission, isLoading: permissionLoading, isFreePlan } = 
  useWorkspaceFunctionPermissions('Compliance');

// Later in the component
if (!hasPermission && !isFreePlan) {
  toast({
    title: "Permission Denied",
    description: "You do not have permission to run compliance analysis.",
    variant: "destructive",
  });
  return;
}
```

### Resumable Operations with Checkpoints

For long-running operations, the application supports resuming from checkpoints:

**Implementation** (`src/components/AIDocumentationSpecialistPanel.tsx`, lines 55-92):

```typescript
// Check for resume data
if (resumeExecution?.hasCheckpoints) {
  loadCheckpointData();
}

// Load checkpoint function
const loadCheckpointData = async () => {
  if (!resumeExecution?.id) return;
  
  const { data: checkpoint, error } = await supabase
    .from('function_checkpoints')
    .select('checkpoint_data')
    .eq('execution_id', resumeExecution.id)
    .eq('execution_type', 'documentation')
    .order('created_at', { ascending: false })
    .limit(1)
    .single();

  if (checkpoint?.checkpoint_data) {
    // Restore state from checkpoint
    const checkpointData = checkpoint.checkpoint_data;
    setInstructions(checkpointData.userInstructions);
    // ... restore other configuration
  }
};
```

---

## API Patterns and Best Practices

### 1. Workspace Context

All API operations require a workspace context. Components use the `useWorkspace` hook:

```typescript
import { useWorkspace } from "@/contexts/WorkspaceContext";

const { currentWorkspace } = useWorkspace();

if (!currentWorkspace) {
  return { success: false, error: "No workspace selected" };
}
```

### 2. Loading States

Components track loading states for better UX:

```typescript
const [isStarting, setIsStarting] = useState(false);
const [loadingWorkflowConfig, setLoadingWorkflowConfig] = useState(false);

const performOperation = async () => {
  setIsStarting(true);
  try {
    const result = await apiCall();
    return result;
  } finally {
    setIsStarting(false);
  }
};
```

### 3. Conditional Feature Access

Features are conditionally enabled based on configuration:

```typescript
const [isComplianceAllowed, setIsComplianceAllowed] = useState(true);

// Check configuration
const config = await workflowService.getWorkflowConfiguration(
  currentWorkspace.id, 
  'Compliance'
);

const isAllowed = config && (
  config.enablement === 'analysis_only' || 
  config.enablement === 'analysis_and_fix'
);
setIsComplianceAllowed(isAllowed);

// Use in UI
<Button disabled={!isComplianceAllowed}>
  Start Analysis
</Button>
```

### 4. Progress Dialogs

Long-running operations use progress dialogs with checkpointing:

```typescript
const [showProgressDialog, setShowProgressDialog] = useState(false);

const startOperation = async () => {
  setShowProgressDialog(true);
};

const handleProgressComplete = (result: { success: boolean; error?: string }) => {
  setShowProgressDialog(false);
  
  if (result.success) {
    toast({ title: "Complete", description: "Operation succeeded" });
  } else {
    toast({ 
      title: "Failed", 
      description: result.error,
      variant: "destructive"
    });
  }
};

<ComplianceProgressDialog
  isOpen={showProgressDialog}
  onClose={() => setShowProgressDialog(false)}
  onComplete={handleProgressComplete}
  onStartAnalysis={handleStartAnalysis}
/>
```

### 5. External Link Handling

For workflow configuration, components provide links to settings:

```typescript
<Button
  onClick={() => window.open('/product/workflow', '_blank')}
  variant="outline"
>
  <ExternalLink className="h-4 w-4 mr-2" />
  Go to Workflow Settings
</Button>
```

---

## Error Reference

### Common Error Scenarios

#### 1. No Workspace Selected
```typescript
{ success: false, error: "No workspace selected" }
```
**Cause**: Operation attempted without active workspace context  
**Resolution**: Ensure user has selected a workspace before API calls

#### 2. Permission Denied
```typescript
{ success: false, error: "Permission denied" }
```
**Cause**: User lacks required workspace function permissions  
**Resolution**: Contact workspace admin to grant permissions

#### 3. Configuration Missing
```typescript
{ success: false, error: "Configuration not found" }
```
**Cause**: Required workflow configuration not set  
**Resolution**: Navigate to `/product/workflow` and configure the function

#### 4. Analysis Failed
```typescript
{ success: false, error: "Analysis failed" }
```
**Cause**: Edge function encountered an error during processing  
**Resolution**: Check edge function logs and retry with different parameters

#### 5. GitHub API Failure
```typescript
{ error: "Failed to fetch commits" }
```
**Cause**: GitHub API request failed (rate limit, auth, network)  
**Resolution**: Verify access token and check rate limits

---

## Navigation and Routing

The application uses React Router for client-side routing configured in `src/App.tsx` (lines 64-92):

### Available Routes

| Route | Component | Purpose |
|-------|-----------|---------|
| `/` | Index | Landing page |
| `/enterprise` | Enterprise | Enterprise information |
| `/product` | Product | Main product dashboard |
| `/product/code` | ProductCode | Code management |
| `/product/code-connected` | ProductCodeConnected | Connected repositories |
| `/product/testing` | ProductTesting | Testing interface |
| `/product/code-quality` | ProductCodeQuality | Code quality dashboard |
| `/product/code-quality/results` | ProductCodeQualityResults | Quality analysis results |
| `/product/workflow` | ProductWorkflow | Workflow configuration |
| `/product/documentation` | ProductDocumentation | Documentation management |
| `/product/compliance` | ProductCompliance | Compliance dashboard |
| `/product/compliance/results` | ProductComplianceResults | Compliance results |
| `/product/workspace-management` | ProductWorkspaceManagement | Workspace settings |
| `/product/permissions` | ProductPermissions | Permission management |
| `/workspace-management` | WorkspaceManagement | Workspace overview |
| `/account` | Account | User account settings |
| `/cost-analysis/:workspaceId` | CostAnalysis | Cost tracking per workspace |
| `/pricing` | Pricing | Pricing plans |
| `/github-success` | GitHubSuccess | GitHub OAuth success |
| `/github-error` | GitHubError | GitHub OAuth error |
| `/privacy` | PrivacyPolicy | Privacy policy |
| `/terms` | TermsOfService | Terms of service |

### Programmatic Navigation

```typescript
// Navigate to results page
window.location.href = `/product/compliance/results?repository=${encodeURIComponent(repository.name)}`;

// Open in new tab
window.open('/product/workflow', '_blank');
```

---

## TypeScript Interfaces

### Repository Type

```typescript
interface Repository {
  id: string;
  name: string;
  full_name: string;
  html_url: string;
  private: boolean;
}
```

### Compliance Panel Props

```typescript
interface AIComplianceAnalystPanelProps {
  repository: Repository;
  isOpen: boolean;
  onClose: () => void;
  onAnalysisComplete?: (analysisId: string) => void;
}
```

### Documentation Panel Props

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

---

## Testing

The application includes comprehensive test coverage for configuration files and components.

### ESLint Configuration Tests

**Location**: `orchestrai_tests/*/javascript/tests/eslint.config.test.js`

**Example Test Suite** (from `orchestrai_tests/2025-08-24_08-38-11/javascript/tests/eslint.config.test.js`):

```javascript
const eslintConfig = require('../../eslint.config.js');

describe('ESLint Configuration', () => {
  test('should export a valid configuration object', () => {
    expect(eslintConfig).toBeDefined();
    expect(typeof eslintConfig).toBe('object');
  });

  test('should have required configuration properties', () => {
    expect(eslintConfig).toHaveProperty('env');
    expect(eslintConfig).toHaveProperty('extends');
    expect(eslintConfig).toHaveProperty('parser');
    expect(eslintConfig).toHaveProperty('parserOptions');
    expect(eslintConfig).toHaveProperty('plugins');
    expect(eslintConfig).toHaveProperty('rules');
  });

  test('should configure environment settings', () => {
    expect(eslintConfig.env).toEqual(
      expect.objectContaining({
        browser: true,
        es2021: true,
        node: true,
        jest: true
      })
    );
  });
});
```

### Component Tests

**Location**: `orchestrai_tests/*/typescript/tests/`

**Example: App Component Tests** (from `orchestrai_tests/2025-08-24_08-38-11/typescript/tests/App.test.tsx`):

```typescript
import { render, screen } from '@testing-library/react';
import { BrowserRouter } from 'react-router-dom';
import App from '../../src/App';

describe('App Component', () => {
  test('renders without crashing', () => {
    render(
      <BrowserRouter>
        <App />
      </BrowserRouter>
    );
    expect(screen.getByTestId('header')).toBeInTheDocument();
  });

  test('renders all main components', () => {
    render(
      <BrowserRouter>
        <App />
      </BrowserRouter>
    );
    
    expect(screen.getByTestId('header')).toBeInTheDocument();
    expect(screen.getByTestId('sidebar')).toBeInTheDocument();
    expect(screen.getByTestId('main-content')).toBeInTheDocument();
  });
});
```

### Running Tests

```bash
# Run all tests
npm test

# Run specific test file
npm test -- eslint.config.test.js

# Run with coverage
npm test -- --coverage
```

---

## Configuration Files

### PostCSS Configuration

**Location**: `postcss.config.js`

```javascript
export default {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
  },
}
```

This configuration enables:
- **Tailwind CSS**: Utility-first CSS framework
- **Autoprefixer**: Automatic vendor prefix addition

### ESLint Configuration

**Location**: `eslint.config.js`

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
        { allowConstantEx