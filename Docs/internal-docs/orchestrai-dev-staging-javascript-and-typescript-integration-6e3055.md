# JavaScript and TypeScript Integration

## Overview

OrchestRAI is built as a modern TypeScript-based React application with comprehensive type safety and JavaScript ecosystem integration. The project uses TypeScript 5.5.3 as its primary language for both frontend components and edge functions, providing end-to-end type safety across the entire application stack. The integration leverages Vite as the build tool, which provides fast hot module replacement (HMR) and optimized production builds with native ES modules support.

The application architecture emphasizes type safety, modern JavaScript features (ES2020+), and a component-based structure using React 18.3.1 with functional components and hooks. TypeScript strict mode is enabled throughout the project to catch potential errors at compile time, ensuring robust code quality.

## Implementation

### TypeScript Configuration

The project uses a multi-configuration TypeScript setup with separate configurations for application code and Node.js tooling:

**Main TypeScript Configuration** (`tsconfig.json`):
```json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ]
}
```

This root configuration delegates to specialized configs for different environments, following TypeScript's project references pattern.

**Application TypeScript Configuration** (`tsconfig.app.json`):
Located at the project root, this configuration defines settings for all application source code:

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "isolatedModules": true,
    "moduleDetection": "force",
    "noEmit": true,
    "jsx": "react-jsx",
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    "noUncheckedSideEffectImports": true,
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  },
  "include": ["src"]
}
```

Key configuration features:
- **Target**: ES2020 for modern JavaScript features
- **Strict Mode**: All strict type checking options enabled
- **Path Aliases**: `@/*` maps to `./src/*` for cleaner imports
- **JSX**: `react-jsx` for React 18+ automatic JSX transform
- **Module Resolution**: Uses bundler mode for Vite compatibility
- **No Emit**: TypeScript only performs type checking; Vite handles transpilation

**Node.js TypeScript Configuration** (`tsconfig.node.json`):
Separate configuration for build tooling:

```json
{
  "compilerOptions": {
    "target": "ES2022",
    "lib": ["ES2023"],
    "module": "ESNext",
    "skipLibCheck": true,
    "moduleResolution": "bundler",
    "allowSyntheticDefaultImports": true,
    "strict": true,
    "noEmit": true
  },
  "include": ["vite.config.ts"]
}
```

This configuration covers Vite configuration files and other Node.js tooling.

### Build System Integration

**Vite Configuration** (`vite.config.ts`):
Located at the project root, this file configures the build tool and development server:

```typescript
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react-swc";
import path from "path";
import { componentTagger } from "lovable-tagger";

export default defineConfig(({ mode }) => ({
  server: {
    host: "::",
    port: 8080,
  },
  plugins: [
    react(),
    mode === 'development' && componentTagger(),
  ].filter(Boolean),
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
}));
```

Implementation details:
- **React Plugin**: Uses SWC-based React plugin (`@vitejs/plugin-react-swc`) for faster compilation
- **Development Server**: Configured to run on port 8080, listening on all interfaces (`::`)
- **Path Aliases**: Resolves `@/*` imports to `src/*` directory
- **Component Tagger**: Development-only plugin for component debugging (from `lovable-tagger`)
- **Conditional Plugins**: Filters out falsy values to enable environment-specific plugins

### Type Definitions Structure

The project organizes TypeScript types in `src/types/` directory. While the specific type files weren't provided in the source code, the architecture documentation indicates the following organization:

**Type Organization Pattern**:
```
src/types/
├── index.ts           # Type exports and aggregation
├── api.ts            # API response interfaces
├── database.ts       # Supabase database types
└── components.ts     # Component prop interfaces
```

Based on code patterns observed in hooks and components, types follow these conventions:

**Interface Naming**: PascalCase for all interfaces
```typescript
interface Repository {
  id: string;
  name: string;
  full_name: string;
  // ... other properties
}

interface CodeQualityResult {
  repository_id: string;
  overall_score: number;
  // ... other properties
}
```

**Component Props Pattern**:
```typescript
interface MyComponentProps {
  title: string;
  onAction?: () => void;
  isLoading?: boolean;
}

export function MyComponent({ title, onAction, isLoading = false }: MyComponentProps) {
  // Component implementation
}
```

### JavaScript Module System

The project uses ES Modules exclusively, configured through `package.json`:

```json
{
  "type": "module"
}
```

This enables:
- Native `import`/`export` syntax
- Top-level `await` support
- Tree-shaking for optimal bundle sizes
- Modern module resolution

**Import Path Patterns**:

1. **Absolute Imports with Path Aliases**:
```typescript
// UI Components
import { Button } from '@/components/ui/button';
import { Card } from '@/components/ui/card';

// Hooks
import { useAuth } from '@/contexts/AuthContext';
import { useWorkspace } from '@/contexts/WorkspaceContext';

// Utilities
import { cn } from '@/lib/utils';
import { supabase } from '@/integrations/supabase/client';
```

2. **Relative Imports**:
```typescript
// Sibling components
import { ComponentA } from './ComponentA';

// Parent directory
import { ParentComponent } from '../ParentComponent';
```

### ESLint Configuration

Code quality is enforced through ESLint with TypeScript support (`eslint.config.js`):

The configuration uses ESLint 9.9.0 with TypeScript plugin integration. Based on the package.json dependencies:

```json
{
  "devDependencies": {
    "@eslint/js": "^9.9.0",
    "eslint": "^9.9.0",
    "eslint-plugin-react-hooks": "^5.1.0-rc.0",
    "eslint-plugin-react-refresh": "^0.4.9",
    "typescript-eslint": "^8.0.1"
  }
}
```

The linting script is available in package.json:
```json
{
  "scripts": {
    "lint": "eslint ."
  }
}
```

### React and TypeScript Integration

**Component Pattern**:
The project uses functional components with TypeScript throughout. From the architecture documentation, the standard pattern is:

```typescript
import { useState } from 'react';
import { Button } from '@/components/ui/button';
import { Card } from '@/components/ui/card';

interface MyComponentProps {
  title: string;
  onAction?: () => void;
}

export function MyComponent({ title, onAction }: MyComponentProps) {
  const [isLoading, setIsLoading] = useState(false);

  const handleClick = async () => {
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
      <Button onClick={handleClick} disabled={isLoading}>
        {isLoading ? 'Loading...' : 'Click Me'}
      </Button>
    </Card>
  );
}
```

**Hook Pattern with TypeScript**:
```typescript
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
    enabled: !!id,
  });
}
```

### State Management with TypeScript

**Context Pattern**:
The project uses React Context API with TypeScript for global state. Based on the architecture guide:

```typescript
// AuthContext pattern
interface AuthContextType {
  user: User | null;
  session: Session | null;
  loading: boolean;
  signIn: (email: string, password: string) => Promise<void>;
  signOut: () => Promise<void>;
}

// Context provider implementation
export const AuthContext = createContext<AuthContextType | undefined>(undefined);

export function useAuth() {
  const context = useContext(AuthContext);
  if (!context) {
    throw new Error('useAuth must be used within AuthProvider');
  }
  return context;
}
```

**TanStack Query Integration**:
The project uses TanStack Query (React Query) for server state management with full TypeScript support:

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

### Form Handling with TypeScript

The project uses `react-hook-form` with Zod for type-safe form validation:

**Dependencies** (from package.json):
```json
{
  "dependencies": {
    "react-hook-form": "^7.53.0",
    "@hookform/resolvers": "^3.9.0",
    "zod": "^3.23.8"
  }
}
```

**Form Pattern**:
```typescript
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import * as z from 'zod';

const formSchema = z.object({
  name: z.string().min(1, 'Name is required'),
  email: z.string().email('Invalid email'),
});

type FormData = z.infer<typeof formSchema>;

function MyForm() {
  const { register, handleSubmit, formState: { errors } } = useForm<FormData>({
    resolver: zodResolver(formSchema),
  });

  const onSubmit = (data: FormData) => {
    console.log(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)} className="space-y-4">
      <div>
        <Label htmlFor="name">Name</Label>
        <Input {...register('name')} id="name" />
        {errors.name && <p className="text-red-500 text-sm">{errors.name.message}</p>}
      </div>
      
      <div>
        <Label htmlFor="email">Email</Label>
        <Input {...register('email')} id="email" type="email" />
        {errors.email && <p className="text-red-500 text-sm">{errors.email.message}</p>}
      </div>
      
      <Button type="submit">Submit</Button>
    </form>
  );
}
```

### Supabase TypeScript Integration

The project integrates with Supabase with full TypeScript support through the Supabase client library:

**Supabase Client Setup** (`src/integrations/supabase/client.ts`):
```typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

**Type-Safe Database Queries**:
```typescript
// Select with type inference
const { data, error } = await supabase
  .from('git_connections')
  .select('*')
  .eq('workspace_id', workspaceId);

// Insert with type checking
const { data, error } = await supabase
  .from('git_connections')
  .insert([
    { 
      workspace_id: workspace.id,
      provider: 'github',
      access_token: token 
    }
  ])
  .select();

// Update with type safety
const { data, error } = await supabase
  .from('git_connections')
  .update({ status: 'active' })
  .eq('id', connectionId);
```

### TypeScript Utility Types

The project leverages TypeScript's built-in utility types and custom type helpers:

**Common Patterns**:
```typescript
// Optional chaining for safe property access
const name = user?.profile?.name;

// Nullish coalescing for default values
const displayName = user?.name ?? 'Guest';

// Type guards
function isError(value: unknown): value is Error {
  return value instanceof Error;
}

// Discriminated unions (pattern used in state management)
type LoadingState = 
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: Data }
  | { status: 'error'; error: Error };
```

### Performance Optimization with TypeScript

**Memoization with Type Safety**:
```typescript
import { useMemo, useCallback } from 'react';

// Memoize expensive calculations
const expensiveValue = useMemo<ComputedType>(() => {
  return computeExpensiveValue(data);
}, [data]);

// Memoize callbacks
const handleClick = useCallback(() => {
  doSomething(value);
}, [value]);
```

**Lazy Loading with TypeScript**:
```typescript
import { lazy, Suspense } from 'react';

const HeavyComponent = lazy<ComponentType<Props>>(
  () => import('./HeavyComponent')
);

function App() {
  return (
    <Suspense fallback={<div>Loading...</div>}>
      <HeavyComponent />
    </Suspense>
  );
}
```

### Development Workflow

**Type Checking**:
The project separates type checking from build processes:

```bash
# Type checking without building
npx tsc --noEmit

# Development with hot reload
npm run dev

# Production build (includes type checking)
npm run build
```

**Development Scripts** (from package.json):
```json
{
  "scripts": {
    "dev": "vite",
    "build": "tsc -b && vite build",
    "build:dev": "vite build --mode development",
    "lint": "eslint .",
    "preview": "vite preview"
  }
}
```

The `build` script runs TypeScript compilation (`tsc -b`) before Vite build, ensuring no type errors in production builds.

## Usage

### Setting Up TypeScript in Components

**Creating a New TypeScript Component**:

1. Create component file with `.tsx` extension in `src/components/`:
```typescript
// src/components/MyComponent.tsx
import { useState } from 'react';
import { Button } from '@/components/ui/button';

interface MyComponentProps {
  title: string;
  onSubmit: (value: string) => void;
}

export function MyComponent({ title, onSubmit }: MyComponentProps) {
  const [value, setValue] = useState('');

  return (
    <div>
      <h2>{title}</h2>
      <input 
        value={value} 
        onChange={(e) => setValue(e.target.value)} 
      />
      <Button onClick={() => onSubmit(value)}>
        Submit
      </Button>
    </div>
  );
}
```

2. Import and use with full type safety:
```typescript
// src/pages/MyPage.tsx
import { MyComponent } from '@/components/MyComponent';

export default function MyPage() {
  const handleSubmit = (value: string) => {
    console.log('Submitted:', value);
  };

  return <MyComponent title="Enter Data" onSubmit={handleSubmit} />;
}
```

### Using Path Aliases

Path aliases are configured in both `tsconfig.app.json` and `vite.config.ts` to enable clean imports:

**Import Examples**:
```typescript
// UI Components (from src/components/ui/)
import { Button } from '@/components/ui/button';
import { Card, CardContent, CardHeader } from '@/components/ui/card';
import { Input } from '@/components/ui/input';

// Custom Hooks (from src/hooks/)
import { useAuth } from '@/contexts/AuthContext';
import { useWorkspace } from '@/contexts/WorkspaceContext';

// Services (from src/integrations/)
import { supabase } from '@/integrations/supabase/client';

// Utilities (from src/lib/)
import { cn } from '@/lib/utils';

// Types (from src/types/)
import type { Repository, CodeQualityResult } from '@/types';
```

### Working with Supabase Types

**Type-Safe Database Operations**:

```typescript
// Query with automatic type inference
const fetchRepositories = async (workspaceId: string) => {
  const { data, error } = await supabase
    .from('git_connections')
    .select('*, repositories(*)')
    .eq('workspace_id', workspaceId);

  if (error) throw error;
  return data;
};

// Mutation with type checking
const updateConnection = async (id: string, updates: Partial<GitConnection>) => {
  const { data, error } = await supabase
    .from('git_connections')
    .update(updates)
    .eq('id', id)
    .select()
    .single();

  if (error) throw error;
  return data;
};
```

### Creating Type-Safe Hooks

**Custom Hook Pattern**:
```typescript
// src/hooks/useRepositories.ts
import { useQuery } from '@tanstack/react-query';
import { supabase } from '@/integrations/supabase/client';

interface Repository {
  id: string;
  name: string;
  full_name: string;
  private: boolean;
}

export function useRepositories(workspaceId: string | undefined) {
  return useQuery({
    queryKey: ['repositories', workspaceId],
    queryFn: async () => {
      if (!workspaceId) return [];
      
      const { data, error } = await supabase
        .from('repositories')
        .select('*')
        .eq('workspace_id', workspaceId);

      if (error) throw error;
      return data as Repository[];
    },
    enabled: !!workspaceId,
  });
}
```

**Usage in Component**:
```typescript
import { useRepositories } from '@/hooks/useRepositories';

export function RepositoryList() {
  const { data: repositories, isLoading, error } = useRepositories(workspaceId);

  if (isLoading) return <div>Loading...</div>;
  if (error) return <div>Error: {error.message}</div>;

  return (
    <ul>
      {repositories?.map(repo => (
        <li key={repo.id}>{repo.name}</li>
      ))}
    </ul>
  );
}
```

### Form Validation with Zod

**Creating Type-Safe Forms**:

```typescript
import { useForm } from 'react-hook-form';
import { zodResolver } from '@hookform/resolvers/zod';
import * as z from 'zod';

// Define schema
const workspaceSchema = z.object({
  name: z.string().min(1, 'Name is required').max(100),
  description: z.string().optional(),
  plan: z.enum(['free', 'enterprise']),
});

// Infer TypeScript type from schema
type WorkspaceFormData = z.infer<typeof workspaceSchema>;

export function CreateWorkspaceForm() {
  const { 
    register, 
    handleSubmit, 
    formState: { errors, isSubmitting } 
  } = useForm<WorkspaceFormData>({
    resolver: zodResolver(workspaceSchema),
  });

  const onSubmit = async (data: WorkspaceFormData) => {
    // data is fully typed
    await createWorkspace(data);
  };

  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <input {...register('name')} />
      {errors.name && <span>{errors.name.message}</span>}
      
      <textarea {...register('description')} />
      
      <select {...register('plan')}>
        <option value="free">Free</option>
        <option value="enterprise">Enterprise</option>
      </select>
      {errors.plan && <span>{errors.plan.message}</span>}
      
      <button type="submit" disabled={isSubmitting}>
        Create
      </button>
    </form>
  );
}
```

### Error Handling with Types

**Type-Safe Error Handling**:

```typescript
// Custom error types
class APIError extends Error {
  constructor(
    message: string,
    public statusCode: number,
    public details?: unknown
  ) {
    super(message);
    this.name = 'APIError';
  }
}

// Type guard
function isAPIError(error: unknown): error is APIError {
  return error instanceof APIError;
}

// Usage in async operations
const handleAction = async () => {
  try {
    await performAction();
  } catch (error) {
    if (isAPIError(error)) {
      console.error(`API Error ${error.statusCode}:`, error.message);
      if (error.statusCode === 404) {
        // Handle not found
      }
    } else if (error instanceof Error) {
      console.error('Error:', error.message);
    } else {
      console.error('Unknown error:', error);
    }
  }
};
```

### Environment Variables with Type Safety

**Accessing Environment Variables**:

```typescript
// Vite provides type-safe access to env variables
const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

// Type definition for env variables (in vite-env.d.ts)
interface ImportMetaEnv {
  readonly VITE_SUPABASE_URL: string;
  readonly VITE_SUPABASE_ANON_KEY: string;
}

interface ImportMeta {
  readonly env: ImportMetaEnv;
}
```

### Development Commands

**Running Type Checks**:
```bash
# Type check without building
npx tsc --noEmit

# Type check specific file
npx tsc --noEmit src/components/MyComponent.tsx

# Watch mode for type checking
npx tsc --noEmit --watch
```

**Linting TypeScript Code**:
```bash
# Run ESLint on all files
npm run lint

# Fix auto-fixable issues
npm run lint -- --fix

# Lint specific file
npx eslint src/components/MyComponent.tsx
```

**Building the Project**:
```bash
# Development build with HMR
npm run dev

# Production build (includes type checking)
npm run build

# Development build (no type checking)
npm run build:dev

# Preview production build
npm run preview
```

### TypeScript in Edge Functions

While edge function source code wasn't provided, the project structure indicates TypeScript support for Supabase Edge Functions in `supabase/functions/`. Edge functions follow Deno's TypeScript patterns:

**Edge Function Pattern** (typical structure):
```typescript
// supabase/functions/my-function/index.ts
import { serve } from 'https://deno.land/std@0.168.0/http/server.ts';

interface RequestBody {
  userId: string;
  action: string;
}

serve(async (req) => {
  try {
    const body: RequestBody = await req.json();
    
    // Type-safe processing
    const result = await processAction(body.userId, body.action);
    
    return new Response(
      JSON.stringify({ success: true, data: result }),
      { headers: { 'Content-Type': 'application/json' } }
    );
  } catch (error) {
    return new Response(
      JSON.stringify({ success: false, error: error.message }),
      { status: 500, headers: { 'Content-Type': 'application/json' } }
    );
  }
});
```

### Best Practices

**Type Safety Guidelines**:

1. **Always Define Interface for Props**:
```typescript
// ✅ Good
interface ButtonProps {
  label: string;
  onClick: () => void;
  disabled?: boolean;
}

// ❌ Avoid
function Button(props: any) { }
```

2. **Use Type Inference Where Appropriate**:
```typescript
// ✅ Good - TypeScript infers the type
const [count, setCount] = useState(0);

// ❌ Unnecessary explicit type
const [count, setCount] = useState<number>(0);
```

3. **Leverage Discriminated Unions for State**:
```typescript
// ✅ Good
type RequestState =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: Data }
  | { status: 'error'; error: Error };

// ❌ Avoid
interface RequestState {
  status: string;
  data?: Data;
  error?: Error;
}
```

4. **Use Optional Chaining and Nullish Coalescing**:
```typescript
// ✅ Good
const name = user?.profile?.name ?? 'Anonymous';

// ❌ Verbose
const name = user && user.profile && user.profile.name 
  ? user.profile.name 
  : 'Anonymous';
```

5. **Export Types Alongside Components**:
```typescript
// ✅ Good
export interface MyComponentProps {
  title: string;
}

export function MyComponent({ title }: MyComponentProps) {
  // ...
}

// Consumers can import both
import { MyComponent, type MyComponentProps } from '@/components/MyComponent';
```

These TypeScript and JavaScript integration patterns provide the foundation for OrchestRAI's type-safe, maintainable codebase across the entire application stack.