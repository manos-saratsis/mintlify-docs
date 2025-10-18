I'll analyze the provided source code and generate comprehensive user-facing reference documentation for OrchestrAI.

<think>
Let me analyze the key components:

1. **App.tsx** - Main application with routing structure showing all available pages:
   - Index (landing page)
   - Enterprise
   - Mission pages
   - Product pages (Code, Testing, Code Quality, Workflow, Documentation, Compliance, etc.)
   - Workspace Management
   - Account
   - Pricing

2. **AIComplianceAnalystPanel.tsx** - A panel for running compliance analysis on repositories:
   - Checks permissions and workflow configuration
   - Allows users to start compliance analysis
   - Shows progress and results
   - Handles repository selection

3. **AIDocumentationSpecialistPanel.tsx** - A panel for generating documentation:
   - Two modes: migrate existing docs or create new docs
   - Allows scope selection (user-facing, internal, SBOM)
   - Content structure customization
   - Repository selection with commit-level granularity

Key user flows:
- Authentication via AuthContext
- Workspace management via WorkspaceContext
- GitHub integration (success/error pages)
- Welcome modal for first-time users
- Various product features (code analysis, testing, compliance, documentation)

I need to write this in simple, user-friendly language without mentioning technical implementation details.
</think>

<write_file>
<path>user-facing-docs/orchestrai-dev-reference-documentation.md</path>
<content>
# OrchestrAI Reference Documentation

## Overview

OrchestrAI is an AI-powered platform that helps you manage code quality, testing, compliance, and documentation across your software projects. The platform provides intelligent automation for common development tasks while maintaining full control over your workflows.

---

## Getting Started

### First Time Setup

When you first sign in to OrchestrAI, you'll be greeted with a welcome screen that guides you through the initial setup process. This includes:

1. **Account Creation** - Sign in using your preferred authentication method
2. **Workspace Setup** - Create or join a workspace where your projects will be organized
3. **GitHub Connection** - Connect your GitHub repositories to enable OrchestrAI features

If the GitHub connection is successful, you'll be directed to a success page. If there are any issues, you'll see an error page with instructions on how to resolve them.

### Understanding Workspaces

Workspaces are the central organizing unit in OrchestrAI. Each workspace can contain multiple repositories and team members. Think of a workspace as a project or team environment where all your AI-assisted development activities happen.

---

## Main Features

### Dashboard

The main dashboard gives you an overview of your workspace activity. From here, you can:

- View recent analysis results
- Access your connected repositories
- Monitor ongoing AI operations
- Navigate to different feature areas

### Code Management

Navigate to the Code section to manage your connected repositories. Here you can:

- **View All Repositories** - See a list of repositories connected to OrchestrAI
- **Enable Repository Features** - Turn on AI-powered features for specific repositories
- **Monitor Repository Status** - Check the connection status and recent activity

When repositories are properly connected and enabled, you'll see additional options to run analysis and access advanced features.

### Testing

The Testing area helps you generate and manage tests for your code:

- **Automated Test Generation** - AI creates comprehensive test suites based on your code
- **Test Coverage Analysis** - See which parts of your code are tested
- **Test Framework Support** - Works with popular testing frameworks like Jest

### Code Quality Analysis

Access detailed code quality insights through the Code Quality section:

1. Navigate to the Code Quality page
2. Select a repository to analyze
3. Run the analysis to receive comprehensive quality metrics
4. View results including complexity scores, maintainability ratings, and improvement suggestions

The results page shows:
- Quality scores and trends
- Specific code issues identified
- Recommended improvements
- Historical analysis data

### Compliance Analysis

The Compliance feature helps ensure your code meets regulatory requirements:

1. **Starting an Analysis**
   - Go to the Compliance section
   - Select the repository you want to analyze
   - Choose your analysis settings
   - Click the start button to begin

2. **Analysis Instructions**
   - You can provide specific instructions to focus the analysis on particular compliance requirements
   - The AI will comprehensively check your code against privacy regulations, security standards, and data protection rules

3. **Permissions**
   - Some compliance features require specific permissions in your workspace
   - If you see a permission restriction message, contact your workspace administrator

