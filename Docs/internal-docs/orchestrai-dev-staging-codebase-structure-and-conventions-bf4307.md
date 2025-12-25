# OrchestRAI - Codebase Structure and Conventions

## Project Structure Overview

OrchestRAI follows a modern React application architecture with TypeScript, organized into clear functional layers. The project uses Vite as the build tool and follows a component-based architecture pattern.

### Root Directory Structure

```
orchestrai-dev/
├── src/                    # Application source code
├── public/                 # Static assets
├── supabase/              # Supabase configuration and migrations
├── orchestrai_tests/      # Test output directory
├── Docs/                  # Project documentation
├── node_modules/          # Dependencies
└── Configuration files    # Build and tooling configs
```

## Source Code Organization

### Core Directory Structure (`src/`)

The application follows a feature-based organization pattern with clear separation of concerns:

```
src/
├── components/            # React components
│   ├── ui/               # shadcn-ui base components
│   └── [Feature]*.tsx    # Feature-specific components
├── pages/                # Route-level page components
├── contexts/             # React Context providers
├── hooks/                # Custom React hooks
├── integrations/         # External service integrations
│   └── supabase/        # Supabase client and types
├── lib/                  # Utility libraries
├── services/             # Business logic and API services
├── types/                # TypeScript type definitions
├── utils/                # Helper functions and utilities
├── App.tsx               # Main application component
├── App.css               # Application-level styles
├── main.tsx              # Application entry point
└── index.css             # Global styles and Tailwind imports
```

## Component Organization

### UI Components (`src/components/ui/`)

**Location**: `src/components/ui/`

Base UI components from shadcn-ui library built on Radix UI primitives. These provide accessible, customizable building blocks for the application.

**Organization Pattern**:
- One component per file
- Named exports using component name
- Includes TypeScript interfaces for props
- Uses `class-variance-authority` for variant-based styling

**Example Component Structure**:
```typescript
// src/components/ui/button.tsx
import { cn } from "@/lib/utils";
import { buttonVariants } from "./button-variants";

interface ButtonProps {
  variant?: 'default' | 'outline' | 'ghost';
  size?: 'default' | 'sm' | 'lg';
  // ...other props
}

export function Button({ variant, size, className, ...props }: ButtonProps) {
  return (
    <button
      className={cn(buttonVariants({ variant, size }), className)}
      {...props}
    />
  );
}
```

**Available UI Components**:
- Buttons and interactive elements
- Form controls (Input, Select, Checkbox, etc.)
- Layout components (Card, Dialog, Sheet, etc.)
- Data display (Table, Badge, Progress, etc.)
- Navigation components (Tabs, Breadcrumb)
- Feedback components (Alert, Toast)

### Feature Components (`src/components/`)

**Location**: `src/components/`

Feature-specific components that implement business logic and compose UI components.

**Naming Convention**: `[Feature][Component].tsx`

**Examples**:
- `WorkspaceSelector.tsx` - Workspace selection component
- `RepositoryTable.tsx` - Repository listing table
- `CodeQualityPanel.tsx` - Code quality analysis panel
- `TestProgressDialog.tsx` - Test generation progress tracking
- `ComplianceConfiguration.tsx` - Compliance analysis configuration
- `AITestEngineerPanel.tsx` - AI test engineer interface

**Component Pattern**:
```typescript
// Feature component example
import { useState } from 'react';
import { Button } from '@/components/ui/button';
import { Card } from '@/components/ui/card';
import { useAuth } from '@/contexts/AuthContext';

interface MyFeatureProps {
  title: string;
  onAction?: () => void;
}

export function MyFeature({ title, onAction }: MyFeatureProps) {
  const [isLoading, setIsLoading] = useState(false);
  const { user } = useAuth();

  const handleAction = async () => {
    setIsLoading(true);
    try {
      await onAction?.();
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <Card className="p-6">
      <h2 className="text-2xl font-bold mb-4">{title}</h2>
      <Button onClick={handleAction} disabled={isLoading}>
        {isLoading ? 'Loading...' : 'Execute'}
      </Button>
    </Card>
  );
}
```

## Page Components

