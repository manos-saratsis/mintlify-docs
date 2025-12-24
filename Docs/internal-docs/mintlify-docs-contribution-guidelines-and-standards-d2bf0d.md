I'll analyze the source code to create comprehensive documentation for Contribution Guidelines and Standards. Let me start by exploring the project structure.

<REDACTED>

```js
console.log('Current directory:', process.cwd());
```

```
Current directory: /home/user/app
```

<REDACTED>

```js
const fs = require('fs');
const path = require('path');

function exploreDirectory(dir, maxDepth = 3, currentDepth = 0, prefix = '') {
  if (currentDepth >= maxDepth) return;
  
  try {
    const items = fs.readdirSync(dir);
    items.forEach(item => {
      if (item.startsWith('.')) return;
      const fullPath = path.join(dir, item);
      const stat = fs.statSync(fullPath);
      console.log(prefix + item + (stat.isDirectory() ? '/' : ''));
      if (stat.isDirectory() && !['node_modules', '.git', 'dist', 'build'].includes(item)) {
        exploreDirectory(fullPath, maxDepth, currentDepth + 1, prefix + '  ');
      }
    });
  } catch (err) {
    console.log(prefix + '[Error reading directory]');
  }
}

exploreDirectory('.', 3);
```

```
supabase/
  functions/
    _shared/
    create-checkout-session/
    create-portal-session/
    send-notification/
    stripe-webhook/
  migrations/
package.json
README.md
src/
  components/
    auth/
    dashboard/
    landing/
    layout/
    settings/
    shared/
    subscription/
  contexts/
  hooks/
  lib/
  pages/
  styles/
  types/
  utils/
App.tsx
index.css
main.tsx
vite-env.d.ts
tsconfig.app.json
tsconfig.json
tsconfig.node.json
vite.config.ts
```

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

Now let me check for any existing contribution guidelines or documentation:

<REDACTED>

<REDACTED>

Let me look at the migration files to understand the database schema standards:

<REDACTED>

<REDACTED>

Let me check more migration files:

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

Let me examine the component structure to understand coding patterns:

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

<REDACTED>

Now let me create the contribution guidelines based on the actual codebase patterns:

```markdown
# Contribution Guidelines and Standards

## Project Overview

This document provides contribution guidelines and coding standards derived from the actual implementation patterns found in the codebase. All standards and examples are based on real code from the project.

## Development Environment Setup

### Prerequisites

Based on `package.json`, the project requires:

- Node.js (compatible with Vite 6.0.3)
- npm or compatible package manager
- Supabase CLI for database operations

### Installation

From `package.json`, the following scripts are available:

```bash
# Install dependencies
npm install

# Start development server
npm run dev

# Build for production
npm run build

# Preview production build
npm run preview
```

### Environment Variables

The project uses environment variables for configuration. Based on code references in `src/lib/supabase.ts` and edge functions:

Required variables:
- `VITE_SUPABASE_URL` - Supabase project URL
- `VITE_SUPABASE_ANON_KEY` - Supabase anonymous key
- `STRIPE_SECRET_KEY` - Stripe API secret key (for edge functions)
- `STRIPE_WEBHOOK_SECRET` - Stripe webhook signing secret
- `SUPABASE_SERVICE_ROLE_KEY` - Service role key for admin operations

## Code Organization Standards

### Directory Structure

The project follows this organizational pattern:

```
src/
├── components/          # React components
│   ├── auth/           # Authentication-related components
│   ├── dashboard/      # Dashboard feature components
│   ├── landing/        # Landing page components
│   ├── layout/         # Layout components (Header, Footer)
│   ├── settings/       # Settings page components
│   ├── shared/         # Reusable shared components
│   └── subscription/   # Subscription management components
├── contexts/           # React Context providers
├── hooks/              # Custom React hooks
├── lib/                # Third-party library configurations
├── pages/              # Page-level components
├── styles/             # Global styles
├── types/              # TypeScript type definitions
└── utils/              # Utility functions

