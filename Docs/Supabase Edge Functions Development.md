# Supabase Edge Functions Development

## Overview

Supabase Edge Functions are Deno-based serverless functions running on Deno Deploy infrastructure. The orchestrai-dev-staging repository contains 54 edge functions located in `supabase/functions/`, handling everything from authentication to AI-powered code analysis and documentation generation.

## Project Structure

```
supabase/functions/
├── accept-invitation/
├── bitbucket-auth/
├── cancel-code-quality-analysis/
├── cancel-documentation-execution/
├── cancel-workspace-subscription/
├── check-subscription/
├── cleanup-stalled-executions/
├── code-compliance-analyzer/
├── code-fix-generator/
├── code-quality-analyzer/
├── code-quality-batch-poller/
├── code-quality-batch-submit/
├── code-quality-check/
├── code-security-analyzer/
├── create-checkout/
├── customer-portal/
├── documentation-batch-poller/
├── documentation-batch-submit/
├── documentation-job-processor/
├── documentation-orchestrator/
├── documentation-planner/
├── documentation-worker/
├── documentation-writer/
├── git-commit-test-results/
├── github-auth/
├── github-test-batch-poller/
├── github-test-batch-submit/
├── github-test-generator/
├── github-test-retry-failed/
├── gitlab-auth/
├── instrumentation-worker/
├── migrate-user-tokens/
├── modify-subscription/
├── process-workspace-deletions/
├── push-interim-documentation/
├── push-interim-instrumentation/
├── send-agent-notification/
├── send-analysis-share/
├── send-auth-email/
├── send-team-invitations/
├── send-welcome-email/
├── setup-stripe-products/
├── shared/                    # Shared utilities and libraries
├── stripe-webhook/
├── sync-billing-usage/
├── test-chunk-worker/
├── test-vault-access/
├── token-health-check/
├── validate-github-token/
├── vault-migrate/
├── vault-retrieve/
└── vault-store/
```

## Function Categories

### Authentication Functions
- **github-auth**: GitHub OAuth authentication flow handler
- **gitlab-auth**: GitLab OAuth authentication flow handler
- **bitbucket-auth**: Bitbucket OAuth authentication flow handler
- **validate-github-token**: Validates GitHub personal access tokens
- **token-health-check**: Monitors health status of stored authentication tokens

### Documentation Generation Functions
- **documentation-orchestrator**: Coordinates multi-step documentation generation workflows
- **documentation-planner**: Plans documentation structure based on repository analysis
- **documentation-writer**: Generates documentation content using AI models
- **documentation-worker**: Processes individual documentation tasks
- **documentation-job-processor**: Manages documentation job queue processing
- **documentation-batch-submit**: Submits batch documentation requests to AI providers
- **documentation-batch-poller**: Polls AI providers for batch job completion
- **cancel-documentation-execution**: Cancels in-progress documentation jobs
- **push-interim-documentation**: Commits interim documentation results to repositories

### Code Quality Functions
- **code-quality-analyzer**: Analyzes code quality metrics and patterns
- **code-quality-check**: Performs quick code quality validation
- **code-quality-batch-submit**: Submits batch code analysis requests
- **code-quality-batch-poller**: Polls for batch analysis completion
- **cancel-code-quality-analysis**: Cancels running code analysis jobs
- **code-compliance-analyzer**: Checks code against compliance standards
- **code-security-analyzer**: Performs security vulnerability scanning
- **code-fix-generator**: Generates automated fixes for identified issues

### Test Generation Functions
- **github-test-generator**: Generates unit tests for GitHub repositories
- **github-test-batch-submit**: Submits batch test generation requests
- **github-test-batch-poller**: Polls for test generation completion
- **github-test-retry-failed**: Retries failed test generation attempts
- **git-commit-test-results**: Commits generated tests back to repositories
- **test-chunk-worker**: Processes individual test generation chunks

### Instrumentation Functions
- **instrumentation-worker**: Adds observability instrumentation to code
- **push-interim-instrumentation**: Commits instrumentation changes to repositories

### Subscription & Billing Functions
- **create-checkout**: Creates Stripe checkout sessions
- **customer-portal**: Provides access to Stripe customer portal
- **check-subscription**: Validates workspace subscription status
- **modify-subscription**: Updates subscription plans or quantities
- **cancel-workspace-subscription**: Cancels active subscriptions
- **stripe-webhook**: Handles Stripe webhook events
- **sync-billing-usage**: Syncs usage data with Stripe for metered billing
- **setup-stripe-products**: Initializes Stripe product catalog

