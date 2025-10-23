I'll analyze the source code to create comprehensive user-facing documentation for the OrchestrAI Getting Started guide.

<thinking>
Let me examine the key source code files to understand:
1. The application structure (App.tsx)
2. Available features and panels (AI components)
3. Authentication and workspace context
4. User flows and capabilities

From the code, I can see:
- App.tsx shows the routing structure with various pages (Index, Product, Enterprise, etc.)
- Authentication system via AuthContext
- Workspace management via WorkspaceContext
- Multiple AI-powered panels: Compliance, Documentation
- Various product pages: Code, Testing, Code Quality, Workflow, Documentation, Compliance, etc.
- GitHub integration for repository connections
- Permission-based feature access
- Pricing/subscription model (free plan vs paid plans)
- Welcome modal for new users

Key user-facing features from the code:
- Code analysis and quality checking
- Testing automation
- Compliance analysis
- Documentation generation (migrate or create)
- Workspace management
- GitHub repository connections
- Cost analysis
- Account management

Now I'll create user-friendly documentation without mentioning technical details.
</thinking>

# orchestrai-dev-getting-started.md

## Getting Started with OrchestrAI

Welcome to OrchestrAI! This guide will help you get up and running with your AI-powered development assistant.

### What is OrchestrAI?

OrchestrAI is your intelligent development companion that helps you automate code quality checks, generate tests, ensure compliance, and create documentation—all powered by AI. Think of it as having an expert team working alongside you, automatically handling the tedious parts of software development.

### Creating Your Account

1. Visit the OrchestrAI homepage
2. Look for the sign-up option
3. Complete the registration process
4. You'll see a welcome screen that introduces you to the platform

Once you're signed up, you'll be taken to your dashboard where the real magic begins!

### Understanding Workspaces

Think of a workspace as your project's home in OrchestrAI. Each workspace represents a team or project where you can:

- Connect your code repositories
- Set up automation workflows
- Manage team permissions
- Track costs and usage

**Your First Workspace:**
- You'll be prompted to create or select a workspace when you first log in
- Give it a meaningful name (like your project or team name)
- You can create multiple workspaces for different projects

### Connecting Your Code

To let OrchestrAI help you, you need to connect your code repository:

1. Navigate to the Code section from your dashboard
2. Click the button to connect a new repository
3. Authenticate with GitHub when prompted
4. Select which repositories you want OrchestrAI to access
5. Enable OrchestrAI for specific repositories you want to work with

**What Happens After Connection:**
- OrchestrAI can now analyze your code
- You'll see your connected repositories listed
- You can enable or disable OrchestrAI for each repository anytime

### Your AI Team

OrchestrAI gives you access to specialized AI assistants:

**AI Compliance Analyst**
Your compliance expert that reviews your code for regulatory requirements like data privacy, security, and access control. Perfect for ensuring your software meets industry standards.

**AI Documentation Specialist**
Creates comprehensive documentation for your project. It can either:
- Build brand new documentation from scratch by analyzing your code
- Reorganize and improve your existing documentation

**AI Quality Engineer**
Checks your code quality, identifies issues, and suggests improvements to make your code more maintainable.

**AI Test Engineer**
Generates automated tests for your code, helping you catch bugs before they reach production.

### Running Your First Analysis

Let's start with a compliance check as an example:

1. Go to the Compliance section from your main menu
2. Select one of your connected repositories
3. Click to open the AI Compliance Analyst panel (it appears on the right side)
4. You'll see a text box where you can provide specific instructions, like:
   - "Focus on data privacy compliance"
   - "Check for security vulnerabilities"
5. Click the button to start the analysis
6. Watch the progress indicator as the AI works
7. When complete, you'll see your results with actionable insights

The same basic flow works for other AI assistants—select your repository, provide instructions, and let the AI do the work!

### Customizing What Gets Analyzed

For most AI functions, you can customize the scope:

**Repository Selection:**
- Choose to analyze your entire repository, or
- Select a specific commit if you only want to check recent changes

**Documentation Scope:**
When generating documentation, you can pick what types you need:
- User-facing documentation (guides for your customers)
- Internal developer documentation (for your team)
- Software Bill of Materials (SBOM)

**Content Structure:**
For user-facing docs, choose which sections to include:
- Quick start guides
- Detailed tutorials
- How-to guides for specific tasks
- API reference documentation
- Conceptual explanations
- Troubleshooting guides
- Release notes