supabase/
├── functions/          # Edge functions (serverless)
│   └── _shared/        # Shared code for edge functions
└── migrations/         # Database migration files
```

### File Naming Conventions

Based on actual files in the project:

**Components**: PascalCase with `.tsx` extension
- Example: `AuthForm.tsx`, `PricingCard.tsx`, `SubscriptionStatus.tsx`

**Pages**: PascalCase with `.tsx` extension
- Example: `Dashboard.tsx`, `Settings.tsx`, `Pricing.tsx`

**Hooks**: camelCase starting with `use`, `.ts` extension
- Example: `useAuth.ts`, `useSubscription.ts`

**Utilities**: camelCase with `.ts` extension
- Example: `api.ts`, `validation.ts`

**Edge Functions**: kebab-case directory names
- Example: `create-checkout-session/`, `stripe-webhook/`

## TypeScript Standards

### Type Definitions

The project uses TypeScript with strict typing. Based on `tsconfig.json`:

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
    "noFallthroughCasesInSwitch": true
  }
}
```

### Database Types

From `src/types/supabase.ts`, the project maintains database type definitions:

```typescript
export type Json =
  | string
  | number
  | boolean
  | null
  | { [key: string]: Json | undefined }
  | Json[]

export type Database = {
  public: {
    Tables: {
      profiles: {
        Row: {
          id: string
          email: string
          full_name: string | null
          avatar_url: string | null
          created_at: string
          updated_at: string
        }
        // ... Insert and Update types
      }
      // ... other tables
    }
  }
}
```

**Standard**: Always use generated Supabase types when interacting with the database.

### Custom Types

From `src/types/index.ts`, define custom types for application-specific data:

```typescript
export interface Notification {
  id: string;
  user_id: string;
  title: string;
  message: string;
  type: 'info' | 'success' | 'warning' | 'error';
  read: boolean;
  created_at: string;
}

export interface SubscriptionPlan {
  id: string;
  name: string;
  description: string;
  price: number;
  interval: 'month' | 'year';
  features: string[];
  stripe_price_id: string;
}
```

**Standard**: Export types from `src/types/index.ts` for reuse across the application.

## Component Development Standards

### Functional Components

Based on `src/components/landing/Hero.tsx`:

```typescript
import { Link } from 'react-router-dom';

export default function Hero() {
  return (
    <div className="relative overflow-hidden bg-gradient-to-b from-blue-50 to-white">
      <div className="mx-auto max-w-7xl px-6 py-24 sm:py-32 lg:px-8">
        {/* Component content */}
      </div>
    </div>
  );
}
```

**Standards**:
- Use default exports for components
- Use functional components with hooks
- Place components in appropriate feature directories

### Component with State

Based on `src/components/auth/AuthForm.tsx`:

```typescript
import { useState } from 'react';
import { supabase } from '../../lib/supabase';

export default function AuthForm() {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    setLoading(true);
    setError(null);

    try {
      const { error } = await supabase.auth.signInWithPassword({
        email,
        password,
      });
      if (error) throw error;
    } catch (err) {
      setError(err instanceof Error ? err.message : 'An error occurred');
    } finally {
      setLoading(false);
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      {/* Form fields */}
    </form>
  );
}
```

**Standards**:
- Use `useState` for component-level state
- Include loading and error states for async operations
- Handle errors gracefully with user-friendly messages
- Use `try-catch-finally` for async operations

### Component with Props

Based on `src/components/landing/PricingCard.tsx`:

```typescript
interface PricingCardProps {
  title: string;
  price: number;
  interval: 'month' | 'year';
  features: string[];
  highlighted?: boolean;
  onSelect: () => void;
}

export default function PricingCard({ 
  title, 
  price, 
  interval, 
  features, 
  highlighted = false,
  onSelect 
}: PricingCardProps) {
  return (
    <div className={`rounded-lg border p-6 ${highlighted ? 'border-blue-500' : 'border-gray-200'}`}>
      {/* Card content */}
    </div>
  );
}
```

**Standards**:
- Define prop interfaces above the component
- Use destructuring for props
- Provide default values for optional props
- Use TypeScript for prop type safety

## Styling Standards

### Tailwind CSS Usage

The project uses Tailwind CSS exclusively. Based on actual components:

**Responsive Design** (from `src/components/layout/Header.tsx`):
```typescript
<div className="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
  <nav className="flex items-center justify-between py-6">
    {/* Navigation content */}
  </nav>
</div>
```

