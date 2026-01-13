# How to Run Code Analysis

## Overview

Code Analysis helps you understand and improve the quality of your code through automated evaluation. The system examines your repositories and provides scores across multiple quality dimensions, helping you identify areas for improvement and track code health over time.

## Getting Started

### Prerequisites

Before running code analysis, ensure you have:

1. **An active workspace** - You must be logged in and have a workspace selected
2. **Connected repositories** - At least one repository must be connected from GitHub, GitLab, or Bitbucket
3. **Enabled repositories** - OrchestrAI must be enabled on the repositories you want to analyze

### Initial Setup

1. Navigate to the Code Quality page from your product dashboard
2. If you haven't connected any repositories yet, click the "Manage Repositories" button
3. Enable OrchestrAI on the repositories you want to analyze
4. Return to the Code Quality page to begin your analysis

## Running Your First Analysis

### Starting an Analysis

1. From the Code Quality page, locate the "Recent Code Quality Analyses" section
2. Find the repository you want to analyze in the list
3. Click the **"Analyze"** button next to the repository name
4. The system will begin processing your code immediately

### Monitoring Progress

Once analysis starts, you'll see:

- **Real-time status updates** showing the current processing stage
- **Progress indicators** displaying how much of the repository has been analyzed
- **Processing metrics** including files scanned and completion percentage

The analysis continues to run even if you navigate away from the page. Your results are saved automatically.

### Analysis Duration

Analysis time varies based on:
- Repository size (number of files and lines of code)
- Code complexity
- Current system load

Most repositories complete analysis within 2-5 minutes. Larger repositories may take up to 15 minutes.

## Understanding Your Results

### The Quality Scoring System

Your code receives scores from 0-100 across six quality dimensions. Each score is color-coded for quick reference:

- **Green (80-100)**: Excellent quality, meets best practices
- **Yellow (60-79)**: Good quality with room for improvement
- **Red (0-59)**: Needs attention and refactoring

### Six Quality Dimensions

#### Readability
Evaluates how easy your code is to understand, including:
- Code clarity and organization
- Documentation quality and completeness
- Variable and function naming conventions
- Comment effectiveness

#### Maintainability
Measures how easily the code can be modified and extended:
- Code structure and modularity
- Complexity levels
- Dependency management
- Technical debt indicators

#### Reliability
Assesses code stability and error resistance:
- Error handling implementation
- Edge case coverage
- Exception management
- Stability indicators

#### Security
Identifies potential security vulnerabilities:
- Security flaws and exploits
- Authentication and authorization issues
- Data handling practices
- Compliance concerns

#### Efficiency
Analyzes performance and resource usage:
- Performance bottlenecks
- Memory management
- Algorithm optimization opportunities
- Resource utilization patterns

#### Testability
Evaluates how well the code supports testing:
- Unit test compatibility
- Test coverage potential
- Mockability and isolation
- Test automation readiness

### Overall Score

The overall score provides a single metric representing your code's general quality. This aggregate score helps you track improvement over time and compare different repositories.

## Viewing Detailed Results

### Accessing Analysis Reports

1. After analysis completes, click the **"View Results"** button at the top of the Code Quality page
2. Select the repository you want to review
3. The detailed report opens showing all quality dimensions with complete breakdowns

### Reading Score Details

To see specific recommendations for any quality dimension:

1. Click on any colored score badge in the results table
2. A detailed breakdown appears showing:
   - Specific issues found in your code
   - File locations where problems exist
   - Concrete improvement recommendations
   - Technical debt assessment

### File-Level Reporting

Each analysis includes file-specific information:
- Individual file quality scores
- Line-specific issue locations
- Code patterns identified
- Recommended refactoring steps

## Acting on Recommendations

### Understanding Issues

Each issue in your report includes:
- **Description**: What the problem is
- **Location**: Where it exists in your code
- **Impact**: How it affects code quality
- **Remediation**: Steps to fix it

### Prioritizing Improvements

Focus on issues in this order:

1. **Security vulnerabilities** - Address immediately
2. **Critical reliability issues** - Fix to prevent failures
3. **Performance bottlenecks** - Improve user experience
4. **Maintainability concerns** - Reduce technical debt
5. **Readability enhancements** - Improve team collaboration
6. **Testability improvements** - Strengthen quality assurance

### Tracking Progress

After making improvements:

1. Commit your changes to the repository
2. Return to the Code Quality page
3. Run a new analysis on the same repository
4. Compare the new scores with previous results
5. Verify that targeted dimensions show improvement

## Managing Multiple Repositories

### Viewing All Analyses

The "Recent Code Quality Analyses" table shows:
- All repositories with analysis history
- Most recent analysis date for each repository
- Current quality scores across all dimensions
- Quick access to analyze any repository

### Comparing Repositories

Use the table view to:
- Identify which repositories need attention
- Compare quality metrics across your codebase
- Spot trends in code quality
- Allocate improvement resources effectively

### Scheduling Regular Analysis

Best practices for ongoing code quality monitoring:

- **After major features**: Run analysis when significant code is added
- **Before releases**: Verify quality before deploying to production
- **Weekly reviews**: Track quality trends over time
- **After refactoring**: Confirm improvements achieved desired results

## Analysis Features

### Multi-Repository Support

Analyze repositories from multiple platforms:
- GitHub repositories
- GitLab projects
- Bitbucket repositories

All results are centralized in one dashboard for easy comparison and tracking.

### Background Processing

Analysis runs in the background, allowing you to:
- Continue working on other tasks
- Navigate away from the page
- Return later to view completed results
- Check progress at any time

### Automatic Result Storage

Every analysis is saved automatically:
- Historical results remain accessible
- Compare current and past performance
- Track improvement trends over time
- Generate progress reports

## Getting Better Results

### Repository Preparation

For optimal analysis results:

1. **Ensure code is up to date** - Pull the latest changes before analyzing
2. **Include documentation** - READMEs and comments improve readability scores
3. **Organize file structure** - Clear organization improves maintainability
4. **Remove generated files** - Focus analysis on your actual code

### Understanding Limitations

The analysis system:
- Examines code structure and patterns
- Identifies common issues and anti-patterns
- Provides guidance based on industry best practices
- Cannot understand business context or requirements

Use the scores as guidance, not absolute measures. Your judgment about code quality should always consider your specific needs and constraints.

## Troubleshooting

### No Repositories Available

If you see "No Enabled Repositories":
1. Click "Manage Repositories" 
2. Ensure OrchestrAI is enabled on at least one repository
3. Return to the Code Quality page

### Analysis Fails to Start

If analysis doesn't begin:
1. Verify you're connected to the repository platform
2. Check that you have workspace permissions
3. Ensure the repository is accessible and hasn't been deleted
4. Try refreshing the page and attempting analysis again

### Missing or Incomplete Results

If results seem incomplete:
1. Wait for the full analysis to complete (check the progress indicator)
2. Verify the repository contains analyzable code files
3. Check that you have sufficient credits remaining
4. Run the analysis again if it appears to have stopped

## Best Practices

### Regular Monitoring

- Run analysis at consistent intervals
- Track scores over time to measure improvement
- Address issues promptly before they accumulate
- Review results as a team to share knowledge

### Team Collaboration

- Share analysis results with your development team
- Discuss priorities for quality improvements
- Use scores to guide code review focus
- Set team goals for quality metrics

### Continuous Improvement

- Address highest-priority issues first
- Re-analyze after making changes
- Celebrate quality improvements
- Document lessons learned from quality issues