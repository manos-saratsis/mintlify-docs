# How to Generate Documentation

## Overview

Generate comprehensive, up-to-date documentation for your projects automatically. The system creates user-friendly guides, developer documentation, API references, and security compliance documents by analyzing your codebase and maintaining them as your product evolves.

## What You Can Create

### User Documentation
Written in simple, everyday language that anyone can understand—no technical jargon or code references.

- **Getting Started Guides**: Welcome walkthroughs and quick start tutorials that help new users reach their first success quickly
- **How-To Guides**: Step-by-step instructions for every feature, including common workflows and best practices
- **FAQs & Troubleshooting**: Answers to common questions and solutions to help users solve problems independently
- **Release Notes**: Clear announcements of new features, improvements, and changes in plain language

### Developer Documentation
Technical documentation for your development team and contributors.

- **Architecture Documentation**: System architecture overview and data flow explanations
- **API Documentation**: Complete API references with endpoint descriptions, request/response examples, and authentication details
- **Component Documentation**: Details about UI components, hooks, and services used in your application
- **Setup Instructions**: Development environment setup and local installation guides
- **Contributing Guidelines**: Code style guides, pull request processes, and review guidelines

### Security Documentation
Compliance and security documentation for audits and regulatory requirements.

- **SBOM (Software Bill of Materials)**: Available in both CycloneDX and SPDX formats for dependency tracking
- **Security Policies**: Access control and data protection documentation
- **Threat Models**: Threat assessments and risk mitigation strategies
- **Compliance Documentation**: Regulatory requirements and audit documentation

## Getting Started

### Prerequisites

Before generating documentation, ensure you have:

1. **Connected a Git Repository**: A GitHub connection set up in the Code section
2. **Created a Product**: At least one product defined in your workspace
3. **Assigned Repositories**: Code repositories assigned to your product
4. **Enabled Documentation**: Documentation workflow enabled in your settings

### Initial Setup

1. Navigate to the Documentation page from the main dashboard
2. Select your workspace from the top navigation bar
3. If you see a setup prompt, click "Add Git Connection" to connect your GitHub account
4. Assign repositories to your product in the Code section
5. Enable the documentation workflow in your settings

## Creating Your First Documentation

### Using the Planning Approach

The planning approach lets you preview and select exactly what documentation to generate.

**Step 1: Generate a Documentation Plan**

1. Open the Documentation page
2. Click the "Planning" tab
3. Select which types of documentation you want (User-Facing, Developer, Security)
4. Choose your AI model:
   - **Haiku**: Faster generation, lower cost, good for straightforward documentation
   - **Sonnet**: More detailed analysis, higher quality, better for complex projects
5. Add any specific instructions or context about your product in the notes field
6. Click "Generate Plan"

The system analyzes your codebase, examining file structures, code patterns, README files, and package configurations to understand your project.

**Step 2: Review the Generated Tasks**

After analysis completes, you'll see a list of proposed documentation pages organized by category:

- Each task shows the documentation page name, description, and estimated effort
- Tasks are prioritized based on importance to users
- You can see which source files will be analyzed for each page

**Step 3: Select and Generate**

1. Review the proposed documentation tasks
2. Check the boxes next to the pages you want to create
3. Click "Generate Selected" to start documentation generation
4. Or click the generate icon next to any single task to create just that page

**Step 4: Monitor Progress**

Watch the generation progress in real-time:

- See which pages are being created
- View completion percentages
- Review any warnings or issues
- Continue in the background if you need to work on other tasks

### Direct Generation

For faster workflows, you can generate documentation without the planning step:

1. Open the Documentation page
2. Navigate to the "Documentation Changes" tab
3. Click the plus icon in the top right
4. Configure your documentation settings
5. Click "Start Generation"

This approach analyzes your code and generates all selected documentation types in one operation.

## Understanding Documentation Generation

### How It Works

**Phase 1: Code Analysis**

The system connects to your repository and examines:

- Project structure and file organization
- Page routes and user interface components
- API endpoints and service layers
- README files and existing documentation
- Package dependencies and configurations
- Recent releases and version tags

**Phase 2: Content Creation**

For each documentation page:

- Relevant source code is identified and analyzed
- AI generates content appropriate for the target audience
- User-facing content uses simple, non-technical language
- Developer content includes technical details and code references
- Examples and step-by-step instructions are created

**Phase 3: Review and Commit**

- Generated documentation is formatted as markdown files
- Files are organized into appropriate folders
- Content is committed to your documentation repository
- You can review changes before they're published

### Documentation Storage

All generated documentation is stored in your designated repository:

- **Default Location**: Documentation is placed in folders matching your documentation structure
- **Migration Mode**: Uses a dedicated "migrated-docs" folder when migrating existing documentation
- **Custom Paths**: Configure specific folder paths in your workflow settings

## Configuration Options

### Selecting Documentation Scope

Choose which types of documentation to generate:

- **User-Facing**: External documentation for product users
- **Internal Developer**: Technical documentation for your team
- **Security**: Compliance and SBOM documentation

Within each scope, select specific categories:

