# Complete Code Quality Analysis Tutorial

## Overview

This tutorial walks you through performing a complete code quality analysis of your repository using AI-powered assessment. You'll learn how to start an analysis, monitor its progress, interpret results across multiple quality dimensions, and take action on identified issues.

## What You'll Learn

- How to initiate a comprehensive code quality assessment
- Understanding the multi-phase analysis process
- Interpreting quality scores across six key dimensions
- Reviewing critical issues and warnings
- Generating automated fixes for code quality problems
- Comparing analyses over time to track improvements

## Prerequisites

Before starting this tutorial, you should have:

- A workspace created with an active subscription
- At least one repository connected to the platform
- Repository access enabled for code analysis
- Sufficient credits in your workspace account

## Step 1: Navigate to Code Quality

1. From the main Dashboard, locate the **Code Quality** section
2. Click to open the Code Quality page
3. You'll see a list of all repositories that have analysis enabled

If you don't see any repositories listed, you'll need to enable analysis on your repositories first by visiting the Code section and toggling on repository access.

## Step 2: Start a New Analysis

### Initiating the Analysis

1. Locate your target repository in the recent analyses table
2. Click the **Analyze** button next to the repository name
3. A progress dialog will appear showing the analysis configuration

The analysis automatically uses the most advanced AI model available and processes your entire repository structure.

### Understanding the Configuration

When the analysis starts, you'll see:

- **Repository Name**: The repository being analyzed
- **Analysis Type**: Code Quality Assessment
- **AI Model**: The Claude model being used (typically Claude Haiku or Sonnet)
- **Processing Mode**: Either Batch (for larger repositories) or Sync (for smaller ones)
- **Analysis ID**: A unique identifier for tracking this specific analysis

## Step 3: Monitor Analysis Progress

The analysis proceeds through four distinct phases. You can monitor progress in real-time through the progress dialog.

### Phase 0: Connectivity Check

**What's Happening**: The system verifies it can connect to your Git provider and access the repository.

**Status Indicators**:
- Connecting icon (spinning): Authentication in progress
- Green checkmark: Successfully connected
- Red alert: Connection failed - check repository permissions

**Typical Duration**: 5-15 seconds

### Phase 1: Analyzing Repository

**What's Happening**: AI examines your entire codebase structure and creates an analysis plan, dividing your code into logical chunks for thorough evaluation.

**Status Indicators**:
- Brain icon (spinning): Scanning codebase
- Green checkmark: Analysis plan created
- Chunk count displayed (e.g., "Found 8 quality chunks to analyze")

**What to Expect**: The AI identifies all analyzable code files and groups them into manageable chunks based on file relationships and dependencies.

**Typical Duration**: 30 seconds to 2 minutes

### Phase 2: Running Quality Analysis

This is the most detailed phase where AI performs deep analysis on each chunk of code.

**What's Happening**: 
- Each code chunk is evaluated against six quality dimensions
- Issues are identified with specific line numbers
- Improvement suggestions are generated
- Quality scores are calculated

**Progress Tracking**:
- Overall progress bar showing percentage complete
- Real-time count: "X / Y chunks analyzed"
- Current chunk being processed with its name
- Elapsed time and estimated remaining time
- Status breakdown: done, running, pending, failed

**Batch Status**:
- **Batch Queued**: Analysis submitted to AI service, waiting to start
- **Processing**: Active analysis in progress
- **Done**: Chunk successfully completed
- **Running**: Currently being analyzed
- **Pending**: Waiting in queue
- **Failed**: Analysis encountered an error (can be retried)

**Typical Duration**: 3-15 minutes depending on repository size

**Monitoring Tips**:
- The "Check batch status" button lets you manually refresh progress
- Processing continues even if you close the dialog
- Failed chunks can be retried without restarting the entire analysis
- Stuck chunks (no progress for 5+ minutes) can be reset and retried

### Phase 3: Generating Quality Report

