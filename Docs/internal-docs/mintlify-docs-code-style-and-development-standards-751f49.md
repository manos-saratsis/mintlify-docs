I'll analyze the codebase to document the actual code style and development standards used in this project.

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find /tmp -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" -o -name "*.json" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="output">
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 12
drwxr-xr-x 1 sandbox sandbox   34 Jan  9 03:19 .
drwxr-xr-x 1 sandbox sandbox   20 Jan  9 03:19 ..
-rw-r--r-- 1 sandbox sandbox 8526 Jan  9 03:19 instructions.md
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">pwd</parameter>
</invoke>
</function_calls>
<parameter name="output">
/home/sandbox</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" \) 2>/dev/null | head -30</parameter>
</invoke>
</function_calls>
<parameter name="output">
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -name "package.json" -o -name "tsconfig.json" -o -name ".eslintrc*" -o -name ".prettierrc*" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="output">
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la /</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 24
drwxr-xr-x 1 sandbox sandbox   60 Jan  9 03:19 .
drwxr-xr-x 1 sandbox sandbox   60 Jan  9 03:19 ..
drwxr-xr-x 1 sandbox sandbox 4096 Jan  6 18:12 bin
drwxr-xr-x 1 sandbox sandbox   38 Jan  9 03:19 etc
drwxr-xr-x 1 sandbox sandbox   26 Jan  9 03:19 home
drwxr-xr-x 1 sandbox sandbox   92 Jan  6 18:12 lib
drwxr-xr-x 1 sandbox sandbox   34 Jan  6 18:12 lib64
drwxr-xr-x 1 sandbox sandbox   40 Jan  9 03:19 tmp
drwxr-xr-x 1 sandbox sandbox   28 Jan  6 18:12 usr
</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la /tmp</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 0
drwxr-xr-x 1 sandbox sandbox 40 Jan  9 03:19 .
drwxr-xr-x 1 sandbox sandbox 60 Jan  9 03:19 ..
drwxr-xr-x 2 sandbox sandbox 60 Jan  9 03:19 inputs
drwxr-xr-x 2 sandbox sandbox 40 Jan  9 03:19 outputs</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la /tmp/inputs</parameter>
</invoke>
</function_calls>
<parameter name="output">
total 0
drwxr-xr-x 2 sandbox sandbox 60 Jan  9 03:19 .
drwxr-xr-x 1 sandbox sandbox 40 Jan  9 03:19 ..
-rw-r--r-- 1 sandbox sandbox  0 Jan  9 03:19 .placeholder</parameter>

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">cat /home/sandbox/instructions.md</parameter>
</invoke>
</function_calls>
<parameter name="output">
You are an expert documentation specialist tasked with creating accurate, implementation-based documentation for software projects. Your documentation MUST be derived directly from the provided source code - no invented features, no generic examples, no placeholder content.

**CRITICAL RULES (Non-Negotiable):**

1. **Code-First Approach**: Every statement in your documentation must be traceable to actual code in the provided source
2. **No Placeholders**: Never use phrases like "configure X", "set up Y", or "implement Z" without showing the actual code/configuration
3. **Mandatory References**: Always cite specific file paths, component names, function signatures, and line numbers when relevant
4. **Verification Required**: Before documenting any feature, verify it exists in the provided source code
5. **Scope Efficiency**: If additional instructions limit the scope (e.g., "only document authentication"), analyze ONLY relevant files - skip unrelated code
6. **Task Explanation**: Only include task explanation comments at the top of documentation files if explicitly instructed to do so
7. **Audience Awareness**: For user-facing docs, write for non-technical users; for developer docs, include technical details

You will be given access to the project's file system.

You have the following tools available:

1.  You can execute javascript code in a node.js environment.
2.  You can read files from the file system.
3.  You can execute shell commands.

When documenting, adhere to the following structure:

**Overview**:
    - High-level summary of the documented feature or component.
    - Explain its purpose and role within the overall system.

**Implementation**:
    - Step-by-step guide on how the feature is implemented.
    - Reference specific code snippets, file paths, and function calls.
    - Explain the logic behind the implementation choices.

**Usage**:
    - Instructions on how to use the documented feature or component.
    - Provide code examples and configuration details.
    - Explain any relevant parameters, inputs, or outputs.

**Example**

Here is an example of documenting a function:

**Overview**:
The `handleSignIn` function is responsible for authenticating users and initiating the sign-in process. It validates user credentials and generates authentication tokens.

**Implementation**:
The function is located in `src/auth/auth.ts` (line 42). It takes the user's email and password as input. The function first checks if the user exists in the database by calling `findUserByEmail(email)`. If the user exists, it compares the provided password with the stored password hash using `comparePasswords(password, storedHash)`. If the passwords match, the function generates an authentication token using `generateAuthToken(userId)`.

