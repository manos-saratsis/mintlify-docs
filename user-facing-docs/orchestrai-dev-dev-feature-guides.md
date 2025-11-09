# orchestrai-dev-feature-guides.md

## Overview

This guide explains how to use the AI Documentation Specialist to generate documentation for your product. The AI Documentation Specialist is an AI-powered tool that analyzes your product and creates comprehensive documentation based on your selected scope, content structure, and custom instructions.

## Creating Documentation from Scratch

### Step 1: Access the AI Documentation Specialist

1. Navigate to the Documentation section in your workspace
2. Click the button to create new documentation
3. The AI Documentation Specialist panel will open on the right side of your screen

### Step 2: Select Your Documentation Scope

The AI Documentation Specialist offers three main documentation types:

**User Facing Documentation** - Documentation designed for end users of your product
- This is selected by default when you open the panel
- Best for creating guides, tutorials, and reference materials for your users

**Internal Developer Documentation** - Technical documentation for your development team
- Select this option by checking the "Internal developer documentation" box
- Creates architecture documentation, development setup guides, and developer overviews

**SBOM (Software Bill of Materials)** - Compliance and security documentation
- Check the "SBOM - Software Bill of Materials" box
- Generates both CycloneDX and SPDX format documentation

You can select multiple scopes at once. The AI will generate documentation for all selected types in a single run.

### Step 3: Customize Your Content Structure

When you select User Facing documentation, you can choose which sections to include:

**Quickstart / Introduction** (`/intro`) - A getting started guide positioned as your quickstart
- Checked by default
- Perfect for helping new users get up and running quickly

**Tutorials** (`/tutorials`) - End-to-end, outcome-driven guides
- Checked by default
- Step-by-step walkthroughs that help users accomplish specific goals

**How-To Guides** (`/how-to`) - Task-centric, focused instructions
- Short, focused guides for specific tasks
- Great for answering "How do I...?" questions

**API Reference** (`/reference`) - API and SDK documentation
- Checked by default
- Automatically generated technical reference documentation

**Concepts** (`/concepts`) - Architecture, models, and technical explanations
- Detailed explanations of how your product works
- Includes architecture diagrams and conceptual information

**Troubleshooting** (`/troubleshooting`) - Error catalog and log references
- Solutions to common problems
- Error messages and their resolutions

**Release Notes** (`/release-notes`) - Automated version history
- Automatically tracks changes and updates
- Keeps users informed of new features and fixes

To customize your content structure:

1. Click on "Customize Scope & Content Structure" to expand the options
2. Check or uncheck boxes based on what you want to include
3. The selected structure will determine which documentation files are created

### Step 4: Select Your Code Scope

If you have repositories connected to your workspace:

1. Click on "Select Code Scope" to expand the repository selector
2. All enabled repositories are selected by default
3. You can choose between two analysis options for each repository:
   - **Whole Repo** - Analyzes the entire repository for comprehensive documentation
   - **Specific Commit** - Documents only changes from a specific commit

To select a specific commit:
1. Click the "Specific Commit" button next to a repository
2. Browse through the list of recent commits that appears
3. Click on a commit to select it
4. The AI will focus on documenting the changes in that specific commit

### Step 5: Add Custom Instructions

The AI Documentation Specialist provides a text area for additional instructions that take priority over default settings:

1. Find the "Additional Instructions" section (marked with a "Priority" badge)
2. Enter specific instructions about what you want the documentation to focus on
3. Examples of useful instructions:
   - "Focus on explaining the authentication flow in detail"
   - "Include code examples for every API endpoint"
   - "Use beginner-friendly language throughout"
   - "Emphasize security best practices"

These instructions override your workspace's default documentation settings and apply only to this specific documentation run.

### Step 6: Choose File Naming Options

**Task Explanation Comments**
- Check "Add documentation task explanation at the top of the file" if you want each documentation file to include a header explaining its purpose
- Unchecked by default

**Custom File Names**
- Scroll down to the "Configuration" section to see the list of files that will be generated
- Each file shows its default name and purpose
- Click on any filename to edit it before generation
- File names use the `.md` format automatically

### Step 7: Generate Your Documentation

1. Review your selected options:
   - Documentation scope (User Facing, Internal, or SBOM)
   - Content structure selections
   - Selected repositories and commit scope
   - Custom instructions
   - File naming preferences

2. Click the "Generate Documentation" button at the bottom of the panel

3. A progress dialog will appear showing:
   - Current analysis stage
   - Estimated time remaining
   - Real-time status updates

4. Once complete, your documentation will be committed to your configured documentation repository

## Creating Focused Documentation with Custom Instructions

You can create highly focused documentation by combining scope selection with detailed instructions. Here's how:

### Example: API Reference Only

