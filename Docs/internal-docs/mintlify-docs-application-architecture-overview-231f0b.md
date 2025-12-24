I'll analyze the source code to create comprehensive architecture documentation. Let me start by exploring the project structure.

```js
const fs = require('fs');
const path = require('path');

function exploreDirectory(dir, maxDepth = 3, currentDepth = 0, prefix = '') {
  if (currentDepth >= maxDepth) return [];
  
  try {
    const items = fs.readdirSync(dir);
    let result = [];
    
    items.forEach(item => {
      if (item.startsWith('.') || item === 'node_modules' || item === 'dist' || item === 'build') return;
      
      const fullPath = path.join(dir, item);
      const stat = fs.statSync(fullPath);
      const relativePath = fullPath.replace(process.cwd() + '/', '');
      
      if (stat.isDirectory()) {
        result.push(`${prefix}📁 ${item}/`);
        result = result.concat(exploreDirectory(fullPath, maxDepth, currentDepth + 1, prefix + '  '));
      } else {
        result.push(`${prefix}📄 ${item}`);
      }
    });
    
    return result;
  } catch (err) {
    return [`${prefix}❌ Error reading directory: ${err.message}`];
  }
}

console.log('Project Structure:\n');
const structure = exploreDirectory(process.cwd(), 4);
console.log(structure.join('\n'));
```

```js
// Let me check for common configuration files
const fs = require('fs');

const configFiles = [
  'package.json',
  'tsconfig.json',
  'vite.config.ts',
  'vite.config.js',
  'next.config.js',
  'README.md',
  '.env.example'
];

configFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content.substring(0, 2000)); // First 2000 chars
    }
  } catch (err) {
    // File doesn't exist, skip
  }
});
```

```js
// Check for source code structure
const fs = require('fs');
const path = require('path');

function findFiles(dir, extension, maxFiles = 50) {
  let results = [];
  
  try {
    const items = fs.readdirSync(dir);
    
    for (const item of items) {
      if (results.length >= maxFiles) break;
      if (item.startsWith('.') || item === 'node_modules' || item === 'dist' || item === 'build') continue;
      
      const fullPath = path.join(dir, item);
      const stat = fs.statSync(fullPath);
      
      if (stat.isDirectory()) {
        results = results.concat(findFiles(fullPath, extension, maxFiles - results.length));
      } else if (fullPath.endsWith(extension)) {
        results.push(fullPath);
      }
    }
  } catch (err) {
    // Skip errors
  }
  
  return results;
}

console.log('\n========== Key Files ==========');
console.log('\nTypeScript/JavaScript files:');
const tsFiles = findFiles(process.cwd(), '.ts', 30);
const jsxFiles = findFiles(process.cwd(), '.tsx', 30);
console.log([...tsFiles, ...jsxFiles].slice(0, 30).join('\n'));
```

```js
// Read main entry points
const fs = require('fs');

const entryPoints = [
  'src/main.tsx',
  'src/main.ts',
  'src/index.tsx',
  'src/index.ts',
  'src/App.tsx',
  'src/App.ts',
  'pages/_app.tsx',
  'pages/index.tsx'
];

entryPoints.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content);
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Check for routing files
const fs = require('fs');
const path = require('path');

const routingFiles = [
  'src/router.tsx',
  'src/router.ts',
  'src/routes.tsx',
  'src/routes.ts',
  'src/App.tsx',
  'src/app/layout.tsx',
  'src/app/page.tsx'
];

routingFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content);
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Check for Supabase functions
const fs = require('fs');
const path = require('path');

function listDirectory(dir) {
  try {
    if (fs.existsSync(dir)) {
      console.log(`\n========== ${dir} Structure ==========`);
      const items = fs.readdirSync(dir);
      items.forEach(item => {
        const fullPath = path.join(dir, item);
        const stat = fs.statSync(fullPath);
        if (stat.isDirectory()) {
          console.log(`📁 ${item}/`);
          const subItems = fs.readdirSync(fullPath);
          subItems.forEach(subItem => {
            console.log(`  📄 ${subItem}`);
          });
        } else {
          console.log(`📄 ${item}`);
        }
      });
    }
  } catch (err) {
    console.log(`Error reading ${dir}: ${err.message}`);
  }
}

listDirectory('supabase/functions');
listDirectory('supabase/migrations');
```

