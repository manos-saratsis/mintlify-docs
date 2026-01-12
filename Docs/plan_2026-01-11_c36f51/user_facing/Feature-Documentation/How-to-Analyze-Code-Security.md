# How to Analyze Code Security

## Overview

The Code Security feature provides AI-powered vulnerability detection and security analysis for your codebase. It examines your repository across six critical security dimensions, identifying vulnerabilities, exposed secrets, and security misconfigurations before they become breaches.

## Understanding Security Dimensions

Every security analysis evaluates your code across six dimensions:

### Input Validation
Reviews how your application handles user input, checking for proper sanitization and validation patterns that prevent malicious data from entering your system.

### Auth & Authorization
Examines authentication flows, session management, and access control patterns to ensure users can only access resources they're authorized to view.

### Injection Prevention
Detects SQL injection, XSS (cross-site scripting), command injection, and other code injection vulnerabilities that could allow attackers to execute malicious code.

### Cryptographic Safety
Analyzes encryption implementations, hashing algorithms, and cryptographic practices to ensure sensitive data is properly protected.

### Secrets Management
Identifies hardcoded credentials, API keys, tokens, and other sensitive data that shouldn't be stored directly in code.

### Secure Configuration
Reviews security headers, CORS policies, SSL/TLS settings, and deployment configurations to ensure production-ready security.

## Starting a Security Analysis

### Prerequisites

Before running a security analysis:

1. You must have connected your GitHub account
2. At least one repository must be enabled for OrchestrAI
3. Your workspace must have sufficient credits available

### Running Your First Analysis

1. Navigate to the Code Security page
2. If you have enabled repositories, you'll see them listed in a table
3. Click the **New Analysis** button to open the analysis panel
4. Select the repository you want to analyze
5. Choose your AI model (Haiku for speed, Sonnet for balanced analysis, or Opus for most thorough review)
6. Add any custom security instructions (optional) to focus on specific concerns
7. Click **Start Security Analysis**

The analysis will begin immediately and run in the background, allowing you to continue working while it completes.

## Monitoring Analysis Progress

### Progress Indicators

While an analysis is running, you'll see several indicators:

- **Orange pulsing dot** next to the repository name shows an active analysis
- **Running (Background)** status badge indicates the analysis is in progress
- **Elapsed time** displays how long the analysis has been running
- A **View Progress** button lets you check detailed progress

### Viewing Live Progress

Click the **View Progress** button (orange play icon) to open the progress dialog:

- See which security chunk is currently being analyzed
- Monitor the number of completed chunks
- View real-time progress percentage
- Continue working while the analysis runs in the background

You can close the progress dialog at any time - the analysis continues running.

### Canceling an Analysis

If you need to stop an analysis:

1. Locate the repository in the table
2. Click the red **Stop** button (stop circle icon)
3. Confirm you want to cancel

The analysis will stop immediately. Any completed chunks are saved, and you can review partial results if available.

## Understanding Results

### Security Scores

Each analysis produces scores for all six security dimensions, rated 0-100:

- **80-100 (Green)**: Strong security posture in this area
- **60-79 (Yellow)**: Adequate but has room for improvement
- **0-59 (Red)**: Significant security concerns requiring attention

An **overall security score** averages all dimensions to provide a single health metric.

### Issue Counts

Results show two types of issues:

- **Critical vulnerabilities**: Severe security flaws requiring immediate attention
- **Warnings**: Lower-severity issues or potential concerns worth reviewing

### Viewing Detailed Results

1. Locate your completed analysis in the table
2. Click **View Results** or click on the date/score to navigate to the full report
3. The results page displays:
   - Overall security score and dimension breakdown
   - List of all identified vulnerabilities
   - Severity ratings for each issue
   - Specific file locations and line numbers
   - Remediation guidance for each vulnerability

### Analysis History

Each repository tracks multiple analysis runs. Click the expand arrow (chevron) next to a repository name to view:

- Previous analysis dates and scores
- Historical security trends
- Past issue counts
- Model used for each analysis

Click any historical run to view its complete results.

## Interpreting Security Reports

### Vulnerability Severity Levels

Issues are categorized by severity:

**Critical**: Immediate security risks that could lead to data breaches, unauthorized access, or system compromise. Address these first.

**High**: Serious vulnerabilities that present significant risk but may require specific conditions to exploit.

**Medium**: Security concerns that should be addressed but pose moderate risk.

**Low**: Minor issues or best practice violations that improve security posture but aren't urgent.

### Common Vulnerability Types

Your security report may identify:

**Injection Flaws**: Code that doesn't properly validate input, allowing attackers to inject malicious commands or queries.

**Authentication Issues**: Weak password policies, insecure session handling, or missing authentication checks.

**Sensitive Data Exposure**: Hardcoded secrets, unencrypted sensitive data, or improper access controls on confidential information.

**Security Misconfiguration**: Missing security headers, overly permissive CORS policies, or insecure default settings.

**Cryptographic Failures**: Use of outdated algorithms, weak encryption, or improper key management.

### OWASP and CWE References

Many vulnerabilities include references to industry standards:

- **OWASP Top 10**: Maps issues to the most critical web application security risks
- **CWE (Common Weakness Enumeration)**: Provides standardized identifiers for tracking and researching vulnerabilities

## Implementing Fixes

### Reading Remediation Guidance

Each vulnerability in your report includes:

1. **Description**: What the security issue is and why it matters
2. **Location**: Specific file path and line numbers where the issue exists
3. **Risk**: Explanation of what could happen if exploited
4. **Recommendation**: Step-by-step guidance on how to fix it
5. **Code examples**: Often includes before/after code snippets

### Prioritizing Security Work

Focus your efforts using this priority order:

1. **Critical vulnerabilities first**: Address any critical-severity issues immediately
2. **Exposed secrets**: Rotate any leaked credentials or API keys right away
3. **High-severity issues**: Fix these in your next sprint
4. **Score-based prioritization**: Focus on dimensions with the lowest scores
5. **Medium and low issues**: Schedule these for ongoing security improvements

### Verifying Fixes

After implementing security improvements:

1. Return to the Code Security page
2. Run a new security analysis on the same repository
3. Compare scores and issue counts to your previous analysis
4. Confirm that fixed vulnerabilities no longer appear in results

## Model Selection Guide

### Haiku (Fastest)
- Completes analysis quickly for faster feedback
- Best for frequent security checks during development
- Good for smaller repositories or focused scans
- More economical credit usage

### Sonnet (Recommended)
- Balanced analysis depth and speed
- Comprehensive vulnerability detection
- Suitable for most security analysis needs
- Good accuracy-to-cost ratio

### Opus (Most Thorough)
- Deepest security analysis with highest accuracy
- Detects subtle and complex vulnerabilities
- Best for production codebases and compliance requirements
- Uses more credits but provides most comprehensive results

## Execution Modes

### Now (Immediate)
- Analysis runs immediately in real-time
- Results available as soon as analysis completes
- Best for small to medium repositories
- Interactive progress monitoring

### Batch (Scheduled)
- Analysis queued for batch processing
- More efficient for large repositories
- Lower credit cost per analysis
- Results available when batch completes (typically within hours)

## Custom Security Instructions

Add custom instructions to focus analysis on specific areas:

**For compliance requirements:**
"Focus on PCI-DSS compliance requirements for payment processing code"

**For specific frameworks:**
"Pay special attention to React security best practices and XSS prevention"

**For particular concerns:**
"Prioritize authentication and authorization vulnerabilities in the API layer"

Custom instructions guide the AI to emphasize certain security aspects while still maintaining comprehensive coverage.

## Best Practices

### Regular Security Scans
- Run security analysis before major releases
- Schedule periodic scans (weekly or monthly) for active repositories
- Analyze after merging significant feature branches
- Scan after adding new dependencies or third-party libraries

### Integrating Security into Development
- Review security scores as part of pull request workflows
- Set minimum security score thresholds for deployments
- Track security improvements over time
- Share reports with your development team

### Managing False Positives
- Review each flagged issue carefully - not all warnings require code changes
- Some warnings highlight areas needing architectural decisions
- Document why certain warnings were assessed as acceptable risks
- Re-scan after fixes to confirm issues are resolved

## Troubleshooting

### No Repositories Available
If you don't see any repositories listed:
- Go to the Code section to manage repositories
- Enable OrchestrAI on at least one repository
- Return to Code Security to run analysis

### Analysis Failed
If an analysis shows "Failed" status:
- Check that the repository is still accessible
- Verify your GitHub connection is active
- Review partial results if available
- Try running the analysis again with a different model

### Insufficient Credits
If you receive an out-of-credits warning:
- Check your workspace's credit balance in the billing section
- Consider upgrading your plan for more credits
- Use Haiku model for more economical analysis
- Choose batch mode for lower credit consumption

### Partially Completed Analysis
If an analysis shows "Partially Completed":
- Some security chunks completed successfully
- View available results to see what was analyzed
- Critical issues found in completed chunks are still valid
- Re-run the analysis to get complete coverage

## Understanding Analysis Architecture

Behind the scenes, your security analysis follows this process:

1. **Connectivity Check**: Verifies repository access and permissions
2. **Repository Analysis**: Scans your codebase structure and identifies security-relevant files
3. **Chunk Processing**: Divides analysis into manageable chunks for thorough examination
4. **Security Evaluation**: AI analyzes each chunk across all six security dimensions
5. **Score Calculation**: Aggregates findings into dimension scores and overall rating
6. **Report Generation**: Compiles detailed vulnerability report with remediation guidance

This multi-phase approach ensures comprehensive coverage while maintaining efficiency.

## Security Standards Compliance

### OWASP Top 10 Coverage
The analysis detects and reports on all OWASP Top 10 categories:
- Broken Access Control
- Cryptographic Failures
- Injection
- Insecure Design
- Security Misconfiguration
- Vulnerable and Outdated Components
- Identification and Authentication Failures
- Software and Data Integrity Failures
- Security Logging and Monitoring Failures
- Server-Side Request Forgery

### Industry Best Practices
Analysis incorporates security best practices from:
- OWASP Application Security Verification Standard (ASVS)
- SANS Top 25 Software Errors
- NIST Secure Software Development Framework
- CWE/SANS Top 25 Most Dangerous Software Weaknesses

## Next Steps

After running your first security analysis:

1. Review the detailed results to understand your security posture
2. Prioritize and fix critical vulnerabilities immediately
3. Create a remediation plan for high and medium severity issues
4. Schedule regular security scans to track improvements
5. Share results with your team to build security awareness

Security is an ongoing process. Regular analysis helps you maintain a strong security posture as your codebase evolves.