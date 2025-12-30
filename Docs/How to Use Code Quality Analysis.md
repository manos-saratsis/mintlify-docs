# How to Use Code Quality Analysis

## Overview

Code Quality Analysis helps you continuously improve your codebase by providing AI-powered insights into maintainability, efficiency, and best practices. Get comprehensive scoring across six quality dimensions with actionable recommendations for every file in your repository.

## Getting Started

### Prerequisites

Before using Code Quality Analysis, ensure you have:

1. **A workspace selected** - Choose your workspace from the top navigation bar
2. **Repository enabled** - At least one repository must have OrchestrAI enabled
3. **GitHub connection** - Your GitHub account must be connected

If you don't see any repositories, navigate to the Code page to enable OrchestrAI on your repositories.

## Running Your First Analysis

### Step 1: Access Code Quality

From your product dashboard, select **Code Quality Analyses** from the navigation menu. You'll see a list of all repositories that have OrchestrAI enabled.

### Step 2: Start an Analysis

1. Locate the repository you want to analyze in the repository table
2. Click the **Analyze** button next to the repository name
3. The analysis will begin processing your code

### Step 3: Monitor Progress

Once started, the analysis runs in the background. You can:

- **Continue working** - Navigate to other pages while the analysis runs
- **Check progress** - Return to the Code Quality page to see the current status
- **Resume tracking** - If you navigate away, the analysis continues and you can check back later

Analysis typically takes a few minutes depending on your repository size.

## Understanding Quality Scores

### The Six Quality Dimensions

Every file in your codebase receives scores across six dimensions:

1. **Readability** - How easy is the code to understand?
2. **Maintainability** - How simple is it to modify and extend?
3. **Reliability** - How dependable and error-resistant is the code?
4. **Security** - Are there potential security vulnerabilities?
5. **Efficiency** - How optimized is the performance?
6. **Testability** - How easy is it to write and maintain tests?

Each dimension is scored from 0-100, with higher scores indicating better quality.

### Score Interpretation

- **80-100**: Excellent - Code meets high-quality standards
- **60-79**: Good - Minor improvements recommended
- **Below 60**: Needs Attention - Significant improvements suggested

## Viewing Analysis Results

### Navigate to Results

After an analysis completes:

1. Click the **Analysis Results** button at the top of the Code Quality page, or
2. Click **View Results** next to a specific repository

### Select Your View

At the top of the results page, use the filter dropdowns to choose:

- **Repository** - Which codebase to examine
- **Run** - Which analysis session to view (displays by date/time)
- **Files** - View all files together or focus on a specific file

### Understanding the Interface

Results are organized into tabs:

#### Score Tab

Displays a radar chart showing quality scores across all six dimensions. The chart provides:

- **Visual comparison** - See which areas are strong and which need work
- **Run comparison** - Select a previous analysis run to compare scores over time
- **Aggregate view** - When viewing "All" files, see average scores across your entire codebase
- **File-specific view** - When selecting a specific file, see scores for just that file

#### Summary Tab

Provides a comprehensive written assessment including:

- **Overall score** - A single quality rating for the selected scope
- **Key findings** - High-level insights about code quality
- **Context** - Understanding what the scores mean for your specific codebase

#### Critical Tab

Lists issues requiring immediate attention:

- **Problem description** - What the issue is and why it matters
- **Location details** - Specific file paths and line numbers
- **Affected dimensions** - Which quality areas are impacted
- **Code snippets** - Examples of problematic code
- **Suggested fixes** - Recommended solutions

#### Warnings Tab

Shows areas for improvement that are important but not urgent:

- **Improvement opportunities** - Code that could be enhanced
- **Best practice deviations** - Where standards aren't being followed
- **Recommendations** - How to address each warning

#### Fix History Tab

Tracks all automated fix attempts for quality issues, showing what has been addressed and the outcomes.

## Working with File-Level Results

### Viewing Individual Files

1. Use the **Files** dropdown to select a specific file
2. All tabs now show data for only that file
3. The radar chart updates to show file-specific scores

### Detailed File Analysis

When viewing a specific file on the Summary tab:

1. Review the file score and written assessment
2. Click **View Detailed Notes & Insights** to see:
   - In-depth quality breakdown
   - Specific code examples
   - Line-by-line recommendations
   - Prioritized action items

## Comparing Analysis Runs

### Track Improvement Over Time

1. Navigate to the Score tab
2. Use the **Compare** dropdown in the top-right
3. Select a previous analysis run

The radar chart now shows two overlapping shapes:
- **Selected run** (primary color) - Your current analysis
- **Comparison run** (secondary color) - The previous analysis

### What to Look For

- **Expanding areas** - Dimensions where scores improved
- **Shrinking areas** - Dimensions where scores declined
- **Overall trend** - Is quality improving across analyses?

## Taking Action on Findings

### Prioritize Issues

Start with the Critical tab to address high-impact problems first, then move to Warnings for incremental improvements.

### Implement Recommendations

For each issue:

1. Review the **description** to understand the problem
2. Check the **code snippet** to see the specific code
3. Follow the **suggested fix** guidance
4. Reference the **line number** to locate the issue in your editor

### Generate Automated Fixes

When viewing critical issues or warnings, you can request automated fixes:

1. Locate the issue you want to address
2. Click the **Fix Issue** button (if available)
3. The system generates a code fix and creates a pull request
4. Review the fix in GitHub and merge when satisfied

### Re-run Analysis

After making improvements:

1. Return to the Code Quality page
2. Click **Analyze** on the same repository
3. Compare the new results with previous runs to measure progress

## Sharing Results

### Share with Your Team

1. Click the **Share** button at the top of the results page
2. Copy the provided URL
3. Share with team members who have access to your workspace

Shared links include:
- The specific repository
- The exact analysis run
- The currently selected file view

Anyone with workspace access can view the shared results.

## Best Practices

### Regular Analysis

- **Run analyses frequently** - After major changes or weekly
- **Track trends** - Use comparison features to monitor progress
- **Set quality goals** - Aim for consistent score improvements

### Team Collaboration

- **Review together** - Discuss critical issues in team meetings
- **Assign ownership** - Designate team members to address specific issues
- **Share insights** - Use the share feature to highlight important findings

### Continuous Improvement

- **Address high-impact items first** - Focus on critical issues before warnings
- **Celebrate wins** - Acknowledge when scores improve
- **Learn from patterns** - If similar issues appear across files, update your coding standards

## Troubleshooting

### No Repositories Available

If you see "No Orchestrai Enabled Repositories":
- Navigate to the Code page
- Enable OrchestrAI on at least one repository
- Return to Code Quality Analyses

### Analysis Not Starting

If clicking Analyze doesn't start an analysis:
- Verify you have a workspace selected
- Check that the repository is still enabled
- Try refreshing the page

### Missing Results

If completed analyses don't show results:
- Use the **Run** dropdown to select the correct analysis session
- Verify the analysis status shows "completed"
- Check that you have the correct repository selected

### Background Analysis

If you navigate away during an analysis:
- The analysis continues running
- Return to Code Quality Analyses to check progress
- Any URL parameters for resuming are automatically handled

## Understanding the Repository Table

On the main Code Quality page, the repository table shows:

- **Repository name** - Your GitHub repository
- **Last analysis** - Date and time of the most recent completed analysis
- **Status** - Current state (completed, processing, or no analysis)
- **Actions** - Analyze button to start new analyses

Active analyses display progress indicators that update in real-time.