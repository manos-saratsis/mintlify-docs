# How to Generate Documentation

## Overview

Generate comprehensive, up-to-date documentation for your product automatically using AI. Create user guides, developer documentation, API references, and security compliance documents—all kept in sync with your codebase.

## What You Can Generate

### User-Facing Documentation

Create documentation written in plain, everyday language that anyone can understand:

- **Getting Started Guides** - Welcome pages and onboarding walkthroughs that help new users reach their first success quickly
- **How-To Guides** - Step-by-step instructions for every feature with visual walkthroughs and best practices
- **Tutorials** - Hands-on learning experiences for common workflows
- **Concept Guides** - Explanations of core concepts and key terms
- **API Reference** - Complete endpoint documentation with examples
- **FAQs & Troubleshooting** - Common questions, error resolution, and known limitations
- **Release Notes** - Clear announcements of new features, bug fixes, and improvements

### Developer Documentation

Technical documentation for your development team:

- **Architecture Documentation** - System architecture and data flow diagrams
- **API Documentation** - Internal APIs and endpoint specifications
- **Component Documentation** - UI components, hooks, and services
- **Testing & QA** - Test strategy, coverage reports, and QA processes
- **Deployment & DevOps** - CI/CD pipelines, infrastructure, and monitoring
- **Contributing Guidelines** - Code style, PR process, and review guidelines

### Security Documentation

Compliance and security documentation:

- **SBOM (CycloneDX)** - Software Bill of Materials in CycloneDX format
- **SBOM (SPDX)** - Software Bill of Materials in SPDX format
- **Security Policies** - Access control and data protection policies
- **Threat Model** - Threat assessment and risk mitigation strategies
- **Compliance Documentation** - Regulatory requirements and audit documentation

## Getting Started

### Prerequisites

Before generating documentation, you need:

1. **A Git Connection** - Connect GitHub to store and manage your documentation
2. **Documentation Enabled** - Enable documentation generation in your Workflow settings
3. **Target Repository** - Select which repository should store your documentation
4. **Assigned Repositories** - Assign source code repositories to your product

### Initial Setup

1. Navigate to the Documentation page from your product dashboard
2. If you haven't connected Git yet, click "Add Git Connection" and follow the prompts
3. Go to Workflow settings and enable Documentation generation
4. Select your target repository and folder where documentation should be saved
5. Assign source code repositories to your product in the Code section

## Creating a Documentation Plan

### Understanding Plans

Documentation plans organize your documentation into specific tasks. Each plan is identified by a unique ID (like `plan_2025-01-15_a3c2f8`) and contains individual documentation pages to generate.

### Generating Your First Plan

1. Navigate to the Documentation page
2. Go to the **Planning** tab
3. Select which types of documentation you want to create:
   - User-Facing Documentation
   - Internal Developer Documentation
   - Security Documentation
4. Click the model selection button to choose:
   - **Claude Haiku** - Faster, more economical for standard documentation
   - **Claude Sonnet** - More detailed analysis for complex projects
5. Optionally add notes about specific areas to focus on
6. Click "Generate Plan"

The AI will analyze your codebase and create a structured plan with specific documentation pages. This typically takes 30-60 seconds.

### What the AI Analyzes

When creating a plan, the AI examines:

- Repository structure and file organization
- README files and existing documentation
- Package dependencies and configuration files
- Page routes and user-facing features
- API endpoints and services
- Component architecture
- Release history and version tags

### Reviewing Your Plan

After generation completes, you'll see a list of documentation tasks organized by:

- **Scope** (User-Facing, Developer, Security)
- **Section** (Getting Started, Tutorials, API Reference, etc.)
- **Individual Pages** - Specific documentation pages to generate

Each task shows:
- Task name and description
- Priority level
- Estimated effort
- Current status (pending, generated, outdated)

### Customizing Your Plan

You can refine the plan before generating documentation:

- Review the suggested pages
- Check that priorities match your needs
- Note any missing topics
- Select specific tasks to generate first

## Generating Documentation

### Generating Selected Tasks

1. From the Planning tab, review your documentation tasks
2. Select the checkboxes next to specific tasks you want to generate
3. Click "Generate Selected"
4. The AI Documentation Specialist panel opens

### Generating All Tasks

To generate all pending tasks:

1. Navigate to the **Documentation Changes** tab
2. Click the **+** button in the top-right corner
3. The AI Documentation Specialist panel opens

### The Generation Process

Once you start generation:

1. **Repository Access** - The system verifies access to your source code
2. **Job Creation** - Individual generation jobs are created for each task
3. **Parallel Processing** - Multiple documentation pages are generated simultaneously
4. **Quality Review** - You can review generated content before committing
5. **Git Commit** - Documentation is committed to your target repository

### Monitoring Progress

During generation:

- View real-time progress in the AI Documentation Specialist panel
- See which pages are being generated
- Track completion percentage
- Monitor any errors or warnings

### Continuing in Background

For large documentation sets:

1. Click "Continue in Background" to close the panel
2. Generation continues without keeping the page open
3. Resume viewing progress anytime from the Documentation page
4. You'll see a "Resume" button when background generation is active

## Working with Generated Documentation

### Reviewing Changes

After generation completes:

1. Navigate to the **Documentation Changes** tab
2. View recent documentation generations
3. Each entry shows:
   - Generation timestamp
   - Number of pages created
   - Commit information
   - Status (completed, failed, or running)

### Viewing in Your Repository

Generated documentation is automatically committed to your target repository:

1. Go to your Git repository
2. Navigate to the documentation folder you configured
3. Find your documentation organized by plan and scope
4. Files use clear, descriptive names based on the task

### File Organization

Documentation is organized in your repository:

```
your-docs-folder/
├── plan_2025-01-15_a3c2f8/
│   ├── user_facing/
│   │   ├── getting-started/
│   │   │   └── quick-start-guide.md
│   │   ├── tutorials/
│   │   └── api-reference/
│   ├── internal_developer/
│   │   ├── architecture/
│   │   └── development-setup/
│   └── security/
│       ├── sbom/
│       └── compliance/
```

### Refreshing Documentation

To update documentation when your product changes:

1. Go to the Planning tab
2. Click "Refresh Plan" to check for outdated content
3. The AI identifies which pages need updates
4. Generate updated versions of outdated pages

## Release Notes

### Special Requirements

Release Notes require specific commit selection:

1. When creating a plan, the AI identifies available releases and tags
2. To generate Release Notes, you must select specific commits or releases
3. This ensures Release Notes accurately reflect changes in that version

### Generating Release Notes

1. In the Planning tab, locate Release Notes tasks
2. If commits weren't specified during planning, the task will show as failed
3. To generate Release Notes properly:
   - Create a new plan
   - When selecting repositories, choose "Specific Commits" scope
   - Select the release tag or commit range
   - Generate the plan with Release Notes scope enabled

## Migration Mode

### When to Use Migration

Use migration to import existing documentation:

1. You have documentation scattered across multiple locations
2. You want to consolidate documentation into your target repository
3. You're standardizing documentation format

### How Migration Works

1. Select "Migrate Documentation" action
2. Point to your existing documentation sources
3. The AI analyzes and imports content
4. Documentation is saved to a dedicated `migrated-docs` folder
5. Review and organize migrated content

## Advanced Options

### Selecting Documentation Scopes

When generating a plan, choose which types to include:

- Generate only User-Facing documentation for public-facing docs
- Focus on Developer documentation for internal teams
- Include Security documentation for compliance requirements
- Combine multiple scopes for comprehensive documentation

### Selecting Sub-Scopes

Within each scope, choose specific sections:

- For User-Facing: Select Getting Started, Tutorials, API Reference, etc.
- For Developer: Choose Architecture, Testing, Deployment, etc.
- For Security: Pick SBOM formats, policies, or threat models

### Adding Context

Provide additional information to improve documentation quality:

- Describe your target audience
- Explain unique features or workflows
- Highlight areas that need special attention
- Note any terminology specific to your product

### Framework Support

Generated documentation works with popular documentation frameworks:

- **Mintlify** - Modern, interactive documentation
- **Docusaurus** - React-based documentation sites
- **MkDocs** - Python-based static site generator
- **Custom Markdown** - Standard markdown for any platform

## Tips for Best Results

### Before Generation

- Ensure your codebase has clear file organization
- Include README files in repositories
- Add comments to complex code sections
- Keep package.json or equivalent files up to date

### During Generation

- Start with a small subset of documentation to test
- Review generated content before committing all pages
- Use Claude Sonnet for complex, technical projects
- Use Claude Haiku for straightforward documentation needs

### After Generation

- Review generated documentation for accuracy
- Customize documentation with brand-specific terminology
- Add screenshots or diagrams where helpful
- Keep documentation updated by regenerating when code changes

### Maintaining Quality

- Regenerate documentation after major feature releases
- Use the Refresh Plan feature to identify outdated pages
- Review Release Notes for accuracy before publishing
- Assign repositories to products correctly for best analysis

## Troubleshooting

### "No repositories assigned to this product"

**Problem**: The system can't generate documentation without source code.

**Solution**: Go to the Code section and assign repositories to your product before generating a plan.

### Documentation is outdated

**Problem**: Your code changed but documentation didn't update.

**Solution**: Use the Refresh Plan feature to identify which pages need updates, then regenerate those specific tasks.

### Generation fails or times out

**Problem**: Large documentation sets may take significant time.

**Solution**: 
- Use "Continue in Background" for large generation jobs
- Generate in smaller batches by selecting specific tasks
- Try Claude Haiku for faster generation of standard documentation

### Release Notes require commits

**Problem**: Release Notes tasks show as failed immediately.

**Solution**: Create a new plan with specific commits selected for repositories, ensuring the Release Notes scope can analyze actual changes.

### Generated content isn't relevant

**Problem**: Documentation doesn't match your product features.

**Solution**:
- Verify correct repositories are assigned to the product
- Add detailed context notes when generating the plan
- Ensure your codebase has descriptive README files
- Try Claude Sonnet for deeper codebase analysis

## Credit Usage

Documentation generation consumes credits based on:

- **Model Selection** - Claude Sonnet uses more credits than Claude Haiku
- **Plan Generation** - Analyzing your codebase to create the plan
- **Page Generation** - Creating each individual documentation page
- **Codebase Size** - Larger codebases require more analysis

Monitor your credit usage in the Organization settings page.