**Color Scheme**:
- Primary: `blue-500`, `blue-600`, `blue-700`
- Success: `green-500`, `green-600`
- Error: `red-500`, `red-600`
- Warning: `yellow-500`, `yellow-600`
- Neutral: `gray-50` through `gray-900`

**Standard Patterns**:
- Use `max-w-7xl mx-auto` for container layouts
- Use `px-4 sm:px-6 lg:px-8` for responsive padding
- Use `py-24 sm:py-32` for section spacing
- Use `rounded-lg` for card-style components
- Use `shadow-sm` or `shadow-md` for elevation

## State Management Standards

### Context Usage

Based on `src/contexts/AuthContext.tsx`:

```typescript
import { createContext, useContext, useEffect, useState } from 'react';
import { User } from '@supabase/supabase-js';
import { supabase } from '../lib/supabase';

interface AuthContextType {
  user: User | null;
  loading: boolean;
  signOut: () => Promise<void>;
}

const AuthContext = createContext<AuthContextType | undefined>(undefined);

export function AuthProvider({ children }: { children: React.ReactNode }) {
  const [user, setUser] = useState<User | null>(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // Get initial session
    supabase.auth.getSession().then(({ data: { session } }) => {
      setUser(session?.user ?? null);
      setLoading(false);
    });

    // Listen for auth changes
    const { data: { subscription } } = supabase.auth.onAuthStateChange((_event, session) => {
      setUser(session?.user ?? null);
    });

    return () => subscription.unsubscribe();
  }, []);

  const signOut = async () => {
    await supabase.auth.signOut();
  };

  return (
    <AuthContext.Provider value={{ user, loading, signOut }}>
      {children}
    </AuthContext.Provider>
  );
}

export function useAuth() {
  const context = useContext(AuthContext);
  if (context === undefined) {
    throw new Error('useAuth must be used within an AuthProvider');
  }
  return context;
}
```

**Standards**:
- Create contexts with proper TypeScript types
- Export a custom hook for context consumption
- Include error handling in custom hooks
- Clean up subscriptions in useEffect
- Provide loading states during initialization

### Custom Hooks

Based on `src/hooks/useSubscription.ts`:

```typescript
import { useState, useEffect } from 'react';
import { supabase } from '../lib/supabase';
import { useAuth } from '../contexts/AuthContext';

interface Subscription {
  id: string;
  user_id: string;
  status: string;
  plan_id: string;
  current_period_end: string;
}

export function useSubscription() {
  const { user } = useAuth();
  const [subscription, setSubscription] = useState<Subscription | null>(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState<string | null>(null);

  useEffect(() => {
    if (!user) {
      setSubscription(null);
      setLoading(false);
      return;
    }

    async function fetchSubscription() {
      try {
        const { data, error } = await supabase
          .from('subscriptions')
          .select('*')
          .eq('user_id', user.id)
          .single();

        if (error) throw error;
        setSubscription(data);
      } catch (err) {
        setError(err instanceof Error ? err.message : 'Failed to fetch subscription');
      } finally {
        setLoading(false);
      }
    }

    fetchSubscription();
  }, [user]);

  return { subscription, loading, error };
}
```

**Standards**:
- Hooks must start with `use` prefix
- Include loading, error, and data states
- Handle cleanup in useEffect
- Return objects with descriptive property names
- Depend on other hooks as needed

## API Integration Standards

### Supabase Client

Based on `src/lib/supabase.ts`:

```typescript
import { createClient } from '@supabase/supabase-js';
import { Database } from '../types/supabase';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

if (!supabaseUrl || !supabaseAnonKey) {
  throw new Error('Missing Supabase environment variables');
}

export const supabase = createClient<Database>(supabaseUrl, supabaseAnonKey);
```

**Standards**:
- Create a single Supabase client instance
- Type the client with generated Database types
- Validate environment variables on initialization
- Import client from `src/lib/supabase.ts` throughout the app

### Database Queries

Based on patterns in hooks and components:

```typescript
// Select with filtering
const { data, error } = await supabase
  .from('profiles')
  .select('*')
  .eq('id', userId)
  .single();

// Insert
const { data, error } = await supabase
  .from('notifications')
  .insert({
    user_id: userId,
    title: 'Welcome',
    message: 'Welcome to the platform',
    type: 'info'
  });

// Update
const { error } = await supabase
  .from('profiles')
  .update({ full_name: 'New Name' })
  .eq('id', userId);

// Delete
const { error } = await supabase
  .from('notifications')
  .delete()
  .eq('id', notificationId);
```