**What's Happening**: All individual chunk analyses are compiled into a comprehensive quality report with overall scores and actionable insights.

**Status Indicators**:
- Spinning icon: Compiling findings
- Green checkmark: Report ready to view

**Typical Duration**: 10-30 seconds

## Step 4: View Analysis Results

Once the analysis completes, click **View Results** to see your quality assessment.

### Results Page Overview

The results page provides multiple ways to explore your code quality:

**Filter Controls** (at the top):
- **Repository**: Switch between different analyzed repositories
- **Run**: Select from historical analyses to compare over time
- **Files**: View all files together or drill down into individual files

**View Tabs**:
- Score: Visual quality metrics across all dimensions
- Summary: Overall assessment narrative
- Critical: Issues requiring immediate attention
- Warnings: Areas for improvement
- Fix History: Track of automated fixes generated

## Step 5: Interpret Quality Scores

### The Six Quality Dimensions

Each dimension is scored from 0-100, with color-coded ratings:

**Readability (80-100: Good | 60-79: Needs Improvement | 0-59: Poor)**
- How easy is the code to understand?
- Are variable and function names clear?
- Is the code structure logical?
- Is commenting appropriate and helpful?

**Maintainability (80-100: Good | 60-79: Needs Improvement | 0-59: Poor)**
- How easy is the code to modify?
- Is complexity manageable?
- Are functions reasonably sized?
- Is there proper separation of concerns?

**Reliability (80-100: Good | 60-79: Needs Improvement | 0-59: Poor)**
- Does the code handle errors properly?
- Are edge cases considered?
- Is null/undefined checking adequate?
- Are assumptions validated?

**Security (80-100: Good | 60-79: Needs Improvement | 0-59: Poor)**
- Are inputs properly validated?
- Are secrets hardcoded?
- Are security best practices followed?
- Are vulnerabilities present?

**Efficiency (80-100: Good | 60-79: Needs Improvement | 0-59: Poor)**
- Are algorithms optimized?
- Is resource usage appropriate?
- Are there performance bottlenecks?
- Is unnecessary processing avoided?

**Testability (80-100: Good | 60-79: Needs Improvement | 0-59: Poor)**
- Can the code be easily tested?
- Are dependencies injectable?
- Is the code modular?
- Are side effects minimized?

### Visual Quality Representation

The **Score** tab displays a radar chart showing all six dimensions simultaneously. This allows you to quickly identify:

- **Strong Areas**: Dimensions with high scores extending outward
- **Weak Areas**: Dimensions with low scores closer to center
- **Balance**: Whether quality is consistent or uneven across dimensions

**Reading the Radar Chart**:
- Each axis represents one quality dimension
- The shaded area shows your current scores
- Larger area = better overall quality
- Uneven shapes indicate specific areas needing attention

### Comparing Across Runs

Use the **Compare** dropdown to overlay previous analysis results:

1. Select a past analysis from the dropdown
2. The comparison appears as a second shaded area on the radar chart
3. Quickly see if scores improved, declined, or stayed consistent
4. Track the impact of code improvements over time

## Step 6: Review the Summary

Navigate to the **Summary** tab for a comprehensive assessment written by AI.

**What You'll Find**:
- **Overall Score**: Single number (0-100) representing aggregate quality
- **Summary Text**: Narrative explanation of findings including:
  - Key strengths of the codebase
  - Primary areas of concern
  - Specific patterns identified
  - Recommendations for improvement

**Interpreting Overall Scores**:
- **80-100** (Green badge): Excellent quality - minimal issues
- **60-79** (Yellow badge): Acceptable quality - moderate improvements needed
- **0-59** (Red badge): Poor quality - significant refactoring recommended

## Step 7: Address Critical Issues

The **Critical** tab lists problems requiring immediate attention.

### Understanding Critical Issues

Each critical issue includes:

**Issue Header**:
- Title summarizing the problem
- Red alert icon indicating severity
- Affected quality dimensions (e.g., "Security, Reliability")

