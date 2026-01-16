# Run Your First Analysis

This guide walks you through running your first code quality analysis with OrchestrAI. You'll see how AI examines your codebase and provides actionable insights to improve code quality.

## What You'll Accomplish

By the end of this guide, you will:

- Start your first automated code quality analysis
- Monitor analysis progress in real-time
- View detailed quality scores across six key dimensions
- Understand the recommendations provided
- Know how to act on the results

## Prerequisites

Before running your first analysis, ensure you have:

- Connected at least one GitHub repository to OrchestrAI
- Enabled OrchestrAI on the repository you want to analyze
- Selected a workspace with available credits

If you haven't completed these steps, visit the Code Repositories page first to connect and enable your repositories.

## Starting Your First Analysis

### 1. Navigate to Code Quality

From the main dashboard, click on the **Code Quality** option in the sidebar. This is where all code quality analyses are managed and viewed.

### 2. View Your Enabled Repositories

You'll see a table titled "Recent Code Quality Analyses" that displays all repositories where OrchestrAI is enabled. Each repository shows:

- Repository name and full path
- Previous analysis results (if any)
- An **Analyze** button to start a new analysis

### 3. Start the Analysis

Click the **Analyze** button next to the repository you want to examine. This opens the AI Quality Engineer progress dialog, where you'll watch the analysis happen in real-time.

## Understanding the Analysis Process

Your analysis goes through four distinct phases. You can monitor each phase as it progresses.

### Phase 0: Connectivity Check

The system first verifies it can access your Git repository. This typically takes just a few seconds. You'll see:

- A connectivity check message
- Confirmation that your Git provider is authenticated

### Phase 1: Analyzing Repository

The AI scans your entire codebase to understand its structure. During this phase:

- The system examines all files and folders
- It creates an analysis plan based on your code structure
- You'll see the total number of code segments (chunks) identified for analysis

This phase shows which AI model is being used (typically Claude Haiku or Sonnet).

### Phase 2: Running Quality Analysis

This is the main analysis phase where your code is evaluated. You'll see:

- **Real-time progress**: A percentage showing how many code segments have been analyzed
- **Chunk status**: Individual progress for each part of your codebase
- **Estimated time**: How long until completion
- **Active processing**: Which segments are currently being analyzed

The progress bar updates continuously as each segment completes. Completed segments show a green checkmark, while segments being processed display a spinning indicator.

#### Monitoring Progress Details

The analysis breaks your codebase into manageable chunks. For each chunk, you can see:

- **Status**: Pending (gray), Processing (blue spinner), Completed (green check), or Failed (red alert)
- **Quality Score**: Once completed, each chunk shows its quality rating
- **Issue Counts**: Number of critical and warning items found

#### Handling Delays or Issues

If chunks appear stuck (no progress for 5+ minutes), you'll see a warning with a **Retry** button. Click this to restart stuck segments.

If any chunks fail, a **Retry Failed** button appears, allowing you to reprocess just those segments without starting over.

### Phase 3: Generating Quality Report

After all code segments are analyzed, the system compiles findings into your final report. This phase:

- Aggregates results from all analyzed segments
- Calculates overall quality scores
- Prepares actionable recommendations

### Analysis Complete

When finished, you'll see a success message. The analysis results are now ready to view.

## Viewing Your Analysis Results

### Access the Results Dashboard

Click **View Results** to see your comprehensive quality report. If you closed the progress dialog, navigate back to the Code Quality page and click **View Results** next to your repository.

### Understanding Quality Scores

Your code is evaluated across six key dimensions, each scored from 0-100:

**Readability** - How easy your code is to understand
- Clear variable and function names
- Logical code organization
- Appropriate use of comments
- Scores above 80 indicate well-structured, easy-to-read code

**Maintainability** - How easy it is to modify and update
- Code organization and modularity
- Consistency in coding patterns
- Documentation quality
- Higher scores mean easier future updates

**Reliability** - How dependable and error-resistant your code is
- Error handling practices
- Edge case coverage
- Code robustness
- Scores above 80 suggest stable, dependable code

**Security** - Protection against vulnerabilities
- Authentication and authorization practices
- Data validation and sanitization
- Security best practices compliance
- Higher scores indicate better security posture

