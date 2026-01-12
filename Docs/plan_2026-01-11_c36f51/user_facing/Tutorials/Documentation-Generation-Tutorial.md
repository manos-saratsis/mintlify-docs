# Documentation Generation Tutorial

Learn how to generate and publish comprehensive documentation for your products, including user guides, developer documentation, API references, and security reports.

## Overview

The Documentation Generation system automatically creates and maintains documentation by analyzing your codebase. It can generate three types of documentation:

- **User-Facing Documentation**: Guides, tutorials, and help content for your end users
- **Internal Developer Documentation**: Architecture, setup guides, and technical references for your development team
- **Security Documentation**: Software Bill of Materials (SBOM) reports and compliance documentation

## Prerequisites

Before generating documentation, ensure you have:

1. **A Git Connection**: Your GitHub account must be connected to store documentation
2. **Documentation Enabled**: Turn on documentation generation in your Workflow settings
3. **Target Repository Configured**: Choose where generated documentation should be saved
4. **Product with Repositories**: At least one code repository assigned to your product

## Getting Started

### Step 1: Connect Your GitHub Account

1. Navigate to the Code section
2. Select the Connection Management tab
3. Click "Add Git Connection"
4. Follow the authorization flow to connect your GitHub account

### Step 2: Enable Documentation

1. Go to your Workflow settings
2. Find the Documentation section
3. Toggle documentation to "Enabled"
4. Select your target repository and folder where documentation will be saved

### Step 3: Assign Repositories to Your Product

1. Visit the Code section
2. Find repositories you want to document
3. Assign them to your product

## Generating Documentation

### Understanding Documentation Plans

Before generating documentation, you can create a plan that outlines all the documentation pages that will be generated. This helps you review and customize what will be created.

**To create a documentation plan:**

1. Navigate to the Documentation Management page
2. Select the Planning tab
3. Choose which types of documentation you want to generate
4. Optionally add notes to guide the AI about specific topics to cover
5. Click "Generate Plan"

The system will analyze your codebase and create a detailed plan showing all the documentation pages it will generate, organized by category.

### Creating New Documentation

Once you're satisfied with your plan:

1. Review the generated tasks in the Planning tab
2. Select specific documentation pages you want to generate, or generate all
3. Click "Generate Selected"
4. The AI will analyze your code and create documentation

**What happens during generation:**

- The system examines your codebase to understand features and functionality
- For each documentation page, it creates comprehensive, accurate content
- Generated documentation is written in clear, user-friendly language
- Files are automatically organized into appropriate folders
- Changes are committed to your documentation repository

### Choosing What to Document

You can select from three main documentation categories:

**User-Facing Documentation** includes:
- Getting Started guides to help new users
- Step-by-step tutorials for common tasks
- Feature guides explaining how to use specific capabilities
- Core concepts explaining how the product works
- Troubleshooting help for common issues
- Release notes describing what's new
- Frequently Asked Questions

**Internal Developer Documentation** includes:
- System architecture overviews
- Development environment setup instructions
- API documentation for internal services
- Component documentation
- Testing and QA guidelines
- Deployment and CI/CD processes
- Contributing guidelines

**Security Documentation** includes:
- Software Bill of Materials in CycloneDX format
- Software Bill of Materials in SPDX format
- Security policies and access controls
- Threat models and risk assessments
- Compliance documentation

### Generating Release Notes

Release notes are special because they document changes in specific code commits:

1. When selecting repositories for documentation, choose the commit scope
2. Select one or more commits you want to document
3. The system will analyze what changed in those commits
4. Generated release notes will describe new features, bug fixes, and improvements

**Note**: Release notes can only be generated when you've selected specific commits. If you select full repository scope, release notes will be skipped.

## Monitoring Generation Progress

### Viewing Active Generations

While documentation is being generated:

1. The Documentation Changes tab shows all active generations
2. Each entry displays current progress and status
3. You can continue working while generation runs in the background
4. Click "Resume" on any active generation to see detailed progress

### Understanding Generation Status

Generations progress through several stages:

- **Connecting**: Establishing access to your code repository
- **Planning**: Creating the documentation outline
- **Generating**: AI is writing documentation content
- **Committing**: Saving completed documentation to your repository
- **Completed**: Documentation is ready and available

If any issues occur, you'll see an error message explaining what went wrong and how to fix it.

## Reviewing and Retrying

### Viewing Generated Documentation

After generation completes:

1. Go to the Documentation Changes tab
2. Find your completed generation
3. Click to view all files that were created
4. Review the content to ensure it meets your needs

### Regenerating Documentation

