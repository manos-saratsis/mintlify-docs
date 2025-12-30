# How to Use Code Security Analysis

## Overview

Code Security Analysis helps you identify and fix security vulnerabilities in your codebase. The system scans your code for common security issues, provides detailed reports with severity ratings, and offers AI-powered fixes to resolve problems quickly.

## Getting Started

### Prerequisites

Before you can analyze your code for security issues, you need:

1. A workspace selected
2. At least one repository connected to your product
3. Orchestrai enabled on the repository you want to analyze

If you haven't connected a repository yet, you'll see helpful guidance to get started with options for detecting vulnerabilities, scanning for exposed secrets, and reviewing your overall security posture.

### Enabling a Repository

To enable security analysis on a repository:

1. Navigate to the Code page in your product
2. Find the repository you want to analyze
3. Enable Orchestrai for that repository
4. Return to the Security page to begin analysis

## Running a Security Analysis

### Starting an Analysis

1. From the main navigation, go to the Security section (look for the shield icon)
2. You'll see a table listing all your enabled repositories
3. Find the repository you want to analyze
4. Click the analyze button for that repository
5. The analysis will begin immediately

While the analysis runs, you'll see:
- A progress indicator showing the analysis is in progress
- The option to continue the analysis in the background
- Real-time status updates

### Background Processing

Security analysis can take several minutes depending on your codebase size. You can:

- Stay on the page to monitor progress
- Continue the analysis in the background and return later
- Navigate to other pages while the analysis completes

You'll receive a notification when the analysis finishes.

## Understanding Your Security Report

### Accessing Results

Once an analysis completes:

1. Click the "View Results" button at the top of the Security page
2. Or click directly on a completed analysis from the repository table

The results page provides multiple ways to explore your security findings.

### Report Sections

Your security report includes several tabs:

**Score Tab**
- Visual radar chart showing security scores across six dimensions
- Injection Prevention: Protection against SQL injection, XSS, and similar attacks
- Auth & Authorization: Proper authentication and access control implementation
- Secrets & Data: Detection of exposed credentials and sensitive information
- Cryptography: Secure encryption and hashing practices
- Configuration: Secure system and application settings
- Input Validation: Proper sanitization and validation of user inputs

Each dimension is scored from 0-100, with higher scores indicating better security.

**Summary Tab**
- Overall security score for the analyzed code
- Written summary explaining the main security findings
- High-level assessment of your security posture

**Critical Issues Tab**
- Lists high and critical severity vulnerabilities
- Issues requiring immediate attention
- Detailed information for each vulnerability

**Warnings Tab**
- Medium and low severity issues
- Recommendations for improvement
- Best practice violations

**Fix History Tab**
- Record of all automated fixes applied
- Status of fix attempts
- Links to pull requests created for fixes

### Filtering Results

You can narrow down your analysis view:

**By Repository**: Select which repository's results to view from the dropdown menu

**By Analysis Run**: Each time you run an analysis, a new report is created. Choose which run to review by selecting a date and time from the dropdown

**By File**: View security issues for:
- All files in the repository (default)
- A specific file to focus on particular areas

### Comparing Analysis Runs

Track your security improvements over time:

1. Open the Score tab
2. Use the "Compare" dropdown in the top-right
3. Select a previous analysis run
4. The radar chart will overlay both analyses
5. See at a glance which areas improved or declined

## Understanding Security Issues

### Severity Levels

Issues are categorized by severity:

**Critical**: Immediate security risks that could lead to data breaches or system compromise. Address these first.

**High**: Serious vulnerabilities that should be fixed promptly to prevent exploitation.

**Medium**: Security weaknesses that should be addressed but don't pose immediate danger.

**Low**: Minor issues and best practice recommendations for long-term security improvements.

### Issue Details

Each security issue includes:

**Title**: Brief description of the vulnerability

**Description**: Detailed explanation of what the issue is and why it matters

**Code Snippet**: The exact code causing the security concern

**Line Number**: Where in the file the issue appears

**Affected Dimensions**: Which security categories this issue impacts (e.g., Input Validation, Cryptography)