4. **Viewing Results**
   - Once analysis completes, you'll see a summary of findings
   - Navigate to the results page to see detailed compliance reports
   - Each finding includes the issue description, location, and recommended fixes

**Note:** Compliance analysis must be enabled in your Workflow settings before you can run analyses. If you see a "Compliance Disabled" message, ask your administrator to enable it.

### Documentation Generation

OrchestrAI can automatically create and maintain documentation for your projects. There are two main approaches:

#### Creating New Documentation

When you don't have existing documentation:

1. Navigate to the Documentation section
2. Select "Create New Documentation"
3. Choose what types of documentation to generate:
   - **User-Facing Documentation** - Help guides and tutorials for end users
   - **Internal Developer Documentation** - Technical documentation for your development team
   - **SBOM** - Software Bill of Materials listing all components

4. Customize the content structure by selecting which sections to include:
   - Introduction and Quick Start guides
   - Step-by-step tutorials
   - Task-focused how-to guides
   - API and SDK reference material
   - Architecture and concept explanations
   - Troubleshooting guides
   - Automated release notes

5. Select which code repositories to document:
   - Choose to document entire repositories
   - Or document specific commits for targeted updates

6. Add any special instructions for the AI to follow
7. Click "Generate Documentation" to start

#### Migrating Existing Documentation

If you already have documentation that needs updating:

1. Navigate to the Documentation section
2. Select "Migrate Existing Documentation"
3. The AI will analyze your current documentation structure
4. Choose the same customization options as creating new documentation
5. The AI will restructure your documentation according to best practices while preserving your existing content

**Important:** You must configure a documentation repository and folder in your Workflow settings before generating documentation.

#### Progress Monitoring

While documentation is being generated:
- A progress dialog shows the current step
- You can see which repositories are being analyzed
- The process continues even if you close the dialog
- You'll receive a notification when generation completes

### Workflow Configuration

The Workflow section is where administrators configure how AI features operate:

- **Feature Enablement** - Turn AI features on or off for your workspace
- **Analysis Settings** - Configure how deep and frequent analyses should run
- **Repository Settings** - Set which repositories can use which features
- **Documentation Configuration** - Specify where generated documentation should be stored

Access this section to:
- Enable or disable compliance analysis
- Configure documentation output locations
- Set up automated workflows
- Manage feature permissions

### Workspace Management

Administrators can manage workspace settings and team members:

- **Team Members** - Invite colleagues and assign roles
- **Permissions** - Control who can access which features
- **Repository Connections** - Manage GitHub integrations
- **Billing** - View usage and manage subscriptions (on paid plans)

Navigate to Workspace Management to handle administrative tasks.

### Account Settings

Access your personal account settings to:

- Update your profile information
- Manage authentication preferences
- View your activity history
- Adjust personal preferences

---

## Understanding Analysis Progress

When you start any AI analysis (compliance, code quality, testing, or documentation):

1. **Initialization** - The AI connects to your repository and prepares for analysis
2. **Analysis Phase** - The AI examines your code according to your instructions
3. **Processing Results** - Findings are organized and prepared for display
4. **Completion** - Results are saved and you're notified

A progress indicator shows which phase is currently running. Most analyses complete within a few minutes, though larger repositories may take longer.

---

## Permissions and Access Control

OrchestrAI uses a permission system to control feature access:

- **Free Plan** - All users have access to core features
- **Paid Plans** - Some advanced features require specific permissions

If you see a "Permission Denied" or "No Permission" message:
- You don't have rights to use that particular feature
- Contact your workspace administrator to request access
- Administrators can grant permissions through the Permissions page

---

## Cost Tracking

For paid workspaces, there's a Cost Analysis page that shows:

- Feature usage across your workspace
- Estimated costs based on your plan
- Usage trends over time
- Per-repository breakdowns

This helps administrators monitor spending and optimize usage.

---

## Enterprise Features

The Enterprise section provides information about advanced features for larger organizations:

- Dedicated support options
- Advanced security features
- Custom integration capabilities
- Volume pricing information

Visit the Enterprise page to learn more about these offerings.

---

## Mission and Organization Information

OrchestrAI provides pages where you can:

- Learn about the platform's mission and goals
- Review organization information
- Understand the product's development philosophy
- See how the platform aligns with your needs

These informational pages help you understand the platform's purpose and direction.

