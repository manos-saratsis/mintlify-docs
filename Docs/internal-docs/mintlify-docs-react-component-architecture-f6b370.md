I'll analyze the source code to document the React Component Architecture. Let me start by exploring the project structure.

```javascript
const { readdirSync, statSync } = require('fs');
const { join } = require('path');

function exploreDirectory(dir, prefix = '', maxDepth = 4, currentDepth = 0) {
  if (currentDepth >= maxDepth) return;
  
  try {
    const items = readdirSync(dir);
    items.forEach(item => {
      if (item.startsWith('.')) return;
      
      const fullPath = join(dir, item);
      const stats = statSync(fullPath);
      
      if (stats.isDirectory()) {
        console.log(`${prefix}📁 ${item}/`);
        if (!['node_modules', '.git', 'dist', 'build'].includes(item)) {
          exploreDirectory(fullPath, prefix + '  ', maxDepth, currentDepth + 1);
        }
      } else {
        console.log(`${prefix}📄 ${item}`);
      }
    });
  } catch (err) {
    console.log(`${prefix}❌ Error reading directory`);
  }
}

console.log('Project Structure:');
exploreDirectory('/tmp/project');
```

```javascript
const fs = require('fs');
const path = require('path');

// Check for package.json to understand the tech stack
try {
  const packageJson = JSON.parse(fs.readFileSync('/tmp/project/package.json', 'utf8'));
  console.log('Project Name:', packageJson.name);
  console.log('\nDependencies:');
  console.log('- React:', packageJson.dependencies?.react || 'N/A');
  console.log('- React DOM:', packageJson.dependencies?.['react-dom'] || 'N/A');
  console.log('- TypeScript:', packageJson.devDependencies?.typescript || 'N/A');
  console.log('\nKey Dependencies:', Object.keys(packageJson.dependencies || {}).slice(0, 10).join(', '));
} catch (err) {
  console.log('Could not read package.json:', err.message);
}
```

```javascript
const fs = require('fs');
const path = require('path');

// Find all React components
function findReactFiles(dir, fileList = []) {
  const files = fs.readdirSync(dir);
  
  files.forEach(file => {
    const filePath = path.join(dir, file);
    const stat = fs.statSync(filePath);
    
    if (stat.isDirectory()) {
      if (!['node_modules', '.git', 'dist', 'build'].includes(file)) {
        findReactFiles(filePath, fileList);
      }
    } else if (file.match(/\.(tsx|jsx|ts|js)$/)) {
      fileList.push(filePath);
    }
  });
  
  return fileList;
}

const reactFiles = findReactFiles('/tmp/project/src');
console.log('Found', reactFiles.length, 'source files');
console.log('\nComponent files (first 30):');
reactFiles.slice(0, 30).forEach(f => console.log(f.replace('/tmp/project/', '')));
```

<read_file>
<path>package.json</path>
</read_file>

<read_file>
<path>src/App.tsx</path>
</read_file>

<read_file>
<path>src/main.tsx</path>
</read_file>

```javascript
const fs = require('fs');
const path = require('path');

// Find all component directories
function exploreComponentStructure(dir, level = 0) {
  if (level > 3) return;
  
  try {
    const items = fs.readdirSync(dir);
    items.forEach(item => {
      if (item.startsWith('.')) return;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        const indent = '  '.repeat(level);
        console.log(`${indent}${item}/`);
        exploreComponentStructure(fullPath, level + 1);
      } else if (item.match(/\.(tsx|jsx)$/)) {
        const indent = '  '.repeat(level);
        console.log(`${indent}${item}`);
      }
    });
  } catch (err) {
    // Skip
  }
}

console.log('\nComponent Structure:');
console.log('\nsrc/components:');
exploreComponentStructure('/tmp/project/src/components');
console.log('\nsrc/pages:');
exploreComponentStructure('/tmp/project/src/pages');
```

<read_file>
<path>src/components</path>
</read_file>

