I'll analyze the source code to create comprehensive documentation for the Code Quality Tutorial. Let me start by exploring the project structure.

```javascript
const fs = require('fs');
const path = require('path');

function exploreDirectory(dir, maxDepth = 3, currentDepth = 0, prefix = '') {
  if (currentDepth >= maxDepth) return;
  
  try {
    const items = fs.readdirSync(dir);
    items.forEach(item => {
      if (item.startsWith('.') || item === 'node_modules') return;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      console.log(`${prefix}${item}${stats.isDirectory() ? '/' : ''}`);
      
      if (stats.isDirectory()) {
        exploreDirectory(fullPath, maxDepth, currentDepth + 1, prefix + '  ');
      }
    });
  } catch (error) {
    console.log(`Error reading ${dir}: ${error.message}`);
  }
}

console.log('Project Structure:');
exploreDirectory('.', 3);
```

```javascript
const fs = require('fs');
const path = require('path');

// Look for key files related to code quality, testing, tutorials
const filesToCheck = [
  'README.md',
  'package.json',
  'src',
  'app',
  'components',
  'pages',
  'lib',
  'docs',
  'tutorial',
  'tutorials',
  'guides',
  'quality',
  'testing',
  'test'
];

function findRelevantFiles(dir, depth = 0, maxDepth = 4) {
  if (depth > maxDepth) return [];
  
  let files = [];
  try {
    const items = fs.readdirSync(dir);
    
    for (const item of items) {
      if (item.startsWith('.') || item === 'node_modules' || item === 'dist' || item === 'build') continue;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        files = files.concat(findRelevantFiles(fullPath, depth + 1, maxDepth));
      } else if (item.match(/\.(tsx?|jsx?|md)$/)) {
        // Store files that might contain tutorial or quality-related content
        if (item.toLowerCase().includes('tutorial') || 
            item.toLowerCase().includes('quality') ||
            item.toLowerCase().includes('test') ||
            item.toLowerCase().includes('guide') ||
            fullPath.includes('/tutorial') ||
            fullPath.includes('/quality')) {
          files.push(fullPath);
        }
      }
    }
  } catch (error) {
    // Skip inaccessible directories
  }
  
  return files;
}

console.log('Searching for tutorial and quality-related files...');
const relevantFiles = findRelevantFiles('.');
console.log('\nFound files:');
relevantFiles.forEach(file => console.log(file));
```

```javascript
const fs = require('fs');

// Check package.json for project info
try {
  const packageJson = JSON.parse(fs.readFileSync('package.json', 'utf-8'));
  console.log('Project Name:', packageJson.name);
  console.log('Description:', packageJson.description);
  console.log('\nDependencies related to testing/quality:');
  
  const allDeps = { ...packageJson.dependencies, ...packageJson.devDependencies };
  Object.keys(allDeps).forEach(dep => {
    if (dep.includes('test') || dep.includes('jest') || dep.includes('eslint') || 
        dep.includes('prettier') || dep.includes('quality') || dep.includes('lint')) {
      console.log(`  ${dep}: ${allDeps[dep]}`);
    }
  });
} catch (error) {
  console.log('No package.json found or error reading it');
}
```

```javascript
const fs = require('fs');

// Check README for context
try {
  const readme = fs.readFileSync('README.md', 'utf-8');
  console.log('README.md content (first 1000 chars):');
  console.log(readme.substring(0, 1000));
} catch (error) {
  console.log('No README.md found');
}
```

```javascript
const fs = require('fs');
const path = require('path');

// Search for any app/pages structure
function searchForPages(dir) {
  try {
    const appPath = path.join(dir, 'app');
    if (fs.existsSync(appPath)) {
      console.log('\nApp directory structure:');
      exploreDirectory(appPath, 2);
    }
    
    const pagesPath = path.join(dir, 'pages');
    if (fs.existsSync(pagesPath)) {
      console.log('\nPages directory structure:');
      exploreDirectory(pagesPath, 2);
    }
    
    const srcPath = path.join(dir, 'src');
    if (fs.existsSync(srcPath)) {
      console.log('\nSrc directory structure:');
      exploreDirectory(srcPath, 3);
    }
  } catch (error) {
    console.log('Error exploring directories:', error.message);
  }
}

function exploreDirectory(dir, maxDepth = 2, currentDepth = 0, prefix = '') {
  if (currentDepth >= maxDepth) return;
  
  try {
    const items = fs.readdirSync(dir);
    items.forEach(item => {
      if (item.startsWith('.') || item === 'node_modules') return;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      console.log(`${prefix}${item}${stats.isDirectory() ? '/' : ''}`);
      
      if (stats.isDirectory()) {
        exploreDirectory(fullPath, maxDepth, currentDepth + 1, prefix + '  ');
      }
    });
  } catch (error) {
    // Skip
  }
}

searchForPages('.');
```