**Efficiency** - Performance and resource usage
- Algorithm efficiency
- Memory usage patterns
- Optimization opportunities
- Better scores mean faster, more efficient execution

**Testability** - How easy it is to test your code
- Code structure for testing
- Dependency management
- Test coverage potential
- Higher scores enable more comprehensive testing

### Overall Quality Score

An aggregate score combining all six dimensions provides a quick health check of your entire codebase. This single number helps you track improvement over time.

### Color-Coded Results

Scores are color-coded for quick assessment:

- **Green (80-100)**: Excellent quality, minimal improvements needed
- **Yellow (60-79)**: Good quality with room for enhancement
- **Red (Below 60)**: Needs attention and improvement

## Exploring Detailed Findings

Click on any dimension score to view specific recommendations for that area.

### Reading the Notes

Each dimension includes detailed notes explaining:

- Specific issues found in your code
- Why each issue matters
- The impact on your codebase
- Priority level of each finding

### File-Level Details

The chunk-based breakdown shows quality scores for different parts of your codebase. This helps you:

- Identify which files or modules need the most attention
- Prioritize improvements based on severity
- Track progress as you make changes

## Taking Action on Results

### Prioritize Based on Scores

Start with the lowest-scoring dimensions:

1. Review dimensions scoring below 60 first
2. Address critical issues highlighted in red
3. Work through warning-level items
4. Enhance areas already performing well

### Focus on High-Impact Areas

The chunk scores help identify which parts of your codebase need immediate attention. Focus your efforts where:

- Multiple issues cluster together
- Critical functionality resides
- Scores are significantly below your target

### Implement Recommendations

Each finding includes guidance on how to improve:

- Read the specific recommendations provided
- Understand why each change matters
- Make incremental improvements
- Re-run analysis to measure progress

## Running Follow-Up Analyses

### Track Your Progress

After implementing improvements, run another analysis to see your progress:

1. Return to the Code Quality page
2. Click **Analyze** on the same repository
3. Compare new scores with previous results
4. Verify that issues have been resolved

### Establish a Routine

For best results, run analyses regularly:

- **After major changes**: Verify quality remains high
- **Before releases**: Catch issues early
- **Monthly reviews**: Track long-term trends
- **After onboarding**: Ensure new team members maintain standards

## Working in the Background

You don't need to watch the entire analysis complete.

### Continue in Background

Click **Continue in Background** to:

- Close the progress dialog
- Let analysis complete automatically
- Work on other tasks
- Check results later when ready

The analysis continues running even after closing the dialog. Return to the Code Quality page anytime to check if it's finished.

### Resume Monitoring

If an analysis is running in the background:

- The Code Quality page shows its current status
- Click the repository row to reopen the progress dialog
- Pick up watching exactly where you left off

## Understanding Credit Usage

Each analysis consumes credits from your workspace balance:

- Credit usage depends on codebase size
- Larger repositories require more credits
- The system estimates credit usage before starting

If you're low on credits, you'll see a banner notification. Contact your workspace administrator to add more credits.

## Troubleshooting Common Issues

### Analysis Appears Stuck

If progress stops for more than 5 minutes:

1. Look for the stuck chunks warning
2. Click the **Retry** button
3. The system resets and restarts stuck segments

### Some Chunks Failed

Occasional failures can happen due to network issues or complex code:

1. Check the failed chunk count
2. Click **Retry Failed** to reprocess only failed segments
3. Review any persistent failures for unusual code patterns

### Analysis Cancelled

If you cancel an analysis:

- Partial results are not saved
- Credits for completed segments are still consumed
- Start fresh with a new analysis when ready

### No Results Appearing

If results don't appear after completion:

1. Refresh the page
2. Verify the analysis shows as "completed" 
3. Check that you're viewing the correct repository

## Next Steps

Now that you've completed your first analysis:

1. **Review all dimension scores** - Understand your overall code quality
2. **Read detailed recommendations** - Learn what to improve
3. **Create an improvement plan** - Prioritize changes based on impact
4. **Make incremental changes** - Don't try to fix everything at once
5. **Run follow-up analysis** - Measure your progress
6. **Share results with your team** - Collaborate on quality improvements

Visit the Code Quality Results page anytime to review your analysis history and track improvements over time.