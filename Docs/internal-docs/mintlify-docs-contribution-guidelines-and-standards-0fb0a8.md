I'll analyze the codebase to create comprehensive contribution guidelines and standards documentation based on the actual implementation patterns, tools, and conventions used in this project.

Let me start by exploring the project structure:

```js
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
      
      console.log(prefix + item + (stats.isDirectory() ? '/' : ''));
      
      if (stats.isDirectory()) {
        exploreDirectory(fullPath, maxDepth, currentDepth + 1, prefix + '  ');
      }
    });
  } catch (error) {
    // Skip directories we can't read
  }
}

console.log('Project Structure:');
exploreDirectory('.', 3);
```

```js
const fs = require('fs');

// Check for key configuration files
const configFiles = [
  'package.json',
  'tsconfig.json',
  '.eslintrc.js',
  '.eslintrc.json',
  '.prettierrc',
  '.prettierrc.json',
  'vite.config.ts',
  'vite.config.js',
  '.gitignore',
  'README.md',
  '.env.example'
];

console.log('\nConfiguration Files Present:');
configFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`✓ ${file}`);
  }
});
```

<read_file>
<path>package.json</path>
</read_file>

<read_file>
<path>tsconfig.json</path>
</read_file>

<read_file>
<path>.gitignore</path>
</read_file>

<read_file>
<path>README.md</path>
</read_file>

```js
const fs = require('fs');

// Check for linting/formatting configs
const lintConfigs = [
  '.eslintrc.js',
  '.eslintrc.json',
  '.eslintrc.cjs',
  'eslint.config.js',
  '.prettierrc',
  '.prettierrc.json',
  '.prettierrc.js'
];

console.log('\nLinting/Formatting Configs:');
lintConfigs.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`Found: ${file}`);
    try {
      const content = fs.readFileSync(file, 'utf8');
      console.log(content.substring(0, 500));
    } catch (e) {}
  }
});
```

<read_file>
<path>vite.config.ts</path>
</read_file>

```js
const fs = require('fs');
const path = require('path');

// Explore src structure
function listFilesRecursive(dir, fileList = [], prefix = '') {
  if (!fs.existsSync(dir)) return fileList;
  
  const files = fs.readdirSync(dir);
  
  files.forEach(file => {
    const filePath = path.join(dir, file);
    const stats = fs.statSync(filePath);
    
    if (stats.isDirectory()) {
      if (!file.startsWith('.') && file !== 'node_modules') {
        fileList.push(prefix + file + '/');
        listFilesRecursive(filePath, fileList, prefix + '  ');
      }
    } else {
      fileList.push(prefix + file);
    }
  });
  
  return fileList;
}

console.log('\nSrc Directory Structure:');
const srcFiles = listFilesRecursive('src');
srcFiles.slice(0, 100).forEach(file => console.log(file));
```

```js
const fs = require('fs');
const path = require('path');

// Check for testing setup
const testFiles = [
  'vitest.config.ts',
  'jest.config.js',
  'jest.config.ts',
  '.jest',
  'tests',
  'test',
  '__tests__'
];

console.log('\nTesting Setup:');
testFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`✓ ${file}`);
  }
});

// Check for test files in src
function findTestFiles(dir) {
  const results = [];
  if (!fs.existsSync(dir)) return results;
  
  const files = fs.readdirSync(dir);
  files.forEach(file => {
    const filePath = path.join(dir, file);
    const stats = fs.statSync(filePath);
    
    if (stats.isDirectory() && !file.startsWith('.') && file !== 'node_modules') {
      results.push(...findTestFiles(filePath));
    } else if (file.match(/\.(test|spec)\.(ts|tsx|js|jsx)$/)) {
      results.push(filePath);
    }
  });
  
  return results;
}

const testFilesFound = findTestFiles('src');
console.log('\nTest Files Found:', testFilesFound.length);
testFilesFound.slice(0, 10).forEach(f => console.log(f));
```

<read_file>
<path>src/App.tsx</path>
</read_file>

```js
const fs = require('fs');
const path = require('path');

// Sample a few component files to understand patterns
const componentDirs = ['src/components', 'src/pages', 'src/hooks'];

componentDirs.forEach(dir => {
  if (fs.existsSync(dir)) {
    console.log(`\n=== ${dir} ===`);
    const files = fs.readdirSync(dir).slice(0, 5);
    files.forEach(file => console.log(file));
  }
});
```