**Usage**:
To use the `handleSignIn` function, import it from `src/auth/auth.ts` and call it with the user's email and password:

```typescript
import { handleSignIn } from 'src/auth/auth.ts';

async function signIn(email, password) {
  const token = await handleSignIn(email, password);
  console.log('Authentication token:', token);
}
```

**Quality Checklist (Validate Before Output):**

Before submitting documentation, verify:
- [ ] Every feature mentioned exists in the provided code
- [ ] All file paths are correct and verifiable
- [ ] All code examples are extracted from actual source files
- [ ] All API endpoints are documented from real edge functions
- [ ] All database operations reference actual tables and columns
- [ ] All UI instructions reference real pages and components
- [ ] No generic placeholders or invented examples remain



**Developer Documentation:**

**File Organization:**
- Internal developer documentation files are placed in an "internal-docs" subfolder
- Files are prefixed with the repository name (e.g., "my-repo-architecture.md")
- This helps developers identify which repository each documentation file belongs to

- **API Documentation**:
  * Document all edge functions in `supabase/functions/`
  * Include actual request/response examples from TypeScript interfaces
  * Show real authentication requirements (JWT, API keys, etc.)
  * Document rate limits and error responses actually implemented
  * Reference actual environment variables needed

- **Architecture**:
  * Map the actual folder structure and its purpose
  * Document real component hierarchy and relationships
  * Show actual state management patterns (contexts, hooks)
  * Explain real routing structure from router configuration
  * Document actual authentication flow and protected routes

- **Development Guides**:
  * Show actual setup steps from package.json scripts
  * Document real environment variables needed (from .env.example or code references)
  * Explain actual build process and deployment steps
  * Include real database migration workflow
  * Reference actual testing setup if it exists

- **Internal APIs**:
  * **Edge Functions**:
    - List all functions in `supabase/functions/` with their purpose
    - Show actual function signatures and types
    - Document real error handling patterns
    - Include actual CORS configuration
    - Note real Supabase client usage patterns
  
  * **Database Schema**:
    - Document actual tables from migration files
    - Show real relationships and foreign keys
    - Include actual RLS policies
    - Document real triggers and functions
    - Show actual indexes and constraints
  
  * **Type Definitions**:
    - Reference actual TypeScript interfaces used
    - Show real Supabase generated types location
    - Document custom type definitions
  
  * **Hooks**:
    - List all custom hooks in `src/hooks/`
    - Show actual hook signatures and return types
    - Document real dependencies and side effects
  
  * **Contexts**:
    - Document all context providers
    - Show actual context values and methods
    - Explain real usage patterns
  
  * **Services**:
    - List all service modules
    - Show actual API methods and their implementations
    - Document real error handling
  
  * **Utilities**:
    - Document utility functions and their purposes
    - Show actual usage examples from the codebase

- **Component Documentation**:
  * List major components with their file paths
  * Show actual prop types and interfaces
  * Document real usage examples from other components
  * Include actual styling approach (Tailwind classes, CSS modules, etc.)
  * Note actual dependencies and imports

- **Code Navigation Guide**:
  * Provide a map of where to find different types of code
  * Show actual patterns for common tasks
  * Reference actual examples of each pattern in the codebase
  * Include actual naming conventions used




**CRITICAL REQUIREMENT - NO TASK EXPLANATIONS**: 
- Do NOT add any task explanation, purpose statement, or "what this documentation covers" section at the top of the file
- Do NOT add any HTML comments like <!-- This documentation covers... --> at the beginning
- Do NOT add any introductory meta-commentary about the documentation itself
- Start DIRECTLY with the actual documentation content (title, introduction to the feature, etc.)
- The first lines should be the actual documentation, not a description of the documentation task

## Documentation Scope
You are generating: **Code Style and Development Standards** for internal_developer documentation.




## Source Code Context


## Additional Context


User Instructions: Create comprehensive documentation from product analysis.


## Task
Generate comprehensive documentation for "Code Style and Development Standards" based on the source code provided. Follow all instructions and examples carefully.
</parameter>

I notice that no source code has been provided in the `/tmp/inputs` directory. Without actual source code to analyze, I cannot create documentation that follows the critical rules, which require:

1. Every statement must be traceable to actual code
2. No invented features or placeholder content
3. Verification of all documented features in the provided source code

Let me create a documentation file that explains this situation:

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">cat > /tmp/outputs/code-style-and-development-standards.md << 'EOF'
# Code Style and Development Standards

## Documentation Status

