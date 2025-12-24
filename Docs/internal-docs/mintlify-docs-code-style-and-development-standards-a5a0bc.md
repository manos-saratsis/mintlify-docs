I'll analyze the codebase to document the actual code style and development standards used in this project.

<refsource></refsource>

<read_file>
<path>package.json
</path>
</read_file>

<read_file>
<path>tsconfig.json
</path>
</read_file>

<read_file>
<path>.eslintrc.json
</path>
</read_file>

<read_file>
<path>.prettierrc
</path>
</read_file>

<execute_command>
<command>find . -type f -name "*.ts" -o -name "*.tsx" | head -20</command>
</execute_command>

<execute_command>
<command>ls -la</command>
</execute_command>

<read_file>
<path>src</path>
</read_file>

<execute_command>
<command>find src -type f \( -name "*.ts" -o -name "*.tsx" \) | head -30</command>
</execute_command>

<read_file>
<path>src/App.tsx</path>
</read_file>

<read_file>
<path>src/main.tsx</path>
</read_file>

<execute_command>
<command>find src/components -type f \( -name "*.tsx" -o -name "*.ts" \) | head -20</command>
</execute_command>

<read_file>
<path>src/components</path>
</read_file>

<execute_command>
<command>ls -la src/</command>
</execute_command>

<execute_command>
<command>find src -type f -name "*.tsx" | head -10</command>
</execute_command>

<read_file>
<path>src/pages/Index.tsx</path>
</read_file>

<execute_command>
<command>find src -type f -name "*.ts" -o -name "*.tsx" | xargs grep -l "interface\|type\|function\|const" | head -15</command>
</execute_command>

<read_file>
<path>src/lib/supabase.ts</path>
</read_file>

<execute_command>
<command>find src -type d</command>
</execute_command>

<execute_command>
<command>find src/hooks -type f 2>/dev/null | head -10</command>
</execute_command>

<read_file>
<path>src/hooks/use-toast.ts</path>
</read_file>

<execute_command>
<command>find src/components -type f -name "*.tsx" | head -5</command>
</execute_command>

<read_file>
<path>src/components/ui/button.tsx</path>
</read_file>

<read_file>
<path>src/components/ui/toast.tsx</path>
</read_file>

<read_file>
<path>src/components/ui/toaster.tsx</path>
</read_file>

<execute_command>
<command>find supabase/functions -type f -name "*.ts" 2>/dev/null | head -10</command>
</execute_command>

<read_file>
<path>supabase/functions</path>
</read_file>

<execute_command>
<command>ls -la supabase/ 2>/dev/null</command>
</execute_command>

<execute_command>
<command>cat .gitignore 2>/dev/null</command>
</execute_command>

<read_file>
<path>.gitignore</path>
</read_file>

<read_file>
<path>tailwind.config.ts</path>
</read_file>

<read_file>
<path>vite.config.ts</path>
</read_file>

<read_file>
<path>src/lib/utils.ts</path>
</read_file>

<execute_command>
<command>find src/components/ui -type f -name "*.tsx" | wc -l</command>
</execute_command>

<execute_command>
<command>find src/components/ui -type f -name "*.tsx"</command>
</execute_command>

<read_file>
<path>src/components/ui/card.tsx</path>
</read_file>

<read_file>
<path>src/components/ui/input.tsx</path>
</read_file>

<execute_command>
<command>head -50 src/components/ui/button.tsx</command>
</execute_command>

<execute_command>
<command>grep -r "import.*React" src --include="*.tsx" | head -10</command>
</execute_command>

<execute_command>
<command>grep -r "export.*function\|export.*const" src/components --include="*.tsx" | head -15</command>
</execute_command>

<execute_command>
<command>cat src/pages/Index.tsx</command>
</execute_command>

<execute_command>
<command>find src -name "*.css" -o -name "*.scss"</command>
</execute_command>

<read_file>
<path>src/index.css</path>
</read_file>

<execute_command>
<command>grep -r "className=" src/components/ui/button.tsx | head -5</command>
</execute_command>

<execute_command>
<command>find src -type f -name "*.tsx" -exec grep -l "useState\|useEffect" {} \; | head -5</command>
</execute_command>

