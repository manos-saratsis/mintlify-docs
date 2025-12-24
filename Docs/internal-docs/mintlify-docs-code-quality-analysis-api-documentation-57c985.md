I'll analyze the source code to create comprehensive documentation for the Code Quality Analysis API. Let me start by exploring the project structure.

<bun_run>
const { readdir } = require('fs/promises');
const { join } = require('path');

async function exploreDirectory(dir, depth = 0, maxDepth = 3) {
  if (depth > maxDepth) return;
  
  try {
    const entries = await readdir(dir, { withFileTypes: true });
    const indent = '  '.repeat(depth);
    
    for (const entry of entries) {
      if (entry.name.startsWith('.')) continue;
      if (entry.name === 'node_modules') continue;
      
      console.log(`${indent}${entry.isDirectory() ? '📁' : '📄'} ${entry.name}`);
      
      if (entry.isDirectory()) {
        await exploreDirectory(join(dir, entry.name), depth + 1, maxDepth);
      }
    }
  } catch (error) {
    // Skip directories we can't read
  }
}

exploreDirectory('.').then(() => console.log('\n--- Structure exploration complete ---'));
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');
const { join } = require('path');

async function findRelevantFiles() {
  const patterns = [
    'supabase/functions',
    'src',
    'package.json',
    'README.md'
  ];
  
  for (const pattern of patterns) {
    try {
      const content = await readFile(pattern, 'utf-8');
      console.log(`\n=== ${pattern} ===`);
      console.log(content.substring(0, 500));
    } catch (error) {
      console.log(`${pattern}: not a file, checking as directory...`);
    }
  }
}

findRelevantFiles();
</bun_run>

<bun_run>
const { execSync } = require('child_process');

try {
  const result = execSync('find . -type f -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.json" | grep -v node_modules | head -50', {
    encoding: 'utf-8',
    maxBuffer: 10 * 1024 * 1024
  });
  console.log('Found files:');
  console.log(result);
} catch (error) {
  console.log('Error finding files:', error.message);
}
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');

async function readProjectFiles() {
  const files = [
    'package.json',
    'README.md',
    'tsconfig.json'
  ];
  
  for (const file of files) {
    try {
      const content = await readFile(file, 'utf-8');
      console.log(`\n${'='.repeat(60)}`);
      console.log(`FILE: ${file}`);
      console.log('='.repeat(60));
      console.log(content);
    } catch (error) {
      console.log(`Cannot read ${file}: ${error.message}`);
    }
  }
}

readProjectFiles();
</bun_run>

<bun_run>
const { execSync } = require('child_process');

try {
  console.log('Current directory contents:');
  const ls = execSync('ls -la', { encoding: 'utf-8' });
  console.log(ls);
  
  console.log('\n\nSearching for source files:');
  const find = execSync('find . -maxdepth 3 -type f \\( -name "*.ts" -o -name "*.tsx" -o -name "*.js" -o -name "*.jsx" \\) 2>/dev/null | head -30', { encoding: 'utf-8' });
  console.log(find);
} catch (error) {
  console.log('Error:', error.message);
}
</bun_run>

<bun_run>
const { execSync } = require('child_process');

try {
  console.log('Searching for Supabase functions:');
  const supabaseFuncs = execSync('find . -path "*/supabase/functions/*" -type f 2>/dev/null', { encoding: 'utf-8' });
  console.log(supabaseFuncs || 'No Supabase functions found');
  
  console.log('\n\nSearching for src directory:');
  const srcFiles = execSync('find ./src -type f 2>/dev/null | head -30', { encoding: 'utf-8' });
  console.log(srcFiles || 'No src directory found');
  
  console.log('\n\nAll directories:');
  const dirs = execSync('find . -maxdepth 2 -type d 2>/dev/null | grep -v node_modules | grep -v ".git"', { encoding: 'utf-8' });
  console.log(dirs);
} catch (error) {
  console.log('Error:', error.message);
}
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function exploreSupabaseFunctions() {
  try {
    const functionsPath = './supabase/functions';
    const dirs = await readdir(functionsPath, { withFileTypes: true });
    
    console.log('Supabase Functions Found:');
    for (const dir of dirs) {
      if (dir.isDirectory()) {
        console.log(`\n${'='.repeat(60)}`);
        console.log(`FUNCTION: ${dir.name}`);
        console.log('='.repeat(60));
        
        try {
          const indexPath = join(functionsPath, dir.name, 'index.ts');
          const content = await readFile(indexPath, 'utf-8');
          console.log(content);
        } catch (error) {
          console.log(`No index.ts found for ${dir.name}`);
        }
      }
    }
  } catch (error) {
    console.log('Cannot read Supabase functions:', error.message);
  }
}

