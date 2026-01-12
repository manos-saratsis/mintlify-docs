# Running Your First Analysis

## Overview

After connecting your repository, you can run your first code analysis to identify quality issues, security vulnerabilities, compliance gaps, and more. This guide walks you through the complete process of starting an analysis, monitoring its progress, and understanding the results.

## Before You Start

To run your first analysis, you need:

1. **A connected Git account** - Link your GitHub, GitLab, or other Git provider
2. **At least one enabled repository** - Turn on OrchestrAI for the repositories you want to analyze
3. **Available credits** - Ensure your workspace has sufficient credits for analysis

If you haven't completed these steps, visit the Dashboard and follow the setup prompts.

## Choosing an Analysis Type

OrchestrAI offers six types of analysis to improve your code's production readiness:

### Code Quality Analysis
Analyzes your codebase for maintainability, efficiency, and best practices. Provides:
- **Quality Metrics** - Overall scores for maintainability, readability, and testability
- **Best Practices** - Identifies deviations from coding standards and design patterns
- **Improvement Suggestions** - Actionable recommendations to enhance code quality

**Best for:** Teams looking to improve code maintainability and reduce technical debt.

### Code Security Analysis
Scans for security vulnerabilities and provides remediation advice. Detects:
- Security vulnerabilities in your code
- Unsafe coding patterns
- Dependency vulnerabilities
- Configuration security issues

**Best for:** Securing applications before deployment and meeting security compliance requirements.

### Compliance Analysis
Checks code against regulatory requirements and compliance standards:
- Industry-specific compliance checks
- Regulatory requirement verification
- Policy adherence validation

**Best for:** Projects that must meet specific regulatory or industry standards.

### Unit Testing
Generates comprehensive test coverage for your codebase:
- Automatically creates unit tests
- Identifies untested code paths
- Ensures reliability and catches bugs early

**Best for:** Projects needing improved test coverage and reliability.

### Documentation
Creates and maintains comprehensive documentation:
- Generates code documentation
- Creates user guides
- Documents API endpoints and usage

**Best for:** Projects requiring clear documentation for maintainers and users.

### Instrumentation
Adds observability and monitoring capabilities:
- Implements logging
- Adds performance monitoring
- Integrates tracing capabilities

**Best for:** Production applications requiring observability and performance tracking.

## Starting Your First Analysis

### Step 1: Navigate to the Analysis Page

1. From the Dashboard, locate the analysis type cards
2. Click on the card for the analysis type you want to run (e.g., "Code Quality")
3. You'll be taken to the analysis page for that specific type

### Step 2: Select a Repository

On the analysis page, you'll see a table showing all your enabled repositories with columns for:
- **Repository Name** - The name of your repository
- **Last Analysis** - When the repository was last analyzed (if applicable)
- **Status** - Current analysis status
- **Actions** - Options to start a new analysis

### Step 3: Start the Analysis

1. Locate the repository you want to analyze in the table
2. Click the **"Start Analysis"** or **"Run Analysis"** button for that repository
3. A progress dialog will open immediately, showing real-time analysis progress

## Understanding the Analysis Process

When you start an analysis, OrchestrAI follows a multi-phase process. The progress dialog shows detailed information about each phase.

### Phase 0: Connectivity Check
**Duration:** A few seconds

The system verifies connection to your Git provider and authenticates access to your repository. You'll see:
- "Connecting to Git provider..." while checking
- "Git provider authenticated" when successful

### Phase 1: Analyzing Repository
**Duration:** 1-3 minutes for most repositories

AI scans your codebase structure and creates an analysis plan:
- Reviews repository structure
- Identifies files to analyze
- Divides work into manageable chunks
- Determines optimal processing strategy

You'll see messages like "Scanning codebase structure and creating analysis plan..." during this phase.

### Phase 2: Running Analysis
**Duration:** 5-30 minutes depending on repository size

This is the main analysis phase where AI examines your code in detail:

**What You'll See:**
- **Progress bar** showing percentage complete
- **Elapsed time** since analysis started
- **Estimated time remaining** until completion
- **Files analyzed** counter (e.g., "15 / 42 chunks analyzed")
- **Current activity** showing which file or chunk is being processed

**Real-time Updates:**
- The progress dialog updates every few seconds
- You can see exactly which file is being analyzed
- A spinning indicator shows active processing
- Status counts show: completed, running, pending, and failed chunks

**Batch Processing:**
When analyzing large repositories, you'll see "AI is analyzing X files..." with a progress indicator showing the batch processing status.