### Organization (`src/pages/`)

**Location**: `src/pages/`

Route-level components that represent full pages in the application. Each page typically composes multiple feature components and handles page-specific logic.

**Naming Convention**: PascalCase matching route names
- `Product.tsx` - Main product dashboard at `/product`
- `Testing.tsx` - Testing interface at `/product/testing`
- `CodeQuality.tsx` - Code quality page at `/product/code-quality`
- `Compliance.tsx` - Compliance page at `/product/compliance`
- `Documentation.tsx` - Documentation page at `/product/documentation`
- `Account.tsx` - Account settings at `/account`
- `WorkspaceManagement.tsx` - Workspace admin at `/workspace-management`

**Page Component Pattern**:
```typescript
// src/pages/MyPage.tsx
import { WorkspaceLayout } from '@/components/WorkspaceLayout';
import { ProductSidebar } from '@/components/ProductSidebar';
import { WorkspaceContent } from '@/components/WorkspaceContent';
import { useAuth } from '@/contexts/AuthContext';

export default function MyPage() {
  const { user } = useAuth();

  if (!user) {
    return <div>Please sign in</div>;
  }

  return (
    <WorkspaceLayout>
      <ProductSidebar />
      <WorkspaceContent>
        <div className="p-6">
          <h1 className="text-3xl font-bold mb-6">My Page</h1>
          {/* Page content */}
        </div>
      </WorkspaceContent>
    </WorkspaceLayout>
  );
}
```

## State Management

### Context Providers (`src/contexts/`)

**Location**: `src/contexts/`

React Context API is used for global state management. Each context follows the provider/hook pattern.

**Available Contexts**:

1. **AuthContext** (`AuthContext.tsx`)
   - Manages user authentication state
   - Handles sign-in/sign-out operations
   - Provides session information
   - Exposes `useAuth()` hook

2. **WorkspaceContext** (`WorkspaceContext.tsx`)
   - Manages workspace selection
   - Handles multi-workspace state
   - Provides workspace switching functionality
   - Exposes `useWorkspace()` hook

**Context Pattern**:
```typescript
// Context provider structure
import { createContext, useContext, useState, useEffect } from 'react';

interface MyContextValue {
  data: any;
  loading: boolean;
  updateData: (newData: any) => void;
}

const MyContext = createContext<MyContextValue | undefined>(undefined);

export function MyProvider({ children }: { children: React.ReactNode }) {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);

  const updateData = (newData: any) => {
    setData(newData);
  };

  return (
    <MyContext.Provider value={{ data, loading, updateData }}>
      {children}
    </MyContext.Provider>
  );
}

export function useMyContext() {
  const context = useContext(MyContext);
  if (!context) {
    throw new Error('useMyContext must be used within MyProvider');
  }
  return context;
}
```

### Custom Hooks (`src/hooks/`)

**Location**: `src/hooks/`

Custom React hooks encapsulate reusable logic and follow the `use[Name]` naming convention.

**Hook Categories**:

1. **Data Fetching Hooks**: Use TanStack Query for server state management
   - `useCodeQualityData.ts` - Fetches code quality analysis data
   - `useComplianceData.ts` - Fetches compliance analysis results
   - `useTestCoverage.ts` - Manages test coverage data
   - `useRepositoryData.ts` - Fetches repository information

2. **Integration Hooks**: Handle external service connections
   - `useGitHubConnection.ts` - Manages GitHub OAuth and repositories
   - `useSupabaseAuth.ts` - Handles Supabase authentication

3. **UI State Hooks**: Manage component-specific state
   - `useAnalysisProgress.ts` - Tracks analysis progress
   - `useModalState.ts` - Manages modal open/close state

**Custom Hook Pattern**:
```typescript
// Data fetching hook with TanStack Query
import { useQuery } from '@tanstack/react-query';
import { supabase } from '@/integrations/supabase/client';

interface DataType {
  id: string;
  name: string;
}

export function useMyData(id?: string) {
  return useQuery({
    queryKey: ['myData', id],
    queryFn: async () => {
      if (!id) return null;
      
      const { data, error } = await supabase
        .from('my_table')
        .select('*')
        .eq('id', id)
        .single();

      if (error) throw error;
      return data as DataType;
    },
    enabled: !!id, // Only fetch when id is available
  });
}
```