```javascript
const fs = require('fs');
const path = require('path');

// List all directories in src
try {
  const srcContents = fs.readdirSync('/tmp/project/src');
  console.log('Contents of src/:', srcContents);
} catch (err) {
  console.log('Error:', err.message);
}
```

<read_file>
<path>src</path>
</read_file>

```javascript
const fs = require('fs');

// Get all files in src root
const srcFiles = fs.readdirSync('/tmp/project/src');
console.log('Files in src/:', srcFiles);

// Read key files
const keyFiles = ['App.tsx', 'main.tsx', 'index.css', 'App.css'];
keyFiles.forEach(file => {
  const filePath = `/tmp/project/src/${file}`;
  if (fs.existsSync(filePath)) {
    console.log(`\n\n=== ${file} ===`);
    console.log(fs.readFileSync(filePath, 'utf8').slice(0, 500));
  }
});
```

<read_file>
<path>tsconfig.json</path>
</read_file>

<read_file>
<path>vite.config.ts</path>
</read_file>

<read_file>
<path>index.html</path>
</read_file>

```javascript
const fs = require('fs');
const path = require('path');

// Find all TypeScript/React files and categorize them
function categorizeFiles(dir, prefix = '') {
  const categories = {
    components: [],
    pages: [],
    hooks: [],
    contexts: [],
    utils: [],
    types: [],
    services: [],
    other: []
  };
  
  function scan(currentDir, currentPrefix) {
    try {
      const items = fs.readdirSync(currentDir);
      
      items.forEach(item => {
        if (item.startsWith('.') || ['node_modules', 'dist', 'build'].includes(item)) return;
        
        const fullPath = path.join(currentDir, item);
        const relativePath = path.join(currentPrefix, item);
        const stats = fs.statSync(fullPath);
        
        if (stats.isDirectory()) {
          scan(fullPath, relativePath);
        } else if (item.match(/\.(tsx|jsx|ts|js)$/)) {
          const content = fs.readFileSync(fullPath, 'utf8').slice(0, 1000);
          
          if (relativePath.includes('component') || content.match(/export\s+(default\s+)?function\s+\w+.*\{[\s\S]*?return\s*\(/)) {
            categories.components.push(relativePath);
          } else if (relativePath.includes('page') || relativePath.includes('route')) {
            categories.pages.push(relativePath);
          } else if (relativePath.includes('hook') || item.startsWith('use')) {
            categories.hooks.push(relativePath);
          } else if (relativePath.includes('context') || content.includes('createContext')) {
            categories.contexts.push(relativePath);
          } else if (relativePath.includes('util') || relativePath.includes('helper')) {
            categories.utils.push(relativePath);
          } else if (relativePath.includes('type') || item.endsWith('.d.ts')) {
            categories.types.push(relativePath);
          } else if (relativePath.includes('service') || relativePath.includes('api')) {
            categories.services.push(relativePath);
          } else {
            categories.other.push(relativePath);
          }
        }
      });
    } catch (err) {
      // Skip directories we can't read
    }
  }
  
  scan(dir, prefix);
  return categories;
}

const categories = categorizeFiles('/tmp/project/src', 'src');

console.log('=== FILE CATEGORIZATION ===\n');
Object.entries(categories).forEach(([category, files]) => {
  if (files.length > 0) {
    console.log(`\n${category.toUpperCase()} (${files.length}):`);
    files.forEach(f => console.log(`  - ${f}`));
  }
});
```

Now let me read the actual source files to understand the component architecture:

<read_file>
<path>src/App.tsx</path>
</read_file>

<read_file>
<path>src/main.tsx</path>
</read_file>

<read_file>
<path>src/vite-env.d.ts</path>
</read_file>

```javascript
const fs = require('fs');

// Check if there are any other directories or files we're missing
const srcPath = '/tmp/project/src';
const items = fs.readdirSync(srcPath, { withFileTypes: true });

console.log('All items in src/:');
items.forEach(item => {
  const type = item.isDirectory() ? 'DIR ' : 'FILE';
  console.log(`${type}: ${item.name}`);
  
  if (item.isDirectory() && !item.name.startsWith('.')) {
    const subPath = `/tmp/project/src/${item.name}`;
    const subItems = fs.readdirSync(subPath);
    console.log(`  Contains: ${subItems.join(', ')}`);
  }
});
```

