# How to Generate Documentation

## Overview

Generate comprehensive documentation for your projects automatically using AI—from user guides and tutorials to API references and security compliance documents. The documentation system analyzes your codebase and creates professional documentation tailored to different audiences, all kept in sync with your code.

## Getting Started

### Prerequisites

Before generating documentation, ensure you have:

- **Active Workspace**: Select your workspace from the top navigation bar
- **Connected Repository**: Link your GitHub repository in the Code section
- **Product Created**: Set up a product and assign repositories to it
- **Documentation Enabled**: Turn on documentation in your Workflow settings

### Initial Setup

1. **Connect Your Repository**
   - Navigate to the Code page
   - Click "Add Git Connection"
   - Authorize OrchestrAI to access your GitHub repositories
   - Select the repositories you want to document

2. **Assign Repositories to Your Product**
   - Go to the Code page
   - Find your repository in the list
   - Select your product from the dropdown menu
   - Save your changes

3. **Enable Documentation**
   - Visit the Workflow settings page
   - Find the "Documentation" workflow
   - Toggle it to "Enabled"
   - Select where documentation should be saved (repository and folder)
   - Save your configuration

## Types of Documentation

The system can generate six distinct types of documentation:

### User-Facing Documentation

Written in plain, everyday language for people using your product:

- **Getting Started Guides**: Quick start tutorials and account setup walkthroughs that help new users reach their first success
- **How-To Guides**: Step-by-step instructions for every feature with visual walkthroughs and common workflows
- **Concept Explanations**: Core concepts and key terms explained without technical jargon
- **API References**: Complete API documentation with examples for developers integrating with your product
- **Troubleshooting**: Common questions answered, error solutions, and performance tips
- **Release Notes**: Updates explained in clear language with new features highlighted and breaking changes called out

### Internal Developer Documentation

Technical documentation for your development team:

- **Architecture Documentation**: System architecture overviews and data flow diagrams
- **API Documentation**: Internal API specifications and edge function references
- **Component Documentation**: UI component guides, React hooks documentation, and service layer explanations
- **Testing & QA**: Test strategy documentation, coverage reports, and QA processes
- **Deployment & DevOps**: CI/CD pipeline documentation, infrastructure guides, and monitoring setup
- **Contributing Guidelines**: Code style guides, pull request processes, and review guidelines

### Security Documentation

Compliance and security materials for audits:

- **SBOM (Software Bill of Materials)**: Dependency lists in both SPDX and CycloneDX formats for security audits
- **Security Policies**: Access control documentation and data protection guidelines
- **Threat Model**: Threat assessments and risk mitigation strategies
- **Compliance Documentation**: Regulatory requirement tracking and audit documentation

## Planning Your Documentation

### Creating a Documentation Plan

The planning feature helps you organize documentation before generation:

1. **Navigate to Documentation**
   - Click "Documentation" in the product sidebar
   - Select the "Planning" tab

2. **Generate a Plan**
   - Click "Generate Plan" in the top right
   - Choose which types of documentation to create
   - Select specific sections if desired
   - Add any notes or context about your product
   - Click "Generate Plan"

3. **Review the Plan**
   - View all proposed documentation pages
   - See descriptions of what each page will cover
   - Check priority and estimated effort
   - Review which source files will be analyzed

### Understanding Plan Details

Each documentation task in your plan shows:

- **Task Name**: The specific page or document to be created
- **Scope Type**: Whether it's user-facing, developer, or security documentation
- **Description**: What the page will cover
- **Priority**: Importance ranking (1-10)
- **Status**: Current state (pending, in progress, completed)
- **Source Files**: Which code files will be analyzed
- **Estimated Effort**: Time investment (small, medium, large)

### Managing Plans

- **Multiple Plans**: Create and compare different documentation plans without losing previous versions
- **Selective Generation**: Choose specific tasks from your plan to generate
- **Bulk Actions**: Select multiple tasks to generate together
- **Plan Refresh**: Update your plan when your product changes

## Generating Documentation

### From a Plan (Recommended)

1. **Review Your Plan**
   - Open the Planning tab
   - Review the list of documentation tasks

2. **Select Tasks**
   - Check the boxes next to tasks you want to generate
   - Or click "Generate All" to create everything at once

3. **Start Generation**
   - Click "Generate Selected"
   - A panel opens showing the documentation process
   - Choose to watch progress or continue in the background

4. **Monitor Progress**
   - View each task as it completes
   - See which files are being analyzed
   - Track the overall completion percentage

### Quick Generation

For immediate documentation needs:

1. **Open the Documentation Panel**
   - Navigate to the Documentation Changes tab
   - Click the "+" button in the top right

2. **Configure Generation**
   - Select documentation types to create
   - Choose specific sections or generate all
   - Add custom instructions if needed

3. **Start the Process**
   - Click "Generate Documentation"
   - Choose to monitor or run in background

### Migration from Existing Documentation

If you have existing documentation to migrate:

1. **Provide Your Current Documentation**
   - Enter the URL of your existing documentation site
   - This helps the AI understand your style and structure

2. **Select What to Migrate**
   - Choose which sections to update or recreate
   - The AI will maintain your existing voice and format

3. **Review and Commit**
   - Check the generated updates
   - Approve or request changes
   - Commit directly to your repository

## Background Processing

Documentation generation runs in the background so you can continue working:

### Starting Background Processes

- Click "Continue in Background" when the generation panel is open
- Close the panel—the process continues running
- Navigate away from the page without interrupting generation

### Monitoring Background Tasks

