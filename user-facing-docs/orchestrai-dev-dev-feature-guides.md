# OrchestrAI-Dev - Feature Guides

## Creating Documentation from Scratch

### Overview

OrchestrAI-Dev provides an AI-powered Documentation Specialist that analyzes your product and automatically generates comprehensive documentation. You can create documentation from the ground up by selecting preset scopes, configuring content structure, and providing custom instructions for focused documentation needs.

### Getting Started

To create documentation from scratch, you'll use the AI Documentation Specialist panel, which becomes available when you have at least one enabled repository in your workspace.

**Prerequisites:**
- A configured workspace with OrchestrAI-enabled repositories
- Sufficient workspace credits
- Documentation repository and folder configured in settings

### Step-by-Step Guide

#### 1. Open the Documentation Specialist

From your product dashboard, locate and click the AI Documentation Specialist option. A panel will slide in from the right side of your screen showing the documentation creation interface.

#### 2. Choose Your Documentation Scope

The Documentation Specialist offers three main types of documentation:

**User Facing Documentation** (selected by default)
This creates documentation for your end users. When selected, you can customize the content structure to include:
- **Quick Start / Introduction**: A positioned quickstart guide to help users get up and running quickly
- **Tutorials**: End-to-end, outcome-driven guides that walk users through complete workflows
- **How-To Guides**: Task-centric, short guides focused on specific actions
- **API Reference**: Auto-generated documentation for your APIs and SDKs
- **Concepts**: Explanations of architecture, models, and quotas
- **Troubleshooting**: Error catalogs and logging information
- **Release Notes**: Automated changelog and version history

**Internal Developer Documentation**
Select this to generate documentation for your development team, including:
- Architecture documentation
- Development setup guides
- Developer overview materials

**SBOM (Software Bill of Materials)**
Choose this option to generate compliance-focused documentation including:
- SBOM in CycloneDX format
- SBOM in SPDX format

**Note:** You must select at least one scope to proceed with documentation generation.

#### 3. Customize Content Structure

If you've selected User Facing documentation, expand the "Customize Scope & Content Structure" section to fine-tune exactly which types of documents you want to generate. 

For example, if you're launching a new product, you might want to start with just:
- Introduction
- Tutorials
- API Reference

You can always generate additional sections later as your product matures.

#### 4. Select Code Repositories

Expand the "Select Code Scope" section to choose which repositories the AI should analyze:

**Whole Repository Analysis**
- Select "Whole Repo" to analyze the entire codebase
- This provides comprehensive documentation coverage
- Best for complete product documentation

**Specific Commit Analysis**
- Select "Specific Commit" to document changes from a particular update
- Click to load recent commits
- Choose the commit you want to document
- Perfect for release notes or documenting new features

**Multiple Repositories**
You can select multiple repositories and configure each one individually. Use "Select All" to quickly enable all OrchestrAI-enabled repositories, or choose specific ones relevant to your documentation needs.

#### 5. Add Focused Documentation Instructions

The Additional Instructions field allows you to provide specific guidance for your documentation generation. These instructions take priority over default workspace settings.

**General Documentation Example:**
```
Create comprehensive documentation from product analysis, 
focusing on beginner-friendly explanations and practical 
examples for each feature.
```

**Focused Documentation Example:**
If you want to create documentation for a specific feature or area, provide detailed instructions:

```
Focus exclusively on the authentication and user management 
features. Include:
- Step-by-step setup for OAuth integration
- User role management workflows
- Security best practices
- Common authentication troubleshooting scenarios
```

#### 6. Customize File Names

In the Configuration section, you'll see a list of files that will be generated based on your selected scopes and content structure. Each file appears with an editable name:

**Default File Organization:**
- User Facing docs appear as: `intro.md`, `tutorials.md`, `how_to.md`, etc.
- Internal docs appear as: `architecture.md`, `development-setup.md`, etc.
- SBOM files appear as: `sbom_cyclonedx.md`, `sbom_spdx.md`

**Creating Focused Documentation Files:**
To create additional focused documentation, simply edit the filename to reflect your specific topic:

**Example 1 - Feature-Specific Documentation:**
- Change `intro.md` to `authentication-quickstart.md`
- Change `tutorials.md` to `oauth-integration-tutorial.md`
- Change `how_to.md` to `user-management-guide.md`

**Example 2 - Team-Specific Documentation:**
- Change `development-setup.md` to `frontend-dev-setup.md`
- Change `architecture.md` to `api-architecture.md`

