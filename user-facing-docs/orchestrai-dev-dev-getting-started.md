I'll analyze the source code and create a comprehensive "Getting Started" guide for OrchestrAI. Let me examine the key components first.

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
<path>src/hooks/useWelcomeModal.tsx</path>
</read_file>

Now let me create the Getting Started documentation:

<write_file>
<path>user-facing-docs/orchestrai-dev-getting-started.md</path>
<content>
# Getting Started with OrchestrAI

Welcome to OrchestrAI! This guide will help you get started with your AI-powered development assistant platform.

## What is OrchestrAI?

OrchestrAI is an intelligent platform that helps teams automate and improve their software development workflows. Think of it as having AI experts on your team who can analyze code quality, generate tests, ensure compliance, and create documentation automatically.

## First Steps

### 1. Sign Up and Access the Platform

When you first visit OrchestrAI, you'll see the homepage with information about what the platform can do. To get started:

1. Look for the sign-in or sign-up button in the top right corner
2. Create your account using your preferred method
3. Once signed in, you'll see a welcome screen that introduces you to the platform's key features

### 2. Understanding the Welcome Screen

The first time you log in, a welcome dialog will appear explaining the platform's main capabilities:

- **Code Quality Analysis**: Automatically check your code for issues and improvements
- **Automated Testing**: Generate and run tests for your codebase
- **Compliance Checking**: Ensure your code meets regulatory and security standards
- **Documentation Generation**: Create comprehensive documentation from your code

Click through this welcome guide to learn about each feature, or close it to jump straight into the platform.

### 3. Set Up Your Workspace

After the welcome screen, you'll be in your main dashboard. Before you can start using OrchestrAI's features, you need to set up a workspace:

**What is a Workspace?**
A workspace is like a project container that holds all your repositories, settings, and configurations. Think of it as your team's dedicated environment within OrchestrAI.

**Creating Your First Workspace:**
1. Navigate to the Workspace Management section
2. Click the button to create a new workspace
3. Give your workspace a meaningful name (like "My Company Project" or "Team Alpha")
4. Save your workspace

### 4. Connect Your Code Repository

OrchestrAI needs access to your code to help you. Here's how to connect your GitHub repositories:

1. Go to the Code section in your workspace
2. Look for the option to connect a repository
3. Click the "Connect GitHub" button
4. You'll be redirected to GitHub to authorize OrchestrAI
5. Select which repositories you want to give OrchestrAI access to
6. Confirm the connection

**After Connecting:**
- You'll see a list of your connected repositories
- Each repository will show its status and available actions
- You can enable or disable OrchestrAI features for each repository individually

### 5. Configure Your Product Information

Before using the AI features, tell OrchestrAI about your product:

1. Navigate to Product Information (also called Organization Information)
2. Fill in details about your product:
   - Product name
   - Description of what it does
   - Your company or team name
   - Documentation URL (if you have existing docs)
3. Save your information

This helps the AI understand your product context when analyzing code or generating documentation.

## Using Your First AI Feature

Now that you're set up, let's try your first AI-powered feature!

### Option A: Analyze Code Quality

