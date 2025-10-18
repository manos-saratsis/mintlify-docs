I'll analyze the source code to create comprehensive getting started documentation for OrchestrAI. Let me examine the key files to understand the application flow.

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
<path>src/components/WelcomeModal.tsx</path>
</read_file>

<read_file>
<path>src/hooks/useWelcomeModal.ts</path>
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

Based on my analysis of the source code, I'll now create user-facing getting started documentation:

---

# **OrchestrAI - Getting Started**

Welcome to OrchestrAI! This guide will help you get started with your AI-powered development platform and show you how to begin automating your software quality, testing, documentation, and compliance workflows.

## **What is OrchestrAI?**

OrchestrAI is an intelligent development platform that brings AI assistance directly into your software development workflow. Think of it as having a team of AI specialists working alongside you - a Quality Engineer checking your code, a Test Engineer creating comprehensive tests, a Documentation Specialist keeping your docs up-to-date, and a Compliance Analyst ensuring regulatory requirements are met.

## **Your First Steps**

### **Step 1: Sign In and Create Your Account**

When you first visit OrchestrAI, you'll arrive at the welcome page. Here's how to get started:

1. Click the "Get Started" button on the homepage
2. Sign in using your GitHub account (this allows OrchestrAI to access your repositories)
3. Grant the necessary permissions when prompted

After signing in, you'll see a welcome dialog that guides you through the initial setup. This is your first introduction to the platform and helps you understand what OrchestrAI can do for you.

### **Step 2: Set Up Your Workspace**

Once you've signed in, you'll need to create or join a workspace. Think of a workspace as your team's project area where all your AI-assisted development happens.

**Creating a New Workspace:**
1. Navigate to the Workspace Management section from the main menu
2. Click "Create New Workspace"
3. Give your workspace a meaningful name (like your project or team name)
4. Click "Create"

**Joining an Existing Workspace:**
If you've been invited to a workspace by your team, you'll see it listed in your workspace selector. Simply click on it to switch to that workspace.

### **Step 3: Connect Your GitHub Repositories**

Now it's time to connect your code repositories so OrchestrAI can help you:

1. Go to the "Code" section from the main navigation
2. You'll see a button to connect your GitHub repositories
3. Click "Connect GitHub" and authorize OrchestrAI to access your repositories
4. Select which repositories you want OrchestrAI to work with
5. For each repository, enable "OrchestrAI" to activate AI features

Once connected, you'll see your repositories listed with their current status and available actions.

### **Step 4: Configure Your Product Information**

Before the AI can help you effectively, it needs to understand what your product does:

1. Navigate to "Organization Information" from the menu
2. Fill in details about your product:
   - What your product does
   - Who uses it
   - Key features and capabilities
   - Any existing documentation URLs
3. Save your information

This helps the AI understand your context and provide more accurate assistance.

## **Core Features and How to Use Them**

### **Code Quality Analysis**

Want to improve your code quality? Here's how:

1. Go to the "Code Quality" section
2. Select a repository you want to analyze
3. Click on the repository card to open the AI Quality Engineer panel
4. The AI will analyze your code and show you:
   - Code quality scores
   - Areas for improvement
   - Security vulnerabilities
   - Best practice recommendations

You can review the findings and see detailed explanations for each issue discovered.

### **Automated Test Generation**

Creating comprehensive tests has never been easier:

1. Navigate to the "Testing" section
2. Choose a repository that needs test coverage
3. Click on the repository to activate the AI Test Engineer
4. Provide any specific testing instructions (optional)
5. Click "Generate Tests"

The AI will analyze your code and create test cases that cover various scenarios. You can review the generated tests before they're added to your repository.

### **Documentation Generation**

Keep your documentation fresh and comprehensive:

1. Go to the "Documentation" section
2. Configure where you want documentation stored (repository and folder)
3. Choose your documentation approach:
   - **Create New:** AI builds documentation from scratch by analyzing your product
   - **Migrate Existing:** AI restructures your current documentation following best practices