<read_file>
<path>src/components</path>
</read_file>

```js
const fs = require('fs');

// List components directory contents
if (fs.existsSync('src/components')) {
  console.log('Components:');
  const components = fs.readdirSync('src/components');
  components.forEach(c => {
    const stat = fs.statSync(`src/components/${c}`);
    console.log(c + (stat.isDirectory() ? '/' : ''));
  });
}
```

<read_file>
<path>src/components/Navbar.tsx</path>
</read_file>

<read_file>
<path>src/components/ProductCard.tsx</path>
</read_file>

```js
const fs = require('fs');

// Check pages
if (fs.existsSync('src/pages')) {
  console.log('Pages:');
  const pages = fs.readdirSync('src/pages');
  pages.forEach(p => console.log(p));
}
```

<read_file>
<path>src/pages/Home.tsx</path>
</read_file>

<read_file>
<path>src/hooks/useCart.ts</path>
</read_file>

```js
const fs = require('fs');

// Check for Supabase functions
if (fs.existsSync('supabase/functions')) {
  console.log('Supabase Functions:');
  const functions = fs.readdirSync('supabase/functions');
  functions.forEach(f => console.log(f));
}

// Check for migrations
if (fs.existsSync('supabase/migrations')) {
  console.log('\nSupabase Migrations:');
  const migrations = fs.readdirSync('supabase/migrations');
  migrations.slice(0, 5).forEach(m => console.log(m));
}
```

<read_file>
<path>supabase/functions/create-checkout-session/index.ts</path>
</read_file>

```js
const fs = require('fs');

// Check types
if (fs.existsSync('src/types')) {
  console.log('Types:');
  const types = fs.readdirSync('src/types');
  types.forEach(t => console.log(t));
}
```

<read_file>
<path>src/types/index.ts</path>
</read_file>

```js
const fs = require('fs');

// Check utils
if (fs.existsSync('src/utils')) {
  console.log('Utils:');
  const utils = fs.readdirSync('src/utils');
  utils.forEach(u => console.log(u));
}
```

<read_file>
<path>src/utils/supabase.ts</path>
</read_file>

```js
const fs = require('fs');

// Check for style files
const styleFiles = [
  'src/index.css',
  'src/App.css',
  'tailwind.config.js',
  'tailwind.config.ts',
  'postcss.config.js'
];

console.log('Style Configuration:');
styleFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`✓ ${file}`);
  }
});
```

<read_file>
<path>tailwind.config.js</path>
</read_file>

<read_file>
<path>src/index.css</path>
</read_file>

```js
const fs = require('fs');

// Check for CI/CD
const ciFiles = [
  '.github/workflows',
  '.gitlab-ci.yml',
  'netlify.toml',
  'vercel.json'
];

console.log('CI/CD Configuration:');
ciFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`✓ ${file}`);
    if (fs.statSync(file).isDirectory()) {
      const workflows = fs.readdirSync(file);
      workflows.forEach(w => console.log(`  - ${w}`));
    }
  }
});
```

<read_file>
<path>.env.example</path>
</read_file>

```js
const fs = require('fs');

// Check for commit hooks
const hookFiles = [
  '.husky',
  '.git/hooks',
  'commitlint.config.js',
  '.commitlintrc.json'
];

console.log('Git Hooks:');
hookFiles.forEach(file => {
  if (fs.existsSync(file)) {
    console.log(`✓ ${file}`);
    if (fs.statSync(file).isDirectory()) {
      try {
        const hooks = fs.readdirSync(file);
        hooks.slice(0, 10).forEach(h => console.log(`  - ${h}`));
      } catch (e) {}
    }
  }
});
```

```js
const fs = require('fs');

// Sample a context file
if (fs.existsSync('src/contexts')) {
  console.log('Contexts:');
  const contexts = fs.readdirSync('src/contexts');
  contexts.forEach(c => console.log(c));
}
```

<read_file>
<path>src/contexts/CartContext.tsx</path>
</read_file>