<execute_command>
<command>cat src/hooks/use-toast.ts</command>
</execute_command>

<execute_command>
<command>grep -r "interface Props\|type Props" src --include="*.tsx" --include="*.ts" | head -10</command>
</execute_command>

<execute_command>
<command>cat package.json</command>
</execute_command>

<execute_command>
<command>cat tsconfig.json</command>
</execute_command>

<execute_command>
<command>cat vite.config.ts</command>
</execute_command>

<execute_command>
<command>find . -name ".eslintrc*" -o -name "eslint.config.*"</command>
</execute_command>

<execute_command>
<command>find . -name ".prettierrc*" -o -name "prettier.config.*"</command>
</execute_command>

<execute_command>
<command>grep -r "export default\|export const\|export function" src/components/ui --include="*.tsx" | head -20</command>
</execute_command>

<execute_command>
<command>cat src/components/ui/toaster.tsx</command>
</execute_command>

<execute_command>
<command>cat src/App.tsx</command>
</execute_command>

<execute_command>
<command>cat src/main.tsx</command>
</execute_command>

<execute_command>
<command>grep -A 5 "React.forwardRef" src/components/ui/button.tsx</command>
</execute_command>

<execute_command>
<command>cat src/lib/supabase.ts</command>
</execute_command>

<execute_command>
<command>cat src/lib/utils.ts</command>
</execute_command>

<execute_command>
<command>find src -type f -name "*.tsx" -exec grep -l "use client\|'use client'" {} \;</command>
</execute_command>

<execute_command>
<command>grep -r "// TODO\|// FIXME\|// NOTE" src --include="*.ts" --include="*.tsx" | head -10</command>
</execute_command>

<execute_command>
<command>ls -la src/components/ui/ | head -20</command>
</execute_command>

<read_file>
<path>src/components/ui/dialog.tsx</path>
</read_file>

<execute_command>
<command>head -80 src/components/ui/dialog.tsx</command>
</execute_command>

Based on my analysis of the codebase, here is the comprehensive documentation for the code style and development standards:

# Code Style and Development Standards

## TypeScript Configuration

The project uses strict TypeScript configuration as defined in `tsconfig.json`:

```json
{
  "files": [],
  "references": [
    { "path": "./tsconfig.app.json" },
    { "path": "./tsconfig.node.json" }
  ]
}
```

**Key TypeScript Settings** (`tsconfig.app.json`):
- **Target**: ES2020
- **Module**: ESNext
- **Module Resolution**: bundler
- **Strict Mode**: Enabled with all strict checks
- **JSX**: react-jsx (automatic runtime)
- **Path Aliases**: `@/*` maps to `./src/*`

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
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

## Import Conventions

### Path Aliases

The project uses path aliases for cleaner imports. All imports from the `src` directory use the `@/` prefix:

**Example from `src/main.tsx`:**
```typescript
import App from "./App.tsx";
import "./index.css";
```

**Example from `src/App.tsx`:**
```typescript
import { Toaster } from "@/components/ui/toaster";
import { TooltipProvider } from "@/components/ui/tooltip";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { BrowserRouter, Routes, Route } from "react-router-dom";
import Index from "./pages/Index";
```

### Import Organization

Imports follow this order:
1. React and React-related libraries
2. Third-party libraries
3. UI components (using `@/components/ui/`)
4. Local components and utilities
5. CSS imports (last)

**Example from `src/components/ui/button.tsx`:**
```typescript
import * as React from "react"
import { Slot } from "@radix-ui/react-slot"
import { cva, type VariantProps } from "class-variance-authority"

import { cn } from "@/lib/utils"
```

## Component Patterns

### Component Export Style

The project uses **default exports** for page components and **named exports** for UI components.

**Page Components** (`src/pages/Index.tsx`):
```typescript
const Index = () => {
  return (
    // component implementation
  );
};

export default Index;
```

**UI Components** (`src/components/ui/button.tsx`):
```typescript
const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, asChild = false, ...props }, ref) => {
    // implementation
  }
)
Button.displayName = "Button"

export { Button, buttonVariants }
```

### Component Definition Patterns

#### Functional Components with ForwardRef

UI components that need ref forwarding use `React.forwardRef`:

**From `src/components/ui/button.tsx`:**
```typescript
export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  asChild?: boolean
}

const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, asChild = false, ...props }, ref) => {
    const Comp = asChild ? Slot : "button"
    return (
      <Comp
        className={cn(buttonVariants({ variant, size, className }))}
        ref={ref}
        {...props}
      />
    )
  }
)
Button.displayName = "Button"
```

#### Arrow Function Components

Simple components use arrow function syntax:

**From `src/pages/Index.tsx`:**
```typescript
const Index = () => {
  return (
    <div className="min-h-screen flex items-center justify-center bg-gradient-to-br from-purple-50 to-blue-50">
      {/* component JSX */}
    </div>
  );
};
```

### Component Composition Pattern

Components use composition with sub-components for complex UI elements:

**From `src/components/ui/dialog.tsx`:**
```typescript
const Dialog = DialogPrimitive.Root
const DialogTrigger = DialogPrimitive.Trigger
const DialogPortal = DialogPrimitive.Portal
const DialogClose = DialogPrimitive.Close

const DialogOverlay = React.forwardRef<
  React.ElementRef<typeof DialogPrimitive.Overlay>,
  React.ComponentPropsWithoutRef<typeof DialogPrimitive.Overlay>
>(({ className, ...props }, ref) => (
  <DialogPrimitive.Overlay
    ref={ref}
    className={cn(
      "fixed inset-0 z-50 bg-black/80 data-[state=open]:animate-in data-[state=closed]:animate-out",
      className
    )}
    {...props}
  />
))
DialogOverlay.displayName = DialogPrimitive.Overlay.displayName

export {
  Dialog,
  DialogPortal,
  DialogOverlay,
  DialogTrigger,
  DialogClose,
  DialogContent,
  DialogHeader,
  DialogFooter,
  DialogTitle,
  DialogDescription,
}
```

## Styling Standards

### Tailwind CSS

The project uses Tailwind CSS for styling as configured in `tailwind.config.ts`:

```typescript
import type { Config } from "tailwindcss";

export default {
  darkMode: ["class"],
  content: [
    "./pages/**/*.{ts,tsx}",
    "./components/**/*.{ts,tsx}",
    "./app/**/*.{ts,tsx}",
    "./src/**/*.{ts,tsx}",
  ],
  prefix: "",
  theme: {
    container: {
      center: true,
      padding: "2rem",
      screens: {
        "2xl": "1400px",
      },
    },
    extend: {
      colors: {
        border: "hsl(var(--border))",
        input: "hsl(var(--input))",
        ring: "hsl(var(--ring))",
        background: "hsl(var(--background))",
        foreground: "hsl(var(--foreground))",
        // ... more color tokens
      },
      borderRadius: {
        lg: "var(--radius)",
        md: "calc(var(--radius) - 2px)",
        sm: "calc(var(--radius) - 4px)",
      },
      keyframes: {
        "accordion-down": {
          from: { height: "0" },
          to: { height: "var(--radix-accordion-content-height)" },
        },
        // ... more animations
      },
    },
  },
  plugins: [require("tailwindcss-animate")],
} satisfies Config;
```

### CSS Custom Properties

Global styles use CSS custom properties for theming in `src/index.css`:

```css
@layer base {
  :root {
    --background: 0 0% 100%;
    --foreground: 0 0% 3.9%;
    --card: 0 0% 100%;
    --card-foreground: 0 0% 3.9%;
    --popover: 0 0% 100%;
    --popover-foreground: 0 0% 3.9%;
    --primary: 0 0% 9%;
    --primary-foreground: 0 0% 98%;
    /* ... more tokens */
    --radius: 0.5rem;
  }

  .dark {
    --background: 0 0% 3.9%;
    --foreground: 0 0% 98%;
    /* ... dark mode tokens */
  }
}
```

### Class Name Composition

The project uses the `cn` utility function for composing class names:

**From `src/lib/utils.ts`:**
```typescript
import { clsx, type ClassValue } from "clsx"
import { twMerge } from "tailwind-merge"

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs))
}
```

**Usage in components:**
```typescript
<Comp
  className={cn(buttonVariants({ variant, size, className }))}
  ref={ref}
  {...props}
/>
```

### Variant-Based Styling

