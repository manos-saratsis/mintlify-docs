# How to View Public Reports

## Overview

Public reports allow you to share product analysis results with anyone, even if they don't have an account. You can share individual product reports or comparison reports that showcase multiple products side by side.

## Accessing a Public Report

When someone shares a public report with you, you'll receive a link that looks like this:
- Single product: `yoursite.com/report/abc123xyz`
- Product comparison: `yoursite.com/report/abc123xyz`

Simply click the link or paste it into your browser to view the report. No login or account required.

## Understanding the Report Layout

### Single Product Reports

When you open a single product report, you'll see:

**Report Header**
- Product name and description at the top
- Last updated timestamp in the upper right corner
- A "Copy Link" button to share the report with others

**Analysis Scores**
The report displays three main scores, each rated from 0-100:

- **Code Quality**: Measures code structure, maintainability, and best practices
- **Code Security**: Evaluates potential security vulnerabilities and risks
- **Compliance**: Assesses adherence to standards and regulations

Each score card shows:
- Overall score with color coding (green for good, amber for needs improvement, red for critical)
- Number of critical issues found
- Number of warning-level issues
- When the analysis was last performed
- Which AI model performed the evaluation

**Score Interpretation**
- **80-100 (Green)**: Good - meets quality standards
- **60-79 (Amber)**: Needs improvement - some issues to address
- **Below 60 (Red)**: Critical - significant issues requiring attention

**Repository Information**
Below the scores, you'll find links to associated code repositories, allowing you to explore the source code directly on GitHub.

**Resources Section**
If available, this section provides quick access to:
- Testing repository links
- Documentation repository links

### Comparison Reports

Comparison reports let you view multiple products side by side to evaluate their relative strengths.

**Report Header**
- Comparison name and number of products being compared
- Last updated timestamp
- "Share" button to copy the comparison link

**Navigation Menu**
A sticky navigation bar at the top allows you to quickly jump to different sections:
- **Overview**: Basic product information and descriptions
- **Code Quality**: Quality scores comparison
- **Code Security**: Security scores comparison
- **Compliance**: Compliance scores comparison
- **Testing**: Testing repository availability
- **Documentation**: Documentation resources

**Product Overview Section**
Shows each product's basic information:
- Product name and description
- Associated repositories
- Link to view individual product report

**Score Comparison Sections**
Each analysis category (Quality, Security, Compliance) displays:
- Side-by-side score cards for all products
- Best-performing product highlighted
- Detailed breakdown of issues for each product
- Color-coded visual indicators

**Testing & Documentation Sections**
Shows which products have:
- Test repositories configured
- Documentation available
- Links to access these resources

**Score Legend**
At the bottom of the comparison, a legend explains the color coding system for all scores.

## Sharing a Report

### Copying the Report Link

1. Look for the "Copy Link" or "Share" button in the upper right corner of any report
2. Click the button to copy the full URL to your clipboard
3. The button will briefly show "Copied!" to confirm
4. Paste the link anywhere you want to share it (email, Slack, documents, etc.)

### What Recipients Can See

When you share a public report link, recipients can view:
- All analysis scores and their detailed breakdowns
- Issue counts (critical and warning levels)
- Repository information and links
- Testing and documentation resources
- Analysis timestamps

Recipients **cannot**:
- Edit the report
- View private repositories or code details
- Access your workspace or other products
- See who created the report

## Report Updates

Public reports automatically reflect the latest analysis results. When you re-run analyses on your products, anyone with the public report link will see the updated scores the next time they view it.

The "Last updated" timestamp shows when the most recent analysis was performed, helping viewers understand how current the information is.

## Privacy and Security

### What's Visible

Public reports show:
- Product names and descriptions
- Analysis scores and metrics
- Issue counts and severity levels
- Links to repositories (if they're public)
- Analysis timestamps

### What's Protected

Public reports **do not** expose:
- Specific code vulnerabilities or issues
- Detailed compliance findings
- Internal workspace information
- User information or account details
- Private repository contents

## Viewing Reports Without Internet

Public reports require an active internet connection to view. They cannot be downloaded or saved for offline viewing, as they display real-time data from the platform.

## Best Practices for Sharing

- Share reports with stakeholders who need to understand product quality metrics
- Use comparison reports when evaluating multiple solutions or tracking improvements over time
- Include context when sharing links (explain what the recipient is looking at)
- Check that reports are up-to-date before sharing by reviewing the "Last updated" timestamp
- Use single product reports for detailed analysis, comparison reports for competitive evaluation

## Troubleshooting

**"Report Not Found" Error**
If you see this message, the report may have been:
- Deleted by the workspace owner
- Made private (no longer publicly accessible)
- Moved or the link may be incorrect

Contact the person who shared the link for an updated URL.

**Loading Issues**
If the report doesn't load:
- Check your internet connection
- Try refreshing the page
- Clear your browser cache and try again
- Try a different browser

**Missing Scores**
If a report shows "No analysis scores available yet," it means:
- The product hasn't been analyzed yet
- Analyses are currently in progress
- Only certain types of analyses have been run

Check back later or contact the report owner for more information.