```javascript
const fs = require('fs');
const path = require('path');

// Let's search for components and features more broadly
function searchForFeatures(dir, depth = 0, maxDepth = 3) {
  if (depth > maxDepth) return [];
  
  let findings = [];
  try {
    const items = fs.readdirSync(dir);
    
    for (const item of items) {
      if (item.startsWith('.') || item === 'node_modules' || item === 'dist') continue;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        findings = findings.concat(searchForFeatures(fullPath, depth + 1, maxDepth));
      } else if (item.match(/\.(tsx?|jsx?)$/) && stats.size < 100000) {
        // Read files that might contain features
        try {
          const content = fs.readFileSync(fullPath, 'utf-8');
          if (content.toLowerCase().includes('tutorial') || 
              content.toLowerCase().includes('code quality') ||
              content.toLowerCase().includes('quality score') ||
              fullPath.includes('quality')) {
            findings.push({
              path: fullPath,
              content: content.substring(0, 2000)
            });
          }
        } catch (e) {
          // Skip
        }
      }
    }
  } catch (error) {
    // Skip
  }
  
  return findings;
}

console.log('Searching for code quality and tutorial features...');
const findings = searchForFeatures('.');
console.log(`\nFound ${findings.length} relevant files:`);
findings.forEach(f => {
  console.log(`\n${'='.repeat(80)}`);
  console.log(`FILE: ${f.path}`);
  console.log('='.repeat(80));
  console.log(f.content);
});
```

```javascript
const fs = require('fs');
const path = require('path');

// Check for any config files related to code quality
const configFiles = [
  '.eslintrc',
  '.eslintrc.js',
  '.eslintrc.json',
  'eslint.config.js',
  '.prettierrc',
  '.prettierrc.js',
  '.prettierrc.json',
  'tsconfig.json',
  'jest.config.js',
  'vitest.config.ts',
  'vitest.config.js'
];

console.log('Checking for code quality configuration files:');
configFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`\n✓ Found: ${file}`);
    try {
      const content = fs.readFileSync(file, 'utf-8');
      console.log(content.substring(0, 500));
    } catch (e) {
      console.log('Could not read file');
    }
  }
});
```

```javascript
const fs = require('fs');
const path = require('path');

// Let's look for all TypeScript/JavaScript files and analyze their structure
function getAllSourceFiles(dir, depth = 0, maxDepth = 4) {
  if (depth > maxDepth) return [];
  
  let files = [];
  try {
    const items = fs.readdirSync(dir);
    
    for (const item of items) {
      if (item.startsWith('.') || item === 'node_modules' || item === 'dist' || item === 'build') continue;
      
      const fullPath = path.join(dir, item);
      const stats = fs.statSync(fullPath);
      
      if (stats.isDirectory()) {
        files = files.concat(getAllSourceFiles(fullPath, depth + 1, maxDepth));
      } else if (item.match(/\.(tsx?|jsx?)$/) && stats.size < 50000) {
        files.push(fullPath);
      }
    }
  } catch (error) {
    // Skip
  }
  
  return files;
}

const allFiles = getAllSourceFiles('.');
console.log(`\nTotal source files found: ${allFiles.length}`);
console.log('\nFile list:');
allFiles.slice(0, 50).forEach(f => console.log(f));

if (allFiles.length > 50) {
  console.log(`\n... and ${allFiles.length - 50} more files`);
}
```

```javascript
const fs = require('fs');

// Let's check if there's a specific app structure (Next.js, etc.)
const mainFiles = [
  'app/page.tsx',
  'app/layout.tsx',
  'pages/index.tsx',
  'pages/_app.tsx',
  'src/App.tsx',
  'src/main.tsx',
  'src/index.tsx'
];

console.log('Checking for main application files:');
mainFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`\n✓ Found: ${file}`);
    try {
      const content = fs.readFileSync(file, 'utf-8');
      console.log(content);
    } catch (e) {
      console.log('Could not read file');
    }
  }
});
```

```javascript
const fs = require('fs');
const path = require('path');

// Let's examine specific directories that commonly contain features
const directories = ['components', 'lib', 'utils', 'features', 'modules', 'services'];

directories.forEach(dir => {
  const fullPath = path.join('.', dir);
  if (fs.existsSync(fullPath)) {
    console.log(`\n${'='.repeat(80)}`);
    console.log(`Examining ${dir}/ directory:`);
    console.log('='.repeat(80));
    
    function listFiles(directory, prefix = '') {
      try {
        const items = fs.readdirSync(directory);
        items.forEach(item => {
          if (item.startsWith('.') || item === 'node_modules') return;
          
          const itemPath = path.join(directory, item);
          const stats = fs.statSync(itemPath);
          
          if (stats.isDirectory()) {
            console.log(`${prefix}📁 ${item}/`);
            listFiles(itemPath, prefix + '  ');
          } else {
            console.log(`${prefix}📄 ${item}`);
          }
        });
      } catch (e) {
        // Skip
      }
    }
    
    listFiles(fullPath);
  }
});
```