**Issue Details**:
- Detailed description explaining why this is critical
- Specific location: file path and line number
- Code snippet showing the problematic code
- Clear explanation of potential consequences

**Suggested Fix**:
- Recommended solution approach
- Code examples where applicable
- Best practices to follow

### Example Critical Issue

```
Title: Unvalidated User Input Leading to Potential Injection
Location: src/api/userController.ts:45
Affected Dimensions: Security, Reliability

Description: User-provided input is directly concatenated into a database 
query without validation or sanitization, creating a critical SQL injection 
vulnerability.

Code Snippet:
const query = `SELECT * FROM users WHERE username = '${req.body.username}'`;

Suggested Fix: Use parameterized queries or an ORM with built-in protection:
const query = 'SELECT * FROM users WHERE username = ?';
db.query(query, [req.body.username]);
```

## Step 8: Review Warnings

The **Warnings** tab shows areas for improvement that aren't immediately critical but should be addressed to maintain code quality.

### Types of Warnings

**Code Smells**:
- Duplicated code blocks
- Overly complex functions
- Dead code
- Inconsistent naming conventions

**Best Practice Violations**:
- Missing error handling
- Inadequate documentation
- Inconsistent formatting
- Poor separation of concerns

**Maintainability Issues**:
- Large functions needing decomposition
- High cyclomatic complexity
- Tight coupling between components
- Insufficient modularity

Each warning includes the same detailed information as critical issues but with lower urgency.

## Step 9: Generate Automated Fixes

For many issues, the platform can automatically generate code fixes.

### Using the Fix Generator

1. **Select an Issue**: In either the Critical or Warnings tab, find an issue you want to fix
2. **Click Fix Issue**: Look for the "Fix Issue" button on the issue card
3. **Monitor Generation**: A progress dialog shows the AI creating your fix
4. **Review the Fix**: Once complete, you'll see:
   - The proposed code changes
   - Files that will be modified
   - Explanation of what the fix accomplishes

### Fix Generation Process

**Phase 1: Analysis**
- AI reviews the issue in full context
- Related code is examined
- Best solution approach is determined

**Phase 2: Code Generation**
- Fix is written following project conventions
- Changes are validated for syntax
- Multiple files updated if necessary

**Phase 3: Pull Request Creation**
- Branch created with descriptive name
- Changes committed with clear message
- Pull request opened with detailed description
- Link provided to review on your Git platform

### Reviewing Generated Fixes

**Important**: Always review AI-generated fixes before merging:

1. Click the pull request link to open it on GitHub/GitLab
2. Review all changed files carefully
3. Check that the fix solves the problem without introducing new issues
4. Verify tests still pass
5. Merge when satisfied or request adjustments

## Step 10: Analyze Individual Files

For deeper investigation, switch from "All" to a specific file in the Files dropdown.

### File-Level Analysis

**Score Tab**: Shows the radar chart for just that file's six quality dimensions

**Summary Tab**: Provides:
- File-specific quality score
- Detailed analysis of that file's code
- "View Detailed Notes & Insights" button for comprehensive breakdown

**Critical/Warnings Tabs**: Filtered to show only issues in the selected file

### Detailed File Insights

Click "View Detailed Notes & Insights" to open a comprehensive dialog with:

**Overview Tab**:
- Overall quality score with color-coded badge
- Issue counts (critical vs warnings)
- Individual dimension scores with progress bars
- Visual quality assessment

**Issues Tab**:
- All critical issues and warnings for this file
- Organized by severity
- Fully detailed with code snippets and fixes

**Full Report Tab**:
- Complete AI-generated analysis text
- Comprehensive discussion of file quality
- Contextual recommendations

## Step 11: Track Fix History

The **Fix History** tab shows all automated fixes generated for quality issues.

### Fix History Table

Displays:
- **Issue**: Title of the problem that was fixed
- **Status**: Current state of the fix (Pending, Completed, Failed)
- **Pull Request**: Link to the PR if created
- **Generated**: Timestamp of fix creation