4. Customize what to include:
   - User-facing guides
   - Internal developer documentation
   - API references
   - Tutorials and how-to guides
5. Select which repositories to document
6. Click "Generate Documentation"

The AI will create comprehensive, well-structured documentation and commit it directly to your chosen repository.

### **Compliance Analysis**

Ensure your code meets regulatory requirements:

1. Visit the "Compliance" section
2. Select a repository to analyze
3. Enable compliance checking in your workflow settings
4. Click "Start Analysis"
5. Review the compliance report showing:
   - Data privacy checks
   - Security requirements
   - Access control validation
   - Audit trail verification

The AI identifies compliance gaps and provides recommendations for fixes.

## **Understanding Your Workflow**

OrchestrAI works through AI specialists that operate in panels on the right side of your screen. Here's what each specialist does:

- **AI Quality Engineer**: Reviews your code for quality issues, security vulnerabilities, and improvement opportunities
- **AI Test Engineer**: Creates comprehensive test suites based on your code functionality
- **AI Documentation Specialist**: Generates and maintains documentation that's always current
- **AI Compliance Analyst**: Ensures your code meets regulatory and security standards

When you open any of these panels, you can:
- Provide specific instructions for what you want
- Start the AI process with a single click
- Monitor progress in real-time
- Review results and findings
- Accept or modify AI-generated content

## **Workspace Management and Permissions**

If you're managing a team workspace, you have additional capabilities:

**Managing Team Members:**
1. Go to Workspace Management
2. Invite team members by email
3. Assign roles and permissions:
   - **Admin**: Full control over workspace settings
   - **Member**: Can use all AI features
   - **Viewer**: Can view but not execute AI operations

**Controlling Feature Access:**
Navigate to the Permissions section to control which team members can:
- Run code quality checks
- Generate tests
- Create documentation
- Perform compliance analysis

## **Tips for Success**

1. **Start Small**: Begin with one repository and one AI feature. Get comfortable with how OrchestrAI works before expanding.

2. **Provide Clear Instructions**: When using AI panels, specific instructions lead to better results. Tell the AI exactly what you're looking for.

3. **Review AI Output**: While the AI is powerful, always review what it generates. You're the expert on your product.

4. **Enable Features Gradually**: Use the Workflow settings to enable AI features one at a time as your team becomes comfortable with them.

5. **Use Checkpoints**: If an AI process is interrupted, OrchestrAI can resume from where it left off. Look for the "Resume" option.

6. **Monitor Costs**: Check the Cost Analysis section regularly to understand your AI usage and associated costs.

## **Common Workflows**

### **Setting Up a New Project**
1. Create workspace
2. Connect repositories
3. Add product information
4. Run initial code quality analysis
5. Generate baseline test suite
6. Create documentation structure

### **Onboarding a New Repository**
1. Connect the repository in Code section
2. Enable OrchestrAI for the repository
3. Run quality analysis to understand current state
4. Generate tests for existing code
5. Create documentation

### **Regular Maintenance**
1. Run weekly code quality checks
2. Update tests when adding new features
3. Refresh documentation after major changes
4. Perform compliance checks before releases

## **Getting Help**

If you run into issues:

- **Configuration Problems**: Check the Workflow settings to ensure features are properly enabled
- **Permission Issues**: Contact your workspace administrator to adjust your permissions
- **AI Generation Errors**: Review your instructions for clarity and try again
- **Repository Connection Problems**: Verify your GitHub authorization is still active

## **What's Next?**

Now that you understand the basics:

1. Explore the Enterprise features if you need advanced team capabilities
2. Set up automated workflows that run on a schedule
3. Integrate OrchestrAI insights into your CI/CD pipeline
4. Customize AI instructions for your specific needs and coding standards

Welcome to a more intelligent way of developing software. OrchestrAI is here to help you build better, faster, and with greater confidence.

---

**Note**: OrchestrAI requires a GitHub account and appropriate repository permissions to function. Make sure you have owner or admin access to repositories you want to analyze and improve.