### Phase 3: Generating Report
**Duration:** 30 seconds - 2 minutes

The system compiles all findings into a comprehensive report:
- Aggregates all analysis results
- Calculates overall scores
- Generates recommendations
- Prepares visualization data

You'll see "Compiling findings into report..." during this final phase.

## Monitoring Analysis Progress

### Progress Indicators

The progress dialog provides detailed visibility:

**Overall Progress Bar:**
- Shows percentage of analysis complete
- Updates in real-time as files are processed
- Turns green when analysis completes successfully

**Status Badges:**
- **Completed** (green) - Successfully analyzed chunks
- **Running** (blue, animated) - Currently processing
- **Pending** (gray) - Waiting to be processed
- **Failed** (red) - Encountered errors

**Time Tracking:**
- **Elapsed Time** - How long the analysis has been running
- **Estimated Remaining** - Approximate time until completion
- **Time Format** - Displays as minutes and seconds (e.g., "5m 23s")

### Chunk Details

For larger analyses, you'll see individual chunks listed:
- Each chunk represents a portion of your codebase
- Click to expand and see which files are in each chunk
- Status icons show the state of each chunk
- Scores appear for completed chunks

## Handling Long-Running Analyses

For large repositories, analysis may take 20-30 minutes or longer.

### Continue in Background

You don't need to keep the progress dialog open:

1. Click **"Continue in Background"** button at the bottom of the dialog
2. The analysis continues running on the server
3. You can navigate to other pages or close your browser
4. Return later to check results

**Important:** The analysis will complete even if you close the dialog or browser.

### Resume Monitoring

To check on a background analysis:

1. Return to the analysis page (e.g., "Code Quality")
2. Find your repository in the table
3. The status column shows "Running" with a progress indicator
4. Click **"View Progress"** to reopen the progress dialog
5. The dialog shows current status and picks up where you left off

## Handling Issues During Analysis

### Failed Chunks

If some chunks fail during analysis:

**What Happens:**
- Analysis continues processing remaining chunks
- Failed chunks are marked in red with error indicators
- Overall analysis still completes, but with warnings

**Resolution:**
1. The dialog shows how many chunks failed
2. Click **"Retry Failed"** button to reprocess failed chunks
3. Failed chunks are reset and reprocessed
4. Progress dialog updates to show retry in progress

### Stuck Chunks

Occasionally, chunks may appear stuck (no updates for 5+ minutes):

**Detection:**
- System automatically detects stuck chunks
- Warning appears: "X chunks appear stuck"
- Message explains: "No heartbeat for 5+ minutes"

**Resolution:**
1. Click **"Retry"** button next to the stuck chunk warning
2. Stuck chunks are automatically reset
3. Processing resumes for those chunks

### Complete Analysis Failures

If the entire analysis fails:

**Common Causes:**
- Network connectivity issues
- Repository access problems
- Invalid repository structure
- Insufficient credits

**What You'll See:**
- Red error message in the progress dialog
- Description of what went wrong
- Suggestions for resolution

**Next Steps:**
1. Review the error message
2. Address the underlying issue
3. Click **"Close"** to dismiss the dialog
4. Start a new analysis once the issue is resolved

## Viewing Results

### Successful Completion

When analysis completes successfully:

1. Progress dialog shows green success message: "Analysis completed successfully!"
2. All phases show green checkmarks
3. Click **"View Results"** button to see findings

### Partial Success

If analysis completes with some failed chunks:

1. Message shows: "Analysis completed with X failed chunks"
2. Click **"View Results"** to see findings from successful chunks
3. Optionally click **"Retry Failed"** to reprocess failed portions
4. Results include data from all successfully analyzed chunks

### Navigating to Results

After clicking "View Results":

1. You're taken to the results page for your analysis type
2. The page displays:
   - **Overall Score** - Numeric rating of your codebase (0-100)
   - **Issue Counts** - Number of critical, warning, and info-level findings
   - **Issue List** - Detailed list of all identified issues
   - **Recommendations** - AI-generated suggestions for improvement
   - **Trends** - Comparison with previous analyses (if available)

## Understanding Analysis Results

### Quality Scores

Each analysis type provides an overall score:

- **90-100** - Excellent quality, minimal issues
- **70-89** - Good quality, some improvements possible
- **50-69** - Moderate quality, several issues to address
- **Below 50** - Needs significant improvement

### Issue Severity Levels

Issues are categorized by severity:

**Critical (Red):**
- Must be addressed immediately
- Can cause security vulnerabilities or major failures
- Examples: SQL injection risks, exposed secrets, critical logic errors

**Warning (Yellow/Orange):**
- Should be addressed soon
- May cause problems or reduce code quality
- Examples: Code smells, inefficient patterns, minor security concerns

**Info (Blue):**
- Nice-to-have improvements
- Suggestions for better practices
- Examples: Style improvements, documentation suggestions

### Issue Details

Each issue includes:

1. **Location** - File path and line number
2. **Description** - Clear explanation of the problem
3. **Recommendation** - Specific steps to fix the issue
4. **Code Context** - Relevant code snippet showing the problem
5. **Severity Level** - Priority for addressing the issue

## Next Steps After Your First Analysis

### Review and Prioritize

1. Sort issues by severity to focus on critical problems first
2. Review recommendations for each issue
3. Create a plan to address findings systematically

### Take Action

For most analysis types, you can:
- Export results for team review
- Create tasks or tickets from findings
- Track remediation progress

For **Unit Testing**, the system can automatically:
- Generate test files
- Create a pull request with new tests
- Integrate tests into your repository

### Run Follow-Up Analyses

After making improvements:

1. Return to the analysis page
2. Run a new analysis on the same repository
3. Compare results to see improvement
4. Track progress over time

### Automate with Workflows

To continuously monitor code quality:

1. Navigate to the Workflow page from the Dashboard
2. Configure automated analysis triggers:
   - Run on every commit
   - Run on pull requests
   - Run on a schedule (daily, weekly)
3. Receive automatic notifications when issues are detected

## Tips for Successful Analysis

### Repository Preparation

**Ensure your repository is accessible:**
- OrchestrAI bot is installed and has proper permissions
- Repository is not archived or locked
- Default branch is set correctly

**Optimize for faster analysis:**
- Large repositories (1000+ files) take longer to analyze
- Consider starting with smaller repositories for your first analysis
- Exclude build artifacts and dependencies if possible

### Credit Management

**Monitor your usage:**
- Each analysis consumes credits based on repository size
- Check remaining credits before starting large analyses
- A banner appears if you're running low on credits

**Estimate costs:**
- Small repositories (< 100 files): 1-2 minutes, minimal credits
- Medium repositories (100-500 files): 5-10 minutes, moderate credits  
- Large repositories (500+ files): 20-30 minutes, significant credits

### Best Practices

**Start small:**
- Run your first analysis on a smaller repository
- Get familiar with the process and results
- Then move to larger, more complex projects

**Review regularly:**
- Run analyses periodically (weekly or monthly)
- Track improvements over time
- Catch issues early before they compound

**Act on findings:**
- Analysis is most valuable when you address issues
- Prioritize critical and warning-level problems
- Use recommendations as a learning tool

## Troubleshooting Common Issues

### "No enabled repositories" message

**Problem:** You see a message that no repositories are enabled.

**Solution:**
1. Click **"Manage Repositories"** button
2. Enable OrchestrAI for at least one repository
3. Return to the analysis page
4. Your enabled repositories will now appear

### Analysis won't start

**Problem:** Clicking "Start Analysis" doesn't begin processing.

**Possible causes:**
- Another analysis is already running on this repository
- Insufficient credits remaining
- Repository access issues

**Solutions:**
1. Wait for any existing analysis to complete
2. Check your credit balance in the Dashboard
3. Verify the OrchestrAI bot has repository access

### Progress dialog shows no updates

**Problem:** Progress appears frozen with no changes.

**Solution:**
1. Click the **"Refresh"** button (circular arrow icon) next to the time estimate
2. If still stuck after 5+ minutes, look for the stuck chunks warning
3. Click **"Retry"** to reset stuck chunks
4. Close and reopen the progress dialog to force a refresh

### Can't view completed results

**Problem:** Analysis completed but results aren't showing.

**Solution:**
1. From the analysis page, click **"View Results"** next to the repository
2. If the button isn't visible, check the status column
3. Refresh the page to ensure status is updated
4. Results may take a moment to fully generate after completion

## Getting Help

If you encounter issues not covered in this guide:

1. Check the status column for error messages
2. Review any error details in the progress dialog
3. Ensure your Git connection is active
4. Verify repository permissions
5. Contact support with your analysis ID (shown in the progress dialog)

---

**Congratulations!** You've now learned how to run your first code analysis. The same process applies to all analysis types - simply choose the analysis you need, select your repository, and monitor progress. Regular analysis helps maintain code quality and catch issues before they reach production.