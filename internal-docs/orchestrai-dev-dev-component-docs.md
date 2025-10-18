# OrchestrAI Component Documentation

## Overview

This document provides comprehensive technical documentation for the major React components in the OrchestrAI project. OrchestrAI is a workspace-based AI development platform that orchestrates code analysis, testing, compliance, and documentation workflows. The components documented here form the core user interface, handling authentication, workspace management, and AI-powered development operations.

The component architecture follows a modern React pattern using:
- **React 18** with TypeScript for type safety
- **Context API** for state management (`AuthContext`, `WorkspaceContext`)
- **React Query** (`@tanstack/react-query`) for server state management
- **React Router v6** for client-side routing
- **Shadcn/ui** components built on Radix UI primitives
- **Tailwind CSS** for styling

---

## Implementation

### Core Application Component

#### File: `src/App.tsx`

**Purpose**: Root application component that sets up routing, authentication, workspace context, and global providers.

**Key Features**:
- **Query Client Setup**: Configures React Query for data fetching and caching
- **Context Providers**: Wraps application in `AuthProvider` and `WorkspaceProvider`
- **Toast Notifications**: Integrates multiple toast systems (Shadcn Toaster and Sonner)
- **Welcome Modal**: Conditionally displays onboarding modal using `useWelcomeModal` hook
- **Route Configuration**: Defines all application routes including product features, management, and marketing pages

**Route Structure**:
```tsx
<Routes>
  {/* Landing & Marketing */}
  <Route path="/" element={<Index />} />
  <Route path="/enterprise" element={<Enterprise />} />
  <Route path="/pricing" element={<Pricing />} />
  
  {/* Product Features */}
  <Route path="/product" element={<Product />} />
  <Route path="/product/code" element={<ProductCode />} />
  <Route path="/product/code-connected" element={<ProductCodeConnected />} />
  <Route path="/product/testing" element={<ProductTesting />} />
  <Route path="/product/code-quality" element={<ProductCodeQuality />} />
  <Route path="/product/workflow" element={<ProductWorkflow />} />
  <Route path="/product/documentation" element={<ProductDocumentation />} />
  <Route path="/product/compliance" element={<ProductCompliance />} />
  
  {/* Management */}
  <Route path="/workspace-management" element={<WorkspaceManagement />} />
  <Route path="/account" element={<Account />} />
  <Route path="/cost-analysis/:workspaceId" element={<CostAnalysis />} />
  
  {/* OAuth & Legal */}
  <Route path="/github-success" element={<GitHubSuccess />} />
  <Route path="/github-error" element={<GitHubError />} />
  <Route path="/privacy" element={<PrivacyPolicy />} />
  <Route path="/terms" element={<TermsOfService />} />
  
  {/* 404 */}
  <Route path="*" element={<NotFound />} />
</Routes>
```

**Provider Hierarchy**:
```tsx
QueryClientProvider
  ├─ TooltipProvider
  │   ├─ Toaster (Shadcn)
  │   ├─ Sonner
  │   └─ BrowserRouter
  │       └─ AuthProvider
  │           └─ WorkspaceProvider
  │               └─ AppContent (Routes + WelcomeModal)
```

**State Management**:
- Uses `useWelcomeModal()` hook to control first-time user onboarding
- Welcome modal state persisted and conditionally shown on mount
- `handleWelcomeComplete` callback closes modal and updates user preferences

---

### AI Feature Panels

#### 1. AI Compliance Analyst Panel

**File**: `src/components/AIComplianceAnalystPanel.tsx`

**Purpose**: Provides interface for running AI-powered compliance analysis on repositories, checking for data privacy, security, access control, and regulatory requirements.

**Props Interface**:
```typescript
interface AIComplianceAnalystPanelProps {
  repository: Repository;
  isOpen: boolean;
  onClose: () => void;
  onAnalysisComplete?: (analysisId: string) => void;
}
```

