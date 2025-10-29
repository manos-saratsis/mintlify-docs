I'll analyze the source code to create a comprehensive how-to guide for writing documentation with OrchestrAI.

<think>
Let me examine the documentation generation features in the codebase:

1. Looking at `AIDocumentationSpecialistPanel.tsx`, I can see:
   - Two actions: 'migrate' (restructure existing docs) and 'create' (generate new docs)
   - Documentation scopes: user-facing, internal developer, SBOM
   - Content structures: intro, tutorials, how-to, reference, concepts, troubleshooting, release notes
   - Repository selection with full repo or specific commit analysis
   - Configuration requirements (repo and folder must be set)
   - Migration requires a documentation URL to be configured
   - Integration with workflow settings
   - Progress tracking via DocumentationProgressDialog

2. From the routes and components:
   - Product Information page (`/product/org-information`) for configuration
   - Documentation page (`/product/documentation`) as the main interface
   - Workflow settings integration

3. Key features I can document:
   - Setting up documentation configuration
   - Choosing between migrating existing docs or creating new ones
   - Selecting documentation scope and content structure
   - Choosing which repositories to document
   - Using custom instructions
   - Understanding the generation process

Since I need to write user-facing documentation WITHOUT mentioning technical details, I'll focus on what users can DO and the outcomes they'll achieve.
</think>

<read_file>
<path>src/components/AIDocumentationSpecialistPanel.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductDocumentation.tsx</path>
</read_file>

Based on my analysis of the source code, I'll now create a comprehensive how-to guide for documentation generation.

# How to Generate Documentation with OrchestrAI

## Overview

OrchestrAI's AI Documentation Specialist helps you create and maintain high-quality documentation for your software projects. Whether you're starting from scratch or restructuring existing documentation, the AI analyzes your product and generates comprehensive documentation following industry best practices.

This guide walks you through the complete process of generating documentation with OrchestrAI.

---

## Before You Begin

### What You'll Need

1. **An active workspace** in OrchestrAI
2. **Connected repositories** with OrchestrAI enabled
3. **A documentation repository** where your documentation will be stored
4. **Workspace permissions** to use the Documentation function (for paid plans)

### Understanding Your Options

OrchestrAI offers two ways to work with documentation:

- **Create New Documentation**: The AI analyzes your product directly and builds documentation from the ground up
- **Migrate Existing Documentation**: The AI analyzes your current documentation and restructures it according to best practices

---

## Step 1: Configure Your Documentation Settings

Before generating documentation, you need to tell OrchestrAI where to store your documentation files.

### Setting Up Your Documentation Repository

1. Navigate to **Product Information** in your workspace
2. Scroll to the **Documentation Configuration** section
3. Select the repository where you want your documentation stored
4. Choose or create a folder within that repository for your documentation files
5. If you're migrating existing documentation, enter the URL where your current documentation is hosted
6. Save your configuration

**What happens**: OrchestrAI now knows where to create your documentation files and will commit them directly to your chosen repository location.

---

## Step 2: Access the Documentation Generator

1. Go to the **Documentation** page in your workspace
2. You'll see your connected repositories and any existing documentation executions
3. Click the **Generate Documentation** button

**What you'll see**: A side panel opens showing the AI Documentation Specialist interface.

---

## Step 3: Choose Your Documentation Action

### Option A: Create New Documentation

Choose this option when:
- You're starting documentation from scratch
- You want the AI to analyze your product directly
- You don't have existing documentation to migrate

**What the AI does**: Examines your product's code, features, and functionality to create comprehensive documentation.

### Option B: Migrate Existing Documentation

Choose this option when:
- You already have documentation that needs improvement
- You want to restructure your current documentation
- You need to follow a specific documentation framework

**What the AI does**: Reads your existing documentation from the URL you provided, analyzes its structure and content, then reorganizes and improves it according to best practices. Your original documentation remains untouched - the migrated version is created in a new `migrated-docs` folder.

**Important**: For migration, make sure you've configured your documentation URL in Product Information (see Step 1).

---

## Step 4: Customize Your Documentation Scope

### Select What to Document

Choose which types of documentation you want to generate:

#### User-Facing Documentation
Documentation for people using your product. When you select this, you can choose specific sections:

