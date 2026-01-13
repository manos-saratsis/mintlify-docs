# How to View Public Reports

Public reports allow you to share analysis results with stakeholders, team members, or clients without requiring them to have an account. Anyone with the report link can view the analysis scores and product information.

## Understanding Public Reports

Public reports come in two types:

**Single Product Reports** - Display analysis results for one product, showing code quality, security, and compliance scores along with repository information.

**Comparison Reports** - Display multiple products side-by-side, allowing viewers to compare scores and analysis results across different products.

## Accessing a Public Report

When someone shares a public report link with you, simply click the link or paste it into your browser. The report opens immediately without requiring login or account creation.

Public report links look like this:
- `https://yoursite.com/report/abc123xyz`

## What You'll See in Single Product Reports

### Report Header
At the top of the report, you'll find:
- **Report name** - The title given to this report
- **Product name** - The name of the product being analyzed
- **Product description** - A brief description of what the product does
- **Copy Link button** - Click this to copy the report URL to share with others
- **Last updated date** - When the analysis was last run

### Analysis Scores

The report displays three main analysis categories in card format:

**Code Quality Score**
- Overall quality rating (0-100)
- Number of critical issues found
- Number of warning issues found
- Analysis model used
- Date when analysis was performed
- Detailed breakdown by quality dimensions

**Code Security Score**
- Overall security rating (0-100)
- Number of critical security issues
- Number of warning security issues
- Analysis model used
- Date when analysis was performed
- Detailed breakdown by security dimensions

**Compliance Score**
- Overall compliance rating (0-100)
- Number of critical compliance issues
- Number of warning compliance issues
- Analysis model used
- Date when analysis was performed
- Detailed breakdown by compliance dimensions

### Understanding Scores

Scores range from 0 to 100:
- **80-100** (Green) - Good performance, minimal issues
- **60-79** (Yellow) - Needs improvement, moderate concerns
- **Below 60** (Red) - Critical issues requiring attention

### Repository Information

If the product has connected repositories, you'll see a list showing:
- Repository name
- Link to view the repository on GitHub

### Additional Resources

The report may include links to:
- Testing repositories
- Documentation repositories

Click these links to view the source code and testing materials directly.

## What You'll See in Comparison Reports

Comparison reports show multiple products arranged side-by-side for easy comparison.

### Navigation

At the top of the report, you'll find:
- **Report title** - The name of this comparison
- **Product count** - How many products are being compared
- **Last updated date** - When analyses were last run
- **Share button** - Copy the comparison link to share with others

A navigation menu provides quick access to different sections:
- **Overview** - Product descriptions and repositories
- **Code Quality** - Quality scores comparison
- **Code Security** - Security scores comparison
- **Compliance** - Compliance scores comparison
- **Testing** - Testing repository information
- **Documentation** - Documentation resources

### Product Overview Section

Shows each product's basic information:
- Product name
- Product description
- Connected repositories with GitHub links

### Score Comparison Sections

Each analysis category (Quality, Security, Compliance) displays products in columns:
- Product name at the top
- Overall score with color coding
- Critical and warning issue counts
- Analysis model used
- When the analysis was performed
- Dimension-by-dimension breakdown

The product with the highest score in each category may be visually highlighted to show the leader.

### Testing and Documentation Sections

Shows which products have:
- Testing repositories configured
- Documentation repositories configured
- Links to view these resources

Products without these resources will show a message indicating they're not configured.

### Score Legend

At the bottom of comparison reports, you'll find a color-coded legend:
- **Green circle** - Score 80+, Good
- **Yellow circle** - Score 60-79, Needs Improvement
- **Red circle** - Score below 60, Critical

## Sharing Reports with Others

### Copying the Report Link

1. Open the public report
2. Click the **Copy Link** or **Share** button at the top
3. The button will briefly show "Copied!" to confirm
4. Paste the link into emails, messages, or documents

The link remains valid indefinitely and can be shared with anyone.

### Who Can View Public Reports

Anyone with the report link can view it - no account or login required. This includes:
- Team members
- Stakeholders
- Clients
- External auditors
- Management
- Partners

### What Information Is Visible

Public reports show:
- Product names and descriptions
- Analysis scores and issue counts
- Repository names and links
- Analysis dates and models used
- Dimension-level breakdowns

Public reports do not show:
- Detailed issue descriptions
- Source code content
- Internal notes or comments
- User information
- Workspace details

## If a Report Isn't Loading

If you see an error message when opening a report link:

**"Report Not Found"** - This means either:
- The link is incorrect or incomplete
- The report has been removed
- The product is no longer set to public

Contact the person who shared the link to request an updated version.

## Viewing Reports on Mobile Devices

Public reports are designed to work on phones and tablets:
- Scores display in a single column on narrow screens
- Navigation menus scroll horizontally if needed
- All buttons and links are touch-friendly
- Comparison tables adapt to smaller screens

For the best experience viewing comparison reports, use a tablet or desktop computer where multiple columns can be displayed side-by-side.

## Understanding "No Scores Available"

If a report shows "No analysis scores available yet," this means:
- The product exists but hasn't been analyzed
- Analysis is currently in progress
- Scores will appear once analysis completes

Check back later or contact the report creator for an updated timeline.

## Security and Privacy

Public reports are designed for safe sharing:
- Reports use unique, unguessable URLs
- Only information explicitly made public is visible
- No sensitive code or detailed vulnerabilities are exposed
- Links can be revoked by removing public access

If you receive a public report containing sensitive information, treat the link confidentially and only share it with appropriate stakeholders.