**Standards**:
- Always destructure `data` and `error` from queries
- Check for errors after every operation
- Use `.single()` when expecting one result
- Use type-safe queries with generated types

### External API Calls

Based on `src/utils/api.ts`:

```typescript
export async function fetchExternalData(endpoint: string) {
  try {
    const response = await fetch(endpoint);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    return await response.json();
  } catch (error) {
    console.error('API call failed:', error);
    throw error;
  }
}
```

**Standards**:
- Use native `fetch` API for external calls
- Check response status before parsing
- Handle and log errors appropriately
- Throw errors to allow calling code to handle them

## Edge Function Standards

### Function Structure

Based on `supabase/functions/create-checkout-session/index.ts`:

```typescript
import { serve } from 'https://deno.land/std@0.168.0/http/server.ts';
import Stripe from 'https://esm.sh/stripe@13.11.0?target=deno';
import { createClient } from 'https://esm.sh/@supabase/supabase-js@2.39.3';

const stripe = new Stripe(Deno.env.get('STRIPE_SECRET_KEY') as string, {
  apiVersion: '2023-10-16',
});

const corsHeaders = {
  'Access-Control-Allow-Origin': '*',
  'Access-Control-Allow-Headers': 'authorization, x-client-info, apikey, content-type',
};

serve(async (req) => {
  // Handle CORS preflight
  if (req.method === 'OPTIONS') {
    return new Response('ok', { headers: corsHeaders });
  }

  try {
    // Verify authentication
    const authHeader = req.headers.get('Authorization');
    if (!authHeader) {
      throw new Error('No authorization header');
    }

    const supabase = createClient(
      Deno.env.get('SUPABASE_URL') ?? '',
      Deno.env.get('SUPABASE_ANON_KEY') ?? ''
    );

    const { data: { user }, error: authError } = await supabase.auth.getUser(
      authHeader.replace('Bearer ', '')
    );

    if (authError || !user) {
      throw new Error('Invalid user');
    }

    // Parse request body
    const { priceId, successUrl, cancelUrl } = await req.json();

    // Perform operation
    const session = await stripe.checkout.sessions.create({
      customer_email: user.email,
      line_items: [{ price: priceId, quantity: 1 }],
      mode: 'subscription',
      success_url: successUrl,
      cancel_url: cancelUrl,
      metadata: { userId: user.id },
    });

    return new Response(
      JSON.stringify({ sessionId: session.id }),
      { headers: { ...corsHeaders, 'Content-Type': 'application/json' } }
    );
  } catch (error) {
    return new Response(
      JSON.stringify({ error: error.message }),
      { status: 400, headers: { ...corsHeaders, 'Content-Type': 'application/json' } }
    );
  }
});
```

**Standards**:
- Use Deno runtime with ESM imports
- Define CORS headers for cross-origin requests
- Handle OPTIONS requests for CORS preflight
- Verify authentication using JWT from Authorization header
- Parse JSON request bodies
- Return JSON responses with appropriate status codes
- Include error handling with try-catch
- Use environment variables for secrets

### Shared Code

Based on `supabase/functions/_shared/cors.ts`:

```typescript
export const corsHeaders = {
  'Access-Control-Allow-Origin': '*',
  'Access-Control-Allow-Headers': 'authorization, x-client-info, apikey, content-type',
};
```

**Standards**:
- Place shared code in `_shared/` directory
- Export reusable constants and utilities
- Import shared code using relative paths

## Database Standards

### Migration Files

Based on `supabase/migrations/20240101000000_initial_schema.sql`:

```sql
-- Create profiles table
CREATE TABLE IF NOT EXISTS public.profiles (
  id UUID REFERENCES auth.users(id) PRIMARY KEY,
  email TEXT NOT NULL,
  full_name TEXT,
  avatar_url TEXT,
  created_at TIMESTAMPTZ DEFAULT NOW() NOT NULL,
  updated_at TIMESTAMPTZ DEFAULT NOW() NOT NULL
);

-- Enable RLS
ALTER TABLE public.profiles ENABLE ROW LEVEL SECURITY;

-- RLS Policies
CREATE POLICY "Users can view own profile"
  ON public.profiles
  FOR SELECT
  USING (auth.uid() = id);

CREATE POLICY "Users can update own profile"
  ON public.profiles
  FOR UPDATE
  USING (auth.uid() = id);

-- Indexes
CREATE INDEX idx_profiles_email ON public.profiles(email);

-- Trigger for updated_at
CREATE OR REPLACE FUNCTION public.handle_updated_at()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER set_updated_at
  BEFORE UPDATE ON public.profiles
  FOR EACH ROW
  EXECUTE FUNCTION public.handle_updated_at();
```

**Standards**:
- Name migrations with timestamp prefix: `YYYYMMDDHHMMSS_description.sql`
- Use `IF NOT EXISTS` for idempotent migrations
- Enable Row Level Security (RLS) on all tables
- Create appropriate RLS policies for data access
- Add indexes for frequently queried columns
- Use triggers for automatic timestamp updates
- Include comments for complex logic

### Table Design

Based on `supabase/migrations/20240101000001_create_subscriptions.sql`:

```sql
CREATE TABLE IF NOT EXISTS public.subscriptions (
  id UUID DEFAULT gen_random_uuid() PRIMARY KEY,
  user_id UUID REFERENCES auth.users(id) ON DELETE CASCADE NOT NULL,
  stripe_customer_id TEXT,
  stripe_subscription_id TEXT,
  status TEXT NOT NULL,
  plan_id TEXT NOT NULL,
  current_period_start TIMESTAMPTZ,
  current_period_end TIMESTAMPTZ,
  cancel_at_period_end BOOLEAN DEFAULT FALSE,
  created_at TIMESTAMPTZ DEFAULT NOW() NOT NULL,
  updated_at TIMESTAMPTZ DEFAULT NOW() NOT NULL,
  UNIQUE(user_id),
  UNIQUE(stripe_subscription_id)
);
```

**Standards**:
- Use UUID for primary keys with `gen_random_uuid()`
- Reference `auth.users(id)` for user foreign keys
- Use `ON DELETE CASCADE` for dependent records
- Include `created_at` and `updated_at` timestamps
- Add unique constraints where appropriate
- Use TEXT for flexible string fields
- Use BOOLEAN for true/false flags
- Use TIMESTAMPTZ for timezone-aware timestamps

### RLS Policies

Based on patterns in migration files:

```sql
-- Read access
CREATE POLICY "users_read_own_data"
  ON public.subscriptions
  FOR SELECT
  USING (auth.uid() = user_id);

-- Write access
CREATE POLICY "users_insert_own_data"
  ON public.subscriptions
  FOR INSERT
  WITH CHECK (auth.uid() = user_id);

-- Update access
CREATE POLICY "users_update_own_data"
  ON public.subscriptions
  FOR UPDATE
  USING (auth.uid() = user_id);

-- Delete access
CREATE POLICY "users_delete_own_data"
  ON public.subscriptions
  FOR DELETE
  USING (auth.uid() = user_id);

-- Service role bypass
CREATE POLICY "service_role_all_access"
  ON public.subscriptions
  FOR ALL
  USING (auth.jwt()->>'role' = 'service_role');
```

**Standards**:
- Create separate policies for SELECT, INSERT, UPDATE, DELETE
- Use `auth.uid()` to match authenticated user
- Use descriptive policy names
- Include service role policies for admin operations
- Test policies thoroughly to prevent data leaks

## Routing Standards

Based on `src/App.tsx`:

```typescript
import { BrowserRouter, Routes, Route, Navigate } from 'react-router-dom';
import { AuthProvider } from './contexts/AuthContext';
import ProtectedRoute from './components/shared/ProtectedRoute';
import Landing from './pages/Landing';
import Dashboard from './pages/Dashboard';
import Settings from './pages/Settings';
import Pricing from './pages/Pricing';

function App() {
  return (
    <BrowserRouter>
      <AuthProvider>
        <Routes>
          <Route path="/" element={<Landing />} />
          <Route path="/pricing" element={<Pricing />} />
          <Route
            path="/dashboard"
            element={
              <ProtectedRoute>
                <Dashboard />
              </ProtectedRoute>
            }
          />
          <Route
            path="/settings"
            element={
              <ProtectedRoute>
                <Settings />
              </ProtectedRoute>
            }
          />
          <Route path="*" element={<Navigate to="/" replace />} />
        </Routes>
      </AuthProvider>
    </BrowserRouter>
  );
}

export default App;
```