**Mutation Hook Pattern**:
```typescript
import { useMutation, useQueryClient } from '@tanstack/react-query';
import { supabase } from '@/integrations/supabase/client';
import { toast } from 'sonner';

interface UpdateData {
  id: string;
  name: string;
}

export function useUpdateData() {
  const queryClient = useQueryClient();

  return useMutation({
    mutationFn: async (data: UpdateData) => {
      const { error } = await supabase
        .from('my_table')
        .update({ name: data.name })
        .eq('id', data.id);

      if (error) throw error;
    },
    onSuccess: () => {
      queryClient.invalidateQueries({ queryKey: ['myData'] });
      toast.success('Updated successfully!');
    },
    onError: (error) => {
      toast.error('Update failed: ' + error.message);
    },
  });
}
```

## Services and Business Logic

### Service Layer (`src/services/`)

**Location**: `src/services/`

Service modules encapsulate business logic and API interactions. Services are organized by feature domain.

**Organization Pattern**:
- One service per major feature area
- Exports functions for specific operations
- Handles error management
- Returns typed results

**Service Module Example**:
```typescript
// src/services/codeQualityService.ts
import { supabase } from '@/integrations/supabase/client';

export interface CodeQualityResult {
  repository_id: string;
  overall_score: number;
  readability: number;
  maintainability: number;
  reliability: number;
  security: number;
  efficiency: number;
  testability: number;
}

export async function fetchCodeQualityResults(
  repositoryId: string
): Promise<CodeQualityResult | null> {
  const { data, error } = await supabase
    .from('code_quality_results')
    .select('*')
    .eq('repository_id', repositoryId)
    .single();

  if (error) {
    console.error('Error fetching code quality results:', error);
    return null;
  }

  return data;
}

export async function startCodeQualityAnalysis(
  repositoryId: string,
  customInstructions?: string
): Promise<{ success: boolean; error?: string }> {
  try {
    const { error } = await supabase.functions.invoke('analyze-code-quality', {
      body: { repositoryId, customInstructions }
    });

    if (error) throw error;
    return { success: true };
  } catch (error) {
    return { 
      success: false, 
      error: error instanceof Error ? error.message : 'Unknown error' 
    };
  }
}
```

## Type Definitions

### TypeScript Types (`src/types/`)

**Location**: `src/types/`

Centralized TypeScript type definitions shared across the application.

**Organization**:
- Interface definitions for API responses
- Shared type definitions
- Component prop types
- Supabase database types (auto-generated)

**Type Definition Pattern**:
```typescript
// src/types/repository.ts
export interface Repository {
  id: string;
  name: string;
  full_name: string;
  owner: string;
  description: string | null;
  is_private: boolean;
  default_branch: string;
  html_url: string;
  created_at: string;
  updated_at: string;
}

export interface RepositoryConnection {
  id: string;
  workspace_id: string;
  repository_id: string;
  enabled: boolean;
  last_synced: string | null;
  repository: Repository;
}

export type RepositoryStatus = 'active' | 'inactive' | 'archived' | 'error';
```

## Integration Layer

### Supabase Integration (`src/integrations/supabase/`)

**Location**: `src/integrations/supabase/`

Contains Supabase client configuration and auto-generated types.

**Structure**:
```
src/integrations/supabase/
├── client.ts          # Supabase client instance
├── types.ts           # Auto-generated database types
└── hooks/             # Supabase-specific hooks
```