**CWE ID**: Common Weakness Enumeration identifier for the vulnerability type

**OWASP Category**: Classification according to OWASP security standards

**Suggested Fix**: Recommended code changes to resolve the issue

## Fixing Security Issues

### Understanding Fix Options

For each security issue, you have two options:

**Automatic Fix**: Let AI generate and apply a fix automatically (when available)

**Manual Fix**: Review the suggested fix and implement it yourself in your code editor

### Using Automatic Fixes

To generate an automated fix:

1. Find the issue you want to fix in the Critical or Warnings tab
2. Click the "Fix Issue" button next to the vulnerability
3. A progress dialog appears showing the fix generation steps:
   - Analyzing the issue and surrounding code
   - Generating a secure code replacement
   - Creating a pull request with the fix
4. Wait for the process to complete

The system will:
- Analyze the vulnerable code in context
- Generate a secure replacement following best practices
- Create a new branch in your repository
- Open a pull request with the fix
- Provide a link to review the changes

### Reviewing Generated Fixes

After a fix is generated:

1. You'll receive a link to the pull request
2. Review the code changes carefully
3. Check that the fix doesn't break existing functionality
4. Run your tests to verify everything works
5. Merge the pull request when satisfied

**Important**: Always review automated fixes before merging. While AI-generated fixes follow security best practices, you should verify they work correctly in your specific context.

### When Automatic Fixes Aren't Available

Automatic fix generation may be unavailable if:
- The AI workflow hasn't been enabled for your workspace
- Your subscription plan doesn't include this feature
- The specific vulnerability type isn't supported for automatic fixing

In these cases:
1. Review the "Suggested Fix" section of the issue
2. Manually implement the recommended changes in your code editor
3. Test your changes thoroughly
4. Commit and push your fixes

### Tracking Fix Progress

Monitor all your fix attempts in the Fix History tab:

- See which issues have been addressed
- Check the status of each fix (successful, failed, or in progress)
- Access pull requests created for fixes
- Review any errors that occurred during fix generation

## Best Practices

### Regular Analysis Schedule

Run security analysis:
- After significant code changes
- Before major releases
- Weekly or monthly as part of your development cycle
- When adding new features that handle sensitive data

### Prioritizing Fixes

Address security issues in this order:

1. **Critical vulnerabilities first**: These pose immediate risks
2. **High severity issues next**: Prevent potential exploits
3. **Medium severity warnings**: Improve overall security
4. **Low severity items**: Enhance long-term security posture

### File-Level Focus

When you have many issues:
1. Use the file filter to focus on one file at a time
2. Fix all issues in that file before moving to the next
3. This prevents overwhelming yourself and ensures thorough fixes

### Comparing Progress

Use the comparison feature to:
- Verify your security improvements over time
- Identify areas that may have regressed
- Demonstrate security progress to stakeholders
- Guide future security efforts

### Team Collaboration

Share security results with your team:
- Review critical issues together
- Assign fixes to appropriate team members
- Discuss complex vulnerabilities before implementing fixes
- Use pull requests to get peer review on security fixes

## Troubleshooting

### No Analysis Results Appear

If your analysis doesn't show results:
- Verify Orchestrai is enabled on the repository
- Check that the analysis completed successfully
- Refresh the page to load the latest data
- Ensure the repository contains analyzable code files

### Analysis Takes Too Long

If analysis seems stuck:
- Continue the analysis in the background
- Check back after 10-15 minutes
- Large repositories naturally take longer to analyze
- Complex codebases may require extended processing time

### Can't Generate Fixes

If the Fix button is disabled:
- Verify your subscription includes this feature
- Check that AI workflows are enabled for your workspace
- Contact support if the feature should be available

### Fix Generation Fails

If a fix attempt fails:
- Review the error message in Fix History
- The issue may be too complex for automated fixing
- Try manually implementing the suggested fix instead
- Report persistent failures to support

## Getting Help

If you encounter issues or have questions:
- Review the suggested fixes provided for each vulnerability
- Consult your team's security experts for complex issues
- Check the Fix History for patterns in successful fixes
- Contact support for technical assistance with the analysis system