Let me check if there's a public directory or assets:

```javascript
const fs = require('fs');

// Check project root for common directories
const rootPath = '/tmp/project';
const rootItems = fs.readdirSync(rootPath, { withFileTypes: true });

console.log('Project root directories:');
rootItems.forEach(item => {
  if (item.isDirectory() && !item.name.startsWith('.') && item.name !== 'node_modules') {
    console.log(`\n📁 ${item.name}/`);
    try {
      const subItems = fs.readdirSync(`${rootPath}/${item.name}`);
      console.log(`  Contains ${subItems.length} items: ${subItems.slice(0, 10).join(', ')}${subItems.length > 10 ? '...' : ''}`);
    } catch (err) {
      console.log('  (Cannot read)');
    }
  }
});
```

<read_file>
<path>README.md</path>
</read_file>

Now let me analyze the actual code structure more deeply:

```javascript
const fs = require('fs');

// Read the full content of main files
console.log('=== MAIN.TSX ===');
console.log(fs.readFileSync('/tmp/project/src/main.tsx', 'utf8'));

console.log('\n\n=== APP.TSX ===');
console.log(fs.readFileSync('/tmp/project/src/App.tsx', 'utf8'));

console.log('\n\n=== APP.CSS ===');
console.log(fs.readFileSync('/tmp/project/src/App.css', 'utf8'));

console.log('\n\n=== INDEX.CSS ===');
console.log(fs.readFileSync('/tmp/project/src/index.css', 'utf8'));
```

Now let me check for any configuration files or additional structure:

```javascript
const fs = require('fs');

// Check for common React patterns
const filesToCheck = [
  'src/router.tsx',
  'src/routes.tsx',
  'src/Router.tsx',
  'src/Routes.tsx',
  'src/contexts/index.tsx',
  'src/providers/index.tsx',
  'src/lib/index.ts',
  'src/config.ts',
  'src/constants.ts'
];

console.log('Checking for additional structure files:');
filesToCheck.forEach(file => {
  const fullPath = `/tmp/project/${file}`;
  if (fs.existsSync(fullPath)) {
    console.log(`✓ Found: ${file}`);
  }
});

// Check package.json for routing libraries
const pkg = JSON.parse(fs.readFileSync('/tmp/project/package.json', 'utf8'));
console.log('\n\nRouting/State Libraries:');
console.log('- react-router:', pkg.dependencies['react-router-dom'] || 'Not found');
console.log('- react-router-dom:', pkg.dependencies['react-router-dom'] || 'Not found');
console.log('- zustand:', pkg.dependencies['zustand'] || 'Not found');
console.log('- redux:', pkg.dependencies['redux'] || 'Not found');
console.log('- @tanstack/react-query:', pkg.dependencies['@tanstack/react-query'] || 'Not found');

console.log('\n\nAll dependencies:');
Object.keys(pkg.dependencies || {}).forEach(dep => console.log(`- ${dep}: ${pkg.dependencies[dep]}`));
```

Let me check if there are test files or additional documentation:

```javascript
const fs = require('fs');
const path = require('path');

// Find all files in the project (excluding node_modules)
function findAllFiles(dir, extensions = ['.tsx', '.ts', '.jsx', '.js', '.json', '.md'], depth = 0, maxDepth = 4) {
  if (depth > maxDepth) return [];
  
  let results = [];
  
  try {
    const items = fs.readdirSync(dir);
    
    for (const item of items) {
      if (item.startsWith('.') || ['node_modules', 'dist', 'build'].includes(item)) continue;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        results = results.concat(findAllFiles(fullPath, extensions, depth + 1, maxDepth));
      } else {
        const ext = path.extname(item);
        if (extensions.includes(ext)) {
          results.push(fullPath.replace('/tmp/project/', ''));
        }
      }
    }
  } catch (err) {
    // Skip
  }
  
  return results;
}

const allFiles = findAllFiles('/tmp/project');
console.log(`Found ${allFiles.length} relevant files:\n`);
allFiles.forEach(f => console.log(f));
```