- Return to the Documentation page anytime
- View active processes in the Documentation Changes tab
- See a "Resume" button for any running generation
- Check progress percentages and current steps

### Resuming Progress View

- Click "Resume" next to any active process
- View detailed progress of what's being generated
- Watch real-time updates as tasks complete
- Switch back to background mode anytime

## Reviewing Generated Documentation

### Documentation Changes Tab

View all documentation generation activities:

- **Recent Changes**: List of all documentation runs
- **Status Indicators**: See completed, in-progress, or failed generations
- **Details**: View which sections were created or updated
- **Repository Links**: Jump directly to generated files in GitHub

### What Gets Generated

Each documentation run creates:

- **Markdown Files**: Professional documentation in standard markdown format
- **Organized Structure**: Files organized by type and topic
- **Git Commits**: Changes committed directly to your repository
- **Change History**: Track what was generated and when

### Quality Checks

The system ensures:

- **Accuracy**: All information traced to actual code
- **Clarity**: Plain language for user-facing content, technical detail for developers
- **Completeness**: Comprehensive coverage of selected topics
- **Consistency**: Uniform style and structure across all pages

## Customization Options

### Documentation Frameworks

The system supports popular documentation platforms:

- **Mintlify**: Modern documentation with built-in search and navigation
- **Docusaurus**: Meta's documentation framework for versioned docs
- **MkDocs**: Python-based static site generator
- **Custom Markdown**: Standard markdown files for any system

### Repository Configuration

Control where documentation is saved:

1. **Target Repository**: Choose which repository receives documentation
2. **Folder Path**: Specify the folder (e.g., `/docs`, `/documentation`)
3. **Branch Strategy**: Documentation committed to your default branch

### Custom Instructions

Provide context to improve generation:

- **Product Description**: Explain what your product does
- **Target Audience**: Describe who will read the documentation
- **Special Requirements**: Note any specific needs or constraints
- **Style Preferences**: Request specific tones or formats

## Troubleshooting

### No Repositories Assigned

**Problem**: "No repositories assigned to this product" error

**Solution**: 
- Navigate to the Code page
- Find your repositories in the list
- Assign them to your product using the dropdown menu
- Return to Documentation and try again

### Documentation Not Enabled

**Problem**: "Documentation is not enabled" warning

**Solution**:
- Visit Workflow settings from the Documentation page
- Find "Documentation" in the list
- Toggle it to "Enabled"
- Configure repository and folder settings
- Save your changes

### Target Repository Not Configured

**Problem**: "Target repository not configured" warning

**Solution**:
- Click the Workflow settings link in the warning
- Select a repository for documentation storage
- Choose a folder path (e.g., `/docs`)
- Save your configuration

### Generation Failed

**Problem**: Documentation generation shows "failed" status

**Solution**:
- Click the retry button next to the failed generation
- Check the error message for specific issues
- Verify your GitHub connection is still active
- Ensure the target repository is accessible

### Background Process Stopped

**Problem**: Background generation appears stuck

**Solution**:
- Click "Resume" to view current progress
- Check the last updated timestamp
- If stuck for over 10 minutes, retry the generation
- Review error messages in the changes list

## Best Practices

### Planning Before Generation

- Always create a documentation plan first
- Review and adjust the plan before generating
- Start with high-priority sections
- Generate in batches to review quality

### Keeping Documentation Updated

- Regenerate documentation after major code changes
- Use the refresh feature to update existing plans
- Review generated changes before committing
- Set a regular schedule for documentation updates

### Writing Better Context

When providing custom instructions:

- Describe your product's purpose clearly
- Explain unique features or workflows
- Note any industry-specific terminology
- Mention your target user's technical level

### Organizing Documentation

- Use consistent folder structures
- Group related documentation together
- Separate user guides from developer docs
- Keep security documentation in dedicated sections

## Advanced Features

### Commit-Specific Documentation

Generate documentation for specific code changes:

- Select a commit when configuring generation
- Useful for release notes and changelogs
- Documents only changes in that commit
- Perfect for version-specific documentation

### Multi-Repository Documentation

Document products spanning multiple repositories:

- All assigned repositories are analyzed together
- Documentation covers the complete product
- Cross-repository references are handled automatically
- Unified documentation for distributed systems

### Incremental Updates

Update documentation without regenerating everything:

- Select only outdated sections in your plan
- Regenerate specific pages after code changes
- Preserve manual edits to other sections
- Efficient updates for large documentation sets

## Credits and Billing

Documentation generation consumes credits based on:

- **AI Model Used**: More powerful models cost more per page
- **Documentation Scope**: Larger sections use more credits
- **Code Complexity**: More complex codebases require more analysis

View credit usage:

- Check your remaining credits in the top navigation
- Review credit consumption in billing history
- Upgrade your plan if you need more credits

## Getting Help

### Support Resources

- **Documentation Section**: Examples and templates for each documentation type
- **Pricing Page**: Credit costs for different documentation scopes
- **Workflow Settings**: Configuration guides and tips

### Common Questions

**How long does generation take?**
Most documentation generates in 5-15 minutes depending on scope and complexity. Background processing lets you continue working while it runs.

**Can I edit generated documentation?**
Yes, all documentation is committed as standard markdown files. Edit them directly in your repository—they won't be overwritten unless you regenerate those specific sections.

**What if the AI makes mistakes?**
Review generated documentation before publishing. Use the retry feature with additional context to improve accuracy, or edit the files manually after generation.

**How often should I update documentation?**
Regenerate documentation after significant feature additions, major refactors, or API changes. User-facing documentation may need updates more frequently than developer docs.