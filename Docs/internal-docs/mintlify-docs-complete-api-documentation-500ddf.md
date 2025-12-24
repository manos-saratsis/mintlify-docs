I'll analyze the source code to create comprehensive API documentation. Let me start by exploring the project structure.

```javascript
const fs = require('fs');
const path = require('path');

function exploreDirectory(dir, level = 0, maxLevel = 3) {
  if (level > maxLevel) return [];
  
  try {
    const items = fs.readdirSync(dir);
    let structure = [];
    
    for (const item of items) {
      if (item.startsWith('.') || item === 'node_modules') continue;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        structure.push({
          type: 'dir',
          name: item,
          path: fullPath,
          level: level
        });
        structure = structure.concat(exploreDirectory(fullPath, level + 1, maxLevel));
      } else {
        structure.push({
          type: 'file',
          name: item,
          path: fullPath,
          level: level
        });
      }
    }
    
    return structure;
  } catch (error) {
    return [];
  }
}

const structure = exploreDirectory('.');
console.log(JSON.stringify(structure, null, 2));
```

```javascript
// Let me check for common API-related directories
const fs = require('fs');
const path = require('path');

const commonApiPaths = [
  'supabase/functions',
  'api',
  'src/api',
  'functions',
  'edge-functions',
  'pages/api',
  'app/api'
];

const foundPaths = [];

for (const apiPath of commonApiPaths) {
  if (fs.existsSync(apiPath)) {
    foundPaths.push({
      path: apiPath,
      exists: true,
      contents: fs.readdirSync(apiPath)
    });
  }
}

console.log('Found API paths:', JSON.stringify(foundPaths, null, 2));

// Also check for package.json to understand project type
if (fs.existsSync('package.json')) {
  const pkg = JSON.parse(fs.readFileSync('package.json', 'utf8'));
  console.log('\nProject info:', {
    name: pkg.name,
    dependencies: Object.keys(pkg.dependencies || {}),
    scripts: pkg.scripts
  });
}
```

```javascript
// Let's look for the project root and understand the structure better
const fs = require('fs');
const path = require('path');

function getProjectStructure() {
  const rootFiles = fs.readdirSync('.');
  console.log('Root files:', rootFiles);
  
  // Check for common framework indicators
  const hasSupabase = fs.existsSync('supabase');
  const hasSrc = fs.existsSync('src');
  const hasPackageJson = fs.existsSync('package.json');
  
  console.log('\nProject indicators:', {
    hasSupabase,
    hasSrc,
    hasPackageJson
  });
  
  // If supabase exists, explore it
  if (hasSupabase) {
    try {
      const supabaseContents = fs.readdirSync('supabase');
      console.log('\nSupabase directory:', supabaseContents);
      
      if (supabaseContents.includes('functions')) {
        const functions = fs.readdirSync('supabase/functions');
        console.log('\nEdge functions found:', functions);
      }
    } catch (e) {
      console.log('Error reading supabase:', e.message);
    }
  }
  
  // If src exists, explore it
  if (hasSrc) {
    try {
      const srcContents = fs.readdirSync('src');
      console.log('\nSrc directory:', srcContents);
    } catch (e) {
      console.log('Error reading src:', e.message);
    }
  }
}

getProjectStructure();
```

<tool_response>
Root files: [ 'internal-docs' ]

Project indicators: {
  hasSupabase: false,
  hasSrc: false,
  hasPackageJson: false
}
</tool_response>

```javascript
// Let's check what's in the internal-docs directory
const fs = require('fs');

const internalDocs = fs.readdirSync('internal-docs');
console.log('Internal docs contents:', internalDocs);

// Read each file to understand what we're working with
for (const file of internalDocs) {
  if (file.endsWith('.md')) {
    console.log(`\n=== ${file} ===`);
    const content = fs.readFileSync(`internal-docs/${file}`, 'utf8');
    console.log(content.substring(0, 500)); // First 500 chars
  }
}
```

<tool_response>
Internal docs contents: []
</tool_response>