### Team & Workspace Functions
- **accept-invitation**: Processes team invitation acceptances
- **send-team-invitations**: Sends invitation emails to team members
- **process-workspace-deletions**: Handles workspace deletion workflows

### Vault Functions (Secure Token Storage)
- **vault-store**: Securely stores encrypted tokens
- **vault-retrieve**: Retrieves and decrypts stored tokens
- **vault-migrate**: Migrates tokens to new encryption scheme
- **test-vault-access**: Tests vault accessibility and encryption
- **migrate-user-tokens**: Batch migrates user tokens to vault

### Notification Functions
- **send-agent-notification**: Sends notifications about AI agent activity
- **send-analysis-share**: Emails shared analysis results
- **send-auth-email**: Sends authentication-related emails
- **send-welcome-email**: Sends welcome emails to new users

### Maintenance Functions
- **cleanup-stalled-executions**: Cleans up stalled or orphaned execution records

## Local Development Setup

### Prerequisites

1. **Supabase CLI Installation**
```bash
# macOS
brew install supabase/tap/supabase

# Windows (via Scoop)
scoop bucket add supabase https://github.com/supabase/scoop-bucket.git
scoop install supabase

# Linux
brew install supabase/tap/supabase
```

2. **Deno Installation**
```bash
# macOS/Linux
curl -fsSL https://deno.land/install.sh | sh

# Windows (PowerShell)
irm https://deno.land/install.ps1 | iex
```

### Environment Configuration

Create a `.env.local` file in your project root:

```bash
# Supabase Configuration
SUPABASE_URL=http://localhost:54321
SUPABASE_ANON_KEY=<your-local-anon-key>
SUPABASE_SERVICE_ROLE_KEY=<your-local-service-role-key>

# AI Provider Keys
OPENAI_API_KEY=<your-openai-key>
ANTHROPIC_API_KEY=<your-anthropic-key>

# OAuth Configuration
GITHUB_CLIENT_ID=<your-github-client-id>
GITHUB_CLIENT_SECRET=<your-github-client-secret>
GITLAB_CLIENT_ID=<your-gitlab-client-id>
GITLAB_CLIENT_SECRET=<your-gitlab-client-secret>

# Stripe Configuration
STRIPE_SECRET_KEY=<your-stripe-secret-key>
STRIPE_WEBHOOK_SECRET=<your-webhook-secret>

# Application Configuration
APP_URL=http://localhost:3000
```

### Starting Local Development

1. **Start Supabase Local Stack**
```bash
supabase start
```

This starts:
- PostgreSQL database (port 54322)
- Studio UI (port 54323)
- API Gateway (port 54321)
- Edge Functions runtime

2. **Serve Functions Locally**
```bash
# Serve all functions
supabase functions serve

# Serve specific function
supabase functions serve documentation-worker

# Serve with environment variables
supabase functions serve --env-file .env.local

# Serve with debugging enabled
supabase functions serve --debug
```

3. **Access Local Services**
- Functions: `http://localhost:54321/functions/v1/<function-name>`
- Studio: `http://localhost:54323`
- Database: `postgresql://postgres:postgres@localhost:54322/postgres`

## Creating New Functions

### Function Structure

Each function follows this standard structure:

```typescript
// supabase/functions/my-function/index.ts

import { serve } from "https://deno.land/std@0.168.0/http/server.ts"
import { createClient } from 'https://esm.sh/@supabase/supabase-js@2'

const corsHeaders = {
  'Access-Control-Allow-Origin': '*',
  'Access-Control-Allow-Headers': 'authorization, x-client-info, apikey, content-type',
}

serve(async (req) => {
  // Handle CORS preflight
  if (req.method === 'OPTIONS') {
    return new Response('ok', { headers: corsHeaders })
  }

  try {
    // Initialize Supabase client
    const supabaseClient = createClient(
      Deno.env.get('SUPABASE_URL') ?? '',
      Deno.env.get('SUPABASE_ANON_KEY') ?? '',
      {
        global: {
          headers: { Authorization: req.headers.get('Authorization')! },
        },
      }
    )

    // Parse request body
    const { param1, param2 } = await req.json()

    // Your business logic here
    const result = await processData(param1, param2)

    // Return response
    return new Response(
      JSON.stringify({ success: true, data: result }),
      {
        headers: { ...corsHeaders, 'Content-Type': 'application/json' },
        status: 200,
      },
    )
  } catch (error) {
    return new Response(
      JSON.stringify({ error: error.message }),
      {
        headers: { ...corsHeaders, 'Content-Type': 'application/json' },
        status: 400,
      },
    )
  }
})
```

