# orchestrai-dev - How to Generate Comprehensive Product Documentation

## Getting Started with Documentation Generation

OrchestrAI's AI Documentation Specialist helps you create professional, well-structured documentation for your product automatically. Whether you're starting from scratch or improving existing documentation, the AI analyzes your product and generates comprehensive guides tailored to your needs.

---

## Preparing to Generate Documentation

### Step 1: Check Your Configuration

Before generating documentation, make sure your workspace is properly set up:

1. Navigate to the **Product Information** page from the main menu
2. Verify that your documentation repository and folder are configured
3. If migrating existing documentation, ensure your documentation URL is set

If you see a yellow warning message saying "Configuration Required," click the **Configure Documentation URL** button to complete your setup.

### Step 2: Connect Your Repositories

The AI needs access to your code to generate accurate documentation:

1. Go to the **Code** section in the main menu
2. Connect your GitHub repositories by clicking **Connect Repository**
3. Enable OrchestrAI for the repositories you want documented
4. The AI will analyze these repositories to understand your product

### Step 3: Check Your Credits

Documentation generation uses AI credits from your plan:

- Look at the top of the documentation panel for your credit status
- Free plans have daily limits that reset every 24 hours
- Paid plans have monthly limits based on your subscription tier
- If you see a red alert about credits, you may need to upgrade your plan

---

## Generating New Documentation from Scratch

### Opening the Documentation Panel

1. Navigate to the **Documentation** page from the main menu
2. Click the **Create New Documentation** button
3. The AI Documentation Specialist panel will open on the right side of your screen

### Choosing What to Document

The AI can generate three main types of documentation:

**User Facing Documentation** (recommended for most products)
- Quick start guides to help users get started quickly
- Step-by-step tutorials for common tasks
- Feature guides showing how to use specific capabilities
- Reference documentation for APIs and technical details

**Internal Developer Documentation**
- Architecture overviews for your engineering team
- Development setup instructions
- Technical details for contributors

**Software Bill of Materials (SBOM)**
- Detailed inventory of software components
- Security and compliance tracking
- Available in CycloneDX and SPDX formats

### Selecting Content Structure

Click **Customize Scope & Content Structure** to expand advanced options:

1. **Check "User Facing documentation"** to generate customer-facing guides
2. Choose which types of content to create:
   - **Intro**: A quick start guide positioned at the beginning
   - **Tutorials**: End-to-end guides with specific outcomes
   - **How-To**: Short, task-focused instructions
   - **Reference**: Technical API and SDK documentation
   - **Troubleshooting**: Common problems and solutions
   - **Release Notes**: Automated change logs

Start with just **Intro**, **Tutorials**, and **Reference** for your first documentation run. You can always generate more types later.

### Choosing Which Code to Analyze

Expand the **Select Code Scope** section to choose what the AI should analyze:

1. You'll see all your OrchestrAI-enabled repositories
2. Click **Select All** to analyze your entire product, or select specific repositories
3. For each repository, choose:
   - **Whole Repo**: Analyzes all code in the repository
   - **Specific Commit**: Documents only changes in a particular code update

For your first documentation, select **Whole Repo** for all repositories to get complete coverage.

### Adding Instructions

In the **Additional Instructions** box, tell the AI about any special requirements:

- "Focus on getting started quickly with code examples"
- "Include security best practices in all guides"
- "Use simple language suitable for non-technical users"
- "Add troubleshooting tips for common errors"

These instructions take priority over default settings and help customize the output.

### Naming Your Documentation Files

Scroll down to see the **Files to be generated** section. Each file has:
- An editable filename (without the .md extension)
- A label describing what it contains

You can customize these filenames before generating. For example, change "intro" to "quickstart" if that fits your style better.

### Starting Generation

1. Review your selections in the panel
2. Click the blue **Generate Documentation** button at the bottom
3. A progress dialog will appear showing the AI's work
4. Generation typically takes 5-15 minutes depending on your product size

The AI will:
- Analyze your product's functionality
- Study your code structure
- Create well-organized documentation
- Commit the files to your repository

---

## Migrating Existing Documentation

If you already have documentation that needs improvement, the AI can restructure it:

### Before You Start

1. Navigate to the **Product Information** page
2. Enter your documentation URL in the **Documentation URL** field
3. Save your changes

### Opening the Migration Panel