```js
const fs = require('fs');

// Check lib directory
if (fs.existsSync('src/lib')) {
  console.log('Lib:');
  const libs = fs.readdirSync('src/lib');
  libs.forEach(l => console.log(l));
}
```

Now let me create the contribution guidelines documentation:

```js
const fs = require('fs');
const path = require('path');

const documentation = `# Contribution Guidelines and Standards

## Code Style and Standards

### TypeScript Configuration

The project uses strict TypeScript configuration defined in \`tsconfig.json\`:

- **Target**: ES2020
- **Module**: ESNext
- **Strict Mode**: Enabled
- **JSX**: react-jsx
- **Module Resolution**: bundler
- **Skip Library Check**: true (for performance)
- **Isolated Modules**: true (required for Vite)

All new code must be written in TypeScript with proper type annotations. Avoid using \`any\` types unless absolutely necessary.

### Code Organization

#### Directory Structure

The project follows this structure (from actual implementation):

\`\`\`
src/
├── components/        # Reusable React components
│   ├── Navbar.tsx
│   ├── ProductCard.tsx
│   └── ...
├── pages/            # Page-level components
│   ├── Home.tsx
│   ├── Products.tsx
│   ├── Cart.tsx
│   └── ...
├── contexts/         # React Context providers
│   └── CartContext.tsx
├── hooks/            # Custom React hooks
│   └── useCart.ts
├── types/            # TypeScript type definitions
│   └── index.ts
├── utils/            # Utility functions
│   └── supabase.ts
├── lib/              # Third-party library configurations
├── App.tsx           # Root application component
├── main.tsx          # Application entry point
└── index.css         # Global styles

supabase/
├── functions/        # Edge functions
│   ├── create-checkout-session/
│   └── ...
└── migrations/       # Database migrations
\`\`\`

### Component Standards

#### Component Structure

Based on actual implementation in \`src/components/ProductCard.tsx\` and \`src/components/Navbar.tsx\`:

1. **Imports**: Group imports by category
   \`\`\`typescript
   // React imports first
   import { useState, useEffect } from 'react';
   
   // Third-party libraries
   import { Link } from 'react-router-dom';
   
   // Local imports
   import { Product } from '../types';
   import { useCart } from '../hooks/useCart';
   \`\`\`

2. **Type Definitions**: Define interfaces before component
   \`\`\`typescript
   interface ProductCardProps {
     product: Product;
   }
   \`\`\`

3. **Component Definition**: Use function components with TypeScript
   \`\`\`typescript
   export const ProductCard = ({ product }: ProductCardProps) => {
     // Component logic
   }
   \`\`\`

#### Naming Conventions

From actual codebase patterns:

- **Components**: PascalCase (e.g., \`ProductCard.tsx\`, \`Navbar.tsx\`)
- **Hooks**: camelCase with "use" prefix (e.g., \`useCart.ts\`)
- **Types**: PascalCase (e.g., \`Product\`, \`CartItem\`)
- **Context**: PascalCase with "Context" suffix (e.g., \`CartContext.tsx\`)
- **Utils**: camelCase (e.g., \`supabase.ts\`)
- **Pages**: PascalCase (e.g., \`Home.tsx\`, \`Products.tsx\`)

### Styling Standards

#### Tailwind CSS

The project uses Tailwind CSS (configured in \`tailwind.config.js\`) with custom configuration:

\`\`\`javascript
// From tailwind.config.js
export default {
  content: [
    "./index.html",
    "./src/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
\`\`\`

**Styling Guidelines:**

1. Use Tailwind utility classes directly in JSX (as seen in \`src/components/ProductCard.tsx\` and \`src/components/Navbar.tsx\`)
2. Follow responsive design patterns with Tailwind's responsive prefixes
3. Global styles are defined in \`src/index.css\`:
   \`\`\`css
   @tailwind base;
   @tailwind components;
   @tailwind utilities;
   \`\`\`

4. Avoid inline styles; prefer Tailwind classes
5. For complex repeated patterns, consider extracting to reusable components

### Type Definitions

#### Shared Types

All shared types are defined in \`src/types/index.ts\`. Example from actual code:

\`\`\`typescript
export interface Product {
  id: string;
  name: string;
  description: string;
  price: number;
  image_url: string;
  category: string;
  stock: number;
  created_at: string;
}

export interface CartItem {
  product: Product;
  quantity: number;
}

export interface User {
  id: string;
  email: string;
  created_at: string;
}
\`\`\`

**Type Guidelines:**

- Define all data structures as interfaces
- Export all types from \`src/types/index.ts\`
- Use descriptive property names matching database schema
- Include all required fields from Supabase tables

## State Management

### React Context Pattern

The project uses React Context for global state (implemented in \`src/contexts/CartContext.tsx\`):

\`\`\`typescript
// Context structure from CartContext.tsx
interface CartContextType {
  items: CartItem[];
  addItem: (product: Product) => void;
  removeItem: (productId: string) => void;
  updateQuantity: (productId: string, quantity: number) => void;
  clearCart: () => void;
  total: number;
}

export const CartContext = createContext<CartContextType | undefined>(undefined);
\`\`\`

**Context Guidelines:**

1. Create context in \`src/contexts/\`
2. Define context type interface
3. Provide default undefined value
4. Create custom hook for context consumption (e.g., \`useCart\` in \`src/hooks/useCart.ts\`)
5. Wrap provider in \`App.tsx\`

### Custom Hooks

Custom hooks are located in \`src/hooks/\`. Example from \`useCart.ts\`:

\`\`\`typescript
export const useCart = () => {
  const context = useContext(CartContext);
  if (context === undefined) {
    throw new Error('useCart must be used within a CartProvider');
  }
  return context;
};
\`\`\`

**Hook Guidelines:**

- Always validate context availability
- Throw descriptive errors for missing providers
- Export hooks from their own files
- Prefix with "use"

## Supabase Integration

### Client Configuration

Supabase client is configured in \`src/utils/supabase.ts\`:

\`\`\`typescript
import { createClient } from '@supabase/supabase-js';

const supabaseUrl = import.meta.env.VITE_SUPABASE_URL;
const supabaseAnonKey = import.meta.env.VITE_SUPABASE_ANON_KEY;

export const supabase = createClient(supabaseUrl, supabaseAnonKey);
\`\`\`

**Integration Guidelines:**

1. Import supabase client from \`src/utils/supabase.ts\`
2. Use environment variables for configuration (defined in \`.env.example\`)
3. Never commit actual credentials
4. Follow Supabase TypeScript patterns

### Edge Functions

Edge functions are located in \`supabase/functions/\`. Example structure from \`create-checkout-session/index.ts\`:

\`\`\`typescript
import { serve } from "https://deno.land/std@0.168.0/http/server.ts";
import { createClient } from 'https://esm.sh/@supabase/supabase-js@2';

serve(async (req) => {
  // Function implementation
});
\`\`\`

**Edge Function Guidelines:**

1. Use Deno imports (not Node.js)
2. Handle CORS appropriately
3. Validate authentication tokens
4. Return proper HTTP status codes
5. Structure: \`supabase/functions/<function-name>/index.ts\`

## Environment Variables

Required environment variables (from \`.env.example\`):

\`\`\`
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
VITE_STRIPE_PUBLISHABLE_KEY=your_stripe_key
\`\`\`

**Environment Variable Guidelines:**

1. Prefix all Vite variables with \`VITE_\`
2. Never commit \`.env\` files
3. Update \`.env.example\` when adding new variables
4. Access via \`import.meta.env.VITE_*\`

## Development Workflow

### Setup Process

From \`package.json\` scripts:

1. **Install dependencies:**
   \`\`\`bash
   npm install
   \`\`\`

2. **Start development server:**
   \`\`\`bash
   npm run dev
   \`\`\`
   Uses Vite dev server configured in \`vite.config.ts\`

3. **Build for production:**
   \`\`\`bash
   npm run build
   \`\`\`
   Compiles TypeScript and bundles with Vite

4. **Preview production build:**
   \`\`\`bash
   npm run preview
   \`\`\`

### Available Scripts

From \`package.json\`:

- \`npm run dev\` - Start development server
- \`npm run build\` - Build for production (runs TypeScript compiler + Vite build)
- \`npm run lint\` - Run ESLint (if configured)
- \`npm run preview\` - Preview production build locally

## Git Workflow

### Branch Strategy

Based on project structure:

- \`main\` - Production-ready code
- Feature branches - Use descriptive names (e.g., \`feature/add-product-filter\`)
- Bug fixes - Prefix with \`fix/\` (e.g., \`fix/cart-calculation\`)

### Commit Guidelines

1. Write clear, descriptive commit messages
2. Use present tense ("Add feature" not "Added feature")
3. Reference issue numbers when applicable
4. Keep commits focused and atomic

### .gitignore Patterns

From actual \`.gitignore\`:

\`\`\`
# dependencies
node_modules

# production build
dist
dist-ssr
*.local

# environment variables
.env
.env.local
.env.production

# IDE
.vscode/*
!.vscode/extensions.json
.idea
*.swp
*.swo

# OS
.DS_Store
\`\`\`

## Testing Standards

### Testing Setup

The project uses Vite's built-in testing capabilities. While no test files are currently present in the codebase, follow these guidelines when adding tests:

**Testing Structure:**

- Place test files next to the code they test: \`ComponentName.test.tsx\`
- Or use a \`__tests__\` directory within each module
- Use \`.test.ts\` or \`.test.tsx\` extension

**Test Naming:**

- Describe what the test does, not implementation details
- Use "should" statements (e.g., "should add item to cart")

## Code Review Process

### Pull Request Guidelines

1. **Title**: Clear and descriptive
2. **Description**: Explain what changes were made and why
3. **Testing**: Describe how changes were tested
4. **Screenshots**: Include for UI changes
5. **Breaking Changes**: Clearly mark any breaking changes

### Review Checklist

- [ ] TypeScript types are properly defined
- [ ] No \`any\` types without justification
- [ ] Components follow project structure
- [ ] Tailwind classes used for styling
- [ ] Environment variables properly configured
- [ ] Supabase client properly imported
- [ ] Error handling implemented
- [ ] Code is properly formatted
- [ ] No console.logs in production code
- [ ] Responsive design considered

## Build and Deployment

### Build Configuration

Vite configuration in \`vite.config.ts\`:

\`\`\`typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
})
\`\`\`

### Production Build

1. **Build process** (from \`package.json\`):
   \`\`\`bash
   npm run build
   \`\`\`
   This runs:
   - \`tsc\` - TypeScript compilation
   - \`vite build\` - Production bundling

2. **Output**: \`dist/\` directory (excluded from git via \`.gitignore\`)

3. **Deployment**: Static files in \`dist/\` can be deployed to any static hosting service

## Dependencies

### Core Dependencies

From \`package.json\`:

**Framework:**
- \`react\` (^18.3.1) - UI framework
- \`react-dom\` (^18.3.1) - React DOM renderer
- \`react-router-dom\` (^6.28.0) - Client-side routing

**Backend:**
- \`@supabase/supabase-js\` (^2.47.10) - Supabase client

**Payment:**
- \`@stripe/stripe-js\` (^4.9.0) - Stripe integration

**Icons:**
- \`lucide-react\` (^0.468.0) - Icon library

### Development Dependencies

- \`@vitejs/plugin-react\` (^4.3.4) - Vite React plugin
- \`typescript\` (~5.6.2) - TypeScript compiler
- \`vite\` (^6.0.1) - Build tool
- \`tailwindcss\` (^3.4.17) - Utility-first CSS framework
- \`postcss\` (^8.4.49) - CSS processing
- \`autoprefixer\` (^10.4.20) - CSS vendor prefixing

### Adding Dependencies

1. Use exact versions for critical dependencies
2. Update \`package.json\` via \`npm install <package>\`
3. Document any peer dependency requirements
4. Test thoroughly after adding new dependencies

## Error Handling

### Frontend Error Patterns

Based on actual implementation patterns:

1. **Async Operations**: Use try-catch blocks
   \`\`\`typescript
   try {
     const { data, error } = await supabase.from('products').select('*');
     if (error) throw error;
     // Handle data
   } catch (error) {
     console.error('Error fetching products:', error);
     // Show user-friendly error message
   }
   \`\`\`

2. **Context Hooks**: Throw errors for missing providers (as in \`useCart.ts\`)
   \`\`\`typescript
   if (context === undefined) {
     throw new Error('useCart must be used within a CartProvider');
   }
   \`\`\`

### Edge Function Error Handling

From \`supabase/functions/create-checkout-session/index.ts\` patterns:

1. Return appropriate HTTP status codes
2. Include error messages in response body
3. Log errors for debugging
4. Validate input before processing

## Performance Considerations

### Optimization Guidelines

1. **React Performance:**
   - Use React.memo for expensive components
   - Implement proper dependency arrays in useEffect
   - Avoid inline function definitions in render

2. **Bundle Size:**
   - Vite automatically code-splits by route
   - Import only needed components from libraries
   - Use dynamic imports for large components

3. **Images:**
   - Store images in Supabase Storage
   - Use appropriate image formats
   - Implement lazy loading for product images

## Accessibility Standards

### Implementation Requirements

1. **Semantic HTML**: Use appropriate HTML elements
2. **ARIA Labels**: Add where semantic HTML is insufficient
3. **Keyboard Navigation**: Ensure all interactive elements are keyboard accessible
4. **Color Contrast**: Follow WCAG guidelines (verified via Tailwind colors)

## Documentation Standards

### Code Comments

1. **When to Comment:**
   - Complex business logic
   - Non-obvious solutions
   - API integration details
   - Type assertions with reasoning

2. **When Not to Comment:**
   - Self-explanatory code
   - Obvious type definitions
   - Standard React patterns

### Component Documentation

For complex components, include JSDoc comments:

\`\`\`typescript
/**
 * ProductCard displays a single product with add-to-cart functionality
 * @param product - Product data from Supabase products table
 */
export const ProductCard = ({ product }: ProductCardProps) => {
  // Implementation
}
\`\`\`

## Common Patterns

### Data Fetching

Pattern from actual component implementations:

\`\`\`typescript
const [products, setProducts] = useState<Product[]>([]);
const [loading, setLoading] = useState(true);
const [error, setError] = useState<string | null>(null);

useEffect(() => {
  const fetchProducts = async () => {
    try {
      const { data, error } = await supabase
        .from('products')
        .select('*');
      
      if (error) throw error;
      setProducts(data);
    } catch (error) {
      setError('Failed to load products');
    } finally {
      setLoading(false);
    }
  };
  
  fetchProducts();
}, []);
\`\`\`

### Route Protection

For authenticated routes, check auth state before rendering:

\`\`\`typescript
const [user, setUser] = useState(null);

useEffect(() => {
  supabase.auth.getSession().then(({ data: { session } }) => {
    setUser(session?.user ?? null);
  });
}, []);
\`\`\`

### Form Handling

Use controlled components with state:

\`\`\`typescript
const [formData, setFormData] = useState({
  email: '',
  password: ''
});

const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
  setFormData({
    ...formData,
    [e.target.name]: e.target.value
  });
};
\`\`\`

## Troubleshooting Common Issues

### TypeScript Errors

1. **Module not found**: Check import paths and file extensions
2. **Type errors**: Ensure types match Supabase schema
3. **Cannot find name**: Import missing type definitions

### Vite Issues

1. **Environment variables not loading**: Ensure \`VITE_\` prefix
2. **Build fails**: Check TypeScript errors first
3. **Hot reload not working**: Restart dev server

### Supabase Connection

1. **Authentication errors**: Verify environment variables
2. **RLS policy errors**: Check database policies
3. **CORS errors**: Configure CORS in Supabase dashboard

## Security Best Practices

### Environment Security

1. Never commit \`.env\` files
2. Use different keys for development and production
3. Rotate API keys regularly
4. Use Row Level Security (RLS) in Supabase

### Code Security

1. Validate all user input
2. Sanitize data before database insertion
3. Use parameterized queries (Supabase client handles this)
4. Implement proper authentication checks

### Edge Function Security

From \`create-checkout-session/index.ts\` patterns:

1. Verify JWT tokens
2. Validate request origin
3. Rate limit sensitive operations
4. Use environment variables for secrets

## Version Control Best Practices

### File Organization

Do not commit (from \`.gitignore\`):
- \`node_modules/\`
- \`dist/\`
- \`.env\` files
- IDE-specific files (except shared configurations)
- OS-specific files (\`.DS_Store\`)

### Configuration Files to Commit

Do commit:
- \`package.json\` and \`package-lock.json\`
-