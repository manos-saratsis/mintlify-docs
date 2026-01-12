I'll retrieve the key source files first to understand the documentation generation workflow.# How to Generate Documentation

## Overview

Create comprehensive documentation for your projects automatically. The platform generates user guides, developer documentation, API references, and compliance documents that stay synchronized with your code.

## Getting Started

### Before You Begin

Make sure you have:

1. **A Connected Repository**: Link your GitHub, GitLab, or Bitbucket account
2. **Documentation Enabled**: Turn on the documentation feature in your workspace
3. **A Target Location**: Choose where your documentation will be saved

### Initial Setup

1. **Connect Your Code Repository**
   - Go to the Code Management page
   - Select "Connection Management"
   - Follow the steps to connect your repository provider
   - Your documentation will be saved directly to your chosen repository

2. **Turn On Documentation Generation**
   - Open Workflow settings
   - Find the Documentation workflow
   - Switch the status to "Enabled"

3. **Choose Where Documentation Goes**
   - In Workflow settings, select your target repository
   - Pick the folder where documentation should be stored
   - Save your settings

## What Documentation You Can Generate

The platform creates four main types of documentation:

### User Guides

Documentation for people using your product:

- **Quick Start Guides**: Help users get up and running quickly
- **How-To Guides**: Step-by-step instructions for common tasks
- **API Usage Examples**: Show users how to work with your API
- **Troubleshooting Help**: Solutions to frequently encountered problems
- **Release Updates**: Information about new features and changes

### Developer Documentation

Technical guides for your development team:

- **System Architecture**: How your application is structured
- **Setup Instructions**: How to configure development environments
- **Developer Guidelines**: Standards and best practices for contributors

### Compliance Documentation

Documents for audits and regulatory requirements:

- **Software Bill of Materials (SBOM)**: Complete inventory of software components in CycloneDX format
- **SBOM in SPDX Format**: Alternative format for different compliance needs
- **Dependency Lists**: All project dependencies with version information

### API Documentation

Automated reference materials for your API:

- **Endpoint Descriptions**: What each API endpoint does
- **Request/Response Examples**: Expected data formats and structures
- **Authentication Instructions**: How to authenticate API requests
- **Error Reference**: Complete list of possible errors and their meanings

## Creating Documentation

### Planning Your Documentation

1. **Open the Planning View**
   - Navigate to Documentation Management
   - Select the "Planning" tab
   - See suggested documentation based on your codebase

2. **Choose What to Generate**
   - Browse through recommended documentation items
   - Select the documentation you want to create
   - The system analyzes your code to suggest relevant topics

3. **Generate Your Selection**
   - Click "Generate Selected" after making your choices
   - The AI Documentation Specialist panel opens
   - Follow the guided process to create your documentation

### Starting a New Documentation Project

1. **Begin Generation**
   - Click the "Create New" button
   - The AI Documentation Specialist appears

2. **Configure Your Documentation**
   - Choose the type of documentation you need
   - Select your target audience (users, developers, compliance teams)
   - Pick a framework if you have a preference (Mintlify, Docusaurus, MkDocs, etc.)

3. **AI Analysis**
   - The system examines your repository structure
   - Code patterns and API endpoints are identified
   - Existing documentation is reviewed for context

4. **Review and Save**
   - Preview the generated documentation
   - Make any adjustments you need
   - Approve to save changes to your repository

### Working on Large Projects

For extensive documentation tasks:

1. **Run in Background**
   - Click "Continue in Background" during generation
   - The process continues while you work on other things
   - Return anytime to check progress

2. **Check Your Progress**
   - A notification appears when documentation runs in the background
   - Click to reopen the progress panel
   - See real-time status updates

## Managing Your Documentation

### Viewing Recent Changes

1. **Open the Changes View**
   - Go to Documentation Management
   - Select "Documentation Changes"
   - Review all recently created or updated documentation

2. **Check History**
   - See when documentation was created or modified
   - View which files were affected
   - Check the status of each generation

### Fixing Failed Generations

If something goes wrong:

1. Find the failed execution in the Changes tab
2. Review any error messages shown
3. Click the retry option to try again
4. Your original settings are saved for the retry

## Documentation Frameworks Supported

Choose from popular documentation platforms:

### Mintlify
Modern platform with interactive features and powerful search.

### Docusaurus
React-based framework with support for multiple versions.

### MkDocs
Python-based generator using simple markdown files.

### Custom Markdown
Standard markdown format that works with any documentation system.

## Keeping Documentation Current

### Automatic Updates

Your documentation stays synchronized with code changes:

- **Change Detection**: The system monitors your repository
- **Automatic Regeneration**: Documentation updates when relevant code changes
- **Version Control**: All changes are tracked through your repository

### Manual Updates

Refresh documentation whenever you need:

1. Go to Documentation Management
2. Select the documentation to update
3. Click "Generate" to create updated versions
4. Review and save the changes

## Best Practices

### Organization

- **Add Your Documentation URL**: Include your documentation site URL in Organization Information for easy access
- **Use Clear Names**: Choose descriptive names for documentation files
- **Organize Logically**: Group documentation by audience or topic

### Quality

- **Review Before Saving**: Always preview generated documentation
- **Provide Context**: Add product descriptions and organization details for better results
- **Update Regularly**: Regenerate documentation after major code changes

### Team Collaboration

- **Shared Access**: Everyone in your workspace can view and generate documentation
- **Track Changes**: Use the Changes tab to see team documentation activities
- **Set Standards**: Configure framework preferences once for everyone

## Troubleshooting

### Documentation Won't Generate

**Repository Not Connected**
- Check that your repository provider is connected
- Verify authentication hasn't expired
- Reconnect if needed

**Feature Not Enabled**
- Confirm the documentation workflow is enabled in settings
- Check that you have the necessary permissions

**Target Not Set**
- Make sure a target repository is selected
- Verify the folder path is valid
- Check that you have write permissions

### Documentation Is Incomplete

**Missing Information**
- Add organization details in settings
- Provide product descriptions
- Include a README file in your repository

**Code Analysis Problems**
- Ensure code follows standard patterns
- Check that source files have comments
- Verify API endpoints are properly defined

### Generation Errors

**Timeouts**
- Use background execution for large projects
- Generate documentation in smaller batches
- Check repository size limits

**Permission Issues**
- Verify repository provider permissions
- Confirm repository access rights
- Check branch protection rules

## Getting Help

If you encounter issues not covered here:

- Review error messages in the Changes tab
- Check that all setup steps are complete
- Verify your repository connection is active
- Contact support with specific error details