1. Go to the Code Quality section
2. Select a repository from your connected repositories
3. Click the "Analyze Code Quality" button
4. The AI will start examining your code
5. Wait for the analysis to complete (you'll see a progress indicator)
6. Review the results showing code quality scores, issues found, and suggestions for improvement

### Option B: Generate Documentation

1. Navigate to the Documentation section
2. Choose whether to:
   - **Create new documentation** (if you don't have docs yet)
   - **Migrate existing documentation** (if you want to improve your current docs)
3. An AI Documentation Specialist panel will open on the right side
4. Review the settings and add any specific instructions
5. Click "Generate Documentation"
6. The AI will analyze your product and create documentation
7. Once complete, your documentation will be added to your repository

### Option C: Run Compliance Analysis

1. Go to the Compliance section
2. Select a repository to analyze
3. The AI Compliance Analyst panel opens on the right
4. Add any specific compliance requirements or instructions
5. Click "Start Analysis"
6. Watch the progress as the AI checks your code
7. View the results showing compliance status, issues, and recommendations

## Understanding the Interface

### Main Navigation

The top navigation bar gives you access to all major features:

- **Home**: Return to the main dashboard
- **Product**: Access your workspace and AI features
- **Workspace Management**: Manage your workspaces and team
- **Account**: Update your profile and settings
- **Pricing**: View plan options and upgrade if needed

### Product Section Features

When you're in the Product section, you'll see several options:

- **Code**: View and manage connected repositories
- **Testing**: Generate and run automated tests
- **Code Quality**: Analyze and improve code quality
- **Compliance**: Check regulatory and security compliance
- **Documentation**: Create and maintain documentation
- **Workflow**: Configure how AI features work together
- **Workspace Management**: Manage team members and permissions

### AI Assistant Panels

When you use an AI feature, a panel slides in from the right side showing:

- **Feature name and icon** at the top
- **Configuration options** in the middle (like instructions or settings)
- **Repository information** showing which code is being analyzed
- **Action buttons** at the bottom to start or stop the AI

## Tips for Success

### Start Small
Begin with one repository and one feature. Once you're comfortable, expand to more repositories and try other AI capabilities.

### Provide Clear Instructions
When using AI features, the more specific your instructions, the better the results. For example:
- Instead of: "Analyze my code"
- Try: "Focus on security vulnerabilities and performance issues in the authentication module"

### Review AI Suggestions
The AI provides recommendations, but you're in control. Always review suggestions before implementing them in your production code.

### Use Workspaces to Organize
If you work on multiple projects, create separate workspaces for each. This keeps everything organized and maintains separate configurations.

### Check Your Permissions
If a button is grayed out or you see "No Permission" messages, contact your workspace administrator. They control who can use which features.

## Common Questions

**Q: Why can't I start an analysis?**
A: Make sure you have:
- Connected at least one repository
- Configured your product information
- The necessary permissions in your workspace
- Enabled the feature in Workflow settings

**Q: How long does analysis take?**
A: Most analyses complete in a few minutes, depending on your repository size. You'll see a progress indicator showing status.

**Q: Can I stop an analysis in progress?**
A: Yes, you can close the AI panel to stop an ongoing analysis.

**Q: Where do results go?**
A: Results are typically:
- Shown in the interface immediately
- Saved in a results page you can view later
- Committed to your repository (for documentation and code changes)

**Q: Is my code secure?**
A: Yes. OrchestrAI only accesses the repositories you explicitly connect and follows security best practices.

## Next Steps

Now that you're familiar with the basics:

1. **Explore each AI feature** to see what works best for your team
2. **Configure workflows** to automate your development process
3. **Invite team members** to collaborate in your workspace
4. **Set up permissions** to control who can use which features
5. **Review the documentation** for advanced features and tips

## Getting Help

If you need assistance:
- Check the documentation sections for detailed guides
- Look for help icons (?) throughout the interface for contextual help
- Contact support if you encounter issues
- Visit the pricing page to learn about plan features and upgrades

Welcome to OrchestrAI – let's make your development workflow more efficient and intelligent!
</content>
</write_file>

Now let me create the "How to Write Documentation with OrchestrAI" guide:

<write_file>
<path>user-facing-docs/orchestrai-dev-how-to-documentation.md</path>
<content>
# How to Write Documentation with OrchestrAI

This guide walks you through the process of creating and managing documentation using OrchestrAI's AI Documentation Specialist.

## Before You Begin

### Prerequisites

You'll need:
- An active OrchestrAI account
- At least one repository connected to your workspace
- Your repository enabled for OrchestrAI features
- Product information configured (your product name, description, etc.)

### Choose Your Documentation Path

OrchestrAI offers two ways to create documentation:

1. **Create New Documentation**: Start from scratch if you don't have existing docs
2. **Migrate Existing Documentation**: Improve and restructure your current documentation

## Setting Up Documentation

### Step 1: Configure Documentation Settings

Before generating documentation, you need to tell OrchestrAI where to put it:

1. Navigate to the Product Information section
2. Scroll to the documentation configuration area
3. Fill in these details:
   - **Repository**: Select which repository should store your documentation
   - **Folder**: Choose the folder path (like `/docs` or `/documentation`)
   - **Documentation URL**: If you have existing docs, provide the URL where they're hosted

4. Save your configuration

**Why This Matters**: The AI needs to know where to create files and how to structure your documentation repository.

### Step 2: Enable Documentation in Workflow

1. Go to the Workflow section
2. Find the Documentation workflow
3. Make sure it's enabled for your workspace
4. Configure any workflow-specific settings
5. Save your changes

## Creating New Documentation

Follow these steps to generate documentation from scratch:

### Step 1: Access the Documentation Feature

1. Go to the Documentation section in your workspace
2. Click the "Create New Documentation" button
3. The AI Documentation Specialist panel will open on the right side of your screen

### Step 2: Provide Instructions

In the instructions box, tell the AI what kind of documentation you need. The more specific you are, the better the results.

**Good instruction examples:**
- "Create user-facing documentation with a focus on getting started guides and API reference"
- "Generate internal developer documentation explaining the architecture and setup process"
- "Build comprehensive documentation including tutorials for common use cases"

**Tip**: Your custom instructions take priority over default settings, so be specific about what you want for this particular generation.

### Step 3: Customize Your Documentation Scope

Click on "Customize Scope & Content Structure" to expand the options:

**Choose Documentation Types:**
- ☑ **User Facing Documentation**: For end users of your product
- ☐ **Internal Developer Documentation**: For your development team
- ☐ **SBOM (Software Bill of Materials)**: Component and dependency tracking

**Select Content Structure** (when User Facing is selected):
- ☑ **/intro**: Quick start guides to get users up and running
- ☑ **/tutorials**: End-to-end guides focused on accomplishing specific outcomes
- ☐ **/how-to**: Short, task-focused instructions for specific actions
- ☑ **/reference**: API and SDK documentation (auto-generated from code)
- ☐ **/concepts**: Explanation of architecture, models, and technical concepts
- ☐ **/troubleshooting**: Error catalogs and debugging help
- ☐ **/release-notes**: Automatically generated from version changes

**Recommended Starting Point**: Enable "intro", "tutorials", and "reference" for a solid documentation foundation.

### Step 4: Select Code Scope

Click on "Select Code Scope" to choose which code to document:

**Choose Repositories:**
- Check the boxes next to repositories you want to document
- Use "Select All" if you want comprehensive documentation across all repos

**For Each Selected Repository, Choose:**
- **Whole Repo**: Document the entire repository (recommended for initial documentation)
- **Specific Commit**: Document only changes in a particular commit (useful for updates)

**When to Use Specific Commit:**
- You've made significant changes and want to update docs for just those changes
- You want to document a specific feature addition
- You're creating release-specific documentation

**To Select a Commit:**
1. Click the "Specific Commit" button for a repository
2. A list of recent commits will appear
3. Click on the commit you want to document
4. The selected commit will be highlighted

### Step 5: Generate Documentation

1. Review all your settings one final time
2. Click the "Generate Documentation" button at the bottom
3. A progress dialog will appear showing the AI's work

**What Happens Next:**
- The AI analyzes your code and product
- Documentation is generated following your selected structure
- Files are created and organized in your configured folder
- The documentation is committed to your repository
- You'll see a completion message when finished

### Step 6: Review and Refine

Once generation is complete:

1. Click "View Documentation" or navigate to your repository
2. Review the generated documentation files
3. Check that structure and content meet your needs
4. Make manual edits if needed for specific details or tone
5. Commit any additional changes

**Common Review Points:**
- Are code examples accurate and helpful?
- Is the tone appropriate for your audience?
- Are there any missing sections you want to add?
- Do links and references work correctly?

## Migrating Existing Documentation

If you already have documentation that needs improvement:

### Step 1: Prepare for Migration

1. Make sure your existing documentation URL is configured in Product Information
2. Go to the Documentation section
3. Click "Migrate Existing Documentation"

### Step 2: Set Migration Instructions

The AI will:
- Access your current documentation
- Analyze its structure and content
- Restructure it according to best practices
- Fill in gaps and improve clarity

**Migration Instructions Example:**
"Restructure our documentation to follow the Diátaxis framework, improve code examples, and ensure consistency in terminology"

### Step 3: Choose Migration Scope

Select the same options as creating new documentation:
- Documentation types to include
- Content structure to follow
- Repositories to reference

### Step 4: Start Migration

1. Click "Generate Documentation"
2. The AI will process your existing docs
3. New, improved documentation will be created in a `migrated-docs` folder

**Why a Separate Folder?**
Your original documentation stays intact while the AI creates the improved version. This lets you:
- Compare old and new versions
- Keep your current docs live during migration
- Gradually transition to the new structure

### Step 5: Transition to New Documentation

After reviewing the migrated docs:

1. Test the new documentation with users or team members
2. Fix any issues or gaps
3. When ready, replace your old docs with the migrated version
4. Update any documentation links in your product

## Advanced Documentation Options

### Resuming from Checkpoints

If a documentation generation is interrupted:

1. Go back to the Documentation section
2. You'll see a notice about incomplete generation
3. Click "Resume" to continue from where it stopped
4. The AI will load your previous configuration and continue

**What Gets Saved:**
- Your selected scopes and repositories
- Custom instructions
- Progress on file generation
- Partially created documentation

### Updating Documentation

To update docs after code changes:

1. Use "Create New Documentation" with specific commits
2. Select only changed repositories
3. Choose "Specific Commit" and pick your recent changes
4. Generate documentation for just those updates

**Result**: Only documentation related to your changes gets updated, leaving the rest intact.

### Creating Different Documentation Types

**For User-Facing Docs:**
- Focus on use cases and outcomes
- Include plenty of examples
- Use simple, clear language
- Add troubleshooting sections

**For Internal Developer Docs:**
- Explain architecture and design decisions
- Include setup and contribution guides
- Document code standards and practices
- Add technical deep-dives

**For SBOM:**
- Lists all components and dependencies
- Tracks versions and licenses
- Helps with security audits
- Useful for compliance requirements

## Tips for Great Documentation

### Write Better Instructions

**Do:**
- Be specific about your audience: "Create documentation for data analysts using our API"
- Mention format preferences: "Include runnable code examples for every endpoint"
- State priorities: "Focus on the authentication flow and data models"

**Don't:**
- Be too vague: "Make it good"
- Contradict configured settings without reason
- Forget to mention special requirements

### Structure Your Documentation

**Start with these essentials:**
1. **Introduction**: What is your product and why should someone use it?
2. **Quick Start**: Get users to their first success quickly
3. **Reference**: Detailed API/SDK documentation for when they need specifics

**Then add based on user needs:**
4. **Tutorials**: Walk through complete workflows
5. **How-To Guides**: Quick answers to common questions
6. **Troubleshooting**: Help when things go wrong

### Keep Documentation Fresh

**Set up a routine:**
- Generate updates after major releases
- Review and regenerate quarterly
- Update when you get user feedback
- Add new sections as your product evolves

**Use commit-based updates:**
- Document new features immediately after merging
- Keep docs in sync with code changes
- Maintain version-specific documentation

## Common Questions

**Q: How long does documentation generation take?**
A: Usually 5-15 minutes depending on your codebase size and selected scope.

**Q: Can I edit AI-generated documentation?**
A: Yes! The generated files are regular markdown files in your repository. Edit them as needed.

**Q: What if I don't like the generated docs?**
A: Try again with more specific instructions, or use the generated docs as a starting point and edit them manually.

**Q: Can I preview before committing to my repository?**
A: The AI commits directly to your repository. Review the results there, and you can always revert the commit if needed.

**Q: Will this overwrite my existing documentation?**
A: New documentation goes to your configured folder. Migration creates a separate folder. Your original docs stay safe unless you explicitly replace them.

**Q: Can I generate docs for private repositories?**
A: Yes, as long as you've connected the repository and given OrchestrAI the necessary permissions.

**Q: Does the AI understand my domain-specific terminology?**
A: The AI learns from your code, comments, and Product Information. The better you describe your product, the better it understands your domain.

**Q: Can I generate documentation in different languages?**
A: Currently, documentation is generated in English. If you need other languages, you can translate the generated docs separately.

## Troubleshooting

**"Configuration Required" button is disabled:**
- Check that you've set up documentation repository and folder in Product Information
- Ensure the repository is connected and OrchestrAI-enabled

**"Select at least one scope" message:**
- You must check at least one documentation type (User Facing, Internal, or SBOM)
- Expand the "Customize Scope & Content Structure" section to make selections

**Generation fails or times out:**
- Try selecting fewer repositories at once
- Use specific commits instead of whole repositories
- Check that all selected repositories are accessible

**Generated documentation is incomplete:**
- The AI might have been interrupted - look for a resume option
- Try generating again with more specific instructions
- Break large documentation tasks into smaller pieces

**Documentation doesn't match my expectations:**
- Provide more detailed instructions about tone, audience, and content
- Select different content structure options
- Add examples of what you want in your instructions

## Best Practices

1. **Start Small**: Generate docs for one repository first to see how it works
2. **Be Specific**: Detailed instructions lead to better documentation
3. **Review Everything**: AI is helpful but not perfect - always review and edit
4. **Iterate**: Regenerate sections that aren't quite right with better instructions
5. **Keep Updated**: Generate new documentation after significant code changes
6. **Use Checkpoints**: If generation is interrupted, resume instead of starting over
7. **Organize Well**: Use clear folder structures in your repository
8. **Version Control**: Treat documentation like code - review changes before merging

## Next Steps

Now that you know how to generate documentation:

1. Try creating documentation for a small project first
2. Experiment with different content structures
3. Share generated docs with your team for feedback
4. Set up a regular documentation update schedule
5. Explore automating documentation updates in your workflow

Happy documenting! Your users (and future self) will thank you for great documentation.
</content>
</write_file>

I've created two comprehensive user-facing documentation files:

## 1. **orchestrai-dev-getting-started.md**
This is a complete beginner's guide covering:
- What OrchestrAI is (in simple terms)
- First-time setup steps
- Workspace creation
- Repository connection
- Product information configuration
- How to use the first AI features (Code Quality, Documentation, Compliance)
- Interface navigation
- Tips for success
- Common questions and troubleshooting

## 2. **orchestrai-dev-how-to-documentation.md**
A detailed guide specifically for writing documentation with OrchestrAI, including:
- Prerequisites and setup
- Complete step-by-step instructions for creating new documentation
- How to migrate existing documentation
- Advanced options (checkpoints, updates, different doc types)
- Tips for writing better instructions
- Documentation structure recommendations
- Common questions and troubleshooting
- Best practices

Both documents follow the critical guidelines:
- ✅ **No technical jargon** - No mentions of code, file paths, or components
- ✅ **User-friendly language** - Written as if explaining to someone seeing the product for the first time
- ✅ **Focus on actions** - "Click the button", "Navigate to the section", "Select from the list"
- ✅ **Real features only** - Every instruction is based on actual components found in the source code
- ✅ **Clear, simple explanations** - Using everyday language and analogies
- ✅ **Actionable steps** - Numbered steps with clear outcomes

The documentation is placed in the `user-facing-docs` folder with the `orchestrai-dev-` prefix as required.