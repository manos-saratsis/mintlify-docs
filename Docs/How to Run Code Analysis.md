# How to Run Code Analysis

## Overview

Code Analysis helps you understand and improve your codebase by automatically evaluating code quality across multiple dimensions. The system analyzes your repositories and provides scores, detailed insights, and actionable recommendations to help you maintain high code standards.

## Getting Started

### Prerequisites

Before running code analysis, you need:

1. **Active Workspace**: Select a workspace from your account
2. **Connected Repository**: Link your GitHub, GitLab, or Bitbucket repository
3. **Repository Access**: Enable OrchestrAI on the repositories you want to analyze

### Initial Setup

1. Navigate to the Code Quality section from your product dashboard
2. If you haven't connected any repositories yet, click "Add Git Connection"
3. Authorize OrchestrAI to access your repositories
4. Enable OrchestrAI on the repositories you want to analyze by visiting the repository management page

## Running Your First Analysis

### Starting an Analysis

1. Open the Code Quality page from your workspace
2. Locate the repository you want to analyze in the "Recent Code Quality Analyses" table
3. Click the **Analyze** button next to the repository name
4. The analysis will begin processing your codebase

### Monitoring Progress

Once analysis starts:

- A progress indicator appears showing "Analyzing..." next to your repository
- The system processes your code in real-time
- You can navigate away from the page - analysis continues in the background
- Return anytime to check status updates

### Background Processing

Analysis runs automatically in the background:

- You'll see a notification when you navigate away confirming "Your code quality analysis is running in the background"
- The system maintains analysis state even if you close the browser
- Progress tracking updates automatically when you return to the page
- Multiple repositories can be analyzed simultaneously

## Understanding Quality Dimensions

The analysis evaluates your code across six critical quality dimensions, each scored from 0-100:

### 1. Readability
**What it measures**: How easy your code is to read and understand

- Code clarity and structure
- Documentation quality and completeness
- Variable and function naming conventions
- Comment effectiveness
- Code formatting consistency

**Score Guide**:
- 80-100 (Green): Excellent readability with clear documentation
- 60-79 (Yellow): Acceptable but could be clearer
- 0-59 (Red): Difficult to understand, needs improvement

### 2. Maintainability
**What it measures**: How easily your code can be modified and extended

- Code complexity and organization
- Modular design patterns
- Dependency management
- Code duplication levels
- Update and extension potential

**Why it matters**: Low maintainability increases the time and cost to add features or fix bugs.

### 3. Reliability
**What it measures**: Code stability and error resistance

- Error handling implementation
- Edge case coverage
- Input validation
- Exception management
- Defensive programming practices

**Why it matters**: High reliability means fewer crashes and better user experience.

### 4. Security
**What it measures**: Protection against vulnerabilities and exploits

- Security vulnerability detection
- Input sanitization
- Authentication and authorization checks
- Data protection practices
- Compliance with security standards

**Why it matters**: Security issues can lead to data breaches and system compromises.

### 5. Efficiency
**What it measures**: Performance and resource usage

- Algorithm optimization
- Memory usage patterns
- Processing speed
- Resource consumption
- Performance bottlenecks

**Why it matters**: Inefficient code leads to slow applications and higher infrastructure costs.

### 6. Testability
**What it measures**: How well the code supports testing

- Unit test compatibility
- Test coverage potential
- Dependency injection usage
- Mock-friendly design
- Automated testing support

**Why it matters**: Testable code is easier to verify and maintain with confidence.

## Viewing Analysis Results

### Results Table

After analysis completes, view your scores in the results table:

1. Each row represents one repository
2. Scores appear as colored badges:
   - **Green badges** (80-100): Excellent quality
   - **Yellow badges** (60-79): Needs improvement
   - **Red badges** (0-59): Requires immediate attention
3. An overall score combines all dimensions

### Detailed Insights

Click any score badge to see detailed information:

1. **Score Details**: Exact numerical score for that dimension
2. **Specific Issues**: List of detected problems
3. **File References**: Which files contain issues
4. **Recommendations**: Concrete steps to improve the score

The notes dialog shows:
- Repository name and quality dimension
- Current score with color-coded indicator
- Detailed explanation of detected issues
- Actionable improvement suggestions

### Accessing Full Reports

To view comprehensive results for a repository:

1. Click the **View Results** button at the top of the Code Quality page
2. Browse file-level analysis reports
3. Review line-specific recommendations
4. Track improvements over time

## Interpreting Scores

### Overall Score Calculation

The overall score represents your codebase's general quality:
- Calculated by averaging all six dimension scores
- Weighted equally across all dimensions
- Provides quick health indicator for your repository

### Score Trends

Monitor how scores change over time:
- The "Last Analyzed" timestamp shows when analysis ran
- Run analysis periodically to track improvements
- Compare scores before and after making changes

### Priority Actions

Use scores to prioritize improvements:

1. **Red Scores (0-59)**: Address immediately - critical issues present
2. **Yellow Scores (60-79)**: Schedule improvements - moderate concerns
3. **Green Scores (80-100)**: Maintain current quality - minor refinements only

## Acting on Recommendations

### Understanding Issues

Each detected issue includes:
- **Issue Type**: Which quality dimension it affects
- **Description**: What the problem is
- **Location**: File and line references (when available)
- **Severity**: How critical the issue is

### Implementation Steps

To improve your scores:

1. **Review Notes**: Click score badges to read detailed findings
2. **Prioritize Fixes**: Start with security and reliability issues
3. **Make Changes**: Update your code based on recommendations
4. **Re-analyze**: Run analysis again to verify improvements
5. **Track Progress**: Compare new scores to previous results

### Best Practices

- Run analysis before major releases
- Address security issues first
- Improve one dimension at a time for focused improvements
- Re-analyze after significant code changes
- Use analysis to guide code review priorities

## Managing Multiple Repositories

### Repository Selection

The analysis table shows all enabled repositories:
- Only repositories with OrchestrAI enabled appear
- Enable more repositories from the repository management page
- Each repository maintains independent analysis history

### Batch Analysis

Analyze multiple repositories efficiently:
- Click Analyze on each repository in sequence
- All analyses run simultaneously in the background
- Track progress for each repository independently
- Results appear as each analysis completes

### Cross-Repository Insights

Compare quality across your codebase:
- View all repository scores in one table
- Identify patterns across projects
- Set organization-wide quality standards
- Share best practices from high-scoring repositories

## Troubleshooting

### Analysis Doesn't Start

If analysis fails to begin:
- Verify the repository is enabled for OrchestrAI
- Check that you have sufficient credits in your workspace
- Ensure repository connection is active
- Try refreshing the page and clicking Analyze again

### No Scores Displayed

If scores show as dashes (-):
- Analysis hasn't run yet for this repository
- Previous analysis may have failed
- Click Analyze to start a new analysis run

### Analysis Takes Too Long

Analysis duration depends on repository size:
- Small repositories: 1-3 minutes
- Medium repositories: 3-10 minutes
- Large repositories: 10-30+ minutes
- Analysis continues in the background if you navigate away

### Missing Repositories

If your repository doesn't appear:
- Check that OrchestrAI is enabled on the repository
- Visit the repository management page to enable it
- Ensure your workspace has access to the repository
- Verify repository connection is still active

## Advanced Features

### Real-Time Updates

The analysis system provides live feedback:
- Progress indicators update automatically
- Status changes reflect immediately
- No page refresh needed to see updates
- Background analysis state persists across sessions

### Performance Analysis

Beyond quality scores, the system identifies:
- Specific performance bottlenecks
- Memory usage patterns
- Optimization opportunities
- Complexity metrics for individual files

### Security Scanning

Security analysis detects:
- Known vulnerability patterns
- Potential exploit vectors
- Compliance violations
- Input validation gaps
- Authentication weaknesses

### File-Level Reporting

Detailed reports show:
- Individual file scores
- Line-specific issues
- Code pattern analysis
- Technical debt assessment
- Improvement priorities per file

## Integration Workflows

### Development Workflow

Incorporate analysis into your process:
1. **Before Starting**: Analyze existing code to establish baseline
2. **During Development**: Focus on maintaining or improving scores
3. **Before Commit**: Check that changes don't reduce quality
4. **After Merge**: Re-analyze to verify overall impact

### Code Review Process

Use analysis to enhance reviews:
- Reference quality scores in review discussions
- Prioritize reviewing files with low scores
- Verify improvements claimed in pull requests
- Set minimum score thresholds for merging

### Continuous Improvement

Build quality into your culture:
- Schedule regular analysis runs (weekly or sprint-based)
- Track quality trends over time
- Celebrate improvements in team meetings
- Set team goals for quality dimension scores

## Getting the Most Value

### Regular Analysis

Run analysis consistently:
- After completing major features
- Before releases or deployments
- When onboarding new team members
- After refactoring efforts

### Team Collaboration

Share results with your team:
- Discuss findings in team meetings
- Assign improvement tasks based on recommendations
- Use scores to guide pair programming sessions
- Document lessons learned from quality improvements

### Quality Goals

Set measurable targets:
- Define minimum acceptable scores per dimension
- Create improvement roadmaps for red/yellow scores
- Track progress toward quality objectives
- Recognize team members who improve code quality

## Next Steps

After running your first analysis:

1. **Review all dimension scores** to understand your baseline quality
2. **Prioritize improvements** starting with security and reliability
3. **Make targeted changes** based on detailed recommendations
4. **Re-analyze regularly** to track improvements over time
5. **Expand coverage** by enabling analysis on more repositories

For more advanced features, explore the full results view where you can access file-level details, historical trends, and comprehensive quality reports.