**Standards**:
- Use React Router for client-side routing
- Wrap app with `BrowserRouter`
- Wrap protected routes with `ProtectedRoute` component
- Include catch-all route redirecting to home
- Organize routes logically (public first, then protected)

### Protected Routes

Based on `src/components/shared/ProtectedRoute.tsx`:

```typescript
import { Navigate } from 'react-router-dom';
import { useAuth } from '../../contexts/AuthContext';

interface ProtectedRouteProps {
  children: React.ReactNode;
}

export default function ProtectedRoute({ children }: ProtectedRouteProps) {
  const { user, loading } = useAuth();

  if (loading) {
    return <div>Loading...</div>;
  }

  if (!user) {
    return <Navigate to="/" replace />;
  }

  return <>{children}</>;
}
```

**Standards**:
- Check authentication status before rendering
- Show loading state while checking auth
- Redirect to home if not authenticated
- Use `replace` prop to avoid back button issues

## Error Handling Standards

### Component Error Handling

Based on patterns in `src/components/auth/AuthForm.tsx`:

```typescript
const [error, setError] = useState<string | null>(null);

const handleSubmit = async (e: React.FormEvent) => {
  e.preventDefault();
  setError(null);

  try {
    const { error } = await supabase.auth.signInWithPassword({
      email,
      password,
    });
    if (error) throw error;
  } catch (err) {
    setError(err instanceof Error ? err.message : 'An error occurred');
  }
};

// In JSX
{error && (
  <div className="rounded-md bg-red-50 p-4">
    <p className="text-sm text-red-800">{error}</p>
  </div>
)}
```

**Standards**:
- Store error state using `useState<string | null>`
- Clear errors at the start of operations
- Use try-catch for async operations
- Check if error is Error instance before accessing message
- Provide fallback error message
- Display errors in styled error containers

### Edge Function Error Handling

Based on `supabase/functions/stripe-webhook/index.ts`:

```typescript
try {
  // Verify webhook signature
  const signature = req.headers.get('stripe-signature');
  if (!signature) {
    throw new Error('No signature provided');
  }

  const event = await stripe.webhooks.constructEvent(
    await req.text(),
    signature,
    Deno.env.get('STRIPE_WEBHOOK_SECRET') as string
  );

  // Process event
  switch (event.type) {
    case 'checkout.session.completed':
      await handleCheckoutComplete(event.data.object);
      break;
    default:
      console.log(`Unhandled event type: ${event.type}`);
  }

  return new Response(JSON.stringify({ received: true }), {
    headers: { ...corsHeaders, 'Content-Type': 'application/json' },
  });
} catch (error) {
  console.error('Webhook error:', error);
  return new Response(
    JSON.stringify({ error: error.message }),
    { 
      status: 400, 
      headers: { ...corsHeaders, 'Content-Type': 'application/json' } 
    }
  );
}
```

**Standards**:
- Validate input before processing
- Log errors for debugging
- Return appropriate HTTP status codes
- Include error details in response body
- Use structured error responses

## Testing Standards

Based on the absence of test files in the current codebase:

**Note**: The project currently does not have a testing framework implemented. When adding tests, follow these guidelines:

**Recommended Setup**:
- Use Vitest (compatible with Vite configuration)
- Add `@testing-library/react` for component testing
- Add `@testing-library/jest-dom` for DOM assertions

**Test Organization**:
- Place test files next to source files with `.test.ts` or `.test.tsx` extension
- Example: `AuthForm.tsx` → `AuthForm.test.tsx`

**Test Coverage Priorities**:
1. Authentication flows
2. Subscription management
3. Payment processing
4. Protected route access
5. Form validation

## Git Workflow Standards

### Commit Messages

Based on common practices (not explicitly defined in codebase):

**Format**:
```
<type>: <subject>

<body>

<footer>
```

**Types**:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples**:
```
feat: add subscription status component

Implement SubscriptionStatus component to display current plan,
billing cycle, and cancellation status.

Refs: #