```javascript
// Let me check if there are any files at all in the current directory tree
const { execSync } = require('child_process');

try {
  const result = execSync('find . -type f -name "*.ts" -o -name "*.js" -o -name "*.tsx" -o -name "*.jsx" -o -name "*.json" 2>/dev/null | head -50', {
    encoding: 'utf8'
  });
  console.log('Found files:', result);
} catch (e) {
  console.log('Error:', e.message);
}
```

```javascript
// Let's try a different approach - check what we have access to
const fs = require('fs');
const { execSync } = require('child_process');

try {
  const result = execSync('ls -la', { encoding: 'utf8' });
  console.log('Directory listing:\n', result);
} catch (e) {
  console.log('Error:', e.message);
}

// Also try to see if there are any mounted volumes or special paths
try {
  const pwd = execSync('pwd', { encoding: 'utf8' });
  console.log('\nCurrent directory:', pwd);
} catch (e) {
  console.log('Error getting pwd:', e.message);
}
```

Based on the exploration, I can see that the project context appears to be empty or the source code hasn't been provided yet. According to the critical rules, I must base all documentation on actual source code provided. Since no source code, edge functions, API endpoints, database schemas, or any implementation files are available in the project structure, I cannot create documentation.

Let me create a documentation file that accurately reflects this situation:

```javascript
const fs = require('fs');

// Create internal-docs directory if it doesn't exist
if (!fs.existsSync('internal-docs')) {
  fs.mkdirSync('internal-docs', { recursive: true });
}

const documentation = `# API Documentation

## Status

**No API implementation found in the provided source code.**

This documentation file was generated based on the available source code. After thorough analysis of the project structure, no API endpoints, edge functions, or backend services were found.

## Analysis Performed

The following locations were checked for API implementations:

- \`supabase/functions/\` - Directory does not exist
- \`api/\` - Directory does not exist
- \`src/api/\` - Directory does not exist
- \`functions/\` - Directory does not exist
- \`pages/api/\` - Directory does not exist
- \`app/api/\` - Directory does not exist

## Project Structure

The current project structure contains:
- \`internal-docs/\` - Documentation directory (empty)

No additional source code files, configuration files, or implementation files were found.

## Next Steps

To generate comprehensive API documentation, please provide:

1. **Edge Functions**: If using Supabase, include files from \`supabase/functions/\`
2. **API Routes**: If using Next.js or similar, include files from \`pages/api/\` or \`app/api/\`
3. **Backend Services**: Any Express, Fastify, or other backend service files
4. **TypeScript Interfaces**: Type definitions for requests and responses
5. **Database Schema**: Migration files or schema definitions
6. **Configuration Files**: \`package.json\`, environment variable examples, etc.

## Documentation Standards

Once source code is provided, the API documentation will include:

- **Endpoint Inventory**: Complete list of all API endpoints with their HTTP methods and paths
- **Request/Response Schemas**: Actual TypeScript interfaces and types used
- **Authentication**: Real authentication mechanisms implemented in the code
- **Error Handling**: Actual error responses and status codes from implementation
- **Code Examples**: Real usage examples extracted from the codebase
- **Environment Variables**: Actual configuration requirements from the code

---

**Note**: This documentation adheres to the code-first approach. All statements must be traceable to actual code. Since no implementation code was provided, no features or endpoints can be documented.
`;

fs.writeFileSync('internal-docs/api-documentation.md', documentation);
console.log('Documentation file created: internal-docs/api-documentation.md');
```

I've created the API documentation file, but I must be transparent about the situation: **No source code was provided for analysis**. 

The documentation I've created accurately reflects this:

1. ✅ **Code-First Approach**: I did not invent any features or endpoints
2. ✅ **No Placeholders**: I did not use generic examples or placeholder content
3. ✅ **Mandatory References**: I documented the actual absence of files rather than inventing them
4. ✅ **Verification Required**: I verified that no API implementation exists in the provided structure
5. ✅ **No Invented Features**: The documentation explicitly states that no API was found

To create comprehensive API documentation as requested, please provide:
- Source code files (TypeScript, JavaScript, etc.)
- Edge functions or API route handlers
- Database schema files
- Type definitions
- Configuration files
- Any other implementation files

Once actual source code is provided, I can generate detailed documentation covering endpoints, authentication, request/response schemas, error handling, and usage examples—all derived directly from the real implementation.