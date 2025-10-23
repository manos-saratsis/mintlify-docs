I'll analyze the source code and generate comprehensive reference documentation for the orchestrai-dev project. Let me start by exploring the codebase structure.

<think>
Looking at the provided source code, I can see:

1. Main App component (App.tsx) - Routes and application structure
2. ESLint and PostCSS configuration files
3. Several test files for various components
4. Two major AI agent panels:
   - AIComplianceAnalystPanel.tsx
   - AIDocumentationSpecialistPanel.tsx

The project appears to be a React/TypeScript application focused on AI-powered development tools with:
- Compliance analysis
- Documentation generation
- Code quality analysis
- Testing capabilities
- Workspace and permission management

I need to create user-facing documentation that:
- Avoids technical jargon
- Explains features in simple terms
- Describes what users can DO, not how it's built
- Uses everyday language

Let me create comprehensive reference documentation for the main features I can identify from the code.
</think>

<read_file>
<path>src/pages</path>
</read_file>

Let me check what pages are available to understand the full feature set:

<list_files>
<path>src</path>
<recursive>false</recursive>
</list_files>

<read_file>
<path>src/contexts/WorkspaceContext.tsx</path>
</read_file>

<read_file>
<path>src/contexts/AuthContext.tsx</path>
</read_file>

Now I'll create comprehensive reference documentation based on the actual features found in the code.

---

# OrchestrAI Reference Documentation

## Overview

OrchestrAI is an AI-powered platform that helps development teams automate quality assurance, testing, compliance, and documentation tasks. The platform uses specialized AI agents to analyze your code, generate tests, ensure compliance with regulations, and create comprehensive documentation - all automatically.

## Getting Started

### Accessing the Platform

When you first visit OrchestrAI, you'll land on the homepage where you can explore the platform's capabilities. To start using the AI-powered features, you'll need to:

1. Create an account or sign in
2. Set up your workspace
3. Connect your code repositories

### Your First Steps

After signing in, you'll be guided through a welcome process that helps you:
- Set up your organization information
- Define your team's mission and goals
- Connect to your code repositories (like GitHub)
- Configure your preferences

## Core Features

### Workspaces

**What it is:** A workspace is your team's central hub where all your projects, code, and AI agents work together.

**What you can do:**
- Create separate workspaces for different teams or projects
- Invite team members and assign roles
- Manage permissions for who can access different features
- Monitor costs and usage across your workspace

**How to use it:**
Navigate to the Workspace Management section from the main menu to create and manage your workspaces. You can switch between workspaces using the selector at the top of the screen.

### Code Management

**What it is:** Connect your code repositories so the AI agents can analyze and work with your code.

**What you can do:**
- Link repositories from GitHub
- Enable or disable AI features for specific repositories
- View repository status and activity
- Monitor which repositories are being analyzed

**How to use it:**
Go to the Code section and click the connect button. You'll be guided through authorizing OrchestrAI to access your repositories. Once connected, you can enable AI features for each repository individually.

### AI Compliance Analyst

**What it is:** An AI agent that examines your code to ensure it meets regulatory requirements and compliance standards.

**What you can do:**
- Run compliance checks on your repositories
- Get detailed reports about compliance issues
- Receive recommendations for fixing compliance problems
- Focus on specific compliance areas like data privacy, access control, or encryption

**How to use it:**
1. Go to the Compliance section
2. Select a repository to analyze
3. Choose your compliance focus areas
4. Click "Start Analysis"
5. View your compliance report when complete

**What happens:**
The AI will scan through your code, looking for potential compliance issues. It checks things like:
- How you handle sensitive data
- Whether you have proper access controls
- If encryption is used correctly
- Whether audit trails are in place

You'll receive a detailed report showing what's compliant and what needs attention.

### AI Documentation Specialist

**What it is:** An AI agent that creates and maintains documentation for your product by analyzing your code and understanding what it does.

**What you can do:**
- Generate documentation automatically from your code
- Migrate existing documentation to a better structure
- Create user guides, API references, and developer documentation
- Keep documentation in sync with code changes
- Choose specific sections to generate (like tutorials, how-to guides, or troubleshooting)

**How to use it:**
1. Go to the Documentation section
2. Choose whether to create new documentation or migrate existing docs
3. Select what types of documentation you want:
   - User-facing guides
   - Internal developer documentation
   - Software Bill of Materials (SBOM)
4. Pick which parts to include:
   - Quick start guides
   - Tutorials
   - How-to guides
   - API reference
   - Concepts and architecture
   - Troubleshooting guides
   - Release notes
5. Add any specific instructions
6. Click "Generate Documentation"

**What happens:**
The AI will:
- Analyze your product to understand how it works
- Review any existing documentation you have
- Create well-organized documentation in the structure you chose
- Save the documentation to your repository

### Code Quality Analysis

**What it is:** Tools that evaluate your code's quality, identify issues, and suggest improvements.

**What you can do:**
- Check code for potential bugs and problems
- Get suggestions for making code easier to maintain
- Identify complex areas that might need simplification
- Monitor code quality over time

**How to use it:**
Navigate to the Code Quality section, select a repository, and run an analysis. You'll see quality scores and specific recommendations for improvements.

### Testing

**What it is:** AI-powered test generation and execution for your code.

**What you can do:**
- Generate tests automatically for your code
- Run tests and see results
- Track test coverage
- Identify areas that need more testing

**How to use it:**
Go to the Testing section, select your code, and ask the AI to generate tests. You can then run those tests and see what passes or fails.

### Workflow Automation

**What it is:** Configure how the AI agents work together and what actions they can take automatically.

**What you can do:**
- Set up which AI features are enabled
- Configure automatic actions (like fixing issues vs. just reporting them)
- Customize how each AI agent behaves
- Set up rules for when agents should run