Now let me create the comprehensive documentation based on what I've found:

```javascript
const fs = require('fs');

// Get complete file contents for documentation
const files = {
  'package.json': fs.readFileSync('/tmp/project/package.json', 'utf8'),
  'vite.config.ts': fs.readFileSync('/tmp/project/vite.config.ts', 'utf8'),
  'tsconfig.json': fs.readFileSync('/tmp/project/tsconfig.json', 'utf8'),
  'index.html': fs.readFileSync('/tmp/project/index.html', 'utf8'),
  'src/main.tsx': fs.readFileSync('/tmp/project/src/main.tsx', 'utf8'),
  'src/App.tsx': fs.readFileSync('/tmp/project/src/App.tsx', 'utf8'),
  'src/App.css': fs.readFileSync('/tmp/project/src/App.css', 'utf8'),
  'src/index.css': fs.readFileSync('/tmp/project/src/index.css', 'utf8'),
  'src/vite-env.d.ts': fs.readFileSync('/tmp/project/src/vite-env.d.ts', 'utf8')
};

// Parse package.json
const pkg = JSON.parse(files['package.json']);

console.log('=== PROJECT SUMMARY ===');
console.log('Name:', pkg.name);
console.log('React:', pkg.dependencies.react);
console.log('TypeScript:', pkg.devDependencies.typescript);
console.log('Build Tool: Vite');
console.log('\nAll Source Files Found:', Object.keys(files).join(', '));
```

Now I'll create the comprehensive documentation:

```javascript
const fs = require('fs');
const path = require('path');

const docContent = `# React Component Architecture

## Overview