The AI will use your custom filenames combined with your instructions to generate precisely focused documentation.

#### 7. Optional: Add Task Explanations

Check the "Add documentation task explanation at the top of the file" option if you want each generated document to include a brief explanation of what the documentation covers and why. This is particularly helpful for internal documentation where team members need context about the document's purpose.

#### 8. Start Documentation Generation

Once you've configured everything:

1. Review your selected scopes and content structure
2. Verify your repository selections and scope settings
3. Check that your instructions clearly convey your documentation goals
4. Click the "Generate Documentation" button

The AI Documentation Specialist will:
- Analyze your selected repositories
- Understand your product's functionality
- Generate documentation according to your structure and instructions
- Commit the files to your configured documentation repository

You'll see a progress dialog showing each step of the generation process. When complete, your new documentation files will be available in your repository.

### Creating Multiple Focused Documents

You can run the Documentation Specialist multiple times to create different focused documentation sets:

**Workflow Example:**

1. **First Run - Core User Documentation:**
   - Scope: User Facing only
   - Content: Introduction, Tutorials, API Reference
   - Instructions: "Create beginner-friendly core documentation"
   - Files: Keep default names

2. **Second Run - Advanced Feature Documentation:**
   - Scope: User Facing only
   - Content: How-To Guides, Troubleshooting
   - Instructions: "Document advanced features and integration patterns"
   - Files: Rename to `advanced-integration.md`, `troubleshooting-guide.md`

3. **Third Run - Developer Documentation:**
   - Scope: Internal Developer only
   - Instructions: "Create technical architecture documentation for backend team"
   - Files: Rename to reflect specific components

Each run generates new documentation files without overwriting previous ones, allowing you to build a comprehensive documentation library incrementally.

### Best Practices

**Start Simple**
- Begin with just Introduction and API Reference
- Add more sections as your product and team grow

**Be Specific in Instructions**
- Instead of "Document features," write "Document the user authentication flow including OAuth setup, token management, and session handling"
- The more specific your instructions, the more focused and useful your documentation will be

**Use Clear File Names**
- Name files based on their content: `payment-integration.md` is clearer than `guide1.md`
- Use consistent naming conventions across your documentation

**Leverage Repository Scope Options**
- Use "Whole Repo" for initial comprehensive documentation
- Use "Specific Commit" when documenting new features or updates

**Iterate and Refine**
- Generate initial documentation, review it, then create more focused documents for areas needing deeper coverage
- Each generation run is independent, so you can experiment freely

### Common Use Cases

**New Product Launch**
- Scope: User Facing (Introduction, Tutorials, API Reference)
- Instructions: "Create comprehensive getting-started documentation for first-time users"

**Feature Addition**
- Scope: User Facing (How-To Guides)
- Repository: Specific commit where feature was added
- Instructions: "Document the new dashboard customization feature"
- File name: `dashboard-customization.md`

**Developer Onboarding**
- Scope: Internal Developer
- Instructions: "Create onboarding guide for new backend developers"
- File names: `backend-setup.md`, `api-architecture.md`

**Compliance Requirements**
- Scope: SBOM
- Instructions: "Generate complete software bill of materials for security audit"

### Understanding Generated Files

Generated documentation files are committed to your configured documentation repository in the specified folder. Each file follows markdown formatting and includes:

- Clear section headers and organization
- Code examples (when relevant)
- Step-by-step instructions
- Contextual explanations based on your product's actual functionality

If you enabled task explanations, each file begins with a brief overview explaining its purpose and intended audience.

### Tips for Success

1. **Review Configuration First**: Before clicking "Generate Documentation," check that your documentation repository and folder are properly configured in your workspace settings.

2. **Monitor Credit Usage**: Documentation generation consumes workspace credits. Check your available credits before starting large documentation projects.

3. **Plan Your Structure**: Sketch out what documentation you need before starting. This helps you make informed decisions about scopes and content structure.

4. **Use Progressive Enhancement**: Start with basic documentation, then add more sophisticated sections like Concepts and Troubleshooting as your product matures.

5. **Combine Instructions with File Names**: Your instructions guide the content, while file names organize the output. Use both effectively for best results.

### Need Help?

If your documentation generation doesn't produce the results you expected:
- Refine your instructions to be more specific
- Review your selected content structure
- Try generating documentation for a smaller scope first
- Ensure your repositories are properly configured and accessible

The AI Documentation Specialist learns from your product's actual code and structure, so the more organized and well-commented your codebase, the better the generated documentation will be.