```js
// Check for context providers and hooks
const fs = require('fs');
const path = require('path');

function listDirectoryContents(dir) {
  try {
    if (fs.existsSync(dir)) {
      console.log(`\n========== ${dir} ==========`);
      const items = fs.readdirSync(dir);
      items.forEach(item => {
        console.log(`- ${item}`);
      });
      return items;
    }
  } catch (err) {
    // Skip
  }
  return [];
}

const contexts = listDirectoryContents('src/contexts');
const hooks = listDirectoryContents('src/hooks');
const components = listDirectoryContents('src/components');
const pages = listDirectoryContents('src/pages');
const services = listDirectoryContents('src/services');
const utils = listDirectoryContents('src/utils');
const lib = listDirectoryContents('src/lib');
```

```js
// Read key architectural files
const fs = require('fs');

const architecturalFiles = [
  'src/contexts/AuthContext.tsx',
  'src/contexts/ThemeContext.tsx',
  'src/hooks/useAuth.ts',
  'src/lib/supabase.ts',
  'src/services/api.ts',
  'src/utils/helpers.ts'
];

architecturalFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content.substring(0, 3000));
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Check for environment variables and configuration
const fs = require('fs');

const configFiles = [
  '.env.example',
  '.env.local.example',
  'src/config.ts',
  'src/config/index.ts',
  'src/constants.ts'
];

configFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content);
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Read database schema migrations
const fs = require('fs');
const path = require('path');

try {
  const migrationsDir = 'supabase/migrations';
  if (fs.existsSync(migrationsDir)) {
    console.log('\n========== Database Migrations ==========');
    const files = fs.readdirSync(migrationsDir).sort();
    
    files.slice(0, 5).forEach(file => {
      const fullPath = path.join(migrationsDir, file);
      console.log(`\n--- ${file} ---`);
      const content = fs.readFileSync(fullPath, 'utf8');
      console.log(content.substring(0, 2000));
    });
  }
} catch (err) {
  console.log('No migrations found');
}
```

```js
// Read Supabase edge functions
const fs = require('fs');
const path = require('path');

try {
  const functionsDir = 'supabase/functions';
  if (fs.existsSync(functionsDir)) {
    console.log('\n========== Supabase Edge Functions ==========');
    const functions = fs.readdirSync(functionsDir);
    
    functions.forEach(funcName => {
      const funcPath = path.join(functionsDir, funcName);
      const stat = fs.statSync(funcPath);
      
      if (stat.isDirectory()) {
        console.log(`\n--- Function: ${funcName} ---`);
        const indexPath = path.join(funcPath, 'index.ts');
        
        if (fs.existsSync(indexPath)) {
          const content = fs.readFileSync(indexPath, 'utf8');
          console.log(content.substring(0, 2000));
        }
      }
    });
  }
} catch (err) {
  console.log('No edge functions found');
}
```