### Creating a New Function

```bash
# Create function directory and files
supabase functions new my-function

# This creates:
# supabase/functions/my-function/index.ts
```

### Shared Utilities

The `supabase/functions/shared/` directory contains reusable utilities:

```typescript
// Import shared utilities in your function
import { validateAuth } from '../shared/auth.ts'
import { logError } from '../shared/logging.ts'
import { sendEmail } from '../shared/email.ts'
```

## Testing Functions

### Local Testing with curl

```bash
# Test function locally
curl -i --location --request POST \
  'http://localhost:54321/functions/v1/my-function' \
  --header 'Authorization: Bearer YOUR_ANON_KEY' \
  --header 'Content-Type: application/json' \
  --data '{"param1": "value1", "param2": "value2"}'
```

### Testing with Supabase Client

```typescript
// From your frontend application
const { data, error } = await supabase.functions.invoke('my-function', {
  body: { param1: 'value1', param2: 'value2' }
})
```

### Automated Testing

Create test files alongside your functions:

```typescript
// supabase/functions/my-function/test.ts
import { assertEquals } from "https://deno.land/std@0.168.0/testing/asserts.ts"

Deno.test("my-function processes data correctly", async () => {
  const result = await processData("test", "data")
  assertEquals(result.status, "success")
})
```

Run tests:
```bash
deno test supabase/functions/my-function/test.ts
```

## Deployment

### Manual Deployment

```bash
# Deploy single function
supabase functions deploy my-function

# Deploy all functions
supabase functions deploy

# Deploy with environment variables
supabase functions deploy my-function --no-verify-jwt
```

### Set Environment Variables

```bash
# Set secret for specific function
supabase secrets set MY_SECRET=value --env-file .env.production

# Set secret for all functions
supabase secrets set OPENAI_API_KEY=sk-xxx STRIPE_SECRET_KEY=sk_live_xxx
```

### CI/CD Deployment

Example GitHub Actions workflow:

```yaml
# .github/workflows/deploy-functions.yml
name: Deploy Edge Functions

on:
  push:
    branches: [main]
    paths:
      - 'supabase/functions/**'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      
      - uses: supabase/setup-cli@v1
        with:
          version: latest
      
      - name: Deploy functions
        run: supabase functions deploy
        env:
          SUPABASE_ACCESS_TOKEN: ${{ secrets.SUPABASE_ACCESS_TOKEN }}
          SUPABASE_PROJECT_ID: ${{ secrets.SUPABASE_PROJECT_ID }}
```

## Debugging Techniques

### Local Debugging

1. **Enable Debug Logging**
```bash
supabase functions serve --debug
```

2. **Console Logging**
```typescript
console.log('Debug info:', { variable1, variable2 })
console.error('Error occurred:', error)
```

3. **Inspect Function Logs**
```bash
# View logs for specific function
supabase functions logs my-function

# Stream logs in real-time
supabase functions logs my-function --follow

# Filter by time range
supabase functions logs my-function --since 1h
```

### Production Debugging

1. **View Production Logs**
```bash
# Authenticate to production project
supabase link --project-ref your-project-ref

# View logs
supabase functions logs my-function --project-ref your-project-ref
```

2. **Log Structured Data**
```typescript
console.log(JSON.stringify({
  level: 'error',
  function: 'my-function',
  error: error.message,
  stack: error.stack,
  context: { userId, requestId }
}))
```

3. **Error Tracking Integration**
```typescript
import * as Sentry from "https://deno.land/x/sentry/index.ts"

Sentry.init({
  dsn: Deno.env.get("SENTRY_DSN"),
  environment: "production"
})

try {
  // Your code
} catch (error) {
  Sentry.captureException(error)
  throw error
}
```

## Common Patterns

### Authentication & Authorization

