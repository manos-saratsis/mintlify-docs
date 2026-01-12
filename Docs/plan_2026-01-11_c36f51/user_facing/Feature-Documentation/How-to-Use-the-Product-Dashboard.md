# How to Use the Product Dashboard

## Overview

The Product Dashboard is your central hub for managing code quality, security, and documentation across your repositories. It provides quick access to all analysis tools and displays the current status of your codebase.

## Getting Started

### First-Time Setup

When you first access the Dashboard, you'll see a welcome message with OrchestrAI's production readiness flow:

**Testing → Quality → Compliance → Security → Docs → Instrumentation**

This flow represents the complete journey from basic testing to production-ready code.

### Connecting Your Code

To begin using the Dashboard:

1. Click the **"Connect Git Management Tool"** button
2. Follow the prompts to connect your GitHub account
3. Once connected, you'll see your available repositories
4. Enable OrchestrAI for the repositories you want to analyze

## Dashboard Layout

### Navigation Sidebar

The sidebar provides access to all OrchestrAI features, organized into two sections:

#### Functions
- **Testing** - Generate comprehensive unit tests for your code
- **Code Quality** - Analyze code for quality issues and improvements
- **Code Security** - Scan for security vulnerabilities
- **Compliance** - Check regulatory and compliance requirements
- **Instrumentation** - Add monitoring and observability tools
- **Documentation** - Generate and manage code documentation
- **Release Management** (Coming Soon)

#### Organization
- **Team** - Manage workspace members and permissions
- **Code** - Configure repository settings and connections
- **Information** - View and edit product details
- **Integrations** (Coming Soon)
- **Workflow** - Set up automated quality assurance workflows

### Main Dashboard Area

Once your repositories are connected and enabled, the Dashboard displays cards for each available analysis type.

## Analysis Cards

Each analysis card shows:

### Current Status Information
- **Last Run Date** - When the analysis last completed
- **Status Badge** - Current state (Completed, Running, Failed)
- **Score** - Overall quality score (when available)
- **Issues Count** - Number of problems detected
- **Quick Links** - Direct links to pull requests or commits

### Available Analysis Types

**Testing**
- Generate unit tests automatically
- View test coverage
- Access generated test pull requests

**Code Quality**
- Review code quality scores
- See detected quality issues
- Get improvement recommendations

**Code Security**
- Check for security vulnerabilities
- View security scores
- Access remediation advice

**Compliance**
- Monitor compliance scores
- Track regulatory issues
- Review compliance reports

**Instrumentation**
- Add observability tools
- View instrumentation commits
- Monitor implementation status

**Documentation**
- Track documentation progress
- See completed vs. total tasks
- View last update dates

## Configuration Status Panel

At the bottom of the Dashboard, you'll find a status panel showing:

- **Git Connections** - Number of connected Git accounts
- **Enabled Repositories** - Active repositories out of total available
- **OrchestrAI Bot** - Installation status with quick install link
- **Products** - Number of configured products

Click on the Products count to view and manage your product configurations.

## Running Analyses

To start any analysis:

1. Click on the corresponding card (e.g., "Code Quality")
2. Select the repository you want to analyze
3. Choose your analysis options
4. Click the run button to begin

The Dashboard will update automatically to show the analysis progress.

## Workflow Automation

Access the Workflow configuration card to:
- Set up automated quality checks
- Schedule regular analyses
- Configure continuous monitoring
- Enable agentic workflows for automatic issue detection

## Switching Workspaces

If you belong to multiple workspaces, you can switch between them using the workspace selector in the header. The Dashboard will update to show the repositories and analysis results for the selected workspace.

## Understanding Status Indicators

**Completed** - Analysis finished successfully, results available
**Running** - Analysis currently in progress
**Failed** - Analysis encountered an error, review logs for details
**None** - No analysis has been run yet

## Quick Actions

From the Dashboard, you can:
- Click any analysis card to view detailed results
- Access pull requests directly from status links
- Navigate to configuration pages using the sidebar
- Install the OrchestrAI Bot with one click
- Switch between different products and workspaces

## Best Practices

- **Enable repositories** you actively work on to keep analyses relevant
- **Check the Dashboard regularly** for new security or compliance issues
- **Review scores and issue counts** to track code quality trends
- **Set up workflows** to automate routine quality checks
- **Install the OrchestrAI Bot** for automatic pull request creation

## Permissions

Access to certain features depends on your role:
- **Owners and Admins** can access all features including Team, Code, and Workflow settings
- **Members** can view analysis results and information but cannot modify settings

## Getting Help

If you don't see expected data:
- Verify your Git connection is active
- Ensure repositories are enabled for OrchestrAI
- Check that the OrchestrAI Bot is installed
- Confirm you have the necessary permissions

The Dashboard automatically refreshes when you connect new repositories or complete analyses, keeping your view up-to-date.