# Security Analysis and Remediation Tutorial

## Overview

Security Analysis helps you find and fix vulnerabilities in your code automatically. The system scans your entire codebase, identifies security issues, and provides actionable recommendations for improvement. You can track security scores across six dimensions, view detailed vulnerability reports, and generate automated fixes for detected issues.

## What You'll Learn

- How to run a comprehensive security scan on your code
- Understanding security scores and vulnerability reports
- Prioritizing issues by severity level
- Implementing automated security fixes
- Tracking security improvements over time

## Before You Begin

**Prerequisites:**
- A connected GitHub repository with code to analyze
- Access to a workspace with security analysis enabled
- Repository must have OrchestrAI enabled

**Time Required:** 15-30 minutes depending on repository size

## Step 1: Starting a Security Analysis

### Launching Your First Scan

1. Navigate to the Security Analysis page from your product dashboard
2. Click the shield icon button to open the analysis panel
3. Select the repository you want to analyze from the dropdown menu
4. Click **Start Analysis** to begin the security scan

The analysis will run in the background and you can continue working while it processes your code.

### What Happens During Analysis

The system examines your code in organized chunks based on security context:
- **Authentication & Authorization:** Login systems, access control, session management
- **API Security:** Endpoints, controllers, request handlers
- **Cryptography:** Encryption, key management, secure data handling
- **Data Access:** Database queries, data models, repositories
- **Configuration:** Settings files, environment variables
- **Business Logic:** Core application functionality

High-priority security areas (like authentication) are analyzed first to surface critical issues faster.

## Step 2: Monitoring Analysis Progress

### Real-Time Status Updates

Once your analysis starts, you'll see:
- Current processing status (Queued, Running, or Completed)
- Progress percentage as files are analyzed
- Elapsed time for the current analysis
- Which security context is currently being processed

### Background Processing

If you need to navigate away:
1. Click **Continue in Background** in the progress dialog
2. The analysis keeps running and you can check back anytime
3. View the status from the Recent Analyses table

Analysis typically takes 5-15 minutes depending on repository size.

## Step 3: Understanding Security Results

### Accessing Your Security Report

After analysis completes:
1. Click **View Results** from the Recent Analyses table
2. Select your repository and analysis run from the dropdown filters
3. Choose to view all files or focus on specific security contexts

### The Security Dashboard

Your results dashboard provides four key views:

**Score Tab:**
- Overall security score (0-100 scale)
- Six-dimensional radar chart showing:
  - Injection Prevention
  - Auth & Authorization
  - Secrets & Sensitive Data
  - Cryptographic Safety
  - Secure Configuration
  - Input Validation
- Comparison with previous analysis runs to track improvements

**Summary Tab:**
- High-level assessment of your security posture
- Breakdown of analyzed files by security context
- Analysis metadata (AI model used, processing time, files analyzed)
- Context-specific insights and patterns detected

**Critical Issues Tab:**
- High and critical severity vulnerabilities requiring immediate attention
- CWE (Common Weakness Enumeration) classifications
- OWASP Top 10 mappings where applicable
- Code snippets showing vulnerable code
- Specific remediation guidance

**Warnings Tab:**
- Medium and low severity issues that should be addressed
- Best practice recommendations
- Code quality improvements related to security

## Step 4: Interpreting Security Scores

### Score Ranges

- **80-100 (Green):** Excellent security posture with minimal vulnerabilities
- **60-79 (Yellow):** Moderate security with several areas needing improvement
- **0-59 (Red):** Critical security gaps requiring immediate attention

### The Six Security Dimensions

**Injection Prevention:**
Measures protection against SQL injection, command injection, and code injection attacks. Common issues include unvalidated user input and unsafe query construction.

**Auth & Authorization:**
Evaluates authentication mechanisms, session management, and access control. Flags weak password policies, insecure token handling, and broken authorization checks.

**Secrets & Sensitive Data:**
Detects hardcoded credentials, exposed API keys, leaked tokens, and improper handling of sensitive information.

**Cryptographic Safety:**
Assesses encryption implementations, hashing algorithms, and secure random number generation. Identifies weak ciphers and improper key management.

**Secure Configuration:**
Reviews security settings, CORS policies, CSP headers, and environment-specific configurations. Finds insecure defaults and missing security headers.

**Input Validation:**
Checks validation of user inputs, sanitization practices, and boundary checking. Prevents XSS, path traversal, and other input-based attacks.

## Step 5: Prioritizing Vulnerabilities

### Understanding Severity Levels

**Critical Severity:**
- Immediate exploitation risk
- Could lead to data breach or system compromise
- Examples: SQL injection vulnerabilities, exposed admin credentials, authentication bypasses

**High Severity:**
- Significant security risk
- Exploitable under certain conditions
- Examples: Weak encryption, missing authorization checks, insecure deserialization

**Medium Severity:**
- Moderate security concern
- May require multiple steps to exploit
- Examples: Missing input validation, weak password requirements, information disclosure

