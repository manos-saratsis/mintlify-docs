I'll start by reading the critical files to understand the product and generate FAQ documentation.# Frequently Asked Questions

## Getting Started

### What is OrchestrAI?

OrchestrAI is a platform that helps make your code more ready for production by automating essential quality assurance tasks including testing, code quality analysis, compliance checking, security scanning, documentation generation, and instrumentation.

### How do I get started with OrchestrAI?

Getting started is simple:

1. Create an account and sign in
2. Connect your Git management tool (currently GitHub)
3. Enable OrchestrAI for your repositories
4. Choose which production readiness features you want to use

Once set up, you can run analyses on demand or configure automated workflows.

### Do I need to connect a Git repository to use OrchestrAI?

Yes, OrchestrAI works by analyzing and improving your code repositories. You'll need to connect your GitHub account and enable at least one repository to use the platform's features.

### What Git management tools are supported?

Currently, OrchestrAI supports GitHub. Integrations with GitLab and Bitbucket are coming soon.

### How do I enable OrchestrAI for my repositories?

After connecting your GitHub account, navigate to the Code page where you'll see a list of your repositories. From there, you can enable OrchestrAI for the repositories you want to work with.

### What is the OrchestrAI Bot and do I need it?

The OrchestrAI Bot is a GitHub application that allows OrchestrAI to interact with your repositories, create pull requests, and commit changes. While you can analyze your code without it, you'll need to install the bot to receive automated code improvements and updates directly in your repositories.

## Billing & Credits

### What is a credit?

Credits are used when OrchestrAI analyzes or performs actions on your code, either on demand or as part of automated workflows. It's usage-based pricing where requests can cost less than 1 credit or several credits, depending on their complexity. This ensures you only pay for what you actually use.

Since OrchestrAI agents perform many analyses, process multiple files, and write code or documentation, each action can have a different cost for different situations.

### What does the Free plan include?

The Free plan includes:
- 50 credits per month
- 1 public repository
- 5 collaborators
- No daily restrictions

With 50 credits, you can run approximately 3-4 complete AI workflows per month. Credits reset at the beginning of each month.

### What does the Pro plan include?

The Pro plan includes everything in the Free plan, plus:
- Flexible monthly credit allocation (100 to 5,000+ credits)
- All your public and private repositories
- Unlimited collaborators
- Role-based access control

Pricing starts at $25/month for 100 credits, with the rate at $0.25 per credit.

### How do I choose how many credits I need?

When selecting a Pro plan, you can choose from preset credit amounts ranging from 100 to 5,000 credits per month. The more credits you select, the more analyses and actions OrchestrAI can perform. You can adjust your credit allocation at any time by editing your plan.

### Can I forecast how many credits I'll need?

A forecasting feature is coming soon that will help you estimate the approximate costs of a workflow or analysis before you run it. This will help you better plan your credit usage.

### What happens if I run out of credits?

If you reach your monthly credit limit, you won't be able to run new analyses or workflows until your credits reset at the beginning of the next month, or until you upgrade your plan to include more credits.

### How do I upgrade or change my plan?

To upgrade or change your plan:
1. Go to the Pricing page
2. Select your desired credit amount
3. Click "Edit Plan"
4. You'll be directed to the Cost Analysis page to review and confirm your changes

### Can I see my credit usage history?

Yes! Visit your Account page where you can view your workspaces and click the "Usage" button next to any workspace to see detailed credit usage history by month.

### How do I view my workspace costs?

From your Account page, click the "Cost Analysis" button next to any workspace to see detailed billing information, usage trends, and plan management options.

## Features & Capabilities

### What production readiness features does OrchestrAI provide?

OrchestrAI covers the complete production readiness journey:
- **Testing**: Generate comprehensive unit tests
- **Code Quality**: Analyze code for quality issues and best practices
- **Compliance**: Check for compliance issues and regulatory requirements
- **Security**: Scan for security vulnerabilities with remediation advice
- **Documentation**: Generate and manage comprehensive documentation
- **Instrumentation**: Add observability and monitoring capabilities

### How does unit testing work?

The Unit Testing feature generates comprehensive tests for your codebase to ensure reliability and catch bugs early. OrchestrAI analyzes your code and creates test cases that can be submitted as pull requests to your repository.

### What does code quality analysis include?

Code Quality analysis examines your code for quality issues, best practices violations, and potential improvements. You'll receive a quality score and detailed findings about issues that need attention.

### What compliance standards does OrchestrAI check for?

The Compliance feature checks your code for compliance issues and regulatory requirements. You'll receive a compliance score and specific findings about any issues detected.

### How does security scanning work?

Code Security scans your codebase for security vulnerabilities and provides actionable remediation advice. You'll receive a security score and detailed information about any vulnerabilities found, including their severity and how to fix them.

### What kind of documentation can OrchestrAI generate?

The Documentation feature can generate and manage comprehensive documentation for your codebase. You can create documentation plans with multiple tasks and track progress as each documentation piece is completed.

### What is instrumentation and why do I need it?

Instrumentation adds observability and monitoring capabilities to your code, making it easier to understand how your application behaves in production. OrchestrAI can automatically add instrumentation to help you monitor performance, track errors, and gain insights into your application's behavior.

### Can I automate OrchestrAI workflows?

Yes! You can configure automated workflows that run OrchestrAI's production readiness features continuously. This provides ongoing quality assurance without manual intervention.

### What programming languages and frameworks are supported?

OrchestrAI works with code in GitHub repositories. The specific languages and frameworks supported depend on the feature you're using. Each analysis adapts to your codebase's technology stack.

### Are there limits on repository size?

Repository size limits may apply depending on your plan. The Free plan supports 1 public repository, while Pro plans support all your public and private repositories.

## Account & Workspace Management

### What is a workspace?

A workspace is an organizational unit in OrchestrAI that contains your repositories, team members, billing information, and configuration settings. Each workspace has its own plan and credit allocation.

### Can I have multiple workspaces?

Yes, you can create and manage multiple workspaces. Each workspace operates independently with its own plan, repositories, and team members.

### What is role-based access?

Role-based access (available on Pro plans) ensures that workspace members can only access the resources and actions they're authorized to use. This includes:
- Ability to approve workflows for release
- Operating and calling AI agents based on user role
- Audit logs of user actions (coming soon)

### How do I invite team members to my workspace?

The Free plan supports up to 5 collaborators, while Pro plans support unlimited collaborators. Team management features allow you to invite members and assign appropriate roles.

### Can I switch between workspaces?

Yes, if you belong to multiple workspaces, you can switch between them to access different repositories and configurations.

## Code Ownership & Integration

### Who owns the code and documentation that OrchestrAI generates?

You do. All code and documentation generated by OrchestrAI belongs to you. You can collaborate at the source or check out your changes using Git management tools like GitHub (with GitLab and Bitbucket integrations coming soon).

### How does OrchestrAI integrate with my existing workflow?

OrchestrAI integrates directly with your Git repositories. When enabled, it can create pull requests, commit changes, and work within your existing development workflow without disrupting your team's processes.

### Can I review changes before they're applied?

Yes, OrchestrAI typically submits changes as pull requests, allowing you to review, discuss, and approve changes before merging them into your codebase.

### Where can I see the results of OrchestrAI analyses?

Analysis results are available in the OrchestrAI platform for each feature. Additionally, when the OrchestrAI Bot is installed, results may be delivered as pull requests or commits in your GitHub repository, including links to view the changes directly.

## Troubleshooting

### Why can't I see my repositories?

If you don't see your repositories after connecting GitHub:
1. Ensure you've completed the GitHub connection process
2. Check that you granted OrchestrAI the necessary permissions
3. Try refreshing the page or reconnecting your Git account from the Code page

### Why does it say I have no enabled repositories?

After connecting GitHub, you need to explicitly enable OrchestrAI for the repositories you want to work with. Visit the Code page to enable your repositories.

### How do I know if my Git connection is working?

On your main dashboard, you'll see configuration status showing your Git connections count and enabled repositories. A properly configured setup will show at least 1 Git connection and 1 enabled repository.

### What should I do if an analysis fails?

If an analysis fails:
1. Check your credit balance to ensure you have sufficient credits
2. Review the error message for specific details
3. Verify that the OrchestrAI Bot has proper permissions on your repository
4. Try running the analysis again

### Why is the "Install Bot" button showing?

The "Install Bot" button appears when the OrchestrAI Bot is not yet installed for your repositories. Installing the bot is necessary for OrchestrAI to create pull requests and commit changes to your repositories.

### How do I check my workspace billing status?

Visit your Account page to see all your workspaces along with their billing status. Statuses include:
- **Active**: Your workspace is operating normally
- **Reached limits**: You've used all available credits for the current period
- **Paused**: Your workspace is temporarily paused
- **Closed**: Your workspace has been closed

### What does "reached limits" billing status mean?

This means you've used all your monthly credits. You can either wait until credits reset at the beginning of the next month or upgrade your plan to add more credits immediately.

### How do I contact support?

If you can't find answers to your questions in this FAQ or need additional help, please reach out to OrchestrAI support through your account dashboard.