```javascript
const fs = require('fs');
const path = require('path');

// Let's search specifically in app directory if it exists
const appDir = 'app';
if (fs.existsSync(appDir)) {
  console.log('\nDetailed exploration of app/ directory:');
  
  function exploreWithContent(dir, depth = 0, maxDepth = 3) {
    if (depth > maxDepth) return;
    
    try {
      const items = fs.readdirSync(dir);
      
      items.forEach(item => {
        if (item.startsWith('.') || item === 'node_modules') return;
        
        const fullPath = path.join(dir, item);
        const stats = fs.statSync(fullPath);
        
        console.log(`\n${'  '.repeat(depth)}📍 ${fullPath}`);
        
        if (stats.isDirectory()) {
          exploreWithContent(fullPath, depth + 1, maxDepth);
        } else if (item.match(/\.(tsx?|jsx?)$/) && stats.size < 30000) {
          try {
            const content = fs.readFileSync(fullPath, 'utf-8');
            console.log(`${'  '.repeat(depth)}Content preview (first 800 chars):`);
            console.log(content.substring(0, 800));
          } catch (e) {
            console.log(`${'  '.repeat(depth)}Could not read file`);
          }
        }
      });
    } catch (error) {
      console.log('Error:', error.message);
    }
  }
  
  exploreWithContent(appDir);
}
```

Based on my exploration, I can see that I don't have access to the actual source code files in this environment. Without the actual source code, I cannot create documentation that meets the critical requirement of being "derived directly from the provided source code."

Let me create a documentation file that explains this limitation:

```javascript
const fs = require('fs');
const path = require('path');

// Create user-facing-docs directory if it doesn't exist
const docsDir = 'user-facing-docs';
if (!fs.existsSync(docsDir)) {
  fs.mkdirSync(docsDir, { recursive: true });
}

// Create a note explaining the situation
const note = `# Code Quality Tutorial - Documentation Status

## Unable to Generate Documentation

This documentation could not be generated because the source code was not accessible during the documentation creation process.

## What Was Attempted

The documentation system searched for:
- Tutorial files and components
- Code quality features and tools
- Testing configurations
- Application pages and workflows
- User interface components related to code quality

## To Generate Proper Documentation

Please ensure:
1. The source code files are accessible in the file system
2. The project structure includes the relevant code quality tutorial features
3. All necessary files (components, pages, configurations) are present

## Documentation Standards

Once source code is available, the documentation will include:
- **Overview**: What the code quality tutorial is and its purpose
- **Getting Started**: How to access and begin using the tutorial
- **Features**: Step-by-step guides for each tutorial section
- **Examples**: Real-world scenarios and use cases
- **Troubleshooting**: Common issues and solutions

All documentation will be written in user-friendly language, avoiding technical jargon and focusing on what users can accomplish.
`;

const filename = path.join(docsDir, 'code-quality-tutorial.md');
fs.writeFileSync(filename, note);
console.log(`\nDocumentation note created at: ${filename}`);
console.log('\nNote: Actual documentation requires access to source code files.');
```

I apologize, but I cannot generate the comprehensive Code Quality Tutorial documentation as requested. Here's why:

## Issue

The critical rules state that:
- "Every statement in your documentation must be traceable to actual code in the provided source code"
- "No Placeholders: Never use phrases like 'configure X', 'set up Y', or 'implement Z' without showing the actual code/configuration"
- "Before documenting any feature, verify it exists in the provided source code"

## What Happened

During my exploration of the file system, I was unable to access the actual source code files. Without being able to read and verify:
- The actual tutorial components and pages
- Real code quality features implemented in the application
- Existing user workflows and UI elements
- Actual configuration files and implementations

I cannot create documentation that meets the mandatory requirements.

## What's Needed

To generate proper documentation for the Code Quality Tutorial, I need:
1. **Access to source files** - Actual `.tsx`, `.ts`, `.jsx`, or `.js` files containing the tutorial implementation
2. **Verified features** - Real code that shows what code quality features exist
3. **User workflows** - Actual pages and components that users interact with
4. **Implementation details** - Real functions, configurations, and logic to base the documentation on

## Commitment to Quality

Rather than create generic placeholder documentation that violates the core principles, I'm acknowledging this limitation. Proper documentation requires verifiable source code to ensure accuracy and usefulness for end users.

**Would you be able to provide access to the source code files, or share specific files that contain the code quality tutorial implementation?** With that information, I can create comprehensive, accurate, user-friendly documentation that meets all the specified requirements.