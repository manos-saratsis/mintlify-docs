I need to analyze the source code to create comprehensive documentation for the Documentation Management Tutorial. Let me start by exploring the project structure.

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | head -30</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">pwd</parameter>
</invoke>
</function_calls>
<parameter name="command">pwd</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -maxdepth 3 -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" -o -name "*.json" \) 2>/dev/null | grep -E "(doc|page|component|route)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -maxdepth 3 -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" -o -name "*.json" \) 2>/dev/null | grep -E "(doc|page|component|route)" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -maxdepth 2 -type d 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -maxdepth 2 -type d 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la .</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la .</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -name "package.json" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -name "package.json" 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f 2>/dev/null | head -50</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f 2>/dev/null | head -50</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -R . 2>/dev/null | head -100</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -R . 2>/dev/null | head -100</parameter>
</invoke>
</function_calls>

Let me try a different approach to understand the available context:

<function_calls>
<invoke name="execute_javascript">
<parameter name="code">
const fs = require('fs');
const path = require('path');

// Check current directory
console.log('Current directory:', process.cwd());

// List files in current directory
try {
  const files = fs.readdirSync('.');
  console.log('\nFiles in current directory:', files);
} catch (e) {
  console.log('Error reading directory:', e.message);
}
</parameter>
</invoke>
</function_calls>
<parameter name="code">
const fs = require('fs');
const path = require('path');

// Check current directory
console.log('Current directory:', process.cwd());

// List files in current directory
try {
  const files = fs.readdirSync('.');
  console.log('\nFiles in current directory:', files);
} catch (e) {
  console.log('Error reading directory:', e.message);
}
</parameter>
</invoke>
</function_calls>

Based on the instructions provided and the absence of accessible source code in the current context, I need to note that I cannot create documentation without actual source code to analyze. However, I understand this appears to be a test or template scenario.

According to the CRITICAL RULES provided:
1. **Code-First Approach**: Every statement must be traceable to actual code
2. **No Placeholders**: Never use generic examples without showing actual code
3. **Verification Required**: Before documenting any feature, verify it exists in the source code

Since no source code is accessible in the current environment, I cannot create valid documentation that adheres to these rules. Creating documentation without verifiable source code would violate the fundamental principles outlined in the instructions.

## Response:

I cannot generate the requested "Documentation Management Tutorial" because:

**No Source Code Available**: The current environment does not contain any accessible source code files to analyze. The tools attempted to locate project files but found no TypeScript, JavaScript, or configuration files.

**Critical Rules Compliance**: According to the documentation guidelines provided:
- "Every statement in your documentation must be traceable to actual code in the provided source"
- "Before documenting any feature, verify it exists in the provided source code"
- "Never use phrases like 'configure X', 'set up Y', or 'implement Z' without showing the actual code/configuration"

**Required Next Steps**:

To create proper documentation, I need access to:
1. The actual project source code files
2. Component implementations related to documentation management
3. Page routes and navigation structures
4. Any API endpoints or database schemas related to documentation features
5. UI components that users interact with for documentation tasks

Please provide the source code or ensure the files are accessible in the working directory, and I will create comprehensive, code-based documentation that follows all the specified guidelines.