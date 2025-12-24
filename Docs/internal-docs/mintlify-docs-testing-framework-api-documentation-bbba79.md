I'll analyze the source code to create comprehensive Testing Framework API Documentation. Let me start by exploring the project structure to identify testing-related files and frameworks.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.json" | grep -E "(package|tsconfig)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f -name "*.json" | grep -E "(package|tsconfig)" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.test.*" -o -name "*.spec.*" -o -name "*test*" -o -name "*spec*" \) 2>/dev/null | head -30</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f \( -name "*.test.*" -o -name "*.spec.*" -o -name "*test*" -o -name "*spec*" \) 2>/dev/null | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -maxdepth 3 -type f -name "package.json" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -maxdepth 3 -type f -name "package.json" 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type d -name "__tests__" -o -name "test" -o -name "tests" 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type d -name "__tests__" -o -name "test" -o -name "tests" 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la src/ 2>/dev/null || ls -la</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la src/ 2>/dev/null || ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.config.*" 2>/dev/null | grep -E "(jest|vitest|mocha|karma|playwright|cypress)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f -name "*.config.*" 2>/dev/null | grep -E "(jest|vitest|mocha|karma|playwright|cypress)" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat package.json | grep -A 5 -B 5 -E "(test|jest|vitest|mocha|playwright|cypress)"</parameter>
</invoke>
</function_calls>
<parameter name="command">cat package.json | grep -A 5 -B 5 -E "(test|jest|vitest|mocha|playwright|cypress)"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" 2>/dev/null | head -30</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" 2>/dev/null | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -R | grep -E "(test|spec)" | head -40</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -R | grep -E "(test|spec)" | head -40</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -name "*.config.js" -o -name "*.config.ts" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -name "*.config.js" -o -name "*.config.ts" 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -r "describe\|it\|test\|expect" --include="*.ts" --include="*.tsx" --include="*.js" --include="*.jsx" . 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">grep -r "describe\|it\|test\|expect" --include="*.ts" --include="*.tsx" --include="*.js" --include="*.jsx" . 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" \) -path "*/test/*" -o -path "*/__tests__/*" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -type f \( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" \) -path "*/test/*" -o -path "*/__tests__/*" 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la supabase/functions/ 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la supabase/functions/ 2>/dev/null | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions -type f -name "*.test.ts" -o -name "*_test.ts" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions -type f -name "*.test.ts" -o -name "*_test.ts" 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -name "deno.json" -o -name "deno.jsonc" 2>/dev/null</parameter>
</invoke>
</function_calls>
<parameter name="command">find . -name "deno.json" -o -name "deno.jsonc" 2>/dev/null</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls supabase/functions/</parameter>
</invoke>
</function_calls>
<parameter name="command">ls supabase/functions/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions -type f -name "*.ts" | head -10</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions -type f -name "*.ts" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/deno.json</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/deno.json</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions -name "*.test.ts" -o -name "*_test.ts"</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions -name "*.test.ts" -o -name "*_test.ts"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la supabase/functions/fetch-github-repos/</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la supabase/functions/fetch-github-repos/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions -name "*test*" -type f</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions -name "*test*" -type f</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/fetch-github-repos/testUtils.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/fetch-github-repos/testUtils.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la supabase/functions/analyze-repository/</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la supabase/functions/analyze-repository/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/analyze-repository/testUtils.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/analyze-repository/testUtils.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la supabase/functions/generate-documentation/</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la supabase/functions/generate-documentation/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/generate-documentation/testUtils.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/generate-documentation/testUtils.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions -name "index.ts" | head -10</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions -name "index.ts" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/fetch-github-repos/index.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/fetch-github-repos/index.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/analyze-repository/index.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/analyze-repository/index.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/generate-documentation/index.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/generate-documentation/index.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -r "assertEquals\|assertExists\|assert" supabase/functions --include="*.ts" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">grep -r "assertEquals\|assertExists\|assert" supabase/functions --include="*.ts" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/deno.json</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/deno.json</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions -type d | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions -type d | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la supabase/functions/_shared/</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la supabase/functions/_shared/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/_shared/testHelpers.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/_shared/testHelpers.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">find supabase/functions/_shared -name "*.ts"</parameter>
</invoke>
</function_calls>
<parameter name="command">find supabase/functions/_shared -name "*.ts"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/_shared/cors.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/_shared/cors.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">supabase/functions/_shared/types.ts</parameter>
</invoke>
</function_calls>
<parameter name="path">supabase/functions/_shared/types.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">head -50 supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">head -50 supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">head -50 supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">head -50 supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">head -50 supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">head -50 supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">wc -l supabase/functions/*/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">wc -l supabase/functions/*/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -n "Deno.test" supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">grep -n "Deno.test" supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -n "Deno.test" supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">grep -n "Deno.test" supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -n "Deno.test" supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">grep -n "Deno.test" supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/fetch-github-repos/index.test.ts | grep -A 5 "mock"</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/fetch-github-repos/index.test.ts | grep -A 5 "mock"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/analyze-repository/index.test.ts | grep -A 5 "mock"</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/analyze-repository/index.test.ts | grep -A 5 "mock"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -n "import" supabase/functions/fetch-github-repos/index.test.ts | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">grep -n "import" supabase/functions/fetch-github-repos/index.test.ts | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/deno.json | jq '.tasks'</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/deno.json | jq '.tasks'</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">pwd</parameter>
</invoke>
</function_calls>
<parameter name="command">pwd</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">basename $(pwd)</parameter>
</invoke>
</function_calls>
<parameter name="command">basename $(pwd)</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">mkdir -p internal-docs</parameter>
</invoke>
</function_calls>
<parameter name="command">mkdir -p internal-docs</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/fetch-github-repos/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/analyze-repository/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/generate-documentation/index.test.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/_shared/testHelpers.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/_shared/testHelpers.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/fetch-github-repos/testUtils.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/fetch-github-repos/testUtils.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions/analyze-repository/testUtils.ts</parameter>
</invoke>
</function_calls>
<parameter name="command">cat supabase/functions/analyze-repository/testUtils.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_command">
<parameter name="command">cat supabase/functions