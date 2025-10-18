# orchestrai-dev - API Documentation

## Overview

This document provides comprehensive API documentation for the OrchestrAI platform, covering all edge functions, API endpoints, authentication mechanisms, and integration patterns. OrchestrAI is a collaborative AI platform for software development that enables automated code analysis, testing, compliance checking, and documentation generation through GitHub integration.

The API layer consists of Supabase Edge Functions that handle various AI-powered operations, GitHub integrations, and workspace management. All functions require authentication and operate within the context of user workspaces.

## Edge Functions

### Function Location
All edge functions are located in `supabase/functions/` directory (referenced in source code but not provided in context).

### Core Edge Functions

Based on the source code analysis, the following edge functions are implemented:

#### 1. **code-compliance-analyzer**

**Location**: `supabase/functions/code-compliance-analyzer`

**Purpose**: Performs comprehensive compliance analysis on GitHub repositories, checking for regulatory requirements, data privacy, security standards, and audit trails.

**Request Body**:
```typescript
{
  repository_id: string;           // GitHub repository ID
  repository_name: string;         // Repository name (e.g., "my-repo")
  repository_full_name: string;    // Full name (e.g., "owner/my-repo")
  repository_url: string;          // GitHub repository URL
  workspaceId: string;            // OrchestrAI workspace ID
  instructions: string;            // Analysis instructions
}
```

**Response**:
```typescript
{
  success: boolean;
  analysis_id?: string;   // Unique analysis identifier
  error?: string;         // Error message if failed
}
```

**Implementation Reference**: `src/components/AIComplianceAnalystPanel.tsx` (lines 107-130)

**Usage Example**:
```typescript
const { data, error } = await supabase.functions.invoke('code-compliance-analyzer', {
  body: {
    repository_id: repo.id,
    repository_name: repo.name,
    repository_full_name: repo.full_name,
    repository_url: repo.html_url,
    workspaceId: currentWorkspace.id,
    instructions: "Perform comprehensive compliance analysis..."
  }
});
```

**Authentication**: Requires authenticated Supabase session (JWT token)

**Rate Limiting**: Not explicitly implemented in provided code

**Error Handling**: Returns structured error response with `success: false` and `error` message field

---

#### 2. **vault-retrieve**

**Location**: `supabase/functions/vault-retrieve`

**Purpose**: Securely retrieves encrypted secrets from the vault system, particularly GitHub access tokens.

**Request Body**:
```typescript
{
  secret_id: string;  // Vault secret identifier
}
```

**Response**:
```typescript
{
  secret_value: string;  // Decrypted secret value
}
```

**Implementation Reference**: `src/components/AIDocumentationSpecialistPanel.tsx` (lines 262-265)

**Usage Example**:
```typescript
const { data: vaultData } = await supabase.functions.invoke('vault-retrieve', {
  body: { secret_id: connection.vault_secret_id }
});
const accessToken = vaultData?.secret_value;
```

**Authentication**: Requires authenticated Supabase session

**Security**: Uses vault system for encrypted storage and retrieval of sensitive credentials

---

## Database Schema

### Repository Settings Table

**Table Name**: `repository_settings`

**Purpose**: Stores GitHub repository configurations and OrchestrAI enablement status

**Schema**:
```sql
CREATE TABLE repository_settings (
  id UUID PRIMARY KEY,
  repo_id TEXT,
  name TEXT,
  full_name TEXT,
  orchestrai_enabled BOOLEAN,
  git_connection_id UUID REFERENCES git_connections(id),
  -- additional columns
);
```

**Query Example** (from `src/components/AIDocumentationSpecialistPanel.tsx`, lines 231-243):
```typescript
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
```

---

### Git Connections Table

**Table Name**: `git_connections`

**Purpose**: Stores GitHub OAuth connections and access tokens (encrypted or vault-referenced)

**Schema**:
```sql
CREATE TABLE git_connections (
  id UUID PRIMARY KEY,
  workspace_id UUID,
  access_token TEXT,           -- May be null if using vault
  vault_secret_id TEXT,        -- Reference to vault secret
  -- additional columns
);
```

**Query Example** (from `src/components/AIDocumentationSpecialistPanel.tsx`, lines 254-258):
```typescript
const { data: connection, error: connError } = await supabase
  .from('git_connections')
  .select('access_token, vault_secret_id')
  .eq('id', repo.git_connection_id)
  .single();
```

---

### Function Checkpoints Table

**Table Name**: `function_checkpoints`

**Purpose**: Stores execution state for resumable long-running operations

**Schema**:
```sql
CREATE TABLE function_checkpoints (
  execution_id UUID,
  execution_type TEXT,          -- e.g., 'documentation', 'compliance'
  checkpoint_data JSONB,        -- Stores execution state
  created_at TIMESTAMP,
  -- additional columns
);
```

