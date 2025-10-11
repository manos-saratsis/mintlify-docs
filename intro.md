# Quick Start Guide

OrchestRAI is a comprehensive AI-powered software development platform that provides automated code quality analysis, test generation, compliance monitoring, and documentation generation for your GitHub repositories. Built as a modern web application using React and TypeScript, OrchestRAI streamlines the entire software development lifecycle by integrating intelligent AI agents that work together to improve code quality, ensure compliance, and maintain comprehensive documentation.

The platform is designed for development teams who want to maintain high code quality standards while reducing manual overhead. Whether you're working on a small project or managing enterprise-level repositories, OrchestRAI provides the tools and insights needed to deliver reliable, maintainable software. The platform integrates seamlessly with GitHub, analyzing your existing repositories and providing actionable insights through an intuitive web interface.

This quick start guide will walk you through the essential steps to get up and running with OrchestRAI, from initial account setup to running your first automated analysis. By the end of this guide, you'll have connected your GitHub repositories and experienced the power of AI-driven code analysis firsthand.

## System Requirements and Prerequisites

Before getting started with OrchestRAI, ensure your development environment meets the following requirements:

### Browser Compatibility
OrchestRAI is optimized for modern web browsers and requires:
- Google Chrome (version 90+)
- Mozilla Firefox (version 88+)
- Safari (version 14+)
- Microsoft Edge (version 90+)

JavaScript must be enabled in your browser, as the application is built using React (`src/App.tsx`) and relies heavily on client-side functionality.

### GitHub Account Requirements
You'll need:
- An active GitHub account with repository access
- Administrative permissions for repositories you want to analyze
- GitHub OAuth app permissions (granted during the connection process)

The platform connects to GitHub through OAuth authentication, implemented in the `AuthModal` component (`src/components/AuthModal.tsx`), which handles both sign-in and sign-up flows.

### Network Requirements
Ensure your network allows:
- HTTPS connections to orchestrai.dev
- WebSocket connections for real-time updates
- Access to GitHub's API endpoints
- Supabase backend connections for data persistence

## Account Creation and Authentication

### Creating Your OrchestRAI Account

1. **Navigate to the Platform**
   Visit [https://orchestrai.dev/](https://orchestrai.dev/) in your web browser. The landing page (`src/pages/Index.tsx`) provides an overview of the platform's capabilities and includes prominent call-to-action buttons for getting started.

2. **Access the Authentication Modal**
   Click the "Get Started" or "Sign Up" button to open the authentication modal. The `AuthModal` component (`src/components/AuthModal.tsx`) handles both new user registration and existing user sign-in.

3. **Choose Your Registration Method**
   OrchestRAI offers multiple authentication options:
   - **Email and Password**: Enter your email address and create a secure password
   - **GitHub OAuth**: Connect directly using your GitHub credentials (recommended for seamless repository integration)
   - **Google OAuth**: Use your Google account for quick access

4. **Complete Email Verification**
   If registering with email, check your inbox for a verification email. Click the verification link to activate your account. The authentication system is powered by Supabase Auth, which handles email verification automatically.

5. **Set Up Your Profile**
   After successful authentication, you'll be prompted to complete your profile information. This includes your display name, organization (optional), and initial workspace preferences.

### First-Time Login Experience

New users are greeted with the `WelcomeModal` component (`src/components/WelcomeModal.tsx`), which provides a guided introduction to the platform's key features. The welcome flow includes:

- **Platform Overview**: Introduction to AI agents and their capabilities
- **Workspace Setup**: Creating your first workspace for organizing projects
- **Integration Options**: Overview of available third-party integrations
- **Quick Tour**: Interactive walkthrough of the main interface

The modal system uses the `useWelcomeModal` hook (`src/hooks/useWelcomeModal`) to track user onboarding progress and ensure new users receive appropriate guidance.

## Workspace Setup and Configuration

### Understanding Workspaces

Workspaces in OrchestRAI serve as organizational containers for your projects and repositories. The `WorkspaceProvider` context (`src/contexts/WorkspaceContext`) manages workspace state throughout the application, providing access to workspace-specific settings, permissions, and resources.

### Creating Your First Workspace

1. **Access Workspace Management**
   After initial login, navigate to the workspace creation flow. The system automatically prompts new users to create their first workspace as part of the onboarding process.

2. **Configure Workspace Settings**
   Provide the following information:
   - **Workspace Name**: Choose a descriptive name for your workspace
   - **Organization**: Optionally associate the workspace with your organization
   - **Default Settings**: Configure default analysis settings for repositories added to this workspace

3. **Set Permission Levels**
   Configure who can access your workspace and what actions they can perform. The `useWorkspaceFunctionPermissions` hook (`src/hooks/useWorkspaceFunctionPermissions`) manages these permissions across different platform features.

### Workspace-Specific Features

Each workspace provides access to:
- **Repository Management**: Connect and manage GitHub repositories
- **AI Agent Configuration**: Customize how AI agents analyze your code
- **Team Collaboration**: Invite team members and assign roles
- **Compliance Profiles**: Set up compliance standards for your projects
- **Report Generation**: Access historical analysis reports and trends

## GitHub Repository Connection

### Connecting to GitHub

The repository connection process is handled through the `RepositoryConnectionModal` component (`src/components/RepositoryConnectionModal.tsx`) and the main code management interface.

1. **Navigate to Code Management**
   From the main dashboard, click on "Code" in the navigation menu. This takes you to the code management page (`src/pages/ProductCode.tsx`), which serves as the central hub for repository management.

2. **Initiate GitHub Connection**
   On the code page, you'll see a "Connect GitHub" button if you haven't connected your account yet. The `CodePageContent` component (`src/components/CodePageContent.tsx`) manages the connection state and displays appropriate UI based on your connection status.

3. **Authorize OrchestRAI**
   Clicking "Connect GitHub" redirects you to GitHub's OAuth authorization page. You'll need to grant OrchestRAI permission to:
   - Read repository metadata
   - Access repository contents
   - Read organization membership (if applicable)
   - Access commit history and branch information

4. **Repository Discovery**
   After successful authorization, OrchestRAI automatically discovers all repositories you have access to. The system displays both public and private repositories, with clear indicators of your access level for each.

### Repository Selection and Management

The `RepositoryManagement` component (`src/components/RepositoryManagement.tsx`) provides comprehensive tools for managing your connected repositories:

1. **Repository Listing**
   All accessible repositories are displayed in a table format with the following information:
   - Repository name and description
   - Visibility (public/private)
   - Primary programming language
   - Last activity timestamp
   - Current analysis status

2. **Enabling Repositories for Analysis**
   Select which repositories you want to include in OrchestRAI analysis by toggling the enable/disable switch for each repository. The `CodeQualityRepositoryTable` component (`src/components/CodeQualityRepositoryTable.tsx`) manages repository enablement and displays analysis status.

3. **Repository Configuration**
   For each enabled repository, configure:
   - **Analysis Frequency**: How often to run automated analysis
   - **Branch Selection**: Which branches to monitor (main, develop, etc.)
   - **AI Agent Settings**: Customize which AI agents analyze this repository
   - **Notification Preferences**: Set up alerts for analysis results

## Running Your First Analysis

### Automated Code Quality Analysis

With repositories connected and configured, you can run your first analysis using the AI Quality Engineer agent:

1. **Access the AI Quality Engineer Panel**
   Navigate to an enabled repository and click the "Analyze" button. This opens the `AIQualityEngineerPanel` component (`src/components/AIQualityEngineerPanel.tsx`), which provides comprehensive code quality analysis capabilities.

2. **Configure Analysis Parameters**
   The panel allows you to customize the analysis:
   - **Scope**: Select specific files, directories, or analyze the entire repository
   - **Quality Dimensions**: Choose which aspects to analyze (readability, maintainability, reliability, security, efficiency, testability)
   - **Severity Levels**: Set thresholds for different types of issues
   - **Custom Instructions**: Provide specific guidance for the AI agent

3. **Monitor Analysis Progress**
   The `CodeQualityProgressDialog` component (`src/components/CodeQualityProgressDialog.tsx`) displays real-time progress updates as the analysis runs. The process includes:
   - Repository cloning and preparation
   - File discovery and categorization
   - AI-powered code analysis
   - Report generation and scoring
   - Results storage and indexing

4. **Review Analysis Results**
   Once complete, results are displayed in the `CodeQualityTable` component (`src/components/CodeQualityTable.tsx`), showing:
   - Overall quality scores across six dimensions
   - File-level analysis results
   - Identified issues and recommendations
   - Historical trends and comparisons

### Understanding Quality Metrics

OrchestRAI evaluates code across six key dimensions:

- **Readability (0-100)**: How easy the code is to understand
- **Maintainability (0-100)**: How easy the code is to modify and extend
- **Reliability (0-100)**: How dependable and error-free the code is
- **Security (0-100)**: How well the code protects against vulnerabilities
- **Efficiency (0-100)**: How well the code performs and uses resources
- **Testability (0-100)**: How easy the code is to test thoroughly

Each dimension includes detailed notes accessible through the `CodeQualityNotesDialog` component (`src/components/CodeQualityNotesDialog.tsx`), providing specific feedback and improvement suggestions.

### Automated Test Generation

Experience the AI Test Engineer capabilities:

1. **Open the Test Engineer Panel**
   Access the `AITestEngineerPanel` component (`src/components/AITestEngineerPanel.tsx`) for a selected repository to generate comprehensive test suites.

2. **Configure Test Generation**
   Specify parameters for test creation:
   - **Test Framework**: Choose your preferred testing framework (Jest, Mocha, Pytest, etc.)
   - **Coverage Goals**: Set target coverage percentages
   - **Test Types**: Select unit tests, integration tests, or both
   - **Mock Strategy**: Configure how external dependencies should be mocked

3. **Generate and Review Tests**
   The AI agent analyzes your code structure and generates appropriate test files. The `TestProgressDialog` component (`src/components/TestProgressDialog.tsx`) shows progress as tests are created and validated.

## Advanced Configuration Options

### AI Agent Customization

Each AI agent can be customized for your specific needs:

1. **Quality Engineer Settings**
   In the `AIQualityEngineerPanel`, configure:
   - **Analysis Depth**: Surface-level vs. deep structural analysis
   - **Language-Specific Rules**: Enable specialized checks for your primary programming language
   - **Framework Detection**: Automatic detection and analysis of frameworks in use
   - **Code Style Standards**: Align analysis with your team's coding standards

2. **Documentation Specialist Configuration**
   The `AIDocumentationSpecialistPanel` component (`src/components/AIDocumentationSpecialistPanel.tsx`) offers:
   - **Documentation Types**: API docs, user guides, architectural documentation
   - **Format Preferences**: Markdown, HTML, or integrated wiki formats
   - **Audience Targeting**: Technical vs. non-technical documentation styles
   - **Update Frequency**: Automatic regeneration on code changes

3. **Compliance Analyst Setup**
   Configure compliance monitoring through the `AIComplianceAnalystPanel` (`src/components/AIComplianceAnalystPanel.tsx`):
   - **Compliance Frameworks**: GDPR, HIPAA, SOX, PCI DSS, and more
   - **Industry Standards**: ISO 27001, NIST, CIS controls
   - **Custom Policies**: Define organization-specific compliance requirements
   - **Violation Severity**: Categorize compliance issues by impact level

### Notification and Integration Setup

Configure how OrchestRAI communicates analysis results:

1. **Email Notifications**
   Set up automated email alerts for:
   - Analysis completion notifications
   - Critical security issues discovered
   - Compliance violations detected
   - Weekly/monthly summary reports

2. **Slack Integration**
   Connect OrchestRAI to your Slack workspace for:
   - Real-time analysis notifications
   - Team collaboration on identified issues
   - Shared access to analysis reports
   - Integration with existing development workflows

3. **GitHub Integration**
   Enable deeper GitHub integration for:
   - Pull request analysis and comments
   - Commit-triggered automatic analysis
   - Issue creation for identified problems
   - Status checks on pull requests

## Troubleshooting Common Setup Issues

### Authentication Problems

**Issue**: "Unable to connect to GitHub"
**Solution**: Check that your GitHub account has the necessary permissions and that you've granted all required OAuth scopes. The `AuthModal` component handles authentication errors and provides specific error messages to help identify the issue.

**Issue**: "Email verification not received"
**Solution**: Check your spam folder and ensure the email address is correct. You can request a new verification email through the authentication interface. Supabase Auth handles email delivery, so temporary delays may occur.

**Issue**: "Session expired" errors
**Solution**: The application automatically handles session refresh, but network issues can interfere. Clear your browser cache and log in again. The `AuthContext` (`src/contexts/AuthContext`) manages session state and should automatically redirect you to the login page when sessions expire.

### Repository Connection Issues

**Issue**: "No repositories found"
**Solution**: Ensure you have at least read access to repositories in your GitHub account. Private repositories require explicit permissions. Check the GitHub OAuth settings to confirm OrchestRAI has been granted access to the appropriate repositories.

**Issue**: "Repository analysis fails to start"
**Solution**: Verify that the repository contains code files in supported languages. Empty repositories or those containing only documentation may not trigger analysis. The `workflowService` (`src/services/workflowService`) manages analysis workflows and provides detailed error messages for troubleshooting.

**Issue**: "Connection timeout during repository sync"
**Solution**: Large repositories with extensive history may take time to sync. Wait for the process to complete, or try again later. The sync process is designed to handle interruptions gracefully and resume where it left off.

### Analysis and Performance Issues

**Issue**: "Analysis takes too long to complete"
**Solution**: Large repositories require more processing time. The `CodeQualityProgressDialog` shows detailed progress updates. Consider analyzing specific directories or file types first to get faster results on critical code sections.

**Issue**: "Inconsistent quality scores"
**Solution**: Quality scores may vary between analysis runs as the AI models improve and code changes. Focus on trends over time rather than absolute scores. The `CodeQualityNotes` component (`src/components/CodeQualityNotes.tsx`) provides detailed explanations for score variations.

**Issue**: "Missing analysis results"
**Solution**: Ensure your browser allows JavaScript execution and has a stable internet connection. Results are stored in Supabase and should persist across browser sessions. Try refreshing the page or logging out and back in to reload data.

### Workspace and Permissions Issues

**Issue**: "Cannot access workspace features"
**Solution**: Verify your workspace permissions through the `useWorkspaceFunctionPermissions` hook functionality. Some features require specific permission levels. Contact your workspace administrator to adjust permissions if needed.

**Issue**: "Team member invitations not working"
**Solution**: Check that email addresses are correct and that invited users check their spam folders. The invitation system uses Supabase's authentication flow and may take a few minutes to process.

## Next Steps After Setup

With your OrchestRAI account set up and repositories connected, you're ready to explore the platform's full capabilities:

1. **Explore Advanced Features**: Dive into compliance analysis, automated documentation generation, and team collaboration features
2. **Customize AI Agents**: Fine-tune each AI agent's behavior to match your development workflow and quality standards
3. **Set Up Continuous Integration**: Configure automated analysis to run on every code commit or pull request
4. **Build Quality Dashboards**: Create custom views of your code quality metrics and trends over time
5. **Scale to Enterprise**: Explore enterprise features for larger organizations, including advanced security, compliance reporting, and team management

The platform is designed to grow with your needs, from individual developers to enterprise development teams. Each feature builds on the foundation established during this initial setup, providing increasingly sophisticated tools for maintaining high-quality, compliant software.