If you want to update or recreate documentation:

1. Find the previous generation in the Documentation Changes tab
2. Click "Retry" to regenerate with the same settings
3. Or create a new generation with different parameters

### Refreshing Documentation Plans

As your product evolves, you can refresh your documentation plan:

1. Go to the Planning tab
2. Click "Refresh Plan"
3. The system identifies which documentation is outdated
4. New documentation pages are suggested for new features
5. Review and generate updated content

## Advanced Options

### Customizing Generated Content

You can provide specific guidance to the AI:

1. When creating a plan or generating documentation, look for the "Additional Instructions" field
2. Enter notes about specific topics to emphasize or exclude
3. Mention particular features that need extra attention
4. Request specific formats or styles

### Selecting Specific Documentation Pages

Instead of generating all documentation:

1. Review your documentation plan
2. Check the boxes next to specific pages you want to generate
3. Click "Generate Selected"
4. Only those pages will be created

### Organizing Documentation

Generated documentation is automatically organized:

- **User-facing documentation** goes into a "user-facing-docs" subfolder
- **Internal developer documentation** goes into an "internal-docs" subfolder
- **Security documentation** goes into a "security-docs" subfolder
- Files are prefixed with repository names for multi-repository products

Each plan creates a unique folder (e.g., "plan_2024-01-15_a3b4c5") to keep different documentation versions separate.

## Integration with Documentation Frameworks

The generated markdown files work seamlessly with popular documentation frameworks:

### Using with Mintlify

If your documentation URL points to Mintlify:
1. Generated files follow Mintlify's markdown conventions
2. Navigation structure is compatible with Mintlify's sidebar
3. Simply commit the files and Mintlify will automatically publish them

### Using with Docusaurus

For Docusaurus documentation sites:
1. Generated markdown includes proper frontmatter
2. File organization matches Docusaurus conventions
3. Move generated files to your Docusaurus docs folder

### Custom Documentation Sites

Generated markdown works with any documentation system:
1. Files use standard markdown syntax
2. Clear heading hierarchy for navigation
3. No framework-specific syntax or dependencies

## Publishing Your Documentation

### Automatic Publishing

If you have continuous deployment set up:
1. Documentation is committed to your repository
2. Your CI/CD pipeline detects the changes
3. Documentation is automatically built and deployed

### Manual Publishing

To publish manually:
1. Pull the latest changes from your documentation repository
2. Review the generated content
3. Push to your deployment branch
4. Your documentation site will update

## Best Practices

### Planning Before Generating

- Always create and review a plan before generating documentation
- Check that all important features are covered
- Remove any documentation pages that aren't relevant

### Keeping Documentation Current

- Set a regular schedule to refresh your documentation plan
- Regenerate documentation after major feature releases
- Use release notes generation after each significant update

### Providing Clear Context

- Include links to your product documentation site in settings
- Add notes about your target audience when generating content
- Specify any terminology or branding preferences

### Organizing Multiple Products

- Create separate plans for different products
- Use consistent naming conventions across products
- Keep documentation repositories organized by product

## Troubleshooting

### Documentation Won't Generate

**If you see "No repositories assigned"**:
- Go to the Code section
- Assign at least one repository to your product
- Return to Documentation Management and try again

**If you see "Target repository not configured"**:
- Visit Workflow settings
- Select a repository and folder for documentation
- Save your changes

**If you see "Documentation is not enabled"**:
- Open Workflow settings
- Enable the Documentation workflow
- Confirm your changes

### Generation Gets Stuck

If a generation seems frozen:
- Check the Documentation Changes tab for error messages
- Click "Retry" to attempt generation again
- Ensure your Git connection is still active
- Verify you have sufficient credits available

### Generated Content Is Incomplete

If documentation is missing information:
- Add specific notes when generating to guide the AI
- Ensure all relevant repositories are assigned to your product
- Check that your codebase has descriptive comments and README files
- Try refreshing the plan to identify what's missing

### Release Notes Show an Error

Release notes require specific commits:
- When selecting repositories, choose "Commit scope"
- Select one or more commits to document
- If you selected "Full repository", release notes cannot be generated

## Getting Help

If you encounter issues not covered here:
- Check the error messages for specific guidance
- Review your workflow and repository settings
- Ensure all prerequisites are met
- Contact support with details about the generation that failed

## What's Next

After generating documentation:
- **Review and refine**: Check generated content for accuracy
- **Customize further**: Edit files directly in your repository
- **Set up automation**: Configure automatic documentation updates
- **Share with your team**: Publish to your documentation site
- **Iterate regularly**: Keep documentation fresh as your product evolves