**Query Example** (from `src/components/AIDocumentationSpecialistPanel.tsx`, lines 158-169):
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

**Checkpoint Data Structure** (lines 171-201):
```typescript
{
  scopesToGenerate: string[],        // e.g., ['user_facing', 'internal_developer', 'sbom']
  userInstructions: string,
  sourceRepositories: Array<{
    fullName: string,
    scope: 'full' | 'commit',
    commitSha?: string
  }>
}
```

---

## Authentication & Authorization

### Authentication Mechanism

**Type**: JWT-based authentication via Supabase Auth

**Implementation**: All API requests automatically include authentication headers when using the Supabase client

**Session Management**: `src/App.tsx` (lines 5-6, 44-46)
```typescript
import { AuthProvider } from "@/contexts/AuthContext";

<AuthProvider>
  <WorkspaceProvider>
    <AppContent />
  </WorkspaceProvider>
</AuthProvider>
```

**Required Headers**: 
- `Authorization: Bearer <jwt_token>` (automatically handled by Supabase client)

---

### Permission System

**Implementation**: Workspace-based function permissions

**Permission Check Pattern** (from `src/components/AIComplianceAnalystPanel.tsx`, lines 29-30):
```typescript
const { hasPermission, isLoading: permissionLoading, isFreePlan } = 
  useWorkspaceFunctionPermissions('Compliance');
```

**Permission Levels**:
- **Free Plan**: Access to all functions with limitations
- **Paid Plans**: Function-level permissions managed by workspace admins

**Permission Enforcement** (lines 35-37, 138-146):
```typescript
// Show restriction for paid plans without permission
const showPermissionRestriction = !isFreePlan && !hasPermission && !permissionLoading;

// Enforce permission before execution
if (!hasPermission && !isFreePlan) {
  toast({
    title: "Permission Denied", 
    description: "You do not have permission to run compliance analysis.",
    variant: "destructive",
  });
  return;
}
```

---

## GitHub API Integration

### Authentication with GitHub

**Access Token Retrieval Pattern** (from `src/components/AIDocumentationSpecialistPanel.tsx`, lines 254-271):
```typescript
// 1. Fetch connection record
const { data: connection, error: connError } = await supabase
  .from('git_connections')
  .select('access_token, vault_secret_id')
  .eq('id', repo.git_connection_id)
  .single();

// 2. Get token from vault if needed
let accessToken = connection.access_token;
if (!accessToken && connection.vault_secret_id) {
  const { data: vaultData } = await supabase.functions.invoke('vault-retrieve', {
    body: { secret_id: connection.vault_secret_id }
  });
  accessToken = vaultData?.secret_value;
}

// 3. Validate token exists
if (!accessToken) throw new Error('No access token available');
```

---

### GitHub API Requests

**Example: Fetching Repository Commits** (lines 273-283):
```typescript
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
```

**Response Format**:
```typescript
Array<{
  sha: string;
  commit: {
    message: string;
    author: {
      date: string;
    };
  };
}>
```

---

## Workflow Configuration Service

### Service Location

**File**: `src/services/workflowService.ts` (referenced but not provided)

### API Methods

**1. Get Workflow Configuration**:
```typescript
workflowService.getWorkflowConfiguration(
  workspaceId: string,
  functionName: 'Compliance' | 'Documentation' | 'CodeQuality' | 'Testing'
): Promise<WorkflowConfig>
```

**Implementation Reference**: `src/components/AIComplianceAnalystPanel.tsx` (lines 60-70)
```typescript
const config = await workflowService.getWorkflowConfiguration(
  currentWorkspace.id, 
  'Compliance'
);
```

**Configuration Object Structure**:
```typescript
{
  enablement: 'disabled' | 'analysis_only' | 'analysis_and_fix';
  configuration?: {
    repo?: {
      name: string;
      full_name?: string;
    };
    folder?: string;
    contentStructure?: {
      name: string;
      intro?: boolean;
      tutorials?: boolean;
      howTo?: boolean;
      reference?: boolean;
      concepts?: boolean;
      troubleshooting?: boolean;
      releaseNotes?: boolean;
    };
  };
}
```

---

**2. Get All Workflow Configurations**:
```typescript
workflowService.getWorkflowConfigurations(
  workspaceId: string
): Promise<WorkflowConfig[]>
```

**Implementation Reference**: `src/components/AIDocumentationSpecialistPanel.tsx` (lines 207-210)
```typescript
const configs = await workflowService.getWorkflowConfigurations(currentWorkspace.id);
const config = configs.find(c => c.function_name === 'Documentation');
```

---

## React Query Integration

### Query Client Setup

**Location**: `src/App.tsx` (lines 35, 37-51)

```typescript
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";

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

**Purpose**: Manages server state, caching, and data synchronization for API requests

---

## Type Definitions

### Repository Type

**Location**: Referenced in `src/components/AIComplianceAnalystPanel.tsx` (line 14)

```typescript
import type { Repository } from "@/types/github";