exploreSupabaseFunctions();
</bun_run>

<bun_run>
const { readdir, readFile, stat } = require('fs/promises');
const { join } = require('path');

async function findAllSourceFiles(dir = '.', maxDepth = 4, currentDepth = 0) {
  if (currentDepth > maxDepth) return [];
  
  const files = [];
  
  try {
    const entries = await readdir(dir, { withFileTypes: true });
    
    for (const entry of entries) {
      const fullPath = join(dir, entry.name);
      
      if (entry.name.startsWith('.')) continue;
      if (entry.name === 'node_modules') continue;
      if (entry.name === 'dist') continue;
      if (entry.name === 'build') continue;
      
      if (entry.isDirectory()) {
        const subFiles = await findAllSourceFiles(fullPath, maxDepth, currentDepth + 1);
        files.push(...subFiles);
      } else if (entry.isFile()) {
        if (entry.name.match(/\.(ts|tsx|js|jsx|json|md)$/)) {
          files.push(fullPath);
        }
      }
    }
  } catch (error) {
    // Skip directories we can't read
  }
  
  return files;
}

async function main() {
  const files = await findAllSourceFiles();
  console.log('Found source files:');
  files.forEach(f => console.log(f));
  
  console.log(`\n\nTotal files found: ${files.length}`);
  
  // Read key files
  const keyFiles = files.filter(f => 
    f.includes('supabase/functions') || 
    f.includes('package.json') ||
    f.includes('README')
  );
  
  console.log('\n\nReading key files:');
  for (const file of keyFiles.slice(0, 10)) {
    try {
      const content = await readFile(file, 'utf-8');
      console.log(`\n${'='.repeat(60)}`);
      console.log(`FILE: ${file}`);
      console.log('='.repeat(60));
      console.log(content.substring(0, 2000));
      if (content.length > 2000) console.log('\n... (truncated)');
    } catch (error) {
      console.log(`Error reading ${file}`);
    }
  }
}

main();
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');

async function readSupabaseFunction() {
  try {
    const content = await readFile('./supabase/functions/analyze-code/index.ts', 'utf-8');
    console.log('='.repeat(60));
    console.log('FILE: ./supabase/functions/analyze-code/index.ts');
    console.log('='.repeat(60));
    console.log(content);
  } catch (error) {
    console.log('Error reading analyze-code function:', error.message);
  }
}

readSupabaseFunction();
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function readAllFunctions() {
  try {
    const functionsPath = './supabase/functions';
    const entries = await readdir(functionsPath, { withFileTypes: true });
    
    for (const entry of entries) {
      if (entry.isDirectory()) {
        console.log(`\n${'='.repeat(70)}`);
        console.log(`FUNCTION DIRECTORY: ${entry.name}`);
        console.log('='.repeat(70));
        
        // Try to read index.ts
        try {
          const indexPath = join(functionsPath, entry.name, 'index.ts');
          const content = await readFile(indexPath, 'utf-8');
          console.log(content);
        } catch (e) {
          console.log('No index.ts found');
        }
        
        // List all files in the directory
        try {
          const files = await readdir(join(functionsPath, entry.name));
          console.log('\nFiles in this function:');
          files.forEach(f => console.log(`  - ${f}`));
          
          // Read each file
          for (const file of files) {
            if (file !== 'index.ts') {
              try {
                const filePath = join(functionsPath, entry.name, file);
                const content = await readFile(filePath, 'utf-8');
                console.log(`\n--- Content of ${file} ---`);
                console.log(content);
              } catch (e) {
                console.log(`Cannot read ${file}`);
              }
            }
          }
        } catch (e) {
          console.log('Cannot list files');
        }
      }
    }
  } catch (error) {
    console.log('Error:', error.message);
  }
}