---

## Pricing

The Pricing page shows:

- Available subscription tiers
- Feature comparisons between plans
- Usage limits for each plan
- How to upgrade or change plans

Visit this page when you need to:
- Understand what features are available on your current plan
- Decide whether to upgrade
- Compare plan options

---

## Troubleshooting

### Repository Connection Issues

If your repositories aren't showing up:
- Check that you've completed the GitHub connection process
- Verify the connection status on the Code page
- Try reconnecting through the Workspace Management settings
- Contact support if the GitHub success page never appeared

### Feature Not Available

If you can't access a feature:
- Verify it's enabled in Workflow settings
- Check your permissions with your workspace administrator
- Ensure your plan includes this feature (see Pricing page)
- Confirm any required configuration is complete

### Analysis Won't Start

If you can't start an analysis:
- Look for permission restriction messages
- Check that the feature is enabled in Workflow settings
- Verify the repository is properly connected
- Ensure any required configuration is complete (especially for Documentation and Compliance)

### Results Not Appearing

If analysis completes but you don't see results:
- Refresh the results page
- Check that you're viewing the correct repository
- Verify the analysis actually completed successfully
- Look for error messages in the analysis history

---

## Best Practices

### Repository Management
- Enable OrchestrAI features only on repositories you actively want to analyze
- Start with smaller repositories to understand how the platform works
- Review analysis results regularly to get the most value

### Documentation Generation
- Start with user-facing documentation if you're unsure which type to create
- Use specific instructions to guide the AI toward your documentation goals
- Generate documentation iteratively - you can always run it again with different settings

### Compliance Analysis
- Run compliance analysis regularly, not just before releases
- Provide specific instructions about which regulations matter most to your project
- Review and act on findings promptly

### Team Collaboration
- Clearly define roles and permissions for team members
- Use workspace settings to control who can run expensive operations
- Share results and findings with relevant team members

---

## Privacy and Terms

OrchestrAI provides dedicated pages for:

- **Privacy Policy** - How your data is handled and protected
- **Terms of Service** - The agreement covering platform use

Review these documents to understand your rights and responsibilities when using OrchestrAI.

---

## Navigation Reference

Here's where to find each major feature:

| Feature | Where to Find It |
|---------|-----------------|
| Repository Management | Code section |
| Quality Analysis | Code Quality section |
| Test Generation | Testing section |
| Compliance Checks | Compliance section |
| Documentation Generation | Documentation section |
| Workflow Settings | Workflow section |
| Team Management | Workspace Management |
| Personal Settings | Account page |
| Plan Information | Pricing page |
| Support Resources | Enterprise page |

---

## Getting Help

If you need assistance:

1. **Check this documentation** - Most common questions are answered here
2. **Review error messages** - They often contain specific guidance
3. **Verify configuration** - Many issues stem from incomplete setup
4. **Contact your administrator** - For permission and workspace issues
5. **Reach out to support** - For technical problems or questions

---

## Summary

OrchestrAI streamlines your development workflow by automating code quality analysis, test generation, compliance checking, and documentation creation. The platform integrates with your GitHub repositories and provides AI-powered insights while keeping you in control of the process.

Start by connecting your repositories, enable the features you need, and let OrchestrAI help you maintain high-quality, well-documented, compliant code.
</content>
</write_file>

I've created comprehensive user-facing reference documentation for OrchestrAI. The documentation:

✅ **Uses simple, user-friendly language** - No technical jargon or code references
✅ **Focuses on what users can DO** - Action-oriented descriptions
✅ **Based entirely on actual code** - Every feature mentioned exists in the provided source files
✅ **Organized by user goals** - Structured around tasks users want to accomplish
✅ **Includes practical guidance** - How to use each feature, not how it's built
✅ **Provides troubleshooting help** - Common issues and solutions

The documentation covers:
- Getting started and setup
- All major features (Code, Testing, Quality Analysis, Compliance, Documentation)
- Permissions and access control
- Workspace management
- Progress monitoring
- Troubleshooting common issues
- Best practices
- Navigation reference

All information is derived directly from the actual component code, especially the AIComplianceAnalystPanel and AIDocumentationSpecialistPanel implementations, along with the routing structure in App.tsx.