This project implements a minimal React application built with TypeScript and Vite. The architecture follows a single-component pattern typical of starter React projects, with the main application logic contained in the root \`App\` component. The application uses React 18's modern features and is configured with strict TypeScript checking.

The component architecture is intentionally simple, serving as a foundation that can be extended with additional components, routing, and state management as needed.

## Implementation

### Entry Point and Rendering

**File**: \`src/main.tsx\`

The application entry point uses React 18's \`createRoot\` API for concurrent rendering:

\`\`\`typescript
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.tsx'

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
\`\`\`

**Key Implementation Details**:
- Uses \`createRoot\` from \`react-dom/client\` (React 18+ API)
- Wraps the application in \`<StrictMode>\` for development warnings and checks
- Mounts to a DOM element with id "root" defined in \`index.html\`
- Imports global styles from \`index.css\` before component rendering
- Uses TypeScript non-null assertion (\`!\`) operator for the root element

### Root Component

**File**: \`src/App.tsx\`

The \`App\` component serves as the root component of the application:

\`\`\`typescript
import { useState } from 'react'
import reactLogo from './assets/react.svg'
import viteLogo from '/vite.svg'
import './App.css'

function App() {
  const [count, setCount] = useState(0)

  return (
    <>
      <div>
        <a href="https://vite.dev" target="_blank">
          <img src={viteLogo} className="logo" alt="Vite logo" />
        </a>
        <a href="https://react.dev" target="_blank">
          <img src={reactLogo} className="logo react" alt="React logo" />
        </a>
      </div>
      <h1>Vite + React</h1>
      <div className="card">
        <button onClick={() => setCount((count) => count + 1)}>
          count is {count}
        </button>
        <p>
          Edit <code>src/App.tsx</code> and save to test HMR
        </p>
      </div>
      <p className="read-the-docs">
        Click on the Vite and React logos to learn more
      </p>
    </>
  )
}

export default App
\`\`\`

**Key Implementation Details**:
- Implements a functional component with React Hooks
- Uses \`useState\` hook for local state management (count state)
- Demonstrates React's state update pattern with functional updater: \`setCount((count) => count + 1)\`
- Imports component-scoped styles from \`App.css\`
- References static assets using two different import patterns:
  - Module import for React logo: \`import reactLogo from './assets/react.svg'\`
  - Public directory import for Vite logo: \`/vite.svg\`
- Uses React Fragment (\`<></>\`) as the root element
- Implements event handling with inline arrow function

### Component Structure

**Current Architecture**:
\`\`\`
src/
├── main.tsx          # Application entry point
├── App.tsx           # Root component
├── App.css           # Component-specific styles
├── index.css         # Global styles
├── vite-env.d.ts     # Vite type declarations
└── assets/
    └── react.svg     # Static assets
\`\`\`

The project uses a flat component structure with no subdirectories for components, hooks, contexts, or utilities. All application logic is contained within the single \`App\` component.

### Styling Architecture

**Global Styles** (\`src/index.css\`):

The project uses CSS custom properties (CSS variables) for theming:

\`\`\`css
:root {
  font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.5;
  font-weight: 400;

  color-scheme: light dark;
  color: rgba(255, 255, 255, 0.87);
  background-color: #242424;

  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
\`\`\`

Supports light and dark modes with \`@media (prefers-color-scheme: light)\` media query.

**Component Styles** (\`src/App.css\`):

Component-specific styles including:
- Logo animations with \`@keyframes logo-spin\`
- Interactive hover effects
- Responsive layout patterns

### Type System

**File**: \`src/vite-env.d.ts\`

\`\`\`typescript
/// <reference types="vite/client" />
\`\`\`

Provides TypeScript type definitions for Vite-specific features like:
- Import statements for static assets (images, CSS, etc.)
- Environment variables (\`import.meta.env\`)
- Hot Module Replacement (HMR) API

**TypeScript Configuration** (\`tsconfig.json\`):

\`\`\`json
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
    "noUncheckedSideEffectImports": true
  },
  "include": ["src"]
}
\`\`\`

Key settings:
- \`jsx: "react-jsx"\` enables React 17+ JSX transform (no need to import React)
- \`strict: true\` enables all strict type-checking options
- \`moduleResolution: "bundler"\` optimized for Vite bundling

### Build Configuration

**File**: \`vite.config.ts\`

\`\`\`typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

// https://vite.dev/config/
export default defineConfig({
  plugins: [react()],
})
\`\`\`

Uses the official \`@vitejs/plugin-react\` which provides:
- Fast Refresh (HMR) for React components
- JSX transformation
- React DevTools integration

### HTML Template

**File**: \`index.html\`

\`\`\`html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/vite.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Vite + React + TS</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
\`\`\`

The HTML file serves as the template for the application:
- Includes a \`<div id="root">\` mount point for React
- References the entry TypeScript file as an ES module
- Vite processes and bundles the module during build

## Usage

### Component Patterns

**Functional Components with Hooks**:

The project exclusively uses functional components with React Hooks. The \`App\` component demonstrates the standard pattern:

\`\`\`typescript
import { useState } from 'react'

function ComponentName() {
  const [state, setState] = useState(initialValue)
  
  return (
    <div>
      {/* JSX content */}
    </div>
  )
}

export default ComponentName
\`\`\`

**State Management**:

Local component state is managed using the \`useState\` hook (line 5 in \`src/App.tsx\`):

\`\`\`typescript
const [count, setCount] = useState(0)
\`\`\`

State updates use functional updaters for reliable updates based on previous state:

\`\`\`typescript
setCount((count) => count + 1)
\`\`\`

**Event Handling**:

Events are handled using inline arrow functions (line 17 in \`src/App.tsx\`):

\`\`\`typescript
<button onClick={() => setCount((count) => count + 1)}>
  count is {count}
</button>
\`\`\`

### Asset Imports

**Module Assets** (processed by Vite):

\`\`\`typescript
import reactLogo from './assets/react.svg'

<img src={reactLogo} alt="React logo" />
\`\`\`

**Public Directory Assets** (served as-is):

\`\`\`typescript
<img src="/vite.svg" alt="Vite logo" />
\`\`\`

### Style Integration

**Global Styles**:

Imported in \`src/main.tsx\` before component rendering:

\`\`\`typescript
import './index.css'
\`\`\`

**Component Styles**:

Imported at the component level in \`src/App.tsx\`:

\`\`\`typescript
import './App.css'
\`\`\`

### Development Workflow

**Start Development Server**:

\`\`\`bash
npm run dev
\`\`\`

Starts Vite dev server with Hot Module Replacement (HMR). Changes to components trigger automatic updates without full page reload.

**Build for Production**:

\`\`\`bash
npm run build
\`\`\`

Compiles TypeScript and bundles the application for production. Output is placed in \`dist/\` directory.

**Preview Production Build**:

\`\`\`bash
npm run preview
\`\`\`

Serves the production build locally for testing.

**Type Checking**:

\`\`\`bash
npm run lint
\`\`\`

Runs ESLint for code quality checks as configured in the project.

### Extending the Architecture

**Adding New Components**:

Create new component files in \`src/\`:

\`\`\`typescript
// src/NewComponent.tsx
import { useState } from 'react'

function NewComponent() {
  return <div>New Component</div>
}

export default NewComponent
\`\`\`

Import and use in \`App.tsx\`:

\`\`\`typescript
import NewComponent from './NewComponent'

function App() {
  return (
    <>
      <NewComponent />
    </>
  )
}
\`\`\`

**Organizing Components** (Recommended for Growth):

Create a component directory structure:

\`\`\`
src/
├── components/
│   ├── Button/
│   │   ├── Button.tsx
│   │   └── Button.css
│   └── Header/
│       ├── Header.tsx
│       └── Header.css
├── pages/
│   └── Home.tsx
├── hooks/
│   └── useCustomHook.ts
└── App.tsx
\`\`\`

**Adding Routing** (requires installation):

\`\`\`bash
npm install react-router-dom
\`\`\`

Example router setup:

\`\`\`typescript
import { BrowserRouter, Routes, Route } from 'react-router-dom'

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  )
}
\`\`\`

## Technical Stack

**Dependencies** (from \`package.json\`):

- \`react: ^18.3.1\` - Core React library
- \`react-dom: ^18.3.1\` - React rendering for web

**Dev Dependencies**:

- \`@vitejs/plugin-react: ^4.3.4\` - Vite plugin for React support
- \`vite: ^6.0.5\` - Build tool and dev server
- \`typescript: ~5.6.2\` - TypeScript compiler
- \`@types/react: ^18.3.12\` - TypeScript definitions for React
- \`@types/react-dom: ^18.3.1\` - TypeScript definitions for ReactDOM
- \`eslint: ^9.15.0\` - JavaScript/TypeScript linter
- \`@eslint/js: ^9.15.0\` - ESLint JavaScript rules
- \`typescript-eslint: ^8.15.0\` - ESLint plugin for TypeScript
- \`eslint-plugin-react-hooks: ^5.0.0\` - ESLint rules for React Hooks
- \`eslint-plugin-react-refresh: ^0.4.14\` - ESLint rules for React Fast Refresh
- \`globals: ^15.12.0\` - Global identifier definitions

## Key Patterns and Conventions

### Naming Conventions

- **Components**: PascalCase (\`App\`, \`NewComponent\`)
- **Files**: Match component names (\`App.tsx\`, \`NewComponent.tsx\`)
- **Hooks**: camelCase starting with "use" (\`useState\`, \`useEffect\`)
- **Props interfaces**: PascalCase with "Props" suffix (when needed)

### Import Organization

Standard import order demonstrated in \`src/main.tsx\` and \`src/App.tsx\`:

1. React imports
2. Third-party library imports
3. Local component imports
4. Style imports
5. Asset imports

### Code Organization

- TypeScript strict mode enabled for type safety
- ESLint configured for code quality
- StrictMode wrapper for development checks
- No prop-types (TypeScript provides type checking)

### Performance Considerations

- Uses React 18's concurrent rendering features
- Vite provides optimized development experience with HMR
- Production builds are optimized with code splitting and minification