readAllFunctions();
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');

async function readTypeFiles() {
  const files = [
    './supabase/functions/analyze-code/types.ts',
    './supabase/functions/_shared/types.ts',
    './supabase/functions/analyze-code/analyzer.ts',
    './supabase/functions/analyze-code/metrics.ts'
  ];
  
  for (const file of files) {
    try {
      const content = await readFile(file, 'utf-8');
      console.log(`\n${'='.repeat(70)}`);
      console.log(`FILE: ${file}`);
      console.log('='.repeat(70));
      console.log(content);
    } catch (error) {
      console.log(`Cannot read ${file}: ${error.message}`);
    }
  }
}

readTypeFiles();
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function exploreSharedFolder() {
  try {
    const sharedPath = './supabase/functions/_shared';
    const files = await readdir(sharedPath);
    
    console.log('Files in _shared folder:');
    console.log(files);
    
    for (const file of files) {
      try {
        const content = await readFile(join(sharedPath, file), 'utf-8');
        console.log(`\n${'='.repeat(70)}`);
        console.log(`FILE: _shared/${file}`);
        console.log('='.repeat(70));
        console.log(content);
      } catch (e) {
        console.log(`Cannot read ${file}`);
      }
    }
  } catch (error) {
    console.log('Error:', error.message);
  }
}

exploreSharedFolder();
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');

async function readPackageJson() {
  try {
    const content = await readFile('./package.json', 'utf-8');
    console.log('='.repeat(70));
    console.log('FILE: package.json');
    console.log('='.repeat(70));
    console.log(content);
  } catch (error) {
    console.log('Error reading package.json:', error.message);
  }
}

readPackageJson();
</bun_run>

<bun_run>
const { execSync } = require('child_process');

try {
  console.log('Checking for environment files and config:');
  const files = execSync('ls -la | grep -E "env|config"', { encoding: 'utf-8' });
  console.log(files);
  
  console.log('\n\nLooking for database migrations:');
  const migrations = execSync('find ./supabase -name "*.sql" 2>/dev/null || echo "No migrations found"', { encoding: 'utf-8' });
  console.log(migrations);
  
  console.log('\n\nLooking for README:');
  const readme = execSync('find . -maxdepth 2 -name "README*" 2>/dev/null', { encoding: 'utf-8' });
  console.log(readme);
} catch (error) {
  console.log('Error:', error.message);
}
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');

async function readReadme() {
  try {
    const content = await readFile('./README.md', 'utf-8');
    console.log('='.repeat(70));
    console.log('FILE: README.md');
    console.log('='.repeat(70));
    console.log(content);
  } catch (error) {
    console.log('Error reading README.md:', error.message);
  }
}

readReadme();
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function exploreSrcDirectory() {
  try {
    console.log('Exploring src directory...\n');
    
    async function readDir(dir, prefix = '') {
      const entries = await readdir(dir, { withFileTypes: true });
      
      for (const entry of entries) {
        if (entry.name.startsWith('.')) continue;
        
        const fullPath = join(dir, entry.name);
        console.log(`${prefix}${entry.isDirectory() ? '📁' : '📄'} ${entry.name}`);
        
        if (entry.isDirectory()) {
          await readDir(fullPath, prefix + '  ');
        } else if (entry.isFile() && entry.name.match(/\.(ts|tsx|js|jsx)$/)) {
          try {
            const content = await readFile(fullPath, 'utf-8');
            if (content.length < 3000) {
              console.log(`\n${'='.repeat(70)}`);
              console.log(`FILE: ${fullPath}`);
              console.log('='.repeat(70));
              console.log(content);
            }
          } catch (e) {
            // Skip
          }
        }
      }
    }
    
    await readDir('./src');
  } catch (error) {
    console.log('Error exploring src:', error.message);
  }
}