**Key State Variables** (lines 23-34):
```typescript
const [instructions, setInstructions] = useState("Perform a comprehensive compliance analysis...");
const [isStarting, setIsStarting] = useState(false);
const [isComplianceAllowed, setIsComplianceAllowed] = useState(true);
const [loadingWorkflowConfig, setLoadingWorkflowConfig] = useState(false);
const [hasError, setHasError] = useState(false);
const [analysisInProgress, setAnalysisInProgress] = useState(false);
const [analysisProgress, setAnalysisProgress] = useState(0);
const [analysisComplete, setAnalysisComplete] = useState(false);
const [showProgressDialog, setShowProgressDialog] = useState(false);
```

**Permission Checking** (lines 38-52):
- Integrates `useWorkspaceFunctionPermissions('Compliance')` hook
- Checks if user has permission on paid plans (`hasPermission`, `isFreePlan`)
- Shows permission restriction alert if user lacks access
- Loads workflow configuration to verify compliance is enabled

**Workflow Configuration Check** (lines 54-71):
```typescript
const checkWorkflowConfiguration = async () => {
  if (!currentWorkspace) return;

  setLoadingWorkflowConfig(true);
  try {
    const config = await workflowService.getWorkflowConfiguration(
      currentWorkspace.id, 
      'Compliance'
    );
    
    // Compliance disabled by default; check enablement
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

**Analysis Execution** (lines 73-101):
```typescript
const handleStartAnalysis = async (): Promise<{
  success: boolean; 
  analysisId?: string; 
  error?: string 
}> => {
  try {
    // Invokes Supabase edge function
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

**UI Components**:
- **Permission Restriction Alert** (lines 175-182): Shows red alert if user lacks permission
- **Compliance Disabled Card** (lines 184-204): Displays warning and link to Workflow settings if compliance not enabled
- **Analysis Progress Card** (lines 206-228): Shows live progress bar during analysis
- **Analysis Complete Card** (lines 230-252): Displays success message with "View Results" button
- **Error Card** (lines 254-272): Shows error message with retry option
- **Instructions TextArea** (lines 274-283): Allows custom instructions for analysis
- **Repository Info Card** (lines 285-302): Displays repository metadata

**Progress Dialog Integration** (lines 339-348):
```typescript
<ComplianceProgressDialog
  isOpen={showProgressDialog}
  onClose={() => setShowProgressDialog(false)}
  repositoryName={repository.name}
  onComplete={handleProgressComplete}
  onStartAnalysis={handleStartAnalysis}
/>
```

**Start Analysis Button** (lines 312-337):
- Disabled if compliance not allowed, no permission, or already in progress
- Shows different text states: "Checking permissions...", "No Permission", "Starting...", "Analyzing...", "Start Analysis"
- Triggers `startAnalysis()` which opens `ComplianceProgressDialog`

---

#### 2. AI Documentation Specialist Panel

**File**: `src/components/AIDocumentationSpecialistPanel.tsx`

**Purpose**: Manages AI-powered documentation generation, supporting both migration of existing documentation and creation from scratch. Allows granular control over documentation scope, content structure, and repository selection.

**Props Interface** (lines 11-19):
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

**Key State Variables** (lines 29-48):
```typescript
// Core state
const [instructions, setInstructions] = useState(
  action === 'migrate' 
    ? "Analyze existing documentation and restructure..."
    : "Create comprehensive documentation from product analysis."
);
const [isStarting, setIsStarting] = useState(false);
const [loadingWorkflowConfig, setLoadingWorkflowConfig] = useState(false);
const [showProgressDialog, setShowProgressDialog] = useState(false);
const [docConfig, setDocConfig] = useState<any>(null);

// Scope selection
const [isAdvancedExpanded, setIsAdvancedExpanded] = useState(false);
const [selectedScopes, setSelectedScopes] = useState({
  userFacing: true,
  internal: true,
  sbom: true,
});

// Content structure selection
const [selectedContentStructure, setSelectedContentStructure] = useState({
  intro: true,
  tutorials: true,
  howTo: false,
  reference: true,
  concepts: false,
  troubleshooting: false,
  releaseNotes: false,
});

// Repository selection
const [selectedRepositories, setSelectedRepositories] = useState<string[]>([]);
const [availableRepositories, setAvailableRepositories] = useState<any[]>([]);
const [isRepositorySelectorExpanded, setIsRepositorySelectorExpanded] = useState(false);
const [repositoryScopes, setRepositoryScopes] = useState<Record<string, {
  scope: 'full' | 'commit';
  commitSha?: string;
  commitMessage?: string;
}>>({});
const [repositoryCommits, setRepositoryCommits] = useState<Record<string, Array<{
  sha: string;
  message: string;
  date: string;
}>>>({});
const [loadingCommits, setLoadingCommits] = useState<Record<string, boolean>>({});
```

**Resume Execution from Checkpoint** (lines 50-101):
```typescript
useEffect(() => {
  if (isOpen && currentWorkspace) {
    loadDocumentationConfig();
    loadEnabledRepositories();
    
    // Load checkpoint data if resuming
    if (resumeExecution?.hasCheckpoints) {
      loadCheckpointData();
    }
  }
}, [isOpen, currentWorkspace, resumeExecution]);

const loadCheckpointData = async () => {
  if (!resumeExecution?.id) return;
  
  try {
    console.log('[RESUME] Loading checkpoint data for execution:', resumeExecution.id);
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
        
        const scopes: Record<string, { scope: 'full' | 'commit'; commitSha?: string }> = {};
        repos.forEach((repo: any) => {
          scopes[repo.fullName] = {
            scope: repo.scope,
            commitSha: repo.commitSha
          };
        });
        setRepositoryScopes(scopes);
      }
      
      toast({
        title: "Configuration Restored",
        description: "Previous execution settings have been loaded",
      });
    }
  } catch (error) {
    console.error('[RESUME] Error loading checkpoint:', error);
  }
};
```

**Configuration Loading** (lines 103-134):
```typescript
const loadDocumentationConfig = async () => {
  if (!currentWorkspace) return;
  
  setLoadingWorkflowConfig(true);
  try {
    const configs = await workflowService.getWorkflowConfigurations(currentWorkspace.id);
    const config = configs.find(c => c.function_name === 'Documentation');
    
    setDocConfig(config);
    
    // Only set defaults if not resuming
    if (!resumeExecution) {
      // Enable all scopes by default
      setSelectedScopes({
        userFacing: true,
        internal: true,
        sbom: true,
      });
      
      // Initialize content structure from config
      if (config?.configuration?.contentStructure) {
        const structure = config.configuration.contentStructure;
        setSelectedContentStructure({
          intro: structure.intro ?? true,
          tutorials: structure.tutorials ?? true,
          howTo: structure.howTo ?? false,
          reference: structure.reference ?? true,
          concepts: structure.concepts ?? false,
          troubleshooting: structure.troubleshooting ?? false,
          releaseNotes: structure.releaseNotes ?? false,
        });
      }
    }
  } catch (error) {
    console.error('Error loading documentation config:', error);
  } finally {
    setLoadingWorkflowConfig(false);
  }
};
```

**Repository Selection** (lines 136-164):
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
    
    // Auto-select all repositories by default and set to full scope
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

**Commit Loading for Repositories** (lines 166-225):
```typescript
const loadCommitsForRepository = async (repoFullName: string) => {
  if (!currentWorkspace || repositoryCommits[repoFullName]) return;

  setLoadingCommits(prev => ({ ...prev, [repoFullName]: true }));

  try {
    const repo = availableRepositories.find(r => r.full_name === repoFullName);
    if (!repo) return;

    // Fetch connection with access token
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

    if (!response.ok) throw new Error('Failed to fetch commits');

    const commits = await response.json();
    const formattedCommits = commits.map((commit: any) => ({
      sha: commit.sha,
      message: commit.commit.message.split('\n')[0], // First line only
      date: new Date(commit.commit.author.date).toLocaleDateString()
    }));

    setRepositoryCommits(prev => ({ ...prev, [repoFullName]: formattedCommits }));
  } catch (error) {
    console.error('Error loading commits:', error);
    toast({
      title: "Failed to Load Commits",
      description: "Could not fetch commits for this repository",
      variant: "destructive",
    });
  } finally {
    setLoadingCommits(prev => ({ ...prev, [repoFullName]: false }));
  }
};
```

**UI Structure** (lines 300+):

1. **Resume Indicator** (lines 306-315): Shows green alert when resuming from checkpoint
2. **Action Type Card** (lines 317-332): Displays whether migrating or creating new documentation
3. **Migration Warning** (lines 334-342): Alert shown if migration selected but no documentation URL configured
4. **Configuration Required Card** (lines 344-364): Warning with link to Workflow settings if repository/folder not configured
5. **Instructions TextArea** (lines 366-380): Priority instructions that override configured defaults
6. **Advanced Options - Scope & Content** (lines 382-528):
   - Collapsible section with `Collapsible` component
   - **User Facing Documentation** checkbox with nested content structure options:
     - `/intro` (positioned Quickstart)
     - `/tutorials` (end-to-end, outcome-driven)
     - `/how-to` (task-centric, short)
     - `/reference` (API/SDK; autogenerated)
     - `/concepts` (architecture, models, quotas)
     - `/troubleshooting` (error catalog, logs)
     - `/release-notes` (automated)
   - **Internal Developer Documentation** checkbox
   - **SBOM** (Software Bill of Materials) checkbox

7. **Code Scope Selection** (lines 530-686):
   - Collapsible repository selector
   - Lists all OrchestrAI-enabled repositories
   - For each repository:
     - Checkbox to include/exclude
     - Radio buttons for "Whole Repo" vs "Specific Commit"
     - If "Specific Commit" selected, loads and displays last 20 commits
     - Commit selection UI with SHA, message, and date

8. **Configuration Info Card** (lines 688-720): Shows configured repository, folder, and content structure
9. **How it Works Card** (lines 722-736): Explains the documentation generation process

**Start Button Logic** (lines 738-767):
```typescript
<Button
  onClick={startDocumentation}
  disabled={
    !canStartDocumentation || 
    !hasAtLeastOneScope || 
    (action === 'migrate' && !hasDocumentationUrl) || 
    isStarting || 
    loadingWorkflowConfig
  }
>
  {loadingWorkflowConfig ? "Loading configuration..." :
   !canStartDocumentation ? "Configuration Required" :
   !hasAtLeastOneScope ? "Select at least one scope" :
   action === 'migrate' && !hasDocumentationUrl ? "Documentation URL Required" :
   isStarting ? <><Spinner />Starting...</> :
   <><Play />Generate Documentation</>
  }
</Button>
```

**Progress Dialog Integration** (lines 769-783):
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

---

## Usage

### Using the App Component

The `App` component is the entry point and requires no props. It's mounted in `src/main.tsx`:

```tsx
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import './index.css';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

The component automatically:
1. Sets up React Query client for data fetching
2. Initializes authentication context from Supabase session
3. Loads current workspace from context
4. Shows welcome modal on first visit
5. Handles all routing based on URL

---

### Using AI Compliance Analyst Panel

**Import**:
```typescript
import { AIComplianceAnalystPanel } from '@/components/AIComplianceAnalystPanel';
```

**Basic Usage**:
```tsx
import { useState } from 'react';
import { AIComplianceAnalystPanel } from '@/components/AIComplianceAnalystPanel';
import type { Repository } from '@/types/github';

function RepositoryList() {
  const [selectedRepo, setSelectedRepo] = useState<Repository | null>(null);
  const [isPanelOpen, setIsPanelOpen] = useState(false);

  const handleAnalysisComplete = (analysisId: string) => {
    console.log('Analysis completed:', analysisId);
    // Navigate to results page
    window.location.href = `/product/compliance/results?analysisId=${analysisId}`;
  };

  return (
    <>
      <button onClick={() => {
        setSelectedRepo(repository);
        setIsPanelOpen(true);
      }}>
        Analyze Compliance
      </button>

      {selectedRepo && (
        <AIComplianceAnalystPanel
          repository={selectedRepo}
          isOpen={isPanelOpen}
          onClose={() => setIsPanelOpen(false)}
          onAnalysisComplete={handleAnalysisComplete}
        />
      )}
    </>
  );
}
```

**Repository Object Structure**:
```typescript
interface Repository {
  id: number;
  name: string;
  full_name: string;
  html_url: string;
  private: boolean;
  // ... other GitHub repository fields
}
```

**Panel Behavior**:
- Opens as a slide-in panel from the right (fixed position, 384px width)
- Checks user permissions on mount via `useWorkspaceFunctionPermissions('Compliance')`
- Verifies compliance is enabled in workflow configuration
- If disabled, shows "Compliance Disabled" card with link to Workflow settings
- If user lacks permission (paid plan), shows "No Permission" alert
- On "Start Analysis" click, opens `ComplianceProgressDialog` with live progress
- After completion, shows "Analysis Complete" card with "View Results" button

---

### Using AI Documentation Specialist Panel

**Import**:
```typescript
import { AIDocumentationSpecialistPanel } from '@/components/AIDocumentationSpecialistPanel';
```

**Basic Usage** (Create New Documentation):
```tsx
import { useState } from 'react';
import { AIDocumentationSpecialistPanel } from '@/components/AIDocumentationSpecialistPanel';

function DocumentationPage() {
  const [isPanelOpen, setIsPanelOpen] = useState(false);

  const handleComplete = (result: { success: boolean; error?: string }) => {
    if (result.success) {
      console.log('Documentation generated successfully');
      // Refresh page or navigate
    } else {
      console.error('Documentation generation failed:', result.error);
    }
  };

  return (
    <>
      <button onClick={() => setIsPanelOpen(true)}>
        Create Documentation
      </button>

      <AIDocumentationSpecialistPanel
        isOpen={isPanelOpen}
        onClose={() => setIsPanelOpen(false)}
        action="create"
        hasDocumentationUrl={false}
        onComplete={handleComplete}
      />
    </>
  );
}
```

**Migrate Existing Documentation**:
```tsx
<AIDocumentationSpecialistPanel
  isOpen={isPanelOpen}
  onClose={() => setIsPanelOpen(false)}
  action="migrate"
  hasDocumentationUrl={true} // Must be true for migration
  onComplete={handleComplete}
/>
```

**Resume from Checkpoint**:
```tsx
<AIDocumentationSpecialistPanel
  isOpen={isPanelOpen}
  onClose={() => setIsPanelOpen(false)}
  action="create"
  hasDocumentationUrl={false}
  resumeExecution={{
    id: "execution_uuid_123",
    hasCheckpoints: true
  }}
  onComplete={handleComplete}
/>
```

**Panel Features**:
- **Scope Selection**: Choose between User Facing, Internal Developer, and SBOM documentation
- **Content Structure**: Customize which sections to generate (intro, tutorials, how-to, reference, concepts, troubleshooting, release notes)
- **Repository Selection**: Select multiple repositories and choose full repo or specific commit analysis
- **Priority Instructions**: Custom instructions override configured defaults
- **Checkpoint Resume**: Automatically restores previous configuration if resuming

**Repository Scope Options**:
- **Whole Repo**: Analyzes entire repository codebase
- **Specific Commit**: Generates documentation update based on a single commit
  - Shows last 20 commits when selected
  - Displays commit SHA, message, and date
  - Highlights selected commit

---

## Styling and Layout

### Component CSS Classes

All components use Tailwind CSS classes for styling. Key patterns:

**Panel Layout** (used by both AI panels):
```tsx
<div className="fixed inset-y-0 right-0 w-96 bg-white shadow-xl border-l border-gray-200 z-50 flex flex-col">
```
- `fixed inset-y-0 right-0`: Fixed positioning, full height, aligned right
- `w-96`: 384px width (24rem)
- `z-50`: High z-index to overlay other content
- `flex flex-col`: Vertical flex layout for header, content, footer

**Header Section**:
```tsx
<div className="flex items-center justify-between p-6 border-b border-gray-200">
```

**Scrollable Content**:
```tsx
<div className="flex-1 p-6 space-y-6 overflow-y-auto">
```
- `flex-1`: Expands to fill available space
- `overflow-y-auto`: Scrolls if content exceeds height
- `space-y-6`: 24px vertical spacing between children

**Footer Button Section**:
```tsx
<div className="p-6 border-t border-gray-200">
```

### Color Schemes

- **Compliance Panel**: Violet (`violet-600`, `violet-700`, `violet-50`)
- **Documentation Panel**: Purple (`purple-600`, `purple-700`, `purple-50`)
- **Alerts**: 
  - Red for errors/restrictions (`red-200`, `red-50`, `red-700`)
  - Amber for warnings (`amber-200`, `amber-50`, `amber-700`)
  - Green for success (`green-200`, `green-50`, `green-700`)
  - Blue for information (`blue-200`, `blue-50`, `blue-700`)

---

## Dependencies

### Core Libraries (from `src/App.tsx`)

```typescript
import { Toaster } from "@/components/ui/toaster";           // Shadcn toast notifications
import { Toaster as Sonner } from "@/components/ui/sonner"; // Alternative toast system
import { TooltipProvider } from "@/components/ui/tooltip";  // Tooltip context
import { QueryClient, QueryClientProvider } from "@tanstack/react-query"; // Data fetching
import { BrowserRouter, Routes, Route } from "react-router-dom"; // Routing
import { AuthProvider } from "@/contexts/AuthContext";      // Authentication state
import { WorkspaceProvider } from "@/contexts/WorkspaceContext"; // Workspace state
import { WelcomeModal } from "@/components/WelcomeModal";  // Onboarding modal
import { useWelcomeModal } from "@/hooks/useWelcomeModal"; // Welcome modal logic
```

### AI Panel Dependencies (from `src/components/AIComplianceAnalystPanel.tsx`)

```typescript
import { useState, useEffect } from "react";
import { X, Bot, FileText, AlertCircle, ExternalLink, Settings, Shield, CheckCircle, Clock, Play } from "lucide-react"; // Icons
import { Button } from "@/components/ui/button";
import { Label } from "@/components/ui/label";
import { Textarea } from "@/components/ui/textarea";
import { Card, CardContent, CardHeader, CardTitle } from "@/components/ui/card";
import { Progress } from "@/components/ui/progress";
import { Alert, AlertDescription } from "@/components/ui/alert";
import { useToast } from "@/hooks/use-toast";
import { useWorkspace } from "@/contexts/WorkspaceContext";
import { useWorkspaceFunctionPermissions } from "@/hooks/useWorkspaceFunctionPermissions";
import { workflowService } from "@/services/workflowService";
import { supabase } from "@/integrations/supabase/client";
import { ComplianceProgressDialog } from "./ComplianceProgressDialog";
import type { Repository } from "@/types/github";
```

### Documentation Panel Additional Dependencies

```typescript
import { Checkbox } from "@/components/ui/checkbox";
import { Collapsible, Coll