**How to use it:**
Visit the Workflow section to see all available AI features. For each feature, you can:
- Turn it on or off
- Choose whether it should just analyze or also fix issues
- Add custom instructions for how it should work
- Configure where results should be saved

## Permissions and Access Control

### User Roles

Your workspace can have different types of users with different permissions:

**Admins** - Full control over the workspace, can:
- Manage all settings
- Add or remove users
- Configure all AI features
- Access all repositories and reports

**Team Members** - Can use AI features but with limitations based on assigned permissions

### Managing Permissions

Navigate to the Permissions section to:
- See who has access to what
- Grant or restrict access to specific features
- Set up approval workflows
- Control AI agent capabilities per user

## Account Management

### Your Profile

Access your account settings to:
- Update your personal information
- Change your password
- Manage notification preferences
- View your usage and activity

### Billing and Pricing

OrchestrAI offers different plans:

**Free Plan** - Get started with basic features to try the platform

**Paid Plans** - Access advanced features, higher usage limits, and priority support

Go to the Pricing section to see all available plans and upgrade options.

## Understanding AI Agent Progress

When an AI agent is working, you'll see progress updates showing:

- **Initializing** - The agent is preparing to start
- **Analyzing** - The agent is examining your code
- **Generating** - The agent is creating results (like tests or documentation)
- **Committing** - The agent is saving changes to your repository
- **Complete** - The agent has finished

You can watch progress in real-time and see detailed logs of what the agent is doing.

## Repository Connection

### Connecting GitHub

To connect your GitHub repositories:

1. Click the connect button in the Code section
2. You'll be redirected to GitHub to authorize access
3. Choose which repositories to grant access to
4. Return to OrchestrAI - your repositories will now appear
5. Enable AI features for the repositories you want to analyze

### Managing Repository Settings

For each connected repository, you can:
- Enable or disable AI feature access
- View connection status
- Disconnect repositories you no longer want to analyze
- See when the repository was last analyzed

## Resuming Interrupted Work

If an AI agent's work is interrupted (due to network issues, errors, or other problems), OrchestrAI automatically saves checkpoints. This means:

- The AI can pick up where it left off instead of starting over
- Your previous configuration and progress are preserved
- You can resume with one click

When resuming, you'll see an indicator showing that the AI is continuing from a saved checkpoint.

## Viewing Results

### Compliance Results

After a compliance analysis completes:
1. Navigate to the Compliance Results page
2. See an overview of compliance status
3. Review detailed findings by category
4. Read specific recommendations for fixes
5. Track progress on addressing issues

### Documentation Output

Generated documentation is automatically committed to your repository in the location you specified. You can:
- View it directly in your repository
- See it rendered on your documentation site
- Make additional edits if needed
- Let the AI update it as your code changes

### Code Quality Reports

Quality analysis results show:
- Overall quality scores
- Specific issues found
- Complexity metrics
- Maintainability ratings
- Recommendations for improvement

## Cost Monitoring

Keep track of your AI agent usage:
- View usage by workspace
- See costs broken down by feature
- Monitor trends over time
- Set up alerts for usage limits

Access cost analysis from the workspace menu or account settings.

## Tips for Best Results

### Writing Instructions for AI Agents

When providing instructions to an AI agent:
- Be specific about what you want
- Mention any special requirements or focus areas
- Describe the context of your project
- Note any standards or conventions to follow

Example: "Focus on data privacy compliance for healthcare applications, paying special attention to HIPAA requirements."

### Choosing Repository Scope

When running documentation or analysis:
- **Full Repository** - Analyzes everything, best for comprehensive updates
- **Specific Commit** - Focuses on recent changes, faster and more targeted

Choose based on whether you want a complete analysis or just want to document recent changes.

### Organizing Workspaces

For best results:
- Create separate workspaces for different products or teams
- Keep related repositories together in one workspace
- Regularly review and update workspace permissions
- Use workspace settings to standardize AI agent behavior

## Troubleshooting

### AI Agent Doesn't Start

If an AI agent won't start:
- Check that the feature is enabled in Workflow settings
- Verify you have permission to use that feature
- Ensure the repository is connected and accessible
- Check that required configuration is complete

### Repository Connection Issues

If you can't connect a repository:
- Verify you have admin access to the repository on GitHub
- Check that the authorization hasn't expired
- Try disconnecting and reconnecting
- Contact support if the issue persists

### Missing Results

If you don't see results after an analysis:
- Check that the analysis completed successfully
- Verify you're looking in the correct workspace
- Ensure you have permission to view results
- Look for error messages in the activity log

### Permission Errors

If you see "permission denied" messages:
- Contact your workspace administrator
- Check which role you have in the workspace
- Verify that your specific permissions include the feature you're trying to use
- Ask your admin to update your permissions if needed

## Privacy and Security

OrchestrAI takes security seriously:
- All connections to code repositories are encrypted
- Sensitive tokens are stored securely in a vault
- AI agents only access repositories you explicitly authorize
- You can revoke access at any time
- Audit logs track all actions taken by AI agents

For full details, see the Privacy Policy and Terms of Service linked in the footer.

## Getting Help

Need assistance?
- Check this documentation for answers to common questions
- Contact your workspace administrator for permission issues
- Review the activity logs to understand what went wrong
- Reach out to support for technical problems

## Feature Availability

Some features may require:
- A paid subscription plan
- Specific permissions in your workspace
- Admin approval or configuration
- Repository access with appropriate scope

Check the Pricing page for details on what's included in each plan.

---

This documentation describes the features available in OrchestrAI as of the current version. Features and capabilities are continuously being improved based on user feedback and technological advances.