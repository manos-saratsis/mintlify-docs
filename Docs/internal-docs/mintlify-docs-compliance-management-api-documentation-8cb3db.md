I'll analyze the source code to create comprehensive documentation for the Compliance Management API. Let me start by exploring the project structure.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.json" | grep -E "(supabase|src)" | head -30</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type d -name "supabase" -o -name "src" | head -10</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">ls -R | head -100</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -name "*.ts" -o -name "*.tsx" -o -name "*.sql" | head -50</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">pwd && ls -la</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">.</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -maxdepth 3 -type f | head -50</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -R . 2>/dev/null | head -200</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.json" -o -name "*.sql" \) 2>/dev/null | head -100</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">tree -L 3 -I 'node_modules' 2>/dev/null || find . -maxdepth 3 -type d | grep -v node_modules | head -50</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la . && ls -la ./supabase 2>/dev/null && ls -la ./src 2>/dev/null</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">cat package.json 2>/dev/null || echo "No package.json found"</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">for dir in . .. ../.. ../../..; do if [ -f "$dir/package.json" ]; then echo "Found at: $dir" && cat "$dir/package.json"; break; fi; done</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find /tmp -name "*.ts" -o -name "*.tsx" -o -name "package.json" 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la /tmp/ | head -30</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -name "*.md" -o -name "README*" 2>/dev/null | head -10</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">echo "Current directory contents:" && ls -la && echo -e "\n\nSearching for source files:" && find . -type f 2>/dev/null | head -30</parameter>
</invoke>
</function_calls>

I notice that I don't have access to the actual source code files in the current context. Let me check if there are any files available that contain compliance management API information.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*compliance*" -o -name "*api*" 2>/dev/null</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -R 2>/dev/null | grep -i compliance</parameter>
</invoke>
</function_calls>

Based on the available context, I cannot locate the actual source code files for the Compliance Management API. Without access to the actual implementation files (TypeScript functions, database schemas, API endpoints, etc.), I cannot create accurate, code-first documentation as required by the critical rules.

To generate proper documentation, I would need access to:

1. **Edge Functions**: Files in `supabase/functions/` related to compliance management
2. **Database Migrations**: SQL files defining compliance-related tables and schemas
3. **TypeScript Types**: Interface definitions for compliance data structures
4. **Service Files**: Implementation of compliance business logic
5. **API Routes**: Actual endpoint definitions and handlers
6. **Configuration Files**: `package.json`, environment variable references

Since the instruction explicitly states "Your documentation MUST be derived directly from the provided source code - no invented features, no generic examples, no placeholder content," and I cannot access any source code files, I cannot proceed with creating this documentation.

**Required Action**: Please provide access to the source code repository containing the Compliance Management API implementation, including:
- Supabase edge functions directory
- Database migration files
- TypeScript source files
- API route definitions
- Type definitions and interfaces

Without these files, any documentation I create would violate the fundamental requirement of being "traceable to actual code in the provided source."