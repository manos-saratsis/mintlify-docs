I'll analyze the source code to create comprehensive user-facing feature guides for OrchestrAI's documentation generation capabilities.

<read_file>
<path>src/components/AIDocumentationSpecialistPanel.tsx</path>
</read_file>

<read_file>
<path>src/components/DocumentationProgressDialog.tsx</path>
</read_file>

<read_file>
<path>src/App.tsx</path>
</read_file>

Now I'll create the feature guide documentation:

```markdown
# Creating Documentation from Scratch

Learn how to generate comprehensive documentation for your product directly from your codebase using OrchestrAI's AI Documentation Specialist.

## Overview

The AI Documentation Specialist can analyze your product and create documentation from the ground up. You don't need existing documentation - the AI will examine your code, understand your product's functionality, and generate well-structured documentation based on your preferences.

## Getting Started

### Step 1: Access the Documentation Specialist

1. Navigate to the Documentation page in OrchestrAI
2. Click the **Create New Documentation** button
3. The AI Documentation Specialist panel will open on the right side of your screen

### Step 2: Choose Your Documentation Scope

The AI can generate different types of documentation. Expand the **Customize Scope & Content Structure** section to select what you need:

#### Documentation Types

**User Facing Documentation** (Selected by default)
This creates documentation for people who will use your product:
- **Intro** - A quick-start guide to get users up and running fast
- **Tutorials** - Step-by-step lessons that walk users through complete workflows
- **How-To Guides** - Short, focused instructions for specific tasks
- **Reference** - Technical details about your APIs and features (automatically generated)
- **Concepts** - Explanations of how your product works and key ideas
- **Troubleshooting** - Solutions to common problems
- **Release Notes** - What's new in each version

**Internal Developer Documentation**
Documentation for your development team:
- Architecture overview
- Development environment setup
- Technical details for contributors

**SBOM - Software Bill of Materials**
Technical inventory of your software components in industry-standard formats

💡 **Tip**: Start with User Facing documentation and select Intro, Tutorials, and Reference for a solid foundation.

### Step 3: Select Which Code to Analyze

Your documentation needs to know what code to analyze:

1. Expand the **Select Code Scope** section
2. You'll see all repositories that are enabled for OrchestrAI
3. Choose repositories to include in the documentation

For each repository, you can select:
- **Whole Repo** - Analyze the entire repository
- **Specific Commit** - Focus on changes from a particular update (perfect for release notes)

💡 **Tip**: Click "Select All" to include all your repositories for comprehensive documentation.

### Step 4: Add Your Instructions

The **Additional Instructions** box is powerful - use it to tell the AI exactly what you want:

**Priority Instructions**: Whatever you write here takes priority over all other settings. Use this to:
- Emphasize specific features you want documented
- Set the tone and style (formal, casual, technical, beginner-friendly)
- Request specific examples or use cases
- Highlight important information

**Example Instructions**:
```
Focus on the authentication features and include code examples. 
Write for non-technical users who are new to APIs. 
Include troubleshooting steps for common login issues.
```

### Step 5: Optional Settings

**Add Task Explanation**: Check this box if you want a brief explanation at the top of each documentation file describing what it covers. This helps readers understand the purpose of each document.

### Step 6: Generate Your Documentation

1. Review your selections
2. Click the **Generate Documentation** button
3. A progress window will appear showing the AI's work:
   - Analyzing your code
   - Understanding your product
   - Creating documentation structure
   - Writing and organizing content
   - Committing files to your repository

The process typically takes a few minutes depending on your product's size.

## Creating Focused Documentation

Sometimes you need documentation for a specific feature or update rather than your entire product. Here's how to create targeted documentation:

### Focus on Specific Features

1. **In Additional Instructions**, be very specific:
```
Create documentation only for the new payment processing feature. 
Include setup instructions, API reference, and error handling examples.
```

2. **Select only relevant repositories** in the Code Scope section

3. **Choose specific content types** that make sense for your feature:
   - For a new feature: Select How-To Guides and Reference
   - For a major update: Select Release Notes and Tutorials
   - For a technical integration: Select Reference and Concepts

### Update Documentation for Specific Changes

When you've made code changes and want to update just the affected documentation:

1. Select **Specific Commit** for the repository with changes
2. Choose the commit from the list (you'll see the change message and date)
3. Add instructions like:
```
Update the authentication documentation to reflect the new OAuth 2.0 support. 
Add examples for the new login flow.
```

The AI will focus only on documentation related to those specific changes.

## Understanding Your Configuration

Before generating documentation, you'll see a **Configuration** section showing:

- **Repository**: Where your documentation will be saved
- **Folder**: The location within that repository
- **Files to be generated**: A list of all documentation files that will be created

### Customizing File Names

You can rename any documentation file before generation:

1. Find the file in the "Files to be generated" list
2. Click on the filename
3. Type your preferred name (the .md extension is added automatically)

**Example**: Change "intro" to "getting-started" for a more descriptive filename.

## Tips for Best Results

**Be Specific in Your Instructions**
The more detailed your instructions, the better the results. Instead of "document the API," try "document the REST API endpoints with curl examples and explain rate limits."

**Start Small, Then Expand**
Generate core documentation first (Intro and Reference), review it, then add more content types in a second pass.

**Use Commit-Based Updates**
When you update your code, use the Specific Commit option to update only relevant documentation sections automatically.

**Review and Iterate**
After generation, review the documentation and use additional instructions to refine specific sections in subsequent runs.

## What Happens Next

After clicking Generate Documentation:

1. **Analysis Phase** - The AI examines your code and understands your product
2. **Structure Creation** - Documentation is organized according to your selected content structure
3. **Content Generation** - Each documentation file is written with clear, accurate information
4. **Repository Commit** - All files are saved to your configured documentation repository

You'll receive a notification when the process completes, and you can immediately view your new documentation in your repository.

## Troubleshooting

**"Configuration Required" message appears**
You need to set up where documentation should be saved. Click "Configure Documentation URL" and specify your documentation repository and folder.

**"Repository Selection Required" message appears**
Select at least one repository from the Code Scope section so the AI knows what to document.

**Generated documentation is too technical**
Add instructions like "Write for beginners with no technical background" or "Use simple language and avoid jargon."

**Documentation missing important features**
Make those features explicit in your Additional Instructions: "Ensure documentation covers the webhook system and subscription management features."

## Next Steps

Once your documentation is generated:
- Review the files in your repository
- Share the documentation with your team or users
- Run additional generation passes to expand or refine sections
- Set up automated updates by using the Specific Commit option for each release

---

*Remember: The Additional Instructions box is your most powerful tool. Use it to guide the AI toward exactly the documentation you need.*
```