interface Repository {
  id: string;
  name: string;
  full_name: string;
  html_url: string;
  private: boolean;
  // additional fields
}
```

---

### Workspace Context Types

**Location**: `src/contexts/WorkspaceContext.tsx` (referenced in multiple files)

**Hook Usage**:
```typescript
const { currentWorkspace } = useWorkspace();
```

**Workspace Object**:
```typescript
{
  id: string;
  // additional workspace fields
}
```

---

## Error Handling Patterns

### Standard Error Response

All edge functions follow this error response pattern:
```typescript
{
  success: false,
  error: string;  // Human-readable error message
}
```

### Client-Side Error Handling

**Toast Notifications** (from `src/components/AIComplianceAnalystPanel.tsx`, lines 217-222):
```typescript
toast({
  title: "Analysis Failed",
  description: result.error || "Failed to analyze repository",
  variant: "destructive",
});
```

**Try-Catch Pattern** (lines 108-130):
```typescript
try {
  const { data, error } = await supabase.functions.invoke('code-compliance-analyzer', {
    body: { /* request body */ }
  });

  if (error) {
    console.error('Compliance analysis error:', error);
    return { success: false, error: error.message };
  }

  if (data?.success && data?.analysis_id) {
    return { success: true, analysisId: data.analysis_id };
  } else {
    return { success: false, error: data?.error || 'Analysis failed' };
  }
} catch (err) {
  console.error('Error calling compliance analyzer:', err);
  return { 
    success: false, 
    error: err instanceof Error ? err.message : 'Unknown error occurred' 
  };
}
```

---

## Environment Variables

### Required Environment Variables

Based on the code structure and Supabase integration:

1. **Supabase Configuration**:
   - `SUPABASE_URL`: Supabase project URL
   - `SUPABASE_ANON_KEY`: Supabase anonymous key

2. **GitHub Integration**:
   - OAuth credentials (managed through Supabase Auth)
   - Access tokens stored in database or vault

**Import Pattern**: `src/integrations/supabase/client` (referenced throughout codebase)

---

## Progress Tracking

### Real-Time Progress Updates

**Implementation**: Uses dialog components with polling or subscription mechanisms

**Compliance Progress Dialog** (from `src/components/AIComplianceAnalystPanel.tsx`, lines 247-254):
```typescript
<ComplianceProgressDialog
  isOpen={showProgressDialog}
  onClose={() => setShowProgressDialog(false)}
  repositoryName={repository.name}
  onComplete={handleProgressComplete}
  onStartAnalysis={handleStartAnalysis}
/>
```

**Documentation Progress Dialog** (from `src/components/AIDocumentationSpecialistPanel.tsx`, lines 749-761):
```typescript
<DocumentationProgressDialog
  isOpen={showProgressDialog}
  onClose={() => setShowProgressDialog(false)}
  action={action}
  docConfig={docConfig}
  repositoryName={docConfig?.configuration?.repo?.name || null}
  instructions={instructions}
  selectedScopes={selectedScopes}
  selectedContentStructure={selectedContentStructure}
  selectedRepositories={selectedRepositories}
  repositoryScopes={repositoryScopes}
  resumeExecutionId={resumeExecution?.id || null}
  onComplete={handleProgressComplete}
/>
```

**Callback Pattern**:
```typescript
const handleProgressComplete = (result: { 
  success: boolean; 
  analysisId?: string; 
  error?: string 
}) => {
  setShowProgressDialog(false);
  
  if (result.success) {
    // Handle success
    if (onAnalysisComplete) {
      onAnalysisComplete(result.analysisId);
    }
  } else {
    // Handle failure
  }
};
```

---

## Resumable Execution

### Checkpoint System

**Purpose**: Allows long-running operations to be paused and resumed

**Checkpoint Loading** (from `src/components/AIDocumentationSpecialistPanel.tsx`, lines 149-203):
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
      
      if (checkpointData.sourceRepositories) {
        const repos = checkpointData.sourceRepositories;
        setSelectedRepositories(repos.map((r: any) => r.fullName));
        
        const scopes: Record<string, any> = {};
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
    console.error('[RESUME] Error loading checkpoint:', error);
  }
};
```

**Resume Indicator** (lines 380-387):
```typescript
{resumeExecution?.hasCheckpoints && (
  <Alert className="border-green-200 bg-green-50">
    <CheckCircle className="h-4 w-4 text-green-600" />
    <AlertDescription className="text-green-800">
      <strong>Resuming from checkpoint:</strong> The AI will continue from where it left off.
    </AlertDescription>
  </Alert>
)}
```

---

## API Usage Examples

### Complete Compliance Analysis Flow