1. Under "Customize Scope & Content Structure", uncheck all boxes except "API Reference"
2. In "Additional Instructions", add:
   ```
   Create detailed API reference documentation with:
   - Complete endpoint descriptions
   - Request/response examples for each endpoint
   - Parameter definitions and types
   - Authentication requirements
   - Error codes and their meanings
   ```
3. Under "Configuration", change the filename from `reference` to `api-complete`
4. Click "Generate Documentation"

### Example: Troubleshooting Guide

1. Under "Customize Scope & Content Structure", uncheck all boxes except "Troubleshooting"
2. In "Additional Instructions", add:
   ```
   Create a comprehensive troubleshooting guide covering:
   - Common installation issues
   - Configuration problems
   - Runtime errors and solutions
   - Performance optimization tips
   - Debug logging instructions
   ```
3. Change the filename to `troubleshooting-complete`
4. Click "Generate Documentation"

### Example: Feature-Specific Tutorial

1. Select only "Tutorials" under content structure
2. In "Additional Instructions", add:
   ```
   Create a tutorial focused on the user authentication feature:
   - Setting up OAuth integration
   - Implementing sign-up and login flows
   - Managing user sessions
   - Handling password resets
   - Testing authentication locally
   ```
3. Change the filename to `auth-tutorial`
4. Select "Specific Commit" for the repository containing your auth code
5. Choose the commit where you implemented the authentication feature
6. Click "Generate Documentation"

## Understanding the Documentation Process

When you click "Generate Documentation", the AI:

1. **Product Analysis** - Accesses your product through the selected repositories to understand functionality
2. **Structured Generation** - Creates documentation following your selected content structure
3. **Code Deployment** - Commits the generated documentation files to your configured repository

The AI uses:
- Your product's actual code and functionality
- Your selected scope and content structure
- Your custom instructions (which take priority)
- Your workspace's default documentation settings

## Tips for Best Results

**Be Specific with Instructions**
- The more specific your instructions, the better the results
- Include examples of tone, style, or format you prefer
- Mention specific features or areas to emphasize

**Use Commit-Specific Analysis**
- When documenting new features, select the specific commit that introduced them
- This helps the AI focus on what's actually new or changed
- Particularly useful for release notes and change documentation

**Customize File Names**
- Use descriptive file names that clearly indicate content
- Consider version numbers for iterative documentation (e.g., `api-v2`)
- Keep names concise but meaningful

**Combine Multiple Scopes**
- You can generate user-facing and internal documentation in one run
- This ensures consistency across all your documentation
- Saves time by running the analysis only once

**Review Configuration First**
- Make sure your documentation repository and folder are configured in Workflow settings
- Verify that your target repositories are connected and enabled
- Check that you have sufficient credits for the documentation run

## Migrating Existing Documentation

If you have existing documentation that needs to be restructured:

1. Configure your documentation URL in Product Information settings
2. Open the AI Documentation Specialist panel
3. Select "Migrate Existing Documentation" instead of "Create New Documentation"
4. The AI will:
   - Analyze your current documentation structure
   - Restructure it according to best practices
   - Apply your selected content structure
   - Create migrated documentation in a new `migrated-docs` folder
5. Your original documentation remains intact during this process

## Resuming Documentation Generation

If a documentation generation is interrupted:

1. The system automatically saves checkpoints during the process
2. Navigate back to the Documentation section
3. Click to resume the interrupted generation
4. The AI will continue from where it left off using:
   - Your original configuration
   - Previously completed sections
   - The exact same settings you selected initially

You'll see a green indicator showing "Resuming from checkpoint" when this feature is active.

## Troubleshooting Common Issues

**"Configuration Required" Message**
- Your documentation repository and folder must be set up in Workflow settings
- Navigate to Product Information to configure these settings

**"Documentation URL Required" Message (Migration Only)**
- When migrating existing docs, you need to provide the URL where your current documentation is hosted
- Add this URL in Product Information settings

**"Select at least one scope" Message**
- You must choose at least one documentation type (User Facing, Internal, or SBOM)
- Check at least one box under "Documentation Scope"

**Credit Limit Reached**
- Your workspace has reached its monthly credit limit
- Click "Upgrade Plan" if you're an owner or admin
- Contact your workspace owner if you're not an admin

**"No Permission" Message**
- You need the Documentation permission enabled for your role
- Contact your workspace administrator to grant permission

## Best Practices

1. **Start Small** - Begin with a single scope and expand as needed
2. **Iterate** - Generate focused documentation multiple times with different instructions for different audiences
3. **Version Control** - Use custom file names to maintain different versions of documentation
4. **Test Instructions** - Try different instruction styles to find what works best for your product
5. **Regular Updates** - Use commit-specific analysis to keep documentation current with code changes
6. **Review Generated Content** - Always review AI-generated documentation before publishing to ensure accuracy and completeness