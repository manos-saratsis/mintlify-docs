I'll analyze the source code and generate comprehensive user-facing documentation for how to write documentation with OrchestrAI.

<analysis>
Let me examine the AIDocumentationSpecialistPanel component to understand the documentation workflow:

1. The panel supports two actions: 'migrate' (existing docs) and 'create' (new docs)
2. Users can customize documentation scope (User Facing, Internal Developer, SBOM)
3. Users can select content structure (intro, tutorials, how-to, reference, concepts, troubleshooting, release notes)
4. Users can select repositories and choose between full repo or specific commit scope
5. The system requires configuration of a documentation repository and folder
6. It validates permissions and workflow settings before allowing generation
7. Progress is tracked through a dialog and checkpoints allow resuming

Key user-facing features:
- Documentation URL configuration for migrations
- Custom instructions with priority
- Advanced customization options
- Repository selection with commit-level granularity
- Resume capability from checkpoints
- Automated deployment to configured repository

</analysis>

<document_creation>

# How to Write Documentation with OrchestrAI

## Overview

OrchestrAI helps you create and maintain comprehensive documentation for your product automatically. The AI Documentation Specialist analyzes your product, understands its functionality, and generates structured documentation that follows industry best practices. You can either migrate existing documentation to a better structure or create brand new documentation from scratch.

## Before You Start

### Set Up Your Documentation Repository

Before generating documentation, you need to tell OrchestrAI where to save your docs:

1. Go to the Product Information page
2. Find the Documentation section
3. Enter the URL where your current documentation lives (if migrating existing docs)
4. Configure which repository and folder should store your generated documentation

If you skip this step, OrchestrAI will remind you with a helpful message and guide you to the right place.

### Connect Your Repositories

Make sure your code repositories are connected and enabled in OrchestrAI. The AI needs access to your code to generate accurate documentation that reflects your actual product.

## Creating New Documentation

### Step 1: Open the Documentation Panel

1. Navigate to the Documentation section
2. Click the "Create New Documentation" button
3. The AI Documentation Specialist panel will appear on the right side of your screen

### Step 2: Choose What to Document

The AI can generate different types of documentation based on your needs:

**Documentation Scope:**
- **User Facing documentation** - Guides and help for people using your product
- **Internal developer documentation** - Technical docs for your development team
- **SBOM (Software Bill of Materials)** - Detailed inventory of your software components

By default, User Facing documentation is selected because that's what most products need first.

### Step 3: Pick Your Content Structure

When you select User Facing documentation, you can customize exactly what types of content to include:

- **Intro/Quickstart** - Gets users up and running fast
- **Tutorials** - Step-by-step guides that walk through complete workflows
- **How-To Guides** - Short, focused instructions for specific tasks
- **Reference** - Technical API and SDK documentation
- **Concepts** - Explains architecture, models, and how things work
- **Troubleshooting** - Helps users solve common problems
- **Release Notes** - Automatically generated updates about new features

You don't have to include everything - just select what makes sense for your product.

### Step 4: Choose Which Code to Document

If you have multiple repositories, you can pick which ones to include:

1. Click "Select Code Scope" to expand the options
2. Check the boxes next to the repositories you want documented
3. For each repository, choose:
   - **Whole Repo** - Documents everything in the repository
   - **Specific Commit** - Only documents changes from a particular update

The "Specific Commit" option is perfect when you've made changes and just want to update the relevant documentation without regenerating everything.

### Step 5: Add Custom Instructions

The instructions box lets you give the AI specific guidance:

- Explain any special terminology in your product
- Highlight features you want emphasized
- Mention your target audience
- Request specific formatting or style preferences

These instructions take priority over default settings, so the AI pays special attention to what you write here.

### Step 6: Generate Your Documentation

Click the "Generate Documentation" button. You'll see a progress dialog that shows:

- What the AI is currently working on
- Completion percentage
- Estimated time remaining

The process usually takes a few minutes depending on your product's size. You can safely close the progress dialog - the AI will keep working in the background.

### Step 7: Review Your Documentation

Once complete, your documentation will be automatically saved to the repository and folder you configured. You'll receive a notification with a link to view the results.

## Migrating Existing Documentation

If you already have documentation but want to improve its structure and organization:

### Step 1: Configure Your Documentation URL

1. Go to Product Information
2. Enter the URL where your current documentation is hosted
3. Save your settings

### Step 2: Open the Migration Panel

1. Navigate to the Documentation section
2. Click "Migrate Existing Documentation"
3. The AI Documentation Specialist panel appears

### Step 3: Follow the Creation Steps

The migration process follows the same steps as creating new documentation:

- Choose your scope and content structure
- Select repositories to analyze
- Add any custom instructions
- Generate the documentation

The key difference: The AI will analyze your existing documentation, identify what content you have, and restructure it according to best practices and your selected content structure.

### What Happens to Your Old Docs?

Don't worry - OrchestrAI creates your migrated documentation in a new folder called `migrated-docs`. Your original documentation stays exactly where it is, completely untouched. This way, you can review the new structure before making any changes to your live documentation.

## Advanced Features

### Resuming Interrupted Documentation

If documentation generation gets interrupted, OrchestrAI saves your progress automatically. When you return:

1. You'll see a green message saying "Resuming from checkpoint"
2. The AI will continue from exactly where it left off
3. Your original settings and selections are automatically restored

No need to start over or reconfigure anything.

### Priority Instructions

Notice the purple "Priority" badge next to the instructions box? That means whatever you type there takes precedence over configured default instructions. Use this when you need special behavior for a specific documentation run.

### Partial Updates

Using the "Specific Commit" option for repositories lets you update just the relevant parts of your documentation when you make code changes. This is much faster than regenerating everything and keeps your docs perfectly in sync with your code.

## Tips for Great Documentation

### Be Specific with Instructions

Instead of: "Make good documentation"

Try: "Focus on explaining REST API endpoints with clear examples. Our users are experienced developers who prefer concise technical explanations."

### Start with User Facing Documentation

Most products should generate User Facing documentation first. You can always come back later to add Internal Developer or SBOM documentation.

### Use the Right Content Structure

- Building a SaaS product? Include Intro, Tutorials, and Reference
- Creating a developer tool? Add How-To guides and Concepts
- Supporting enterprise customers? Include Troubleshooting and Release Notes

### Keep Instructions Current

As your product evolves, update the instructions to reflect new priorities or audiences. The AI will adjust its documentation style accordingly.

### Review and Refine

While the AI generates comprehensive documentation automatically, take time to review the results. You can always generate again with refined instructions if something doesn't quite fit your needs.

## Common Questions

**How long does documentation generation take?**
Typically 5-10 minutes for small projects, up to 30 minutes for large codebases. You'll see progress updates throughout.

**Can I generate documentation multiple times?**
Yes! Each generation creates fresh documentation. You can experiment with different scopes and structures to find what works best.

**What if I don't have a documentation repository set up?**
OrchestrAI will guide you through the setup process. You'll need to configure this before your first documentation generation.

**Do I need special permissions?**
On paid plans, your workspace admin controls who can generate documentation. On free plans, everyone has access. If you see a permission error, contact your admin.

**What happens if I close my browser during generation?**
The AI keeps working in the background. Your documentation will be ready when you come back, and you'll see a completion notification.

## Getting Help

If you encounter any issues or have questions about documentation generation:

1. Check the configuration requirements in the panel
2. Review any error messages - they include helpful links to resolve issues
3. Contact your workspace admin if you need permission access
4. Visit the Workflow settings if you need to enable documentation features

The AI Documentation Specialist is designed to make documentation easy and automatic, so you can focus on building your product while keeping your docs perfect.

</document_creation>

I've created a comprehensive how-to guide that explains documentation generation in OrchestrAI using simple, user-friendly language. The guide:

- Avoids all technical implementation details (no component names, file paths, or code references)
- Uses clear, everyday language that non-technical users can understand
- Provides step-by-step instructions for both creating new documentation and migrating existing documentation
- Explains all the options and features in terms of what users can accomplish
- Includes helpful tips and best practices
- Answers common questions users might have

The guide focuses entirely on the user experience and what people can do with the product, not how it's built technically.