**Status Indicators**:
- **Completed** (Green): Fix successfully generated and PR created
- **Pending** (Yellow): Fix generation in progress
- **Failed** (Red): Fix generation encountered an error

### Filtering Fix History

When viewing a specific file, the Fix History tab automatically filters to show only fixes for issues in that file. Switch back to "All" to see fixes across your entire repository.

## Step 12: Compare Historical Analyses

Track quality improvements over time by comparing multiple analysis runs.

### Setting Up Comparison

1. Select your target repository
2. Choose your current analysis from the Run dropdown
3. In the Score tab, use the **Compare** dropdown
4. Select a previous analysis to compare against

### Interpreting Comparisons

**Visual Comparison**:
- Current run shown in one color (typically blue)
- Comparison run shown in another color (typically orange)
- Overlapping areas show similar scores
- Non-overlapping areas show improvements or declines

**Score Changes**:
- Larger current area = overall improvement
- Smaller current area = quality has declined
- Similar sizes = quality maintained

**Dimension-Specific Changes**:
- Look at each axis individually
- Identify which dimensions improved most
- Spot dimensions that need more attention

## Step 13: Sharing Results

Share analysis results with team members or stakeholders.

### How to Share

1. Click the **Share** button at the top of the results page
2. A shareable link is generated automatically
3. Copy the link to share via email, chat, or documentation
4. Recipients can view the full analysis without needing an account

### What's Shared

The shared link includes:
- Repository name and analysis date
- Overall quality score
- Critical issue count
- Warning count
- Summary text
- Complete access to all tabs and detailed results

**Privacy Note**: Shared links are public - anyone with the link can view the results. Only share with trusted parties.

## Step 14: Continue Analysis in Background

For large repositories with lengthy analyses, you don't need to keep the progress dialog open.

### Background Processing

1. Click **Continue in Background** in the progress dialog
2. The analysis continues processing on the server
3. You can navigate to other parts of the platform
4. Return to the Code Quality page to check progress
5. View results when complete

**Progress Indicator**: Active analyses show a status indicator in the recent analyses table.

## Step 15: Handle Analysis Issues

Sometimes analyses may encounter problems. Here's how to resolve them.

### Stuck Chunks

**Symptom**: A chunk shows "processing" for more than 5 minutes with no progress

**Resolution**:
1. A warning appears: "X chunks appear stuck"
2. Click the **Retry** button in the warning
3. Stuck chunks are reset and reprocessed
4. Analysis continues normally

### Failed Chunks

**Symptom**: One or more chunks show "failed" status

**Causes**:
- Temporary API issues
- Rate limiting
- Invalid code format
- Extremely large files

**Resolution**:
1. Analysis completes with note: "Analysis completed with X failed chunks"
2. Click **Retry Failed** button
3. Only failed chunks are reprocessed
4. New results integrate with existing successful chunks

### Pending Retry Banner

**What It Means**: Some files couldn't be analyzed due to GitHub API rate limits and are queued for automatic retry within the next hour.

**What to Do**: 
- No action required - retries happen automatically
- Current results are still valid
- Check back later for complete analysis
- Refreshing the page shows updated status

## Best Practices

### Regular Analysis Schedule

- **Daily**: For active development projects
- **Weekly**: For stable codebases with regular updates
- **Before Major Releases**: To catch quality regressions
- **After Large Refactors**: To verify improvements

### Prioritizing Issues

1. **First**: Address all critical security issues
2. **Second**: Fix critical reliability problems
3. **Third**: Improve poor-scoring dimensions (under 60)
4. **Fourth**: Address warnings in frequently modified files
5. **Fifth**: General code quality improvements

### Using Comparisons Effectively

- Establish a baseline with your first analysis
- Compare each new analysis to the baseline
- Set quality score targets for each dimension
- Track trends over multiple analyses
- Celebrate improvements with your team

### Integrating with Development Workflow