**Low Severity:**
- Minor security improvements
- Defense-in-depth enhancements
- Examples: Missing security headers, verbose error messages, outdated dependencies

### Recommended Priority Order

1. Start with **Critical** issues in authentication and authorization systems
2. Address **High** severity vulnerabilities in API endpoints and data access layers
3. Fix **Medium** severity issues in business logic and configuration
4. Improve **Low** severity items as part of regular maintenance

## Step 6: Reviewing Vulnerability Details

### Issue Information Card

Each detected vulnerability shows:

**Header:**
- Issue title (clear description of the problem)
- Severity badge (Critical, High, Medium, or Low)
- File path where the vulnerability exists

**Body:**
- Detailed description explaining the security risk
- CWE ID linking to standard weakness definitions
- OWASP category for web application vulnerabilities
- Affected security dimensions

**Code Context:**
- Vulnerable code snippet with line numbers
- Surrounding code for context
- Specific line where the issue occurs

**Remediation:**
- Step-by-step instructions to fix the vulnerability
- Code examples showing secure implementation
- Best practices for preventing similar issues

## Step 7: Generating Automated Fixes

### Using Fix Generation

For supported vulnerability types, you can generate automated fixes:

1. Locate the vulnerability in your Critical Issues or Warnings tab
2. Click the **Generate Fix** button on the issue card
3. Review the fix generation progress in the dialog
4. Wait for the AI to analyze the vulnerability and create a solution

### What Fix Generation Does

The system:
- Retrieves the vulnerable file from your repository
- Analyzes the security issue in context
- Generates secure replacement code following best practices
- Creates a pull request with the fix and detailed explanation
- Includes testing recommendations in the PR description

### Reviewing Generated Fixes

When the fix completes:
1. Click the **View Pull Request** link in the success dialog
2. Review the proposed code changes on GitHub
3. Read the explanation of what was changed and why
4. Check that the fix addresses the vulnerability without breaking functionality
5. Run your tests against the PR branch
6. Merge the PR after review approval

### Fix Generation Tips

- Review each generated fix carefully before merging
- Test the fixed code thoroughly in your development environment
- Generated fixes follow security best practices but may need project-specific adjustments
- Use fix history to track all automated remediation attempts

## Step 8: Handling Partial Results

### When Analysis Partially Completes

Sometimes analysis encounters issues with specific files or chunks:

**Identifying Partial Results:**
- Status shows "Partially Completed"
- Summary tab displays files analyzed vs. failed
- You can still view results from successfully analyzed portions

**Retry Failed Portions:**
1. Click **Retry Failed** button in the Summary tab
2. Select which failed chunks to retry from the dialog
3. Choose to retry all or select specific security contexts
4. Monitor progress as only the failed portions re-process

This allows you to get complete results without re-analyzing your entire codebase.

## Step 9: Comparing Analysis Runs

### Tracking Security Improvements

After implementing fixes:

1. Run a new security analysis on the same repository
2. Navigate to the Score tab in results
3. Use the **Compare** dropdown to select a previous analysis run
4. View the radar chart overlay showing before/after scores

The comparison shows:
- Which security dimensions improved or declined
- Overall score changes
- New issues introduced or existing issues resolved
- Trend direction for each security area

### Establishing Security Baselines

Run security analysis regularly to:
- Track security posture over time
- Verify that fixes improved scores
- Catch new vulnerabilities introduced in recent changes
- Maintain security compliance requirements

## Step 10: Fix History and Tracking

### Viewing Fix History

The Fix History tab shows all automated remediation attempts:

**Information Displayed:**
- Date and time of fix generation
- Issue title that was addressed
- File path that was modified
- Fix status (Success, Failed, Pending)
- Link to the generated pull request
- AI model used for fix generation

**Filtering History:**
- View fixes for all files or filter by specific file/chunk
- Track success rate of automated fixes
- Review failed fixes to understand limitations

### Learning from Fix Patterns

Use fix history to:
- Identify recurring vulnerability types in your codebase
- Understand which fixes were successful and why
- Refine your code review process based on common issues
- Train team members on secure coding practices

## Real-World Example: Securing Authentication

### Initial Analysis

**Scenario:** E-commerce application with user authentication

**Security Scan Results:**
- Overall Score: 62/100
- Critical Issues: 3
- High Severity: 5
- Medium Severity: 12
- Low Severity: 8

**Top Critical Issues Found:**
1. SQL Injection in login endpoint
2. Hardcoded admin password in configuration
3. Missing authentication on sensitive API routes

### Step-by-Step Remediation

**Issue 1: SQL Injection**

**Before:**
```javascript
// Vulnerable code detected
const query = `SELECT * FROM users WHERE email='${req.body.email}' 
               AND password='${req.body.password}'`;
db.query(query);
```

**Fix Applied:**
- Generated parameterized query implementation
- Added input validation
- Implemented prepared statements

**After:**
```javascript
// Secure implementation
const query = 'SELECT * FROM users WHERE email=? AND password=?';
db.query(query, [req.body.email, hashedPassword]);
```

