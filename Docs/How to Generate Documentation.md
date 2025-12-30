# How to Generate Documentation

## Overview

Generate and maintain comprehensive documentation for your products automatically. The system creates user guides, developer documentation, API references, and security compliance documents that stay synchronized with your codebase.

## Getting Started

### Prerequisites

Before generating documentation, ensure you have:

1. **Connected a Git Provider**: Link your GitHub, GitLab, or Bitbucket account to store documentation
2. **Enabled Documentation**: Activate the documentation feature in your workspace settings
3. **Configured Target Repository**: Select where generated documentation should be saved

### Initial Setup

1. **Connect Your Git Provider**
   - Navigate to the Code Management page
   - Select "Connection Management"
   - Follow the authentication flow to connect your repository provider
   - Your documentation will be committed directly to your chosen repository

2. **Enable Documentation Generation**
   - Go to Workflow settings
   - Locate the Documentation workflow
   - Change the status to "Enabled"

3. **Configure Repository Settings**
   - In Workflow settings, select your target repository
   - Choose the folder where documentation should be stored
   - Save your configuration

## Types of Documentation

The system generates four main categories of documentation:

### End User Documentation

Documentation designed for your product's users:

- **Quickstart Guides**: Help users get started quickly with your product
- **Tutorials & How-To Guides**: Step-by-step instructions for common tasks
- **API Reference**: Complete endpoint descriptions and usage examples
- **Troubleshooting**: Solutions to common problems and issues
- **Release Notes**: Updates on new features and changes

### Internal Developer Documentation

Technical documentation for your development team:

- **Architecture Documentation**: System design and component relationships
- **Development Setup**: Environment configuration and installation instructions
- **Developer Overview**: Technical guidelines and contribution standards

### Security & Compliance Documentation

Documentation for audits and compliance requirements:

- **SBOM (CycloneDX format)**: Software Bill of Materials in industry-standard format
- **SBOM (SPDX format)**: Alternative SBOM format for different compliance needs
- **Dependency Tracking**: Complete list of project dependencies and versions

### API Documentation

Automated API reference materials:

- **Endpoint Descriptions**: What each API endpoint does
- **Request/Response Schemas**: Expected data formats and structures
- **Authentication Details**: How to authenticate API requests
- **Error Codes**: Complete list of possible errors and their meanings

## Generating Documentation

### Planning Your Documentation

1. **Access the Planning Tab**
   - Navigate to Documentation Management
   - Select the "Planning" tab
   - Review suggested documentation tasks based on your codebase

2. **Select Documentation Tasks**
   - Browse through recommended documentation items
   - Check the boxes next to documentation you want to generate
   - The system analyzes your code to suggest relevant documentation

3. **Generate Selected Documentation**
   - Click "Generate Selected" after choosing your tasks
   - The AI Documentation Specialist panel will open
   - Follow the guided process to create your documentation

### Creating New Documentation

1. **Start a New Generation**
   - Click the "Create New" button
   - The AI Documentation Specialist will appear

2. **Configure Your Documentation**
   - Select the type of documentation to generate
   - Choose your target audience (users, developers, compliance teams)
   - Specify any framework preferences (Mintlify, Docusaurus, MkDocs, etc.)

3. **AI Analysis Process**
   - The system analyzes your repository structure
   - Code patterns and API endpoints are identified
   - Existing documentation is reviewed for context

4. **Review and Commit**
   - Preview the generated documentation
   - Make any necessary adjustments
   - Approve to commit changes to your repository

### Background Execution

For large documentation projects:

1. **Continue in Background**
   - Click "Continue in Background" during generation
   - The process continues while you work on other tasks
   - Return anytime to check progress

2. **Resume Viewing Progress**
   - A notification appears when documentation runs in the background
   - Click to reopen the progress panel
   - View real-time status updates

## Managing Documentation Changes

### Viewing Recent Changes

1. **Access the Changes Tab**
   - Navigate to Documentation Management
   - Select "Documentation Changes"
   - Review all recently generated or updated documentation

2. **Change History**
   - See when documentation was created or modified
   - View which files were affected
   - Check the status of each documentation generation

### Retrying Failed Generations

If documentation generation encounters an issue:

1. Locate the failed execution in the Changes tab
2. Review any error messages displayed
3. Click the retry option to attempt generation again
4. The system preserves your original settings for the retry

## Documentation Frameworks

The system supports popular documentation frameworks:

### Mintlify
Modern documentation platform with interactive features and search capabilities.

### Docusaurus
React-based documentation framework with versioning support.

### MkDocs
Python-based documentation generator with simple markdown files.

### Custom Markdown
Standard markdown format compatible with any documentation system.

## Continuous Updates

### Automatic Synchronization

Documentation stays current with your codebase:

- **Code Change Detection**: The system monitors repository changes
- **Automatic Updates**: Documentation regenerates when relevant code changes
- **Version Control Integration**: All changes are tracked through your Git provider

### Manual Updates

Refresh documentation on demand:

1. Navigate to Documentation Management
2. Select the documentation to update
3. Click "Generate" to create updated versions
4. Review and commit the changes

## Best Practices

### Organization Structure

- **Set Documentation URL**: Add your documentation site URL in Organization Information for easy reference
- **Consistent Naming**: Use clear, descriptive names for documentation files
- **Logical Folders**: Organize documentation by audience or category

### Content Quality

- **Review AI Output**: Always preview generated documentation before committing
- **Add Context**: Provide product descriptions and organization information for better results
- **Regular Updates**: Regenerate documentation after significant code changes

### Team Collaboration

- **Shared Access**: All workspace members can view and generate documentation
- **Change Tracking**: Use the Changes tab to monitor team documentation activities
- **Consistent Standards**: Configure framework preferences once for the entire team

## Troubleshooting

### Documentation Not Generating

**Git Connection Missing**
- Verify your Git provider is connected
- Check authentication hasn't expired
- Reconnect if necessary

**Documentation Disabled**
- Confirm the workflow is enabled in settings
- Check you have the necessary permissions

**Repository Not Configured**
- Ensure target repository is selected
- Verify folder path is valid
- Check write permissions to the repository

### Incomplete Documentation

**Missing Context**
- Add organization information in settings
- Provide product descriptions
- Include relevant README files in your repository

**Code Analysis Issues**
- Ensure code follows standard patterns
- Check for proper commenting in source files
- Verify API endpoints are properly defined

### Generation Errors

**Timeout Issues**
- Use background execution for large projects
- Generate documentation in smaller batches
- Check repository size limits

**Permission Errors**
- Verify Git provider permissions
- Confirm repository access rights
- Check branch protection rules

## Support

If you encounter issues not covered in this guide:

- Review error messages in the Changes tab
- Check that all prerequisites are met
- Verify your Git connection is active
- Contact support with specific error details