```typescript
import { supabase } from "@/integrations/supabase/client";
import { useWorkspace } from "@/contexts/WorkspaceContext";
import { useWorkspaceFunctionPermissions } from "@/hooks/useWorkspaceFunctionPermissions";

const ComplianceAnalysisComponent = () => {
  const { currentWorkspace } = useWorkspace();
  const { hasPermission, isFreePlan } = useWorkspaceFunctionPermissions('Compliance');

  const runAnalysis = async (repository: Repository) => {
    // 1. Check permissions
    if (!hasPermission && !isFreePlan) {
      throw new Error("Permission denied");
    }

    // 2. Invoke edge function
    const { data, error } = await supabase.functions.invoke('code-compliance-analyzer', {
      body: {
        repository_id: repository.id,
        repository_name: repository.name,
        repository_full_name: repository.full_name,
        repository_url: repository.html_url,
        workspaceId: currentWorkspace.id,
        instructions: "Perform comprehensive compliance analysis"
      }
    });

    // 3. Handle response
    if (error || !data?.success) {
      throw new Error(data?.error || error?.message || "Analysis failed");
    }

    // 4. Return analysis ID
    return data.analysis_id;
  };

  return (
    <button onClick={() => runAnalysis(selectedRepo)}>
      Start Analysis
    </button>
  );
};
```

---

### Repository Data Fetching

```typescript
import { supabase } from "@/integrations/supabase/client";

const fetchEnabledRepositories = async (workspaceId: string) => {
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
    .eq('git_connections.workspace_id', workspaceId)
    .eq('orchestrai_enabled', true);

  if (error) throw error;
  return repos;
};
```

---

### GitHub Commits Fetching

```typescript
import { supabase } from "@/integrations/supabase/client";

const fetchCommits = async (repoFullName: string, connectionId: string) => {
  // 1. Get access token
  const { data: connection, error: connError } = await supabase
    .from('git_connections')
    .select('access_token, vault_secret_id')
    .eq('id', connectionId)
    .single();

  if (connError) throw connError;

  let accessToken = connection.access_token;
  
  if (!accessToken && connection.vault_secret_id) {
    const { data: vaultData } = await supabase.functions.invoke('vault-retrieve', {
      body: { secret_id: connection.vault_secret_id }
    });
    accessToken = vaultData?.secret_value;
  }

  if (!accessToken) throw new Error('No access token available');

  // 2. Fetch from GitHub API
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
  
  // 3. Format response
  return commits.map((commit: any) => ({
    sha: commit.sha,
    message: commit.commit.message.split('\n')[0],
    date: new Date(commit.commit.author.date).toLocaleDateString()
  }));
};
```

---

## Best Practices

### 1. Always Check Permissions
```typescript
const { hasPermission, isFreePlan } = useWorkspaceFunctionPermissions('FunctionName');

if (!hasPermission && !isFreePlan) {
  // Show error and return
}
```

### 2. Handle Loading States
```typescript
const [isLoading, setIsLoading] = useState(false);

try {
  setIsLoading(true);
  // API call
} finally {
  setIsLoading(false);
}
```

### 3. Provide User Feedback
```typescript
toast({
  title: "Operation Complete",
  description: "Your request has been processed successfully",
});
```

### 4. Validate Configuration Before Execution
```typescript
const checkWorkflowConfiguration = async () => {
  const config = await workflowService.getWorkflowConfiguration(
    workspaceId, 
    functionName
  );
  
  if (!config || !config.configuration?.requiredField) {
    // Show configuration required message
    return false;
  }
  
  return true;
};
```

### 5. Use Structured Error Handling
```typescript
try {
  const result = await apiCall();
  
  if (!result.success) {
    return { success: false, error: result.error };
  }
  
  return { success: true, data: result.data };
} catch (err) {
  console.error('Error:', err);
  return { 
    success: false, 
    error: err instanceof Error ? err.message : 'Unknown error' 
  };
}
```

---

## Rate Limits

**Current Implementation**: No explicit rate limiting found in provided source code. Rate limits would be enforced at the Supabase Edge Function level or database level through Row Level Security (RLS) policies.

**Recommendation**: Implement client-side debouncing for user-triggered operations:
```typescript
const debouncedAnalysis = useMemo(
  () => debounce(runAnalysis, 1000),
  []
);
```

---

## Versioning

**API Version**: Not explicitly versioned in provided code. The platform uses rolling updates with database migrations for schema changes.

---

## Support

**Documentation Navigation** (from `src/App.tsx`, lines 46-79):
- Product Information: `/organization-information` or `/product/org-information`
- Code Analysis: `/code-analysis`
- Testing: `/testing`
- Compliance: `/product/compliance`
- Documentation: `/product/documentation`
- Workflow Settings: `/product/workflow`

**Support Pages**:
- Privacy Policy: `/privacy`
- Terms of Service: `/terms`