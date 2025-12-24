I'll analyze the source code to create comprehensive user-facing documentation. Let me start by exploring the project structure.

<function_calls>
<invoke name="execute_bash">
<parameter name="command">find . -type f -name "*.json" -o -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | grep -E "(package\.json|tsconfig|README)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">pwd && ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">find . -maxdepth 3 -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" -o -name "*.json" \) | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">ls -R | head -50</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">find . -type f | head -40</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">cat package.json 2>/dev/null || echo "No package.json found"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">find . -name "*.md" -o -name "README*" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">tree -L 2 -I 'node_modules' 2>/dev/null || find . -maxdepth 2 -type d | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">cat README.md 2>/dev/null || cat readme.md 2>/dev/null || echo "No README found"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">ls -la / 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">echo "Current directory: $(pwd)" && echo "Files:" && ls -la 2>/dev/null</parameter>
</invoke>
</function_calls>

I notice that there's no source code provided in the current context. According to the critical rules, I cannot create documentation without actual source code to analyze. Let me check if there are any additional files or context available.

<function_calls>
<invoke name="execute_bash">
<parameter name="command">env | grep -i "project\|source\|code" || echo "No environment variables found"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_bash">
<parameter name="command">find /tmp -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" 2>/dev/null | head -10</parameter>
</invoke>
</function_calls>

Based on my analysis, I cannot find any source code in the provided context. According to the **CRITICAL RULES** stated in the instructions:

1. **Code-First Approach**: Every statement in documentation must be traceable to actual code
2. **No Placeholders**: Never use phrases without showing actual code/configuration
3. **Verification Required**: Before documenting any feature, verify it exists in the provided source code

**I cannot create documentation without source code.**

To proceed, I need:

1. **Source code files** - The actual application code (TypeScript, JavaScript, React components, etc.)
2. **Project structure** - Files like package.json, configuration files, or routing definitions
3. **Any existing documentation** - README files or other docs that might exist

**What I should receive:**
- Application source files (`.ts`, `.tsx`, `.js`, `.jsx`)
- Configuration files (`package.json`, `tsconfig.json`, etc.)
- Database schemas or models
- API endpoints or edge functions
- UI components and pages

**Please provide the source code so I can create accurate, implementation-based documentation that follows all the critical rules.**

Without source code, creating documentation would violate the fundamental principle: **"Every statement in your documentation must be traceable to actual code in the provided source"** and would result in placeholder content, which is explicitly forbidden.