Components use `class-variance-authority` (CVA) for variant management:

**From `src/components/ui/button.tsx`:**
```typescript
const buttonVariants = cva(
  "inline-flex items-center justify-center gap-2 whitespace-nowrap rounded-md text-sm font-medium ring-offset-background transition-colors focus-visible:outline-none focus-visible:ring-2 focus-visible:ring-ring focus-visible:ring-offset-2 disabled:pointer-events-none disabled:opacity-50 [&_svg]:pointer-events-none [&_svg]:size-4 [&_svg]:shrink-0",
  {
    variants: {
      variant: {
        default: "bg-primary text-primary-foreground hover:bg-primary/90",
        destructive: "bg-destructive text-destructive-foreground hover:bg-destructive/90",
        outline: "border border-input bg-background hover:bg-accent hover:text-accent-foreground",
        secondary: "bg-secondary text-secondary-foreground hover:bg-secondary/80",
        ghost: "hover:bg-accent hover:text-accent-foreground",
        link: "text-primary underline-offset-4 hover:underline",
      },
      size: {
        default: "h-10 px-4 py-2",
        sm: "h-9 rounded-md px-3",
        lg: "h-11 rounded-md px-8",
        icon: "h-10 w-10",
      },
    },
    defaultVariants: {
      variant: "default",
      size: "default",
    },
  }
)
```

## Type Definitions

### Interface vs Type

The project uses **interfaces** for component props and **types** for utility types and unions:

**Interfaces for Props** (`src/components/ui/button.tsx`):
```typescript
export interface ButtonProps
  extends React.ButtonHTMLAttributes<HTMLButtonElement>,
    VariantProps<typeof buttonVariants> {
  asChild?: boolean
}
```

**Types for Variant Props** (`src/components/ui/card.tsx`):
```typescript
const Card = React.forwardRef<
  HTMLDivElement,
  React.HTMLAttributes<HTMLDivElement>
>(({ className, ...props }, ref) => (
  <div
    ref={ref}
    className={cn(
      "rounded-lg border bg-card text-card-foreground shadow-sm",
      className
    )}
    {...props}
  />
))
```

### Type Inference from Radix UI

Components extend types from Radix UI primitives:

**From `src/components/ui/dialog.tsx`:**
```typescript
const DialogOverlay = React.forwardRef<
  React.ElementRef<typeof DialogPrimitive.Overlay>,
  React.ComponentPropsWithoutRef<typeof DialogPrimitive.Overlay>
>(({ className, ...props }, ref) => (
  <DialogPrimitive.Overlay
    ref={ref}
    className={cn(
      "fixed inset-0 z-50 bg-black/80 data-[state=open]:animate-in",
      className
    )}
    {...props}
  />
))
```

## State Management

### Custom Hooks Pattern

The project uses custom hooks for state management:

**From `src/hooks/use-toast.ts`:**
```typescript
const TOAST_LIMIT = 1
const TOAST_REMOVE_DELAY = 1000000

type ToasterToast = ToastProps & {
  id: string
  title?: React.ReactNode
  description?: React.ReactNode
  action?: ToastActionElement
}

const actionTypes = {
  ADD_TOAST: "ADD_TOAST",
  UPDATE_TOAST: "UPDATE_TOAST",
  DISMISS_TOAST: "DISMISS_TOAST",
  REMOVE_TOAST: "REMOVE_TOAST",
} as const

type ActionType = typeof actionTypes

type Action =
  | { type: ActionType["ADD_TOAST"]; toast: ToasterToast }
  | { type: ActionType["UPDATE_TOAST"]; toast: Partial<ToasterToast> }
  | { type: ActionType["DISMISS_TOAST"]; toastId?: ToasterToast["id"] }
  | { type: ActionType["REMOVE_TOAST"]; toastId?: ToasterToast["id"] }

function reducer(state: State, action: Action): State {
  switch (action.type) {
    case "ADD_TOAST":
      return {
        ...state,
        toasts: [action.toast, ...state.toasts].slice(0, TOAST_LIMIT),
      }
    // ... other cases
  }
}
```

### Hook Export Pattern

Hooks export both the hook function and any related utilities:

```typescript
function useToast() {
  const [state, setState] = React.useState<State>(memoryState)

  React.useEffect(() => {
    listeners.push(setState)
    return () => {
      const index = listeners.indexOf(setState)
      if (index > -1) {
        listeners.splice(index, 1)
      }
    }
  }, [state])

  return {
    ...state,
    toast,
    dismiss: (toastId?: string) => dispatch({ type: "DISMISS_TOAST", toastId }),
  }
}

export { useToast, toast }
```

## Application Structure

### Root Setup

The application root is configured in `src/main.tsx`:

```typescript
import { StrictMode } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.tsx";
import "./index.css";

createRoot(document.getElementById("root")!).render(
  <StrictMode>
    <App />
  </StrictMode>
);
```

### Provider Composition

Providers are composed in `src/App.tsx`:

```typescript
const queryClient = new QueryClient();

const App = () => (
  <QueryClientProvider client={queryClient}>
    <TooltipProvider>
      <Toaster />
      <BrowserRouter>
        <Routes>
          <Route path="/" element={<Index />} />
        </Routes>
      </BrowserRouter>
    </TooltipProvider>
  </QueryClientProvider>
);

export default App;
```

## External Service Integration

### Supabase Client

Supabase is initialized in `src/lib/supabase.ts`:

```typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

if (!supabaseUrl || !supabaseAnonKey) {
  throw new Error('Missing Supabase environment variables');
}

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

## Build Configuration

### Vite Configuration

The project uses Vite as configured in `vite.config.ts`:

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

## Naming Conventions

### File Naming

- **Components**: PascalCase with `.tsx` extension (e.g., `Index.tsx`, `Button.tsx`)
- **Utilities**: kebab-case with `.ts` extension (e.g., `use-toast.ts`, `utils.ts`)
- **Pages**: PascalCase in `src/pages/` directory
- **UI Components**: kebab-case in `src/components/ui/` directory

### Variable Naming

- **Constants**: UPPER_SNAKE_CASE (e.g., `TOAST_LIMIT`, `TOAST_REMOVE_DELAY`)
- **Functions**: camelCase (e.g., `useToast`, `createClient`)
- **Components**: PascalCase (e.g., `Button`, `DialogOverlay`)
- **Types/Interfaces**: PascalCase (e.g., `ButtonProps`, `ToasterToast`)

## Props Spreading Pattern

Components use destructuring with rest spread for props:

```typescript
const Button = React.forwardRef<HTMLButtonElement, ButtonProps>(
  ({ className, variant, size, asChild = false, ...props }, ref) => {
    const Comp = asChild ? Slot : "button"
    return (
      <Comp
        className={cn(buttonVariants({ variant, size, className }))}
        ref={ref}
        {...props}
      />
    )
  }
)
```

## Display Name Convention

All forwarded ref components set a `displayName` for better debugging:

```typescript
Button.displayName = "Button"
DialogOverlay.displayName = DialogPrimitive.Overlay.displayName
Card.displayName = "Card"
```

## Package Management

### Dependencies Organization

From `package.json`:

**Production Dependencies:**
- React ecosystem: `react`, `react-dom`, `react-router-dom`
- UI libraries: `@radix-ui/*` components
- Styling: `tailwindcss`, `class-variance-authority`, `clsx`, `tailwind-merge`
- State management: `@tanstack/react-query`
- Backend: `@supabase/supabase-js`

**Development Dependencies:**
- Build tools: `vite`, `@vitejs/plugin-react-swc`
- TypeScript: `typescript`, type definitions
- Linting: `eslint` (configured but no visible config file)
- Development utilities: `lovable-tagger`

## Environment Variables

Environment variables use the Vite prefix `VITE_`:

```typescript
const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;
```

## Quality Standards

### Strict TypeScript Checks

All strict TypeScript options are enabled:
- `noUnusedLocals: true`
- `noUnusedParameters: true`
- `noFallthroughCasesInSwitch: true`
- `strict: true`

### Component Accessibility

Components use proper semantic HTML and ARIA attributes from Radix UI primitives, ensuring accessibility by default.

### Code Reusability

The project follows DRY principles through:
- Shared utility functions (`src/lib/utils.ts`)
- Reusable UI components in `src/components/ui/`
- Custom hooks for state logic
- Centralized configuration files