**Client Configuration** (`client.ts`):
```typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

## Utility Functions

### Utilities (`src/utils/`)

**Location**: `src/utils/`

Helper functions and utilities used throughout the application.

**Common Utilities**:

1. **Class Name Utility** (`src/lib/utils.ts`):
```typescript
import { type ClassValue, clsx } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}
```

2. **Date Formatting**:
```typescript
export function formatDate(date: string | Date): string {
  return new Date(date).toLocaleDateString('en-US', {
    year: 'numeric',
    month: 'long',
    day: 'numeric'
  });
}
```

3. **Score Formatting**:
```typescript
export function getScoreColor(score: number): string {
  if (score >= 80) return 'text-green-600';
  if (score >= 60) return 'text-yellow-600';
  if (score >= 40) return 'text-orange-600';
  return 'text-red-600';
}
```

## Styling Architecture

### Tailwind CSS Configuration

**Location**: `tailwind.config.ts`

The application uses Tailwind CSS utility-first framework with custom configuration.

**Configuration Pattern**:
```typescript
// tailwind.config.ts
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        // Custom color palette
      },
      fontFamily: {
        // Custom fonts
      },
    },
  },
  plugins: [
    require("tailwindcss-animate"),
  ],
}
```

**Styling Conventions**:

1. **Component Styling**: Use Tailwind utility classes
```typescript
<div className="flex items-center justify-between p-4 bg-white rounded-lg shadow-md">
  <h2 className="text-2xl font-bold text-gray-900">Title</h2>
  <Button className="bg-blue-600 hover:bg-blue-700">Action</Button>
</div>
```

2. **Conditional Classes**: Use `cn()` utility for dynamic classes
```typescript
import { cn } from '@/lib/utils';

<div className={cn(
  'base-class',
  isActive && 'active-class',
  isDisabled && 'disabled-class'
)} />
```

3. **Responsive Design**: Mobile-first with breakpoint prefixes
```typescript
<div className="w-full md:w-1/2 lg:w-1/3">
  {/* Responsive content */}
