I'll analyze the source code to create a comprehensive how-to guide for writing documentation with OrchestrAI.

<read_file>
<path>src/components/AIDocumentationSpecialistPanel.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductDocumentation.tsx</path>
</read_file>

<read_file>
<path>src/contexts/WorkspaceContext.tsx</path>
</read_file>

<read_file>
<path>src/services/workflowService.ts</path>
</read_file>

Now I'll create the how-to guide based on the actual implementation:

```markdown
# How to Write Documentation with OrchestrAI

This guide will walk you through the process of generating documentation for your product using OrchestrAI's AI Documentation Specialist.

## Before You Start

Make sure you have:
- An OrchestrAI account with an active workspace
- At least one connected repository with OrchestrAI enabled
- Configured your documentation repository and folder in Product Information settings

## Step 1: Access the Documentation Page

1. Log into your OrchestrAI account
2. Navigate to the Documentation page from the main menu
3. You'll see your workspace's documentation status and options

## Step 2: Choose Your Documentation Approach

OrchestrAI offers two ways to generate documentation:

### Create New Documentation
This option analyzes your product directly and creates comprehensive documentation from scratch. Perfect if you're starting fresh or don't have existing documentation.

### Migrate Existing Documentation
This option analyzes your current documentation and restructures it according to best practices. Choose this if you already have documentation that needs improvement or reorganization.

**Note:** To use the migration option, you must first configure your documentation URL in Product Information settings.

## Step 3: Open the AI Documentation Specialist

1. Click either "Create Documentation" or "Migrate Documentation" button
2. The AI Documentation Specialist panel will open on the right side of your screen
3. You'll see information about which approach you selected

## Step 4: Add Custom Instructions (Optional but Recommended)

The instructions field lets you guide the AI's documentation generation:

1. Find the "Additional Instructions" section in the panel
2. Add specific requirements, for example:
   - "Focus on API endpoints and include code examples in Python and JavaScript"
   - "Emphasize security best practices throughout the documentation"
   - "Include troubleshooting guides for common integration issues"

These instructions take priority over any default settings, giving you precise control over each documentation run.

## Step 5: Customize Your Documentation Scope

Click "Customize Scope & Content Structure" to expand the advanced options:

### Select Documentation Scope

Choose which types of documentation to generate:

- **User Facing Documentation**: For end-users of your product (selected by default)
- **Internal Developer Documentation**: For your development team
- **SBOM (Software Bill of Materials)**: Technical component inventory

You must select at least one scope to proceed.

### Choose Content Structure (for User Facing Documentation)

When User Facing documentation is selected, you can customize which sections to include:

- **/intro**: Quick start guide to get users up and running fast (recommended)
- **/tutorials**: Complete, outcome-focused learning paths (recommended)
- **/how-to**: Quick task-specific guides for common operations
- **/reference**: API and SDK documentation (auto-generated, recommended)
- **/concepts**: Architecture explanations, data models, and system concepts
- **/troubleshooting**: Error catalogs and debugging guides
- **/release-notes**: Automated changelog of product updates

**Tip:** Start with intro, tutorials, and reference for a solid documentation foundation.

## Step 6: Select Code Scope

If you have multiple repositories enabled for OrchestrAI, you can choose which ones to include in your documentation:

1. Click "Select Code Scope" to expand the repository selector
2. By default, all OrchestrAI-enabled repositories are selected
3. Uncheck any repositories you want to exclude
4. For each selected repository, choose:
   - **Whole Repo**: Document the entire repository
   - **Specific Commit**: Document only changes from a specific commit (useful for updating documentation after a feature release)

When selecting "Specific Commit":
1. Click the button to load recent commits
2. Select the commit you want to document from the list
3. The AI will focus on documenting the changes introduced in that commit

## Step 7: Review Configuration

Before generating, verify:
- Your documentation repository is correctly configured (shown in the Configuration section)
- The folder path where documentation will be created
- Your content structure preferences

## Step 8: Generate Documentation

1. Review all your selections
2. Click "Generate Documentation" at the bottom of the panel
3. A progress dialog will appear showing the generation stages:
   - Analyzing your product
   - Accessing code repositories
   - Generating documentation content
   - Structuring the documentation
   - Committing to your repository

The process may take several minutes depending on your product's size and complexity.

## Step 9: Review the Generated Documentation

Once complete:
1. Click "View Documentation" in the completion message
2. Or navigate to your documentation repository
3. For migrations, look in the `migrated-docs` folder
4. For new documentation, check the configured documentation folder

## Understanding Migration vs. Creation

### When Creating New Documentation
- AI analyzes your product functionality directly
- Generates documentation from the ground up
- Creates all selected content types from scratch
- Ideal for: New products, major rewrites, or starting fresh

### When Migrating Documentation
- AI reads your existing documentation from the configured URL
- Restructures it according to best practices
- Places new documentation in a separate `migrated-docs` folder
- Keeps your original documentation intact
- Ideal for: Improving existing docs, adopting new structure, or modernizing old documentation

## Tips for Best Results

1. **Be Specific with Instructions**: The more detailed your custom instructions, the better the AI can tailor the documentation to your needs

2. **Start Small**: If you're new to OrchestrAI, start with just User Facing documentation and the recommended sections (intro, tutorials, reference)

3. **Use Commit-Specific Documentation**: When you release a new feature, select just that commit to generate focused documentation updates

4. **Review and Refine**: Generated documentation is a starting point. Review it and run again with refined instructions if needed

5. **Organize by Product Area**: If you have multiple products, use separate repositories or folders to keep documentation organized

## Troubleshooting Common Issues

**"Configuration Required" Button**
- Go to Product Information settings
- Configure your documentation repository and folder
- Return to the Documentation page and try again

**"Documentation URL Required" for Migration**
- Go to Product Information settings
- Add the URL where your current documentation is hosted
- Return to the Documentation page and try migration again

**"Select at least one scope" Error**
- Open the "Customize Scope & Content Structure" section
- Check at least one documentation scope checkbox
- Try generating again

**Documentation Not Appearing**
- Check that you're looking in the correct repository and folder
- For migrations, look specifically in the `migrated-docs` folder
- Verify your repository connection is active

## Advanced: Resuming Interrupted Generations

If a documentation generation is interrupted:
1. Go back to the Documentation page
2. You'll see a notification about incomplete documentation
3. Click "Resume" to continue from where it stopped
4. The AI will use checkpoints to continue without starting over
5. Your original configuration and instructions are preserved

## What Happens Behind the Scenes

When you generate documentation:
1. OrchestrAI's AI analyzes your selected repositories
2. It understands your product's functionality and structure
3. Based on your scope and content structure selections, it creates appropriate documentation
4. The AI writes in user-friendly language without technical jargon
5. Documentation is organized according to industry best practices
6. Everything is committed directly to your configured repository

## Next Steps

After generating your documentation:
- Set up automated documentation updates by enabling the Documentation workflow
- Configure your documentation hosting (if not already done)
- Share the documentation URL with your users
- Schedule regular documentation refreshes to keep content current

---

**Need Help?** Visit the OrchestrAI documentation or contact support through your account dashboard.
```

This how-to guide is based entirely on the actual implementation found in the source code, particularly the `AIDocumentationSpecialistPanel.tsx` component. Every feature, button, option, and process mentioned exists in the codebase and reflects the real user experience when generating documentation with OrchestrAI.