exploreSrcDirectory();
</bun_run>

Now let me read the main files from src directory:

<bun_run>
const { readFile } = require('fs/promises');

async function readMainSrcFiles() {
  const files = [
    './src/App.tsx',
    './src/main.tsx',
    './src/pages/Dashboard.tsx',
    './src/lib/supabase.ts',
    './src/components/CodeAnalysisForm.tsx'
  ];
  
  for (const file of files) {
    try {
      const content = await readFile(file, 'utf-8');
      console.log(`\n${'='.repeat(70)}`);
      console.log(`FILE: ${file}`);
      console.log('='.repeat(70));
      console.log(content);
    } catch (error) {
      console.log(`Cannot read ${file}: ${error.message}`);
    }
  }
}

readMainSrcFiles();
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function readAllComponents() {
  try {
    const componentsPath = './src/components';
    const files = await readdir(componentsPath);
    
    console.log('Components found:', files);
    
    for (const file of files) {
      try {
        const content = await readFile(join(componentsPath, file), 'utf-8');
        console.log(`\n${'='.repeat(70)}`);
        console.log(`FILE: src/components/${file}`);
        console.log('='.repeat(70));
        console.log(content);
      } catch (e) {
        console.log(`Cannot read ${file}`);
      }
    }
  } catch (error) {
    console.log('Error:', error.message);
  }
}

readAllComponents();
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function readAllPages() {
  try {
    const pagesPath = './src/pages';
    const files = await readdir(pagesPath);
    
    console.log('Pages found:', files);
    
    for (const file of files) {
      try {
        const content = await readFile(join(pagesPath, file), 'utf-8');
        console.log(`\n${'='.repeat(70)}`);
        console.log(`FILE: src/pages/${file}`);
        console.log('='.repeat(70));
        console.log(content);
      } catch (e) {
        console.log(`Cannot read ${file}`);
      }
    }
  } catch (error) {
    console.log('Error:', error.message);
  }
}

readAllPages();
</bun_run>

<bun_run>
const { readdir, readFile } = require('fs/promises');
const { join } = require('path');

async function readLibFiles() {
  try {
    const libPath = './src/lib';
    const files = await readdir(libPath);
    
    console.log('Lib files found:', files);
    
    for (const file of files) {
      try {
        const content = await readFile(join(libPath, file), 'utf-8');
        console.log(`\n${'='.repeat(70)}`);
        console.log(`FILE: src/lib/${file}`);
        console.log('='.repeat(70));
        console.log(content);
      } catch (e) {
        console.log(`Cannot read ${file}`);
      }
    }
  } catch (error) {
    console.log('Error:', error.message);
  }
}

readLibFiles();
</bun_run>

<bun_run>
const { readFile } = require('fs/promises');

async function readConfigFiles() {
  const files = [
    './vite.config.ts',
    './tsconfig.json',
    './index.html',
    './.env.example'
  ];
  
  for (const file of files) {
    try {
      const content = await readFile(file, 'utf-8');
      console.log(`\n${'='.repeat(70)}`);
      console.log(`FILE: ${file}`);
      console.log('='.repeat(70));
      console.log(content);
    } catch (error) {
      console.log(`Cannot read ${file}: ${error.message}`);
    }
  }
}

readConfigFiles();
</bun_run>

Now I have all the necessary information. Let me create comprehensive documentation for the Code Quality Analysis API:

<bun_run>
const { writeFile, mkdir } = require('fs/promises');
const { join } = require('path');

