# How to View Public Reports

## Overview

Public reports allow you to share analysis results with anyone, even if they don't have an account. You can create shareable links for individual product reports or comparison reports that display multiple products side-by-side.

## Accessing a Public Report

When someone shares a report link with you, simply click the link or paste it into your browser. No login or account is required to view public reports.

### What You'll See

The report loads automatically and displays:
- Product name and description
- Analysis scores for Code Quality, Security, and Compliance
- Issue counts (critical and warnings)
- When each analysis was last performed
- Links to related repositories and documentation

## Single Product Reports

Single product reports focus on one product's analysis results.

### Report Layout

**Header Section**
- Product name prominently displayed at the top
- Product description (if available)
- Last updated timestamp
- "Copy Link" button to share the report with others

**Score Cards**
Three main analysis areas are shown:

1. **Code Quality Score**
   - Overall quality rating (0-100)
   - Number of critical issues found
   - Number of warnings identified
   - Which analysis model was used
   - When the analysis was performed

2. **Code Security Score**
   - Overall security rating (0-100)
   - Critical security issues count
   - Security warnings count
   - Analysis model information
   - Last evaluation date

3. **Compliance Score**
   - Overall compliance rating (0-100)
   - Critical compliance issues
   - Compliance warnings
   - Model used for analysis
   - Evaluation timestamp

**Understanding Scores**
- **80-100**: Good standing (green indicator)
- **60-79**: Needs improvement (yellow indicator)
- **Below 60**: Critical attention needed (red indicator)

**Resources Section**
If configured, you'll see buttons to:
- View the testing repository
- Access product documentation
- Review linked code repositories

### When No Scores Are Available

If the product hasn't been analyzed yet, you'll see a message indicating no analysis scores are available. The page will still display product information and any configured resources.

## Comparison Reports

Comparison reports display multiple products side-by-side, making it easy to evaluate options.

### Navigation

At the top of comparison reports, you'll find:
- Report title showing how many products are being compared
- Last updated date
- "Share" button to copy the comparison link
- Quick navigation tabs to jump to different sections

**Available Sections:**
- Overview
- Code Quality
- Code Security
- Compliance
- Testing
- Documentation

Click any section tab to scroll directly to that comparison.

### Product Overview Section

Each product is shown in its own card with:
- Product name and description
- List of associated code repositories
- Links to view repositories on GitHub

### Score Comparison Sections

For Quality, Security, and Compliance, products are displayed side-by-side showing:
- Product name at the top of each column
- Score with color-coded indicator
- Critical issues count
- Warning issues count
- When the analysis was performed
- A "Best" badge on the highest-scoring product (when applicable)

### Testing and Documentation Sections

These sections show which products have:
- Configured testing repositories
- Available documentation
- Active test runs
- Documentation runs

Products with available resources show a green checkmark and "View" buttons. Products without these resources show a gray placeholder.

### Score Legend

At the bottom of comparison reports, a legend explains the color coding:
- Green (80+): Good
- Yellow (60-79): Needs Improvement
- Red (Below 60): Critical

## Sharing Public Reports

### Copying the Report Link

Every public report has a "Copy Link" or "Share" button in the top-right corner:

1. Click the button
2. The full report URL is copied to your clipboard
3. The button briefly shows "Copied!" to confirm
4. Paste the link anywhere you want to share it

### Who Can Access Shared Reports

Anyone with the link can view the report. They don't need to:
- Create an account
- Log in
- Have special permissions

The link remains valid until the report is deleted by the workspace owner.

## Report Information and Transparency

### Timestamps

Every report shows when analyses were last performed. This helps you understand how current the information is.

### Analysis Model Information

Reports indicate which analysis model was used, providing transparency about how scores were generated.

### Issue Breakdown

Rather than just showing overall scores, reports break down issues by severity:
- **Critical Issues**: Problems that need immediate attention
- **Warnings**: Areas for improvement that aren't urgent

This detail helps you understand what's behind each score.

## Viewing on Different Devices

Public reports are designed to work on:
- Desktop computers
- Tablets
- Mobile phones

The layout automatically adjusts to fit your screen size. On smaller screens, comparison reports stack vertically for easier reading.

## Report Availability

### When Reports Are Not Found

If you click a report link and see "Report Not Found," it means:
- The link may be incorrect
- The report has been deleted
- The report is no longer set to public

Contact the person who shared the link if you believe you should have access.

### Loading Issues

If a report takes a long time to load:
- Check your internet connection
- Refresh the page
- Try again in a few moments

Reports typically load within a few seconds on normal connections.

## Privacy and Security

### What Information Is Shared

Public reports only show:
- Product names and descriptions
- Analysis scores and issue counts
- Repository links (if configured as public)
- Timestamps of analyses

### What Is Not Shared

Public reports do not reveal:
- Specific code vulnerabilities or security details
- Individual file contents
- Private repository information (unless explicitly made public)
- User or workspace information
- Internal comments or notes

### Secure Sharing

Each report has a unique, randomly generated link. The link cannot be guessed or discovered without being shared directly.

## Reading and Interpreting Reports

### Focus on Trends

When viewing multiple reports over time, pay attention to whether scores are:
- Improving (issues being addressed)
- Stable (maintained quality)
- Declining (new issues appearing)

### Consider Context

A lower score isn't always bad if:
- The product is early in development
- Major refactoring is underway
- Issues are already known and scheduled for resolution

### Use Comparisons Wisely

When viewing comparison reports:
- Look beyond just the highest scores
- Consider which issues matter most for your needs
- Review the testing and documentation availability
- Check repository activity and recency

### Ask Questions

Public reports provide transparency, but they're starting points for conversation. If you're evaluating products based on these reports, don't hesitate to ask the product team about:
- Specific issues or concerns
- Plans for addressing identified problems
- Context behind certain scores
- Additional information not shown in the report

## Accessing From Different Sources

Public report links work from anywhere:
- Email messages
- Slack or Teams conversations
- Documents and spreadsheets
- Project management tools
- Embedded in websites
- QR codes

Simply click or visit the URL to view the report.