- Getting Started, Tutorials, Feature Guides (User-Facing)
- Architecture, API Docs, Testing & QA (Developer)
- SBOM formats, Security Policies, Compliance (Security)

### Model Selection

**Haiku (Fast & Efficient)**
- Generates documentation quickly
- Lower credit cost per page
- Ideal for straightforward feature documentation
- Best for established products with clear patterns

**Sonnet (Detailed & Comprehensive)**
- Deeper code analysis and understanding
- More detailed explanations and examples
- Better for complex technical documentation
- Recommended for API references and architecture docs

### Repository Configuration

In your workflow settings, configure:

- **Target Repository**: Where generated documentation will be stored
- **Folder Path**: Specific folder for documentation files (e.g., "docs", "documentation")
- **Source Repositories**: Which code repositories to analyze for documentation generation

### Adding Context

Provide additional information to improve documentation quality:

- **Product Information**: Brief description of what your product does and who uses it
- **Documentation URL**: Link to your live documentation site (if you have one)
- **User Instructions**: Specific guidance about features to emphasize or terminology to use
- **Deployment Type**: Whether you're using Mintlify, Docusaurus, MkDocs, or custom markdown

## Managing Documentation

### Viewing Generated Documentation

The "Documentation Changes" tab shows all documentation generation activity:

- **Recent Generations**: See recent documentation creation jobs
- **Status Tracking**: Monitor which pages completed successfully or encountered issues
- **Change History**: View what was generated in each session
- **Content Preview**: Review generated content before committing

### Updating Documentation

As your product evolves, keep documentation current:

**Refresh Existing Documentation**

1. Navigate to the Planning tab
2. Click "Refresh Plan" to analyze what's outdated
3. The system identifies which existing pages need updates based on code changes
4. Select outdated pages to regenerate
5. New content replaces the outdated documentation

**Generate for New Features**

1. Add new features to your code
2. Generate a new documentation plan
3. The system detects new functionality
4. Creates documentation pages for new features automatically

### Handling Generation Issues

If documentation generation fails for specific pages:

1. Review the error message in the Documentation Changes tab
2. Common issues include:
   - Release Notes require selecting specific code commits
   - Missing repository access or expired credentials
   - Insufficient code context for very new projects
3. Click "Retry" to attempt generation again
4. Adjust your configuration or add more context as needed

## Working with Background Processing

### Continuing in Background

Documentation generation can take several minutes for large projects:

1. Start the generation process
2. Click "Continue in Background" to close the panel
3. Work on other tasks while documentation generates
4. Return anytime to check progress

### Resuming Progress View

If you closed the progress panel:

1. Open the Documentation page
2. Look for the "View Progress" button on active generation jobs
3. Click to resume watching real-time progress
4. See which pages completed and which are still in progress

### Pausing and Resuming

For long-running documentation jobs:

1. Click "Pause" to temporarily stop generation
2. Close your browser or work on other tasks
3. Return later and click "Resume" to continue where you left off
4. All completed pages are saved; generation continues from the next pending page

## Tips for Best Results

### Provide Clear Context

- Add descriptions to your product settings explaining what your application does
- Include any specific terminology or branding preferences in the instructions field
- Specify target audience (e.g., "enterprise developers" vs. "non-technical small business owners")

### Start with a Subset

- Generate a small sample of documentation first (3-5 pages)
- Review the quality and style
- Adjust your settings or add more context
- Then generate the complete documentation set

### Keep Code Well-Organized

- Use clear file and folder naming conventions
- Maintain README files in your repositories
- Add comments to complex code sections
- Organize related functionality together

### Regular Updates

- Regenerate documentation after major feature releases
- Use the refresh function to update changed pages
- Generate release notes after each deployment
- Keep security documentation current for compliance audits

## Understanding Costs

Documentation generation uses AI credits based on:

- **Number of Pages**: Each documentation page requires AI analysis
- **Model Selection**: Sonnet uses more credits than Haiku
- **Code Complexity**: Larger codebases with more files use more credits
- **Scope**: Comprehensive documentation across all types costs more than focused generation

The system shows estimated credit usage before generation begins, and actual usage is tracked in your billing dashboard.

## Troubleshooting

### "No repositories assigned to this product"

You need to assign at least one code repository to your product before generating documentation. Navigate to the Code section and assign repositories to your product.

### Documentation quality is too technical

If user-facing documentation includes too many technical details, add instructions like "Write for non-technical users who have never used developer tools" in the notes field.

### Missing features in generated documentation

Ensure the source code for those features exists in repositories assigned to your product. Check that relevant files aren't excluded by your configuration.

### Generation takes a very long time

Large projects with many files can take 10-20 minutes. Use the background processing feature and check back later, or start with a smaller scope (e.g., just Getting Started guides).

### Release Notes generation fails

Release Notes require selecting specific code commits to document. When configuring documentation, select one or more commits for each repository to generate release notes about changes in those commits.

## Next Steps

After generating your initial documentation:

- Review the generated content in your documentation repository
- Publish to your documentation site (Mintlify, Docusaurus, etc.)
- Share with your team and gather feedback
- Set up a regular schedule to refresh documentation (e.g., after each sprint)
- Monitor which documentation pages users visit most frequently and prioritize keeping those current