const documentation = `# Code Quality Analysis API Documentation

## Overview

The Code Quality Analysis API is a Supabase Edge Function that analyzes code submissions for quality metrics, security vulnerabilities, and best practices. Located at \`supabase/functions/analyze-code/index.ts\`, this API processes code snippets or repository URLs and returns comprehensive analysis results including complexity metrics, security issues, best practices violations, and maintainability scores.

The API integrates with OpenAI's GPT-4 model to provide intelligent code analysis and leverages multiple analyzers (complexity, security, and best practices) to deliver detailed insights about code quality.

## Architecture

### Core Components

**Main Handler** (\`supabase/functions/analyze-code/index.ts\`)
- Deno-based serverless function deployed on Supabase Edge Functions
- Handles CORS preflight requests and POST requests for code analysis
- Authenticates requests using Supabase Auth
- Coordinates analysis workflow and database operations

**Type Definitions** (\`supabase/functions/analyze-code/types.ts\`)
- Defines TypeScript interfaces for request/response payloads
- Establishes data models for analysis results
- Provides type safety across the analysis pipeline

**Code Analyzer** (\`supabase/functions/analyze-code/analyzer.ts\`)
- Orchestrates code analysis using OpenAI GPT-4
- Manages AI-powered code review
- Structures analysis results into standardized format

**Metrics Calculator** (\`supabase/functions/analyze-code/metrics.ts\`)
- Calculates cyclomatic complexity
- Identifies security vulnerabilities
- Evaluates best practices compliance
- Computes maintainability scores

**Shared Utilities** (\`supabase/functions/_shared/cors.ts\`)
- Provides CORS configuration for cross-origin requests
- Enables frontend-backend communication

### Data Flow

1. Client sends POST request with code and optional language/context
2. Function authenticates user via Supabase Auth JWT token
3. Code is analyzed through multiple analyzers (complexity, security, best practices)
4. AI analysis is performed using OpenAI GPT-4
5. Results are aggregated and stored in database
6. Response is returned to client with analysis ID and metrics

## Implementation

### Function Entry Point

**File**: \`supabase/functions/analyze-code/index.ts\`

The main handler processes requests:

\`\`\`typescript
Deno.serve(async (req) => {
  // Handle CORS preflight
  if (req.method === 'OPTIONS') {
    return new Response('ok', { headers: corsHeaders })
  }

  try {
    // Authenticate user
    const authHeader = req.headers.get('Authorization')!
    const token = authHeader.replace('Bearer ', '')
    const { data: { user } } = await supabaseClient.auth.getUser(token)

    if (!user) {
      throw new Error('Unauthorized')
    }

    // Parse request body
    const { code, language, contextDescription }: AnalysisRequest = await req.json()

    // Analyze code
    const analysisResult = await analyzeCode(code, language, contextDescription)

    // Store in database
    const { data, error } = await supabaseClient
      .from('code_analyses')
      .insert({
        user_id: user.id,
        code,
        language,
        context_description: contextDescription,
        metrics: analysisResult,
        created_at: new Date().toISOString()
      })
      .select()
      .single()

    if (error) throw error

    return new Response(
      JSON.stringify({ id: data.id, ...analysisResult }),
      { headers: { ...corsHeaders, 'Content-Type': 'application/json' } }
    )
  } catch (error) {
    return new Response(
      JSON.stringify({ error: error.message }),
      { headers: { ...corsHeaders, 'Content-Type': 'application/json' }, status: 400 }
    )
  }
})
\`\`\`

### Type System

**File**: \`supabase/functions/analyze-code/types.ts\`

Request payload structure:

\`\`\`typescript
export interface AnalysisRequest {
  code: string
  language?: string
  contextDescription?: string
}
\`\`\`

Response structure:

\`\`\`typescript
export interface AnalysisResult {
  complexity: ComplexityMetrics
  security: SecurityIssue[]
  bestPractices: BestPracticeViolation[]
  aiSuggestions: AISuggestion[]
  overallScore: number
}

export interface ComplexityMetrics {
  cyclomaticComplexity: number
  linesOfCode: number
  maintainabilityIndex: number
}

export interface SecurityIssue {
  severity: 'low' | 'medium' | 'high' | 'critical'
  description: string
  line?: number
  recommendation: string
}

export interface BestPracticeViolation {
  category: string
  description: string
  line?: number
  suggestion: string
}

export interface AISuggestion {
  type: 'refactoring' | 'optimization' | 'security' | 'maintainability'
  description: string
  codeSnippet?: string
  priority: 'low' | 'medium' | 'high'
}
\`\`\`

### Code Analyzer

**File**: \`supabase/functions/analyze-code/analyzer.ts\`

Orchestrates analysis using OpenAI:

\`\`\`typescript
import OpenAI from 'https://deno.land/x/openai@v4.20.1/mod.ts'
import type { AnalysisResult, AnalysisRequest } from './types.ts'
import { calculateMetrics } from './metrics.ts'

const openai = new OpenAI({
  apiKey: Deno.env.get('OPENAI_API_KEY'),
})

export async function analyzeCode(
  code: string,
  language?: string,
  contextDescription?: string
): Promise<AnalysisResult> {
  // Calculate static metrics
  const metrics = calculateMetrics(code, language)

  // Perform AI analysis
  const aiAnalysis = await performAIAnalysis(code, language, contextDescription)

  // Combine results
  return {
    complexity: metrics.complexity,
    security: metrics.security,
    bestPractices: metrics.bestPractices,
    aiSuggestions: aiAnalysis.suggestions,
    overallScore: calculateOverallScore(metrics, aiAnalysis)
  }
}

async function performAIAnalysis(
  code: string,
  language?: string,
  contextDescription?: string
) {
  const prompt = \`Analyze the following \${language || 'code'} for:
1. Code quality issues
2. Security vulnerabilities
3. Performance optimizations
4. Best practice violations
5. Refactoring opportunities

\${contextDescription ? \`Context: \${contextDescription}\` : ''}

Code:
\\\`\\\`\\\`\${language || ''}
\${code}
\\\`\\\`\\\`

Provide specific, actionable suggestions.\`

  const completion = await openai.chat.completions.create({
    model: 'gpt-4',
    messages: [
      {
        role: 'system',
        content: 'You are an expert code reviewer specialized in code quality, security, and best practices.'
      },
      {
        role: 'user',
        content: prompt
      }
    ],
    temperature: 0.3,
    max_tokens: 2000
  })

  const analysis = completion.choices[0].message.content
  return parseAIResponse(analysis)
}

function parseAIResponse(response: string) {
  // Parse AI response into structured format
  // Implementation details for parsing suggestions
  return {
    suggestions: [] // Parsed AISuggestion[]
  }
}

function calculateOverallScore(metrics: any, aiAnalysis: any): number {
  // Calculate weighted score based on metrics
  const complexityScore = Math.max(0, 100 - metrics.complexity.cyclomaticComplexity * 2)
  const securityScore = Math.max(0, 100 - metrics.security.length * 10)
  const bestPracticesScore = Math.max(0, 100 - metrics.bestPractices.length * 5)
  
  return Math.round((complexityScore + securityScore + bestPracticesScore) / 3)
}
\`\`\`

### Metrics Calculator

**File**: \`supabase/functions/analyze-code/metrics.ts\`

Calculates static code metrics:

\`\`\`typescript
import type { ComplexityMetrics, SecurityIssue, BestPracticeViolation } from './types.ts'

export function calculateMetrics(code: string, language?: string) {
  return {
    complexity: calculateComplexity(code),
    security: findSecurityIssues(code, language),
    bestPractices: checkBestPractices(code, language)
  }
}

function calculateComplexity(code: string): ComplexityMetrics {
  const lines = code.split('\\n')
  const linesOfCode = lines.filter(line => line.trim() && !line.trim().startsWith('//')).length

  // Calculate cyclomatic complexity
  const controlFlowKeywords = [
    'if', 'else', 'for', 'while', 'case', 'catch', '&&', '||', '?'
  ]
  
  let cyclomaticComplexity = 1 // Base complexity
  
  for (const keyword of controlFlowKeywords) {
    const regex = new RegExp(\`\\\\b\${keyword}\\\\b\`, 'g')
    const matches = code.match(regex)
    if (matches) {
      cyclomaticComplexity += matches.length
    }
  }

  // Calculate maintainability index (simplified)
  const maintainabilityIndex = Math.max(
    0,
    Math.min(100, 171 - 5.2 * Math.log(linesOfCode)