```typescript
// Verify user is authenticated
const authHeader = req.headers.get('Authorization')
if (!authHeader) {
  return new Response(
    JSON.stringify({ error: 'Missing authorization header' }),
    { status: 401, headers: corsHeaders }
  )
}

// Get user from JWT
const supabaseClient = createClient(
  Deno.env.get('SUPABASE_URL') ?? '',
  Deno.env.get('SUPABASE_ANON_KEY') ?? '',
  {
    global: { headers: { Authorization: authHeader } }
  }
)

const { data: { user }, error: authError } = await supabaseClient.auth.getUser()
if (authError || !user) {
  return new Response(
    JSON.stringify({ error: 'Invalid token' }),
    { status: 401, headers: corsHeaders }
  )
}
```

### Database Operations

```typescript
// Using service role for admin operations
const supabaseAdmin = createClient(
  Deno.env.get('SUPABASE_URL') ?? '',
  Deno.env.get('SUPABASE_SERVICE_ROLE_KEY') ?? ''
)

// Query data
const { data, error } = await supabaseAdmin
  .from('workspaces')
  .select('*')
  .eq('user_id', user.id)

// Insert data
const { data: newRecord, error: insertError } = await supabaseAdmin
  .from('executions')
  .insert({ workspace_id, status: 'running' })
  .select()
  .single()

// Update data
const { error: updateError } = await supabaseAdmin
  .from('executions')
  .update({ status: 'completed', completed_at: new Date().toISOString() })
  .eq('id', executionId)
```

### Invoking Other Functions

```typescript
// Call another edge function
const response = await supabaseClient.functions.invoke('other-function', {
  body: { data: 'to-process' }
})

if (response.error) {
  throw new Error(`Function invocation failed: ${response.error}`)
}

return response.data
```

### Handling Long-Running Operations

```typescript
// For operations taking > 30 seconds, use async pattern

// 1. Accept request and return immediately
const { data: execution } = await supabaseAdmin
  .from('executions')
  .insert({ status: 'queued', workspace_id })
  .select()
  .single()

// Return execution ID immediately
return new Response(
  JSON.stringify({ executionId: execution.id }),
  { status: 202, headers: corsHeaders }
)

// 2. Process asynchronously (don't await)
processLongRunningTask(execution.id).catch(error => {
  console.error('Background task failed:', error)
})

// 3. Client polls for completion
async function processLongRunningTask(executionId: string) {
  try {
    const result = await performWork()
    
    await supabaseAdmin
      .from('executions')
      .update({ status: 'completed', result })
      .eq('id', executionId)
  } catch (error) {
    await supabaseAdmin
      .from('executions')
      .update({ status: 'failed', error: error.message })
      .eq('id', executionId)
  }
}
```

### Batch Processing Pattern

The codebase uses a consistent batch processing pattern:

```typescript
// 1. Batch Submit Function
// - Validates input
// - Submits batch to AI provider
// - Returns batch ID

// 2. Batch Poller Function (scheduled)
// - Queries pending batches
// - Polls AI provider for completion
// - Updates status in database

// 3. Result Processor Function
// - Retrieves completed results
// - Processes and stores data
// - Triggers downstream workflows

// Example from code-quality-batch-submit
const batchInput = prepareFileList(files)
const batch = await openai.batches.create({
  input_file_id: uploadedFileId,
  endpoint: "/v1/chat/completions",
  completion_window: "24h"
})

await supabaseAdmin
  .from('batch_jobs')
  .insert({
    batch_id: batch.id,
    status: 'validating',
    workspace_id
  })
```

## Performance Optimization

### Import Maps

Use import maps for faster cold starts:

```json
// import_map.json
{
  "imports": {
    "supabase": "https://esm.sh/@supabase/supabase-js@2",
    "openai": "https://esm.sh/openai@4"
  }
}
```

Reference in function:
```typescript
import { createClient } from "supabase"
import OpenAI from "openai"
```

### Caching

```typescript
// Cache frequently accessed data
const cache = new Map()

function getCachedData(key: string, ttl: number = 60000) {
  const cached = cache.get(key)
  if (cached && Date.now() - cached.timestamp < ttl) {
    return cached.value
  }
  return null
}

function setCachedData(key: string, value: any) {
  cache.set(key, { value, timestamp: Date.now() })
}
```

### Connection Pooling

```typescript
// Reuse Supabase client instances
let supabaseClient: SupabaseClient | null = null

function getSupabaseClient() {
  if (!supabaseClient) {
    supabaseClient = createClient(
      Deno.env.get('SUPABASE_URL') ?? '',
      Deno.env.get('SUPABASE_SERVICE_ROLE_KEY') ?? ''
    )
  }
  return supabaseClient
}
```

## Security Best Practices

### Input Validation

```typescript
import { z } from "https://deno.land/x/zod/mod.ts"

const requestSchema = z.object({
  workspaceId: z.string().uuid(),
  repositoryUrl: z.string().url(),
  options: z.object({
    includeTests: z.boolean().optional()
  }).optional()
})

const validatedData = requestSchema.parse(await req.json())
```

### Rate Limiting

```typescript
// Implement rate limiting per user
const rateLimitKey = `ratelimit:${user.id}:${functionName}`
const { data: attempts } = await supabaseAdmin
  .from('rate_limits')
  .select('count, window_start')
  .eq('key', rateLimitKey)
  .single()

if (attempts && attempts.count >= 100) {
  return new Response(
    JSON.stringify({ error: 'Rate limit exceeded' }),
    { status: 429, headers: corsHeaders }
  )
}
```

### Secrets Management

```typescript
// Never log secrets
const apiKey = Deno.env.get('OPENAI_API_KEY')
console.log('Using API key:', apiKey.substring(0, 7) + '...')

// Validate required secrets on startup
const requiredSecrets = ['OPENAI_API_KEY', 'SUPABASE_URL']
for (const secret of requiredSecrets) {
  if (!Deno.env.get(secret)) {
    throw new Error(`Missing required environment variable: ${secret}`)
  }
}
```

### CORS Configuration

```typescript
const corsHeaders = {
  'Access-Control-Allow-Origin': Deno.env.get('APP_URL') ?? '*',
  'Access-Control-Allow-Headers': 'authorization, x-client-info, apikey, content-type',
  'Access-Control-Allow-Methods': 'POST, OPTIONS'
}
```

## Monitoring & Observability

### Structured Logging

```typescript
interface LogEntry {
  level: 'info' | 'warn' | 'error'
  message: string
  function: string
  userId?: string
  duration?: number
  error?: string
  metadata?: Record<string, any>
}

function log(entry: LogEntry) {
  console.log(JSON.stringify({
    ...entry,
    timestamp: new Date().toISOString()
  }))
}

// Usage
log({
  level: 'info',
  message: 'Processing documentation request',
  function: 'documentation-orchestrator',
  userId: user.id,
  metadata: { workspaceId, repositoryId }
})
```

### Performance Tracking

```typescript
const startTime = Date.now()

try {
  const result = await processData()
  
  log({
    level: 'info',
    message: 'Request completed',
    function: 'my-function',
    duration: Date.now() - startTime
  })
  
  return result
} catch (error) {
  log({
    level: 'error',
    message: 'Request failed',
    function: 'my-function',
    duration: Date.now() - startTime,
    error: error.message
  })
  throw error
}
```

## Troubleshooting

### Common Issues

1. **Function Timeout (150s limit)**
   - Use async processing pattern for long operations
   - Return 202 Accepted and process in background
   - Implement polling endpoint for status checks

2. **Memory Limits**
   - Stream large files instead of loading into memory
   - Process data in chunks
   - Clear variables when no longer needed

3. **Cold Start Latency**
   - Minimize dependencies
   - Use import maps
   - Keep functions focused and lightweight

4. **Database Connection Issues**
   - Reuse Supabase client instances
   - Implement connection retry logic
   - Use connection pooling

5. **CORS Errors**
   - Ensure OPTIONS method handler is implemented
   - Verify CORS headers match frontend domain
   - Check browser console for specific error messages

### Debug Checklist

- [ ] Verify environment variables are set
- [ ] Check function logs for errors
- [ ] Validate request payload format
- [ ] Confirm authentication headers are present
- [ ] Test with minimal payload first
- [ ] Check database permissions
- [ ] Verify external API credentials
- [ ] Review CORS configuration
- [ ] Test locally before deploying
- [ ] Monitor function execution metrics

## Best Practices Summary

1. **Keep functions focused** - One function, one responsibility
2. **Use TypeScript** - Type safety prevents runtime errors
3. **Handle errors gracefully** - Return meaningful error messages
4. **Log strategically** - Include context for debugging
5. **Test thoroughly** - Local testing before deployment
6. **Secure by default** - Validate all inputs, protect secrets
7. **Optimize performance** - Minimize cold starts, use caching
8. **Document your functions** - Include usage examples in comments
9. **Version your APIs** - Plan for backwards compatibility
10. **Monitor in production** - Track errors and performance metrics