```js
// Check for type definitions
const fs = require('fs');
const path = require('path');

const typeFiles = [
  'src/types/index.ts',
  'src/types.ts',
  'src/types/supabase.ts',
  'src/types/database.ts',
  'src/@types/index.d.ts'
];

typeFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content.substring(0, 3000));
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Get component structure
const fs = require('fs');
const path = require('path');

function exploreComponents(dir, depth = 0, maxDepth = 3) {
  if (depth > maxDepth) return;
  
  try {
    if (!fs.existsSync(dir)) return;
    
    const items = fs.readdirSync(dir);
    const indent = '  '.repeat(depth);
    
    items.forEach(item => {
      if (item.startsWith('.')) return;
      
      const fullPath = path.join(dir, item);
      const stat = fs.statSync(fullPath);
      
      if (stat.isDirectory()) {
        console.log(`${indent}📁 ${item}/`);
        exploreComponents(fullPath, depth + 1, maxDepth);
      } else if (item.endsWith('.tsx') || item.endsWith('.ts')) {
        console.log(`${indent}📄 ${item}`);
      }
    });
  } catch (err) {
    // Skip
  }
}

console.log('\n========== Component Structure ==========');
exploreComponents('src/components');

console.log('\n========== Pages Structure ==========');
exploreComponents('src/pages');
```

```js
// Read main layout and component files
const fs = require('fs');

const layoutFiles = [
  'src/components/Layout.tsx',
  'src/components/layout/Layout.tsx',
  'src/components/Layout/index.tsx',
  'src/layouts/MainLayout.tsx',
  'src/components/Navbar.tsx',
  'src/components/Header.tsx',
  'src/components/Sidebar.tsx'
];

layoutFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content.substring(0, 2000));
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Look for authentication implementation
const fs = require('fs');

const authFiles = [
  'src/contexts/AuthContext.tsx',
  'src/contexts/AuthContext.ts',
  'src/hooks/useAuth.tsx',
  'src/hooks/useAuth.ts',
  'src/pages/Login.tsx',
  'src/pages/login.tsx',
  'src/components/ProtectedRoute.tsx',
  'src/guards/AuthGuard.tsx'
];

authFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content);
    }
  } catch (err) {
    // Skip
  }
});
```

```js
// Check state management approach
const fs = require('fs');

const stateFiles = [
  'src/store/index.ts',
  'src/store/store.ts',
  'src/redux/store.ts',
  'src/state/index.ts',
  'src/contexts/AppContext.tsx',
  'src/contexts/index.tsx'
];

stateFiles.forEach(file => {
  try {
    if (fs.existsSync(file)) {
      console.log(`\n========== ${file} ==========`);
      const content = fs.readFileSync(file, 'utf8');
      console.log(content);
    }
  } catch (err) {
    // Skip
  }
});
```

Based on the exploration above, let me read any additional critical files that were found:

```js
// Final check for any critical files found in the structure
const fs = require('fs');
const path = require('path');

// List all immediate children of src
try {
  if (fs.existsSync('src')) {
    console.log('\n========== src/ Directory Contents ==========');
    const items = fs.readdirSync('src');
    items.forEach(item => {
      const fullPath = path.join('src', item);
      const stat = fs.statSync(fullPath);
      console.log(`${stat.isDirectory() ? '📁' : '📄'} ${item}`);
    });
  }
} catch (err) {
  console.log('Cannot read src directory');
}

// Check public/static assets structure
try {
  if (fs.existsSync('public')) {
    console.log('\n========== public/ Directory Contents ==========');
    const items = fs.readdirSync('public');
    console.log(items.join('\n'));
  }
} catch (err) {
  // Skip
}
```

Now let me create the architecture documentation based on what I've discovered:

```js
// Generate a summary of what we found
const fs = require('fs');

console.log('\n========== ARCHITECTURE SUMMARY ==========\n');

// Check what exists
const checks = {
  'package.json': fs.existsSync('package.json'),
  'tsconfig.json': fs.existsSync('tsconfig.json'),
  'vite.config': fs.existsSync('vite.config.ts') || fs.existsSync('vite.config.js'),
  'src/main.tsx': fs.existsSync('src/main.tsx'),
  'src/App.tsx': fs.existsSync('src/App.tsx'),
  'src/components': fs.existsSync('src/components'),
  'src/pages': fs.existsSync('src/pages'),
  'src/hooks': fs.existsSync('src/hooks'),
  'src/contexts': fs.existsSync('src/contexts'),
  'src/lib': fs.existsSync('src/lib'),
  'src/utils': fs.existsSync('src/utils'),
  'src/services': fs.existsSync('src/services'),
  'src/types': fs.existsSync('src/types'),
  'supabase/functions': fs.existsSync('supabase/functions'),
  'supabase/migrations': fs.existsSync('supabase/migrations')
};

Object.entries(checks).forEach(([name, exists]) => {
  console.log(`${exists ? '✅' : '❌'} ${name}`);
});

// If package.json exists, read it for tech stack info
if (checks['package.json']) {
  console.log('\n========== Tech Stack (from package.json) ==========');
  const pkg = JSON.parse(fs.readFileSync('package.json', 'utf8'));
  console.log('\nDependencies:');
  if (pkg.dependencies) {
    Object.keys(pkg.dependencies).slice(0, 15).forEach(dep => {
      console.log(`- ${dep}: ${pkg.dependencies[dep]}`);
    });
  }
}
```

Since I don't have access to the actual source code yet, let me check if there are any files in the current directory:

```js
const fs = require('fs');

console.log('\n========== Current Directory Listing ==========');
try {
  const files = fs.readdirSync('.');
  console.log(files.join('\n'));
} catch (err) {
  console.log('Error:', err.message);
}
```

I notice I don't have access to the actual source code files. Let me create a documentation template that acknowledges this limitation:

# Application Architecture Overview

## Overview

Unable to generate architecture documentation as no source code files are accessible in the current environment. To create comprehensive architecture documentation, the following source code artifacts are required:

### Required Artifacts for Architecture Documentation:

1. **Project Configuration Files**:
   - `package.json` - Dependencies and scripts
   - `tsconfig.json` or `jsconfig.json` - TypeScript/JavaScript configuration
   - Build configuration (`vite.config.ts`, `webpack.config.js`, `next.config.js`, etc.)

2. **Entry Points**:
   - Main application entry (`src/main.tsx`, `src/index.tsx`, `pages/_app.tsx`, etc.)
   - Root application component (`src/App.tsx`, `src/App.jsx`)
   - Router configuration

3. **Directory Structure**:
   - `/src/components` - UI components
   - `/src/pages` or `/pages` - Page/route components
   - `/src/hooks` - Custom React hooks
   - `/src/contexts` - Context providers
   - `/src/lib` - Third-party integrations
   - `/src/services` - API services
   - `/src/utils` - Utility functions
   - `/src/types` - TypeScript type definitions

4. **Backend/API Layer**:
   - `/supabase/functions` - Edge functions
   - `/supabase/migrations` - Database migrations
   - API route handlers
   - Database schema files

5. **State Management**:
   - Context providers
   - Redux/Zustand store configuration
   - Custom hooks for state management

6. **Authentication & Authorization**:
   - Auth context/provider implementation
   - Protected route components
   - Authentication hooks

## Implementation

No implementation details available without source code access.

## Usage

To generate proper architecture documentation:

1. Provide access to the source code repository
2. Ensure all configuration files are readable
3. Include database migration files if applicable
4. Provide access to edge functions or API routes

Once source code is accessible, documentation will include:

- **Technology Stack**: Detailed breakdown of frameworks, libraries, and tools
- **Project Structure**: Complete directory hierarchy with purpose of each folder
- **Component Architecture**: Component relationships and data flow
- **Routing Structure**: Route definitions and navigation patterns
- **State Management**: Context providers, hooks, and state patterns
- **API Integration**: Backend endpoints, edge functions, and database access
- **Authentication Flow**: Login/logout flow and protected routes
- **Build & Deployment**: Build process and deployment configuration
- **Type System**: TypeScript interfaces and type definitions
- **Code Organization Patterns**: Naming conventions and architectural patterns

---

**Note**: This documentation cannot be completed without access to the actual source code. Please provide the codebase for accurate, implementation-based documentation.