1. Go to the **Documentation** page
2. Click the **Migrate Existing Documentation** button
3. The AI Documentation Specialist panel opens with migration options

### How Migration Works

The AI will:
- Access your existing documentation at the URL you provided
- Analyze the current structure and content
- Restructure it according to best practices
- Create improved versions in a new `migrated-docs` folder

Your original documentation remains untouched, so you can review the AI's work before replacing the old version.

### Customizing the Migration

Follow the same steps as creating new documentation:
1. Choose your documentation scope
2. Select content structure types
3. Pick which repositories to reference
4. Add specific instructions for the migration
5. Click **Generate Documentation**

The AI will preserve your existing content while organizing it more effectively.

---

## Resuming Interrupted Documentation

If documentation generation was interrupted, you can continue where it left off:

1. Go to the **Documentation** page
2. You'll see a green **Resume** button next to interrupted runs
3. Click **Resume** to reopen the panel
4. Your previous selections are automatically restored
5. Click **Generate Documentation** to continue

The AI uses saved checkpoints to resume without losing progress.

---

## Monitoring Progress

### Understanding the Progress Dialog

When generation starts, a dialog shows:
- **Current step**: What the AI is working on
- **Progress bar**: Overall completion percentage
- **Status messages**: Details about the current task

Common steps you'll see:
1. "Initializing documentation generation..."
2. "Analyzing product functionality..."
3. "Generating [content type] documentation..."
4. "Committing files to repository..."

### What to Do While Waiting

- You can minimize the progress dialog and continue working
- The process runs in the background
- You'll receive a notification when complete
- Don't close your browser tab until the process finishes

---

## Reviewing Generated Documentation

### Accessing Your Documentation

Once generation completes:

1. You'll see a success message with a green checkmark
2. The files are committed to your documentation repository
3. Navigate to your repository on GitHub to review the files
4. Files are organized in the folder you configured

### What You'll Find

Each generated file contains:
- **Clear structure**: Headings and sections for easy navigation
- **Code examples**: Where applicable to your product
- **Practical guidance**: Step-by-step instructions
- **User-friendly language**: Written for your target audience

### If Generation Fails

If you see a red error message:
1. Check the error details provided
2. Verify your repository permissions
3. Ensure your configuration is correct
4. Try generating again with the same settings

---

## Tips for Best Results

### Start Small
- Generate just user-facing documentation first
- Review the results before adding more types
- Expand to internal documentation after validating quality

### Provide Clear Instructions
- Be specific about your audience
- Mention any technical terms to include or avoid
- Specify the tone you want (formal, casual, technical)

### Choose Relevant Repositories
- Select only repositories that users interact with
- Exclude internal tools or deprecated code
- Focus on your core product features

### Review and Iterate
- Generated documentation is a starting point
- Edit the files in your repository to refine them
- Generate again with improved instructions if needed

### Use Whole Repo Initially
- Start with "Whole Repo" analysis for complete coverage
- Use "Specific Commit" later for updating documentation when you add features

---

## Understanding Your Credit Usage

Each documentation generation run consumes credits:

- **Free Plan**: 10 generations per day
- **Paid Plans**: Monthly allowance based on tier

To check your usage:
1. Look at the credit status alert in the documentation panel
2. Visit the **Account** page for detailed credit information
3. Upgrade your plan if you need more generations

---

## Common Questions

**How long does generation take?**
Most documentation generates in 5-15 minutes. Larger products with many repositories may take longer.

**Can I edit the generated documentation?**
Yes! The files are committed to your repository, where you can edit them like any other file.

**What if I don't like the results?**
Try generating again with more specific instructions. You can also manually edit the generated files.

**Can I generate documentation in multiple languages?**
Currently, documentation is generated in English. Multi-language support may be available in future updates.

**Do I need to regenerate documentation when my product changes?**
Use "Specific Commit" scope to update documentation based on recent changes without regenerating everything.

---

## Next Steps

After generating your documentation:

1. Review the files in your repository
2. Edit and customize the content as needed
3. Publish the documentation to your users
4. Set up a schedule for regular updates as your product evolves
5. Share feedback to help improve the AI's documentation capabilities

Well-structured documentation helps users succeed with your product and reduces support requests. The AI Documentation Specialist makes creating and maintaining high-quality documentation simple and efficient.