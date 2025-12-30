# Local Development Environment Setup

## Overview

This guide covers the complete setup process for the OrchestrAI development environment, including prerequisites, installation, configuration, and debugging setup. This project is built with Vite, React, TypeScript, and integrates with Supabase for backend services.

## Prerequisites

### Required Software

#### Node.js & npm
- **Required Version**: Node.js (LTS recommended)
- **Installation Method**: Use nvm (Node Version Manager)
  ```bash
  # Install nvm
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash
  
  # Install Node.js LTS
  nvm install --lts
  nvm use --lts
  ```

#### Git
- Required for cloning the repository
- Installation: [https://git-scm.com/downloads](https://git-scm.com/downloads)

### Recommended Tools

- **IDE**: Visual Studio Code, WebStorm, or any TypeScript-compatible editor
- **Terminal**: Modern terminal with bash/zsh support
- **Browser**: Chrome/Edge with React DevTools extension

## Project Installation

### 1. Clone the Repository

```bash
# Clone the repository
git clone <YOUR_GIT_URL>

# Navigate to project directory
cd orchestrai-dev-staging
```

**Repository URL**: Available at [Lovable Project](https://lovable.dev/projects/7c862077-7481-4c5d-8bec-4705fd7e59c1)

### 2. Install Dependencies

```bash
# Install all project dependencies
npm i
```

This command installs all dependencies specified in `package.json`, including:

**Core Dependencies**:
- `react@^18.3.1` - UI library
- `react-dom@^18.3.1` - React DOM rendering
- `react-router-dom@^6.26.2` - Client-side routing
- `@supabase/supabase-js@^2.80.0` - Supabase client
- `@tanstack/react-query@^5.56.2` - Data fetching and caching

**UI Components**:
- `@radix-ui/*` - Accessible component primitives
- `shadcn-ui` components - Pre-built UI components
- `lucide-react@^0.462.0` - Icon library
- `tailwindcss@^3.4.11` - Utility-first CSS framework

**Build Tools**:
- `vite@^5.4.1` - Fast build tool and dev server
- `typescript@^5.5.3` - Type checking
- `@vitejs/plugin-react-swc@^3.5.0` - Fast React refresh with SWC

### 3. Start Development Server

```bash
# Start Vite development server
npm run dev
```

**Expected Output**:
- Development server starts on `http://localhost:5173` (default Vite port)
- Hot Module Replacement (HMR) enabled
- Instant preview with auto-reloading

## Project Structure

```
orchestrai-dev-staging/
├── src/                    # Source code
│   ├── components/         # React components
│   ├── pages/             # Page components
│   ├── hooks/             # Custom React hooks
│   ├── lib/               # Utility functions
│   └── integrations/      # Third-party integrations
├── public/                # Static assets
├── package.json           # Dependencies and scripts
├── tsconfig.json          # TypeScript configuration
├── vite.config.ts         # Vite configuration
├── tailwind.config.ts     # Tailwind CSS configuration
└── README.md             # Project documentation
```

## Environment Configuration

### Environment Variables

Create a `.env.local` file in the project root for local environment variables:

```bash
# Supabase Configuration
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key

# Additional environment-specific variables
VITE_API_URL=http://localhost:3000
```

**Important Notes**:
- All Vite environment variables must be prefixed with `VITE_`
- Variables are exposed to client-side code
- Never commit `.env.local` to version control
- Use `.env.example` as a template for required variables

### Accessing Environment Variables

```typescript
// In your React components or utilities
const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseKey = import.meta.env.VITE_SUPABASE_ANON_KEY;
```

## Supabase Local Development

### Supabase Client Setup

The project uses `@supabase/supabase-js@^2.80.0` for backend integration.

**Typical Client Initialization** (expected location: `src/integrations/supabase/client.ts`):

```typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
```

### React Query Integration

The project uses `@tanstack/react-query@^5.56.2` for data fetching and state management.

**Query Client Setup** (expected pattern):

```typescript
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 1000 * 60 * 5, // 5 minutes
      retry: 1,
    },
  },
});

// Wrap your app with QueryClientProvider
<QueryClientProvider client={queryClient}>
  <App />
</QueryClientProvider>
```

## Vite Configuration

### Development Server

**Default Configuration** (`vite.config.ts`):
- Port: 5173
- Hot Module Replacement: Enabled
- React Fast Refresh: Enabled via `@vitejs/plugin-react-swc`

### Build Configuration

```bash
# Production build
npm run build

# Development build (preserves source maps)
npm run build:dev

# Preview production build locally
npm run preview
```

**Build Output**:
- Output directory: `dist/`
- Optimized and minified assets
- Code splitting for optimal loading

### TypeScript Support

The project uses TypeScript with the following configuration:
- **Version**: `typescript@^5.5.3`
- **Type Definitions**: Included for React, React DOM, and Node.js
- **Build Tool**: Vite handles TypeScript compilation
- **Type Checking**: Run `tsc --noEmit` for type-only checking

## Development Workflow

### Available Scripts

From `package.json`:

```json
{
  "scripts": {
    "dev": "vite",                              // Start development server
    "build": "vite build",                      // Production build
    "build:dev": "vite build --mode development", // Development build
    "lint": "eslint .",                         // Run ESLint
    "preview": "vite preview"                   // Preview production build
  }
}
```

### Linting

```bash
# Run ESLint on the entire project
npm run lint
```

**ESLint Configuration**:
- Uses `@eslint/js@^9.9.0`
- Plugins: `eslint-plugin-react-hooks`, `eslint-plugin-react-refresh`
- TypeScript support via `typescript-eslint@^8.0.1`

## Debugging Setup

### Browser DevTools

1. **React Developer Tools**
   - Install React DevTools extension for Chrome/Firefox
   - Inspect component hierarchy and props
   - Profile component performance

2. **Source Maps**
   - Vite generates source maps in development mode
   - Original TypeScript code visible in browser debugger
   - Set breakpoints directly in source files

### VS Code Debugging

Create `.vscode/launch.json`:

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "type": "chrome",
      "request": "launch",
      "name": "Launch Chrome against localhost",
      "url": "http://localhost:5173",
      "webRoot": "${workspaceFolder}/src",
      "sourceMaps": true
    }
  ]
}
```

### Network Debugging

For Supabase API calls:
- Use browser Network tab to inspect requests
- Check request headers for authentication tokens
- Verify response status codes and payloads

## GitHub Integration

### Lovable Platform Sync

This project is connected to the Lovable platform. Changes can be made through:

1. **Lovable Web Interface**
   - URL: [https://lovable.dev/projects/7c862077-7481-4c5d-8bec-4705fd7e59c1](https://lovable.dev/projects/7c862077-7481-4c5d-8bec-4705fd7e59c1)
   - Changes automatically committed to repository

2. **Local Development**
   - Clone repository and push changes
   - Changes reflected in Lovable platform

3. **Direct GitHub Editing**
   - Edit files directly on GitHub
   - Click "Edit" button (pencil icon)

4. **GitHub Codespaces**
   - Launch Codespace from repository
   - Full development environment in browser

### Commit and Push

```bash
# Add changes
git add .