**No source code provided for analysis.**

This documentation cannot be generated because no source code files were found in the provided inputs. To create accurate, implementation-based documentation for code style and development standards, the following files would need to be analyzed:

### Required Source Files

The following types of files are needed to document actual code style and development standards:

- **Configuration Files**: `.eslintrc.js`, `.eslintrc.json`, `.prettierrc`, `tsconfig.json`, `jsconfig.json`
- **Source Code Files**: `.ts`, `.tsx`, `.js`, `.jsx` files to analyze actual coding patterns
- **Package Configuration**: `package.json` to identify linting and formatting tools
- **Git Configuration**: `.gitignore`, `.editorconfig` to understand version control standards
- **CI/CD Configuration**: GitHub Actions, GitLab CI, or other pipeline configurations showing code quality checks

### What Would Be Documented

Once source code is provided, this documentation would cover:

1. **TypeScript/JavaScript Configuration**
   - Actual compiler options from `tsconfig.json`
   - Module resolution patterns
   - Type checking strictness levels

2. **Linting Rules**
   - ESLint configuration and enabled rules
   - Custom rule definitions
   - Disabled rules with justifications

3. **Code Formatting**
   - Prettier configuration (if used)
   - Indentation standards
   - Line length limits
   - Quote styles

4. **Naming Conventions**
   - Component naming patterns from actual files
   - Function naming conventions
   - Variable naming standards
   - File naming patterns

5. **Project Structure Patterns**
   - Directory organization
   - File organization within directories
   - Import patterns and path aliases

6. **Testing Standards**
   - Test file naming conventions
   - Testing library usage patterns
   - Test structure and organization

7. **Git Workflow**
   - Branch naming conventions
   - Commit message format
   - Pre-commit hooks

## Next Steps

To generate this documentation, please provide access to the project's source code repository.
EOF
cat /tmp/outputs/code-style-and-development-standards.md
</parameter>
</invoke>
</function_calls>
<parameter name="output">
# Code Style and Development Standards

## Documentation Status

**No source code provided for analysis.**

This documentation cannot be generated because no source code files were found in the provided inputs. To create accurate, implementation-based documentation for code style and development standards, the following files would need to be analyzed:

### Required Source Files

The following types of files are needed to document actual code style and development standards:

- **Configuration Files**: `.eslintrc.js`, `.eslintrc.json`, `.prettierrc`, `tsconfig.json`, `jsconfig.json`
- **Source Code Files**: `.ts`, `.tsx`, `.js`, `.jsx` files to analyze actual coding patterns
- **Package Configuration**: `package.json` to identify linting and formatting tools
- **Git Configuration**: `.gitignore`, `.editorconfig` to understand version control standards
- **CI/CD Configuration**: GitHub Actions, GitLab CI, or other pipeline configurations showing code quality checks

### What Would Be Documented

Once source code is provided, this documentation would cover:

1. **TypeScript/JavaScript Configuration**
   - Actual compiler options from `tsconfig.json`
   - Module resolution patterns
   - Type checking strictness levels

2. **Linting Rules**
   - ESLint configuration and enabled rules
   - Custom rule definitions
   - Disabled rules with justifications

3. **Code Formatting**
   - Prettier configuration (if used)
   - Indentation standards
   - Line length limits
   - Quote styles

4. **Naming Conventions**
   - Component naming patterns from actual files
   - Function naming conventions
   - Variable naming standards
   - File naming patterns

5. **Project Structure Patterns**
   - Directory organization
   - File organization within directories
   - Import patterns and path aliases

6. **Testing Standards**
   - Test file naming conventions
   - Testing library usage patterns
   - Test structure and organization

7. **Git Workflow**
   - Branch naming conventions
   - Commit message format
   - Pre-commit hooks

## Next Steps

To generate this documentation, please provide access to the project's source code repository.
</parameter>

The documentation file has been created at `/tmp/outputs/code-style-and-development-standards.md`. 

Unfortunately, I cannot generate comprehensive code style and development standards documentation because no source code was provided for analysis. According to the critical rules:

- **Rule 1 (Code-First Approach)**: Every statement must be traceable to actual code
- **Rule 2 (No Placeholders)**: No invented features or generic examples
- **Rule 4 (Verification Required)**: All features must be verified in the provided source code

Without access to configuration files (like `tsconfig.json`, `.eslintrc`, `.prettierrc`) or actual source code files, I cannot document the real code style and development standards used in the project.

To generate accurate documentation, please provide the project's source code files, particularly:
- Configuration files for TypeScript, ESLint, Prettier
- Sample source code files to analyze patterns
- Package.json to identify tooling
- Any style guide documents or CI/CD configurations