</div>
```

## Routing Structure

### React Router Configuration

**Location**: `src/App.tsx`

The application uses React Router v6 for client-side routing with nested routes and protected routes.

**Route Structure**:
```typescript
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import { ProtectedRoute } from '@/components/ProtectedRoute';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<LandingPage />} />
        
        {/* Protected product routes */}
        <Route path="/product" element={
          <ProtectedRoute>
            <ProductDashboard />
          </ProtectedRoute>
        } />
        
        <Route path="/product/testing" element={
          <ProtectedRoute>
            <Testing />
          </ProtectedRoute>
        } />
        
        {/* More routes... */}
      </Routes>
    </BrowserRouter>
  );
}
```

**Route Patterns**:
- `/` - Public landing page
- `/product` - Main product dashboard (protected)
- `/product/*` - Feature-specific pages (protected)
- `/account` - User account settings (protected)
- `/workspace-management` - Workspace admin (protected)

## Configuration Files

### Build Configuration

**Vite Configuration** (`vite.config.ts`):
```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react-swc';
import path from 'path';

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      '@': path.resolve(__dirname, './src'),
    },
  },
  server: {
    port: 8080,
    host: '::',
  },
});
```

**TypeScript Configuration** (`tsconfig.json`):
```json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

## Naming Conventions

### File Naming

1. **Components**: PascalCase
   - `WorkspaceSelector.tsx`
   - `RepositoryTable.tsx`
   - `CodeQualityPanel.tsx`

2. **Hooks**: camelCase with 'use' prefix
   - `useAuth.ts`
   - `useCodeQualityData.ts`
   - `useGitHubConnection.ts`

3. **Services**: camelCase with 'Service' suffix
   - `codeQualityService.ts`
   - `repositoryService.ts`
   - `complianceService.ts`

4. **Utilities**: camelCase
   - `formatDate.ts`
   - `scoreHelpers.ts`
   - `validators.ts`

5. **Types**: camelCase
   - `repository.ts`
   - `codeQuality.ts`
   - `workspace.ts`

### Variable and Function Naming

1. **Variables**: camelCase
```typescript
const repositoryData = useRepositoryData(id);
const isLoading = false;
const currentWorkspace = useWorkspace();
```

2. **Functions**: camelCase, verb-first
```typescript
function fetchRepositories() { }
function handleSubmit() { }
function validateInput() { }
```

3. **Constants**: UPPER_SNAKE_CASE
```typescript
const MAX_RETRIES = 3;
const API_TIMEOUT = 5000;
const DEFAULT_PAGE_SIZE = 10;
```

4. **Interfaces/Types**: PascalCase
```typescript
interface Repository { }
type AnalysisResult = { };
interface ComponentProps { }
```

5. **React Components**: PascalCase
```typescript
function WorkspaceSelector() { }
export const RepositoryTable = () => { };
```

## Import Organization

### Import Order Convention

Imports should be organized in the following order with blank lines between groups:

1. React and React-related imports
2. Third-party libraries
3. UI components
4. Local components
5. Hooks and contexts
6. Services and utilities
7. Types
8. Styles

**Example**:
```typescript
// 1. React imports
import { useState, useEffect } from 'react';
import { useNavigate } from 'react-router-dom';

// 2. Third-party libraries
import { useQuery } from '@tanstack/react-query';
import { toast } from 'sonner';

// 3. UI components
import { Button } from '@/components/ui/button';
import { Card } from '@/components/ui/card';

// 4. Local components
import { WorkspaceSelector } from '@/components/WorkspaceSelector';
import { RepositoryTable } from '@/components/RepositoryTable';

// 5. Hooks and contexts
import { useAuth } from '@/contexts/AuthContext';
import { useWorkspace } from '@/contexts/WorkspaceContext';
import { useCodeQualityData } from '@/hooks/useCodeQualityData';

// 6. Services and utilities
import { fetchRepositories } from '@/services/repositoryService';
import { cn } from '@/lib/utils';

// 7. Types
import type { Repository } from '@/types/repository';

// 8. Styles
import './MyComponent.css';
```

## Code Quality Standards

### TypeScript Best Practices

1. **Always Define Types**:
```typescript
// ✅ Good
interface ButtonProps {
  onClick: () => void;
  label: string;
  disabled?: boolean;
}

// ❌ Bad
function Button(props: any) { }
```

2. **Use Type Inference When Obvious**:
```typescript
// ✅ Good
const count = 0; // TypeScript infers number
const data = await fetchData(); // Type inferred from function return

// ❌ Bad - unnecessary explicit typing
const count: number = 0;
```

3. **Prefer Interfaces Over Types for Objects**:
```typescript
// ✅ Good
interface User {
  id: string;
  name: string;
}

// Use types for unions/intersections
type Status = 'active' | 'inactive';
```

### React Best Practices

1. **Functional Components Only**:
```typescript
// ✅ Good
export function MyComponent() {
  return <div>Content</div>;
}

// ❌ Bad - no class components
export class MyComponent extends React.Component { }
```

2. **Use Hooks for State and Effects**:
```typescript
// ✅ Good
function MyComponent() {
  const [state, setState] = useState(initial);
  useEffect(() => {
    // Effect logic
  }, [dependencies]);
}
```

3. **Props Destructuring**:
```typescript
// ✅ Good
function MyComponent({ title, onAction }: MyComponentProps) {
  return <div>{title}</div>;
}

// ❌ Avoid
function MyComponent(props: MyComponentProps) {
  return <div>{props.title}</div>;
}
```

### Error Handling

1. **Try-Catch for Async Operations**:
```typescript
const handleAction = async () => {
  try {
    setIsLoading(true);
    const result = await performAction();
    toast.success('Success!');
    return result;
  } catch (error) {
    console.error('Action failed:', error);
    toast.error('Failed to perform action');
  } finally {
    setIsLoading(false);
  }
};
```

2. **Error Boundaries for React Errors**: Use error boundaries to catch rendering errors

3. **Proper Error Messages**: Always provide user-friendly error messages

## Testing Output Structure

### Test Directory Organization

**Location**: `orchestrai_tests/`

Generated tests are organized by timestamp and contain metadata, strategies, and test files.

**Structure**:
```
orchestrai_tests/
├── [timestamp]/
│   ├── metadata.json          # Test run metadata
│   ├── test_strategy.md       # Generated test strategy
│   └── tests/                 # Generated test files
│       ├── unit/             # Unit tests
│       ├── integration/      # Integration tests
│       └── e2e/              # End-to-end tests
```

## Development Workflow Patterns

### Feature Development Pattern

1. **Create Types** in `src/types/`
2. **Create Service Functions** in `src/services/`
3. **Create Custom Hook** in `src/hooks/`
4. **Create Components** in `src/components/`
5. **Create Page** in `src/pages/`
6. **Add Route** in `src/App.tsx`
7. **Test Functionality**

### Component Development Checklist

- [ ] Define TypeScript interfaces for props
- [ ] Use proper imports organization
- [ ] Implement loading states
- [ ] Implement error handling
- [ ] Add proper accessibility attributes
- [ ] Use Tailwind for styling
- [ ] Follow naming conventions
- [ ] Add JSDoc comments for complex logic
- [ ] Test component functionality

## Path Aliases

The project uses TypeScript path aliases for cleaner imports:

**Configuration** (`tsconfig.json`):
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

**Usage**:
```typescript
// Instead of: import { Button } from '../../../components/ui/button'
// Use:
import { Button } from '@/components/ui/button';

// Instead of: import { useAuth } from '../../contexts/AuthContext'
// Use:
import { useAuth } from '@/contexts/AuthContext';
```

## Environment Variables

### Configuration

Environment variables are defined in `.env` file (not committed to version control):

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### Usage in Code

```typescript
const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;
```

**Note**: All environment variables must be prefixed with `VITE_` to be exposed to the client-side code.

## Performance Optimization Patterns

### Code Splitting

Use React.lazy for route-based code splitting:

```typescript
import { lazy, Suspense } from 'react';

const Testing = lazy(() => import('@/pages/Testing'));

function App() {
  return (
    <Suspense fallback={<LoadingSpinner />}>
      <Testing />
    </Suspense>
  );
}
```

### Memoization

Use React.memo, useMemo, and useCallback appropriately:

```typescript
import { useMemo, useCallback } from 'react';

function MyComponent({ data }) {
  // Memoize expensive calculations
  const processedData = useMemo(() => {
    return expensiveOperation(data);
  }, [data]);

  // Memoize callbacks
  const handleClick = useCallback(() => {
    doSomething(data);
  }, [data]);

  return <div>{processedData}</div>;
}
```

### TanStack Query Caching

Leverage TanStack Query's built-in caching:

```typescript
export function useRepositoryData(id: string) {
  return useQuery({
    queryKey: ['repository', id],
    queryFn: () => fetchRepository(id),
    staleTime: 5 * 60 * 1000, // 5 minutes
    cacheTime: 10 * 60 * 1000, // 10 minutes
  });
}
```

## Security Patterns

### Authentication Guards

Protected routes use authentication guards:

```typescript
// src/components/ProtectedRoute.tsx
export function ProtectedRoute({ children }: { children: React.ReactNode }) {
  const { user, loading } = useAuth();
  const navigate = useNavigate();

  useEffect(() => {
    if (!loading && !user) {
      navigate('/');
    }
  }, [user, loading, navigate]);

  if (loading) return <LoadingSpinner />;
  if (!user) return null;

  return <>{children}</>;
}
```

### Row Level Security (RLS)

Database access is controlled through Supabase RLS policies. All queries automatically enforce user-level permissions.

### Input Validation

Use Zod for runtime validation:

```typescript
import * as z from 'zod';

const formSchema = z.object({
  name: z.string().min(1, 'Name is required'),
  email: z.string().email('Invalid email'),
  age: z.number().min(18, 'Must be 18 or older'),
});

type FormData = z.infer<typeof formSchema>;
```

## Summary

OrchestRAI follows a well-organized, scalable architecture with:

- **Clear separation of concerns** across components, pages, services, and utilities
- **Consistent naming conventions** for files, variables, and functions
- **Type-safe development** with TypeScript throughout
- **Modern React patterns** using hooks and functional components
- **Efficient state management** with Context API and TanStack Query
- **Component composition** with shadcn-ui base components
- **Utility-first styling** with Tailwind CSS
- **Path aliases** for clean imports using `@/` prefix
- **Secure authentication** with protected routes and RLS policies
- **Performance optimization** with code splitting and memoization

This structure promotes maintainability, scalability, and developer productivity while ensuring code quality and consistency across the entire codebase.