# Commit with message
git commit -m "Your commit message"

# Push to remote
git push origin main
```

## Technology Stack Reference

**Core Technologies** (from `package.json`):

| Technology | Version | Purpose |
|-----------|---------|---------|
| Vite | ^5.4.1 | Build tool and dev server |
| React | ^18.3.1 | UI framework |
| TypeScript | ^5.5.3 | Type safety |
| Tailwind CSS | ^3.4.11 | Styling |
| Supabase JS | ^2.80.0 | Backend client |
| React Query | ^5.56.2 | Data fetching |
| React Router | ^6.26.2 | Routing |
| shadcn-ui | Various | UI components |
| Radix UI | Various | Accessible primitives |

**Form Handling**:
- `react-hook-form@^7.53.0` - Form state management
- `@hookform/resolvers@^3.9.0` - Schema validation
- `zod@^3.23.8` - Schema validation library

**UI Utilities**:
- `lucide-react@^0.462.0` - Icons
- `next-themes@^0.3.0` - Theme management
- `sonner@^1.5.0` - Toast notifications
- `recharts@^2.12.7` - Charts and data visualization

## Troubleshooting

### Common Issues

**Port Already in Use**:
```bash
# Vite will automatically try the next available port
# Or specify a different port in vite.config.ts
```

**Module Not Found**:
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

**TypeScript Errors**:
```bash
# Check TypeScript configuration
npx tsc --noEmit

# Restart TypeScript server in VS Code
# Cmd/Ctrl + Shift + P -> "TypeScript: Restart TS Server"
```

**Supabase Connection Issues**:
- Verify environment variables in `.env.local`
- Check Supabase project status
- Verify API keys are correct and not expired

### Getting Help

- **Project URL**: [https://lovable.dev/projects/7c862077-7481-4c5d-8bec-4705fd7e59c1](https://lovable.dev/projects/7c862077-7481-4c5d-8bec-4705fd7e59c1)
- **Custom Domain Setup**: [Setting up a custom domain](https://docs.lovable.dev/tips-tricks/custom-domain#step-by-step-guide)

## Next Steps

After completing local setup:
1. Review the project architecture documentation
2. Familiarize yourself with the component library
3. Understand the Supabase schema and API patterns
4. Review coding standards and contribution guidelines
5. Set up your IDE with recommended extensions