- Run analysis before pull request reviews
- Include quality scores in code review discussions
- Set minimum score requirements for merges
- Use automated fixes to speed up improvements
- Make quality metrics visible to the team

## Troubleshooting

### Analysis Won't Start

**Check**:
- Repository has analysis enabled
- Workspace has sufficient credits
- Repository connection is active
- You have appropriate permissions

### No Results Appearing

**Check**:
- Analysis completed successfully (no errors in Phase 3)
- Correct repository and run selected in filters
- Page refreshed after completion
- Browser console for errors

### Unexpected Low Scores

**Remember**:
- Scores reflect multiple factors across each dimension
- Legacy code often scores lower initially
- AI is conservative with quality assessment
- Low scores highlight improvement opportunities

### Fix Generation Not Available

**Possible Reasons**:
- Workflow not enabled in workspace settings
- Insufficient credits for fix generation
- Issue type not supported for automated fixes
- Repository permissions don't allow PR creation

## Example Walkthrough

Let's walk through analyzing a sample repository: "example-api"

**Step 1**: Open Code Quality page, locate "example-api" in the table

**Step 2**: Click **Analyze** button

**Step 3**: Progress dialog appears showing:
- Configuration: Claude Haiku model, Batch processing mode
- Phase 0 completes in 8 seconds (green checkmark)
- Phase 1 scans codebase, finds 12 quality chunks (1 minute)
- Phase 2 processes chunks:
  - Chunk 1/12: auth/loginController.ts (completed)
  - Chunk 2/12: auth/registerController.ts (completed)
  - Progress: 3/12 chunks (25%), 2 minutes elapsed, ~6 minutes remaining
  - All chunks complete after 8 minutes
- Phase 3 generates report (15 seconds)

**Step 4**: Click **View Results**

**Step 5**: Score tab shows:
- Overall: 68/100 (yellow - needs improvement)
- Readability: 75/100
- Maintainability: 62/100
- Reliability: 58/100 (red - concerning)
- Security: 71/100
- Efficiency: 80/100
- Testability: 65/100

**Step 6**: Summary tab states: "The codebase demonstrates moderate quality with particular concerns around reliability and maintainability. Error handling is inconsistent, and several functions exceed recommended complexity thresholds."

**Step 7**: Critical tab shows 3 issues:
1. "Missing Input Validation in User Registration" (Security, Reliability)
2. "Unhandled Promise Rejection in Database Query" (Reliability)
3. "Hardcoded API Keys in Configuration File" (Security)

**Step 8**: Select issue #3, click **Fix Issue**

**Step 9**: Fix generates in 45 seconds, PR created: "fix: move API keys to environment variables"

**Step 10**: Review PR on GitHub, merge after verification

**Step 11**: Run new analysis next day, compare to previous run

**Step 12**: Results show Security improved from 71 to 85, Critical issues reduced from 3 to 2

## Next Steps

After completing your first analysis:

1. **Set Quality Goals**: Decide target scores for each dimension
2. **Create Action Plan**: Prioritize which issues to address first
3. **Schedule Regular Runs**: Establish cadence for ongoing analysis
4. **Integrate with CI/CD**: Consider running analyses on key branches
5. **Share with Team**: Make quality metrics visible to all developers
6. **Track Progress**: Use comparisons to demonstrate improvements
7. **Celebrate Wins**: Recognize quality improvements in team meetings

## Summary

You now know how to:

- Start a comprehensive code quality analysis on any repository
- Monitor the multi-phase analysis process from start to finish
- Interpret quality scores across six critical dimensions
- Review and prioritize critical issues and warnings
- Generate automated fixes for identified problems
- Compare analyses over time to track quality improvements
- Share results with team members and stakeholders
- Handle common issues like stuck or failed chunks
- Integrate quality analysis into your development workflow

Regular code quality analysis helps maintain healthy, maintainable codebases and prevents technical debt accumulation. Use this tool proactively to keep your code in excellent condition.