### Understanding Permissions

On paid plans, workspace administrators can control who can do what:

- Some team members might be able to view results but not run analyses
- Others might have full access to all features
- If you see a message about lacking permissions, reach out to your workspace administrator

**Free Plan Note:** On the free plan, you have access to all features without permission restrictions—perfect for trying everything out!

### Managing Workflows

The Workflow section is your control center for automation:

1. Navigate to Workflow from your dashboard
2. Here you can enable or disable different AI functions
3. Configure how each function behaves:
   - Set up where documentation should be saved
   - Define default instructions for analyses
   - Choose what happens automatically

**Important:** Some AI features (like Compliance) need to be explicitly enabled in Workflow before you can use them. If you can't start an analysis, check your Workflow settings first.

### Resuming Interrupted Work

If an AI analysis gets interrupted (maybe you lost internet connection), don't worry:

- OrchestrAI automatically saves checkpoints of your progress
- When you return, you'll see an option to resume from where you left off
- Your original settings and progress are preserved
- No need to start from scratch!

### Viewing Your Results

After an AI analysis completes:

1. You'll see a notification confirming completion
2. Click the "View Results" button in the notification
3. You'll be taken to a detailed results page showing:
   - What the AI found
   - Recommended actions
   - Specific issues with your code (if any)
   - Generated content (like documentation or tests)

### Tracking Costs

For workspace administrators, OrchestrAI provides cost tracking:

1. Go to the Workspace Management section
2. Select "View Cost Analysis" for your workspace
3. See detailed breakdowns of:
   - Which features are being used most
   - Cost per repository
   - Trends over time
   - Budget forecasts

This helps you understand and optimize your OrchestrAI usage.

### Getting Help

**Documentation URL:**
If your project already has documentation, you can tell OrchestrAI where to find it:
- Go to Organization Information
- Add your documentation URL
- This helps the AI understand your existing structure

**Support Resources:**
- Check the Privacy Policy and Terms of Service for important information
- Visit your Account page to manage your profile and settings

### Tips for Success

**Start Small:**
- Try one feature at a time rather than enabling everything at once
- Run your first analysis on a smaller repository to get familiar with the process

**Be Specific with Instructions:**
- The more detailed your instructions, the better results you'll get
- Example: Instead of "check my code," try "check for SQL injection vulnerabilities and data validation issues"

**Review the Configuration:**
- Before running analyses, visit the Workflow section
- Make sure everything is set up the way you want

**Enable Repositories Strategically:**
- You don't have to connect all your repositories
- Start with your most important projects
- You can always add more later

**Check Permissions First:**
- If something isn't working, verify you have the right permissions
- Workspace administrators can adjust access in the Permissions section

**Use Progress Dialogs:**
- When an analysis is running, a progress window shows you what's happening
- You can see each step as it completes
- If something fails, you'll see where it went wrong

### Common Workflows

**Weekly Code Quality Check:**
1. Open Code Quality section
2. Select your main repository
3. Run the AI Quality Engineer
4. Review findings and create tasks for your team

**Pre-Release Compliance Audit:**
1. Go to Compliance section
2. Select the repository for your upcoming release
3. Run AI Compliance Analyst with instructions focused on your industry requirements
4. Address any issues before releasing

**Onboarding New Team Members:**
1. Generate fresh documentation using AI Documentation Specialist
2. Choose "Create New Documentation" option
3. Include tutorials and how-to guides
4. Review and refine the generated content
5. Share with your new team members

**Continuous Documentation:**
1. Connect your documentation repository
2. Set up the AI Documentation Specialist with your preferences
3. After each major commit, run it on that specific commit
4. Keep your docs automatically updated

### What's Next?

Now that you're set up:

1. **Explore Each AI Assistant:** Try each one to see what it can do for your specific needs
2. **Customize Your Workflow:** Configure the automation settings that work best for your team
3. **Invite Your Team:** Add team members to your workspace and assign appropriate permissions
4. **Set Up Regular Analyses:** Make OrchestrAI part of your development routine

Remember, OrchestrAI learns from your instructions—the more you use it, the better you'll get at directing it to give you exactly what you need!

---

**Ready to dive deeper?** Explore each section of your dashboard to discover all the powerful features OrchestrAI offers. Your AI development team is ready to help whenever you need it!