**Issue 2: Hardcoded Credentials**

**Before:**
```javascript
const ADMIN_PASSWORD = "admin123"; // Detected as exposed secret
```

**Fix Applied:**
- Moved credential to environment variables
- Added secret management documentation
- Implemented secure configuration loading

**After:**
```javascript
const ADMIN_PASSWORD = process.env.ADMIN_PASSWORD;
// Environment variable loaded from secure vault
```

**Issue 3: Missing Authentication**

**Before:**
```javascript
// No authentication check on sensitive route
app.get('/api/user-data', (req, res) => {
  res.json(userData);
});
```

**Fix Applied:**
- Added authentication middleware
- Implemented token verification
- Added authorization checks

**After:**
```javascript
app.get('/api/user-data', authenticateToken, (req, res) => {
  res.json(userData);
});
```

### Results After Remediation

**Second Security Scan:**
- Overall Score: 89/100 (↑ 27 points)
- Critical Issues: 0 (↓ 3)
- High Severity: 1 (↓ 4)
- Medium Severity: 6 (↓ 6)
- Low Severity: 5 (↓ 3)

**Dimension Improvements:**
- Injection Prevention: 45 → 95 (+50)
- Auth & Authorization: 58 → 92 (+34)
- Secrets & Sensitive Data: 30 → 88 (+58)
- Cryptographic Safety: 75 → 85 (+10)
- Secure Configuration: 65 → 90 (+25)
- Input Validation: 70 → 88 (+18)

## Advanced Tips

### Optimizing Analysis Coverage

**For Large Repositories:**
- Analysis processes files in intelligent chunks based on security priority
- Authentication and API security are analyzed first
- You can view partial results while analysis continues
- Background processing prevents blocking your workflow

**Managing Analysis Scope:**
- Configure ignored folders in repository settings to exclude vendor code
- Focus on application code rather than dependencies
- Update exclusions if analysis times out on very large codebases

### Interpreting Chunk-Based Results

When viewing results for specific security contexts:
- Click on individual chunks to see which files were analyzed together
- Understand that issues may span multiple related files
- Use chunk context to understand architectural security patterns
- Review chunk summaries for files that couldn't be analyzed

### Continuous Security Integration

**Best Practices:**
1. Run security analysis after major feature additions
2. Schedule weekly scans on active development branches
3. Compare results before and after security-focused refactoring
4. Use scores as security gates for release readiness
5. Track security trends across multiple releases

**Team Workflows:**
- Share analysis results with your development team
- Use pull request links from fix history for code review
- Incorporate findings into sprint planning
- Set team goals for security score improvements

## Troubleshooting Common Issues

### Analysis Shows No Results

**Possible Causes:**
- Repository has no source code files
- All files are in excluded directories
- Repository connection lost

**Solutions:**
- Verify repository contains analyzable code files
- Check exclusion settings in repository configuration
- Re-authenticate GitHub connection

### Fix Generation Fails

**Possible Causes:**
- File was modified since analysis
- Complex multi-file vulnerability
- Ambiguous security context

**Solutions:**
- Re-run analysis to get current file state
- Review the vulnerability manually for multi-file issues
- Check fix history for error details
- Some issues may require manual remediation

### Partial Analysis Results

**Possible Causes:**
- Some files couldn't be accessed
- Analysis timeout on large files
- Temporary processing errors

**Solutions:**
- Use the Retry Failed button to re-process failed chunks
- Check Summary tab for which files failed
- Review error messages for specific issues
- Contact support for persistent failures

## Security Analysis Best Practices

### Regular Scanning Schedule

- **After Code Changes:** Run analysis when adding authentication, payment processing, or data handling features
- **Before Releases:** Scan production branches before deployment
- **Weekly Reviews:** Schedule automatic scans for active repositories
- **Post-Incident:** Analyze after security incidents to prevent recurrence

### Effective Remediation Workflow

1. **Triage:** Address critical and high severity issues first
2. **Batch Fixes:** Group similar vulnerabilities for efficient resolution
3. **Test Thoroughly:** Verify fixes don't break functionality
4. **Document:** Track what was fixed and lessons learned
5. **Re-scan:** Verify improvements with follow-up analysis

### Building Security Culture

- Share security scores with your team
- Celebrate security improvements
- Use findings as learning opportunities
- Incorporate secure coding training based on common issues
- Make security analysis part of definition of done

## Next Steps

Now that you understand security analysis and remediation:

1. **Run Your First Analysis:** Start with your most critical repository
2. **Review Top Issues:** Focus on critical and high severity vulnerabilities
3. **Apply Fixes:** Use automated fix generation for supported issues
4. **Track Progress:** Compare results after implementing fixes
5. **Establish Routine:** Make security scanning part of your development process

Regular security analysis helps you maintain a strong security posture, catch vulnerabilities early, and build more secure applications. The combination of automated scanning, detailed reporting, and fix generation makes security improvements accessible and actionable for development teams.