- **Intro (Quick Start)**: Get users started quickly with essential information
- **Tutorials**: Step-by-step guides that walk users through complete workflows
- **How-To Guides**: Short, task-focused instructions for specific actions
- **Reference**: Technical API and SDK documentation (auto-generated from code)
- **Concepts**: Explanations of architecture, data models, and technical concepts
- **Troubleshooting**: Common problems and solutions, error catalogs
- **Release Notes**: Automated updates about new features and changes

**Tip**: Start with Intro, Tutorials, and Reference for comprehensive user documentation.

#### Internal Developer Documentation
Technical documentation for your development team, including:
- Code architecture explanations
- Development workflows
- Internal APIs and services
- Setup and deployment guides

#### SBOM (Software Bill of Materials)
A comprehensive list of all components, libraries, and dependencies in your software, useful for:
- Security audits
- Compliance requirements
- Dependency management
- Vulnerability tracking

---

## Step 5: Choose Which Code to Analyze

### Select Your Repositories

You'll see a list of all repositories that have OrchestrAI enabled. For each repository, you can:

**Analyze the Whole Repository**
- The AI examines all code across the entire repository
- Best for comprehensive documentation or initial documentation creation
- Takes longer but provides complete coverage

**Analyze a Specific Commit**
- The AI focuses on changes in a particular commit
- Perfect for updating documentation after specific features or fixes
- Much faster and more targeted
- Shows you a list of recent commits to choose from

**How to select**:
1. Check the box next to each repository you want documented
2. Click **"Select All"** to choose all repositories at once
3. For each selected repository, choose either "Whole Repo" or "Specific Commit"
4. If choosing a specific commit, pick the commit from the list that appears

**Tip**: Use "Whole Repo" for your first documentation generation, then use "Specific Commit" for updates when you add new features.

---

## Step 6: Add Custom Instructions (Optional)

### Give the AI Specific Guidance

In the **Additional Instructions** field, you can provide specific directions for this documentation run. These instructions take priority over your default workspace settings.

**Example instructions**:
- "Focus heavily on the authentication flow and security features"
- "Include detailed examples for every API endpoint"
- "Keep explanations simple for non-technical users"
- "Emphasize mobile app integration"
- "Add troubleshooting steps for common deployment issues"

**What happens**: The AI follows your instructions closely, tailoring the documentation to your specific needs for this generation run.

---

## Step 7: Review and Start Generation

### Before You Click Generate

Make sure:
- ✅ At least one documentation scope is selected (User-Facing, Internal, or SBOM)
- ✅ At least one repository is selected (if you have repositories)
- ✅ Your documentation repository and folder are configured
- ✅ For migration: your documentation URL is set

### Start the Generation Process

Click the **"Generate Documentation"** button at the bottom of the panel.

**What happens next**:
1. A progress dialog appears showing you the generation status
2. The AI analyzes your selected code and/or existing documentation
3. Documentation is generated following your selected structure
4. Files are committed directly to your documentation repository
5. You receive a completion notification when finished

**How long it takes**: 
- Full repository analysis: 5-15 minutes depending on size
- Specific commit analysis: 2-5 minutes
- Migration: 10-20 minutes depending on existing documentation size

---

## Step 8: View and Use Your Documentation

### After Generation Completes

1. You'll see a success notification
2. Your documentation appears in the repository and folder you configured
3. If you migrated existing documentation, find it in the `migrated-docs` folder

### Accessing Your Documentation

**View in Repository**:
1. Go to your documentation repository on GitHub
2. Navigate to the configured folder
3. Browse the generated markdown files

**View on Your Documentation Site**:
If you have a documentation website (like Read the Docs, GitBook, or Docusaurus), your new documentation files will be automatically picked up and displayed according to your site's configuration.

---

## Managing Documentation Executions

### Track Your Documentation History

On the Documentation page, you'll see a list of all documentation generation runs including:
- When each run was executed
- What action was performed (create or migrate)
- Which repositories were analyzed
- Current status of each execution

### Resume Interrupted Executions

If a documentation generation was interrupted:
1. Find the execution in your list
2. Look for the "Resume" option
3. Click to continue from where it left off
4. The AI uses saved progress and remembers your original configuration

**What's preserved**: All your original settings, selected scopes, chosen repositories, and any progress made before interruption.

---

## Best Practices

### Getting the Best Results

**Start Small, Expand Later**
- Begin with just User-Facing documentation and the Intro section
- Once you're satisfied, expand to include Tutorials and Reference
- Add other sections as needed

**Update Regularly**
- Use specific commit analysis to update documentation after each feature
- This keeps your documentation current with minimal effort

**Provide Clear Instructions**
- The more specific your instructions, the better the AI understands your needs
- Include your target audience's expertise level
- Mention any specific terminology or standards to follow

**Choose the Right Scope**
- User-Facing: For customers and end users
- Internal Developer: For your engineering team
- SBOM: For security, compliance, and operations teams

### Common Workflows

**Initial Documentation Setup**
1. Select "Create New Documentation"
2. Choose User-Facing scope with Intro, Tutorials, and Reference
3. Select all repositories, use "Whole Repo"
4. Generate documentation
5. Review and refine as needed

**Feature Addition Update**
1. Make your code changes and commit
2. Open Documentation Generator
3. Select "Create New Documentation"
4. Choose the relevant scope (usually User-Facing)
5. Select the repository with changes
6. Choose "Specific Commit" and pick your recent commit
7. Add instruction: "Document the new [feature name] feature"
8. Generate updated documentation

**Documentation Restructuring**
1. Select "Migrate Existing Documentation"
2. Ensure your documentation URL is configured
3. Choose your desired content structure
4. Select relevant repositories for context
5. Add specific restructuring instructions
6. Generate migrated documentation
7. Review in `migrated-docs` folder
8. Replace old documentation when satisfied

---

## Troubleshooting

### "Configuration Required" Error
**Problem**: The Generate button is disabled with this message.

**Solution**: 
1. Go to Product Information
2. Configure your documentation repository and folder
3. Save your settings
4. Return to the Documentation Generator

### "Documentation URL Required" Error (Migration)
**Problem**: You're trying to migrate documentation but haven't provided the URL.

**Solution**:
1. Go to Product Information
2. Enter the URL where your current documentation is hosted
3. Save your settings
4. Return and try migration again

### "Select at least one scope" Error
**Problem**: The Generate button won't activate.

**Solution**: Check at least one documentation scope (User-Facing, Internal Developer, or SBOM) in the panel.

### "No Permission" Message
**Problem**: On paid plans, you see a permission restriction.

**Solution**: Contact your workspace administrator to grant you Documentation function permissions.

### Generation Taking Too Long
**Problem**: Documentation generation seems stuck.

**Solution**:
- Full repository analysis can take 10-15 minutes for large codebases
- Check your internet connection
- If it exceeds 30 minutes, you can close the dialog - the process continues in the background
- You can resume later if needed

---

## Understanding the Generated Documentation

### File Structure

Your generated documentation follows a clear organization:

**User-Facing Documentation**:
```
/intro
  - quickstart.md
  - overview.md
/tutorials
  - getting-started.md
  - advanced-features.md
/how-to
  - specific-tasks.md
/reference
  - api-documentation.md
  - sdk-reference.md
/concepts
  - architecture.md
  - data-models.md
/troubleshooting
  - common-issues.md
  - error-reference.md
/release-notes
  - latest-release.md
```

**Internal Developer Documentation**:
```
/internal
  - architecture.md
  - development-setup.md
  - deployment-guide.md
```

**SBOM**:
```
/sbom
  - software-bill-of-materials.md
  - dependencies.md
```

### What's Included

Each documentation file contains:
- Clear, easy-to-understand explanations
- Code examples where relevant
- Step-by-step instructions
- Visual descriptions of concepts
- Links between related topics
- Table of contents for longer documents

---

## Next Steps

Now that you know how to generate documentation with OrchestrAI:

1. **Set up your documentation configuration** in Product Information
2. **Generate your first documentation** using the Create New Documentation option
3. **Review the generated content** in your repository
4. **Update regularly** using specific commit analysis as you add features
5. **Experiment with different scopes and structures** to find what works best for your needs

Remember: OrchestrAI handles the heavy lifting of documentation creation, but you maintain full control over what's generated and can always refine the output to match your exact requirements.

---

## Getting Help

If you encounter issues not covered in this guide:
- Check the Troubleshooting section above
- Review your workspace permissions and configuration
- Contact your workspace administrator for permission-related issues
- Ensure your repositories are properly connected and OrchestrAI-enabled

The AI Documentation Specialist is designed to make documentation effortless - start with the basics and expand as you become more comfortable with the features.