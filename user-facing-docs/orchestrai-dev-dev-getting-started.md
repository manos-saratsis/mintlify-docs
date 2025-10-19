I'll analyze the provided source code and create a comprehensive Getting Started guide for orchestrai-dev.

<read_file>
<path>src/pages/Index.tsx</path>
</read_file>

<read_file>
<path>src/contexts/AuthContext.tsx</path>
</read_file>

<read_file>
<path>src/contexts/WorkspaceContext.tsx</path>
</read_file>

<read_file>
<path>src/pages/Product.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductCode.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductTesting.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductCodeQuality.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductCompliance.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductDocumentation.tsx</path>
</read_file>

<read_file>
<path>src/pages/WorkspaceManagement.tsx</path>
</read_file>

<read_file>
<path>src/components/WelcomeModal.tsx</path>
</read_file>

<read_file>
<path>src/hooks/useWelcomeModal.ts</path>
</read_file>

Based on my analysis of the source code, I'll now create comprehensive Getting Started documentation for orchestrai-dev.

---

# orchestrai-dev - Getting Started

**Overview**:
OrchestrAI is an AI-powered development platform that helps you automate testing, analyze code quality, ensure compliance, and generate documentation for your software projects. This guide will walk you through your first steps with the platform, from signing in to running your first AI-powered analysis.

**Getting Started with OrchestrAI**:

## Your First Visit

When you first arrive at OrchestrAI, you'll be greeted with a welcome screen that introduces you to the platform's capabilities. The platform is built around AI specialists that work together to improve your code quality, testing, compliance, and documentation.

### Signing In

1. Visit the OrchestrAI website
2. Click the sign-in button to access the platform
3. You'll be authenticated and taken to your workspace

The application uses secure authentication to protect your account and code repositories. Once signed in, you'll have access to all the AI-powered tools.

## Understanding Workspaces

Think of a workspace as your project's home in OrchestrAI. Everything you do - connecting repositories, running analyses, managing team members - happens within a workspace.

### Your First Workspace

When you first sign in, the platform creates a personal workspace for you automatically. This workspace includes:
- Your GitHub repositories
- AI analysis results
- Documentation
- Team settings (if you invite others)

You can create additional workspaces for different projects or organizations from the workspace management area.

## Connecting Your Code

Before the AI can help you, it needs access to your code repositories.

### Connecting GitHub

1. Navigate to the Code section from the main menu
2. Click the "Connect GitHub" button
3. Authorize OrchestrAI to access your repositories
4. Select which repositories you want to enable for AI analysis

After connecting, you'll see a list of your repositories. Each repository can be individually enabled or disabled for OrchestrAI analysis.

### Repository Setup

For each repository you want to work with:
1. Find it in your repository list
2. Toggle the "Enable OrchestrAI" switch
3. The repository is now ready for AI-powered analysis

## Running Your First Analysis

OrchestrAI offers several types of AI-powered analysis. Let's start with code quality analysis, which gives you immediate insights into your codebase.

### Code Quality Analysis

1. Go to the Code Quality section
2. Select a repository from your connected repositories
3. Click "Start Analysis"
4. The AI Quality Engineer will analyze your code

The analysis examines:
- Code complexity and maintainability
- Potential bugs and code smells
- Security vulnerabilities
- Best practice violations

You'll see a progress indicator while the AI works. This typically takes a few minutes depending on your repository size.

### Understanding Results

Once complete, you'll see:
- An overall quality score for your repository
- Detailed findings organized by severity
- Specific file locations where issues were found
- AI-generated recommendations for improvements

Each finding includes:
- **What**: A clear description of the issue
- **Where**: The file and line number
- **Why**: Why it matters for your code quality
- **How**: Suggested fixes

## Generating Tests

The AI Test Engineer can automatically create tests for your code.

### Creating Your First Tests

1. Navigate to the Testing section
2. Choose a repository
3. Click "Generate Tests"
4. Provide any specific instructions (optional)

The AI will:
- Analyze your code structure
- Identify functions and components that need testing
- Generate appropriate test cases
- Create test files in your testing framework

The generated tests are committed directly to your repository, ready to run.

### Test Coverage

After generating tests, you can:
- View which parts of your code are covered
- See suggestions for additional test scenarios
- Run the tests to verify everything works

## Checking Compliance

For projects that need to meet regulatory requirements, the Compliance Analyst helps ensure your code follows necessary standards.

### Running a Compliance Check

1. Visit the Compliance section
2. Select your repository
3. Click "Start Compliance Analysis"
4. Add any specific compliance requirements in the instructions

The AI examines your code for:
- Data privacy practices
- Access control implementation
- Audit trail capabilities
- Encryption usage
- Security best practices

### Compliance Reports

Results show:
- Compliance status for each requirement
- Areas that need attention
- Specific code locations to review
- Remediation suggestions

## Creating Documentation

The Documentation Specialist can create comprehensive documentation for your project.

### Generating Documentation

You have two options:

**Create New Documentation:**
1. Go to the Documentation section
2. Click "Create Documentation"
3. Choose what to document (User guides, API reference, etc.)
4. The AI analyzes your product and creates documentation

**Migrate Existing Documentation:**
1. If you already have documentation, click "Migrate"
2. Provide your documentation URL
3. The AI restructures it according to best practices

### Documentation Types

You can generate:
- **User-facing documentation**: Guides and tutorials for your users
- **Internal documentation**: Technical docs for developers
- **API reference**: Automatically generated from your code
- **SBOM**: Software Bill of Materials

### Customizing Your Documentation

Before generating, you can select:
- Which sections to include (intro, tutorials, reference, etc.)
- Specific repositories to document
- Whether to document the full repository or specific commits
- Additional instructions for the AI

## Managing Your Workspace

The Workspace Management area lets you control your OrchestrAI environment.

### Team Collaboration

If you're working with a team:
1. Go to Workspace Management
2. Invite team members by email
3. Assign roles and permissions
4. Each member can access shared repositories and analyses

### Permissions

Control what team members can do:
- **Admin**: Full access to everything
- **Member**: Can run analyses and view results
- **Viewer**: Can only view results

Permissions are set per workspace and can be customized for different features.

## Workflow Configuration

Configure how AI specialists work for your project.

### Setting Up Workflows

1. Visit the Workflow section
2. For each AI specialist (Testing, Quality, Compliance, Documentation):
   - Enable or disable the feature
   - Choose whether AI can make automatic fixes
   - Set specific instructions
   - Configure output locations

### Automatic vs. Manual

You can configure each AI specialist to:
- **Analysis Only**: AI reviews code and reports findings
- **Analysis and Fix**: AI can automatically create pull requests with fixes

## Tips for Success

### Starting Small
Begin with one or two repositories and one type of analysis. This helps you understand how OrchestrAI works before expanding to your entire codebase.

### Clear Instructions
When running analyses, provide specific instructions. Instead of "analyze my code," try "focus on security vulnerabilities in authentication logic."

### Review AI Suggestions
The AI is powerful but should work with you, not replace you. Always review generated tests, suggested fixes, and documentation before accepting them.

### Use Checkpoints
For long-running tasks, OrchestrAI saves checkpoints. If something interrupts the process, you can resume from where it left off instead of starting over.

### Iterate
Your first analysis might surface many findings. Don't try to fix everything at once. Address critical issues first, then work through recommendations incrementally.

## Common Workflows

### Daily Development
1. Make code changes in your repository
2. Run Code Quality analysis to catch issues early
3. Generate or update tests for new features
4. Review and address any findings

### Release Preparation
1. Run Compliance analysis to ensure regulatory requirements are met
2. Update documentation to reflect new features
3. Run comprehensive Code Quality checks
4. Generate final test coverage reports

### Onboarding New Team Members
1. Share your workspace with the new developer
2. Point them to your generated documentation
3. They can immediately understand the codebase through AI-generated insights
4. Grant appropriate permissions for their role

## What's Next?

Now that you've completed your first analysis, explore:
- **Cost tracking**: Monitor AI usage and costs per workspace
- **Account settings**: Customize your profile and preferences
- **Pricing plans**: Upgrade for more features and higher usage limits
- **Product information**: Configure organizational details for better documentation

## Getting Help

If you encounter issues or have questions:
- Check the product documentation sections for detailed guides
- Review compliance and quality reports for specific guidance
- Ensure your GitHub connection is active and repositories are enabled
- Verify workspace permissions if team members can't access features

## Privacy and Security

OrchestrAI takes security seriously:
- Your code is analyzed securely
- Authentication tokens are encrypted
- Repository access follows GitHub's permission model
- You control what OrchestrAI can access

Your data remains yours. The platform only accesses what you explicitly authorize.

---

Welcome to OrchestrAI! Start with a simple code quality check, explore the results, and gradually discover how AI specialists can transform your development workflow. The platform grows with you, from individual projects to team collaboration to organization-wide automation.