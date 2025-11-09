I'll analyze the source code to create a comprehensive feature guide on how to create documentation from scratch using the AI Documentation Specialist panel.

<think>
Let me trace through the code to understand the documentation creation workflow:

1. The `AIDocumentationSpecialistPanel` component handles both 'migrate' and 'create' actions
2. When action is 'create', the panel allows users to:
   - Select documentation scopes (User Facing, Internal Developer, SBOM)
   - Customize content structure for User Facing docs (intro, tutorials, how-to, reference, concepts, troubleshooting, release notes)
   - Add custom instructions
   - Select source repositories
   - Customize file names for generated documentation
   - Include task explanation option

Key features from the code:
- Scope selection: `selectedScopes` state with userFacing, internal, sbom options
- Content structure: `selectedContentStructure` with 7 different content types
- Instructions field: `instructions` state with placeholder text
- File name customization: `documentFiles` array with updateFileName function
- Task explanation option: `includeTaskExplanation` boolean
- Repository selection with full repo or specific commit options

The workflow starts when user clicks "Generate Documentation" button, which opens the DocumentationProgressDialog.
</think>

# orchestrai-dev-create-documentation-guide.md

## Overview

The AI Documentation Specialist feature in OrchestrAI allows you to automatically generate comprehensive documentation for your software product directly from your codebase. Unlike migrating existing documentation, creating documentation from scratch means the AI analyzes your product's code and functionality to build new documentation files following industry best practices.

This guide walks you through the complete process of generating new documentation, customizing what gets created, adding your own specific instructions, and organizing the output with custom file names.

## Getting Started

### Accessing the Documentation Creator

1. Navigate to the Documentation page in your OrchestrAI workspace
2. Look for the "Create Documentation" option
3. Click to open the AI Documentation Specialist panel on the right side of your screen

You'll see a side panel titled "AI Documentation Specialist" with a purple robot icon at the top.

### Prerequisites

Before you can create documentation, you need to:

1. **Configure your documentation repository**: The system needs to know where to save the generated files. Go to your Organization Information settings to set this up.
2. **Have repositories connected**: At least one code repository should be connected and enabled in OrchestrAI so the AI can analyze your product.
3. **Have available credits**: Documentation generation uses workspace credits. Check your credit status at the top of the panel.

If any of these are missing, you'll see helpful alerts in the panel with links to complete the setup.

## Choosing What to Document

### Understanding Documentation Scopes

The system offers three main categories of documentation you can generate:

**User Facing Documentation**
This is for your product's end users - the people who use your software. It includes guides, tutorials, and reference materials written in friendly, non-technical language.

**Internal Developer Documentation**
This is for your development team. It covers technical architecture, development setup instructions, and developer-focused overviews of how the system works.

**SBOM (Software Bill of Materials)**
These are standardized files that list all the components and dependencies in your software. The system can generate these in two industry-standard formats: CycloneDX and SPDX.

### Selecting Your Scope

By default, when you open the panel, User Facing documentation is already selected. This is the most common starting point.

To customize what gets created:

1. Look for the "Customize Scope & Content Structure" section
2. Click to expand it if it's collapsed
3. You'll see checkboxes for:
   - User Facing documentation
   - Internal developer documentation
   - SBOM - Software Bill of Materials

Check the boxes for the types of documentation you want to generate. You can select multiple types - for example, you might want both User Facing and Internal Developer documentation in a single run.

## Customizing User Facing Content

When you select User Facing documentation, you can choose exactly what kind of content gets created. The system follows a structured approach based on documentation best practices.

### Content Structure Options

Click on User Facing documentation to reveal the Content Structure section underneath. You'll see several content types you can include:

**Intro (Quickstart/Introduction)**
This creates a getting-started guide that helps new users understand and start using your product quickly. Think of it as the "Hello World" of your documentation.

**Tutorials**
These are comprehensive, end-to-end guides that walk users through complete workflows. Tutorials focus on teaching by doing, leading users to accomplish real outcomes.

**How-To Guides**
These are shorter, task-focused instructions. Each guide answers a specific "How do I...?" question. They're practical and to-the-point.

**API Reference**
This automatically generates technical reference documentation for your APIs and SDKs based on your code. It includes endpoints, parameters, and response formats.

**Concepts**
These explain the big ideas behind your product - the architecture, data models, limitations, and important concepts users need to understand.

**Troubleshooting**
This creates a guide to common problems and how to solve them, including error messages and debugging steps.

**Release Notes**
This generates documentation about what's new, what's changed, and what's been fixed in your product updates.

### Selecting Content Types

By default, Intro, Tutorials, and Reference are already selected - these are the foundation of good documentation. To add or remove content types:

1. Check or uncheck the boxes next to each content type
2. The system will adjust the list of files it plans to generate based on your selections

For example, if you're documenting a new API, you might want Intro, Reference, and Troubleshooting. If you're documenting a user interface, Tutorials and How-To Guides might be more important.

## Adding Your Specific Instructions

At the top of the panel, you'll find a text box labeled "Additional Instructions" with a purple "Priority" badge.

### Why Instructions Matter

While the AI is smart about analyzing your code and creating documentation, your specific instructions help guide what gets emphasized. These instructions take priority over any default settings, so they're your way to steer the documentation in the direction you need.

### Writing Effective Instructions

In the text box, you can type specific guidance for this documentation run. Here are some examples:

**For technical products:**
```
Focus on security features and authentication flows. Include code examples in Python and JavaScript. Emphasize best practices for handling sensitive data.
```

**For user-friendly products:**
```
Write for non-technical users. Use simple language and include lots of screenshots. Focus on common workflows for small business owners.
```

**For API documentation:**
```
Provide complete request and response examples for every endpoint. Include common error codes and rate limiting information. Show authentication examples.
```

**For compliance-focused documentation:**
```
Highlight GDPR compliance features and data protection mechanisms. Include information about audit trails and data encryption.
```

The more specific you are, the better the AI can tailor the documentation to your needs.

### The Default Instruction

If you don't add anything, the system uses this default instruction:
"Create comprehensive documentation from product analysis."

While this works, adding your own instructions usually produces better, more focused results.

## Selecting Source Code to Analyze

The AI needs to analyze your actual code to create documentation. You can control which parts of your codebase get analyzed.

### Finding Your Repositories

Look for the "Select Code Scope" section. Click to expand it and you'll see all your OrchestrAI-enabled repositories listed.

At the top, there's a "Select All" button. By default, when you open the panel, all your repositories are already selected, but you can customize this.

### Choosing Individual Repositories

For each repository, you can:

1. **Include or exclude it**: Check or uncheck the box next to the repository name
2. **Choose the analysis scope**: Select between analyzing the whole repository or just a specific commit

### Whole Repository vs. Specific Commit

**Whole Repo Analysis**
This analyzes your entire codebase as it currently exists. Use this when you want comprehensive documentation that covers everything.

**Specific Commit Analysis**
This analyzes only the changes made in a particular commit. Use this when you want to update documentation to reflect recent changes without regenerating everything.

To analyze a specific commit:

1. Select the repository
2. Click "Specific Commit" instead of "Whole Repo"
3. A list of recent commits will load
4. Click on the commit you want to analyze
5. The selected commit will be highlighted

Each commit shows:
- The commit message (first line)
- The commit ID (first 7 characters)
- The date of the commit

This is particularly useful when you've just added a new feature and want to update documentation to reflect only that change.

## Customizing File Names

The system generates documentation files based on your selected scopes and content types. You can customize what these files are named.

### Viewing Planned Files

In the Configuration section, scroll down to "Files to be generated." You'll see a list of all the markdown files the AI plans to create, such as:

- intro.md
- tutorials.md
- reference.md
- architecture.md
- sbom_cyclonedx.md

Each file is listed with:
- A text box containing the current filename
- The file type label (like "Quickstart / Introduction" or "API Reference")

### Changing a File Name

To customize any filename:

1. Click in the text box next to the file you want to rename
2. Type your preferred name (without the .md extension)
3. The file will be saved with your custom name

**Examples:**

If you want your introduction to be called "getting-started" instead of "intro":
- Find the intro file in the list
- Change "intro" to "getting-started"
- The file will be created as getting-started.md

If you want your API reference organized by version:
- Change "reference" to "api-v2-reference"
- The file will be created as api-v2-reference.md

### Best Practices for File Names

- Use lowercase letters
- Separate words with hyphens (not spaces or underscores)
- Be descriptive but concise
- Match your existing documentation naming conventions if you have them

### Creating Multiple Files for One Type

If you want to split content into multiple files:

1. You can run the documentation generator multiple times with different custom instructions
2. Each time, give the output file a unique name
3. For example, first run: "tutorial-basics" with instructions "Cover installation and first steps"
4. Second run: "tutorial-advanced" with instructions "Cover advanced configuration and customization"

## Adding Task Explanations

At the bottom of the instructions section, you'll find a checkbox labeled "Add documentation task explanation at the top of the file."

### What This Does

When checked, the AI adds a special note at the very beginning of each generated documentation file explaining what that specific file is meant to contain and how it fits into the overall documentation structure.

### When to Use This

This is helpful when:

- You're generating documentation that will be reviewed or edited by your team
- You want to understand the AI's interpretation of each document's purpose
- You're generating internal developer documentation where context about the document's role is valuable
- You're planning to expand the documentation later and want guidance on what belongs in each file

### What It Looks Like

The task explanation appears as a comment or note section at the top of the file, before the actual documentation content begins. It explains the document's purpose, target audience, and suggested content approach.

## Generating the Documentation

Once you've configured everything, you're ready to create your documentation.

### The Generate Button

At the bottom of the panel, you'll see a purple button labeled "Generate Documentation" with a play icon.

### Button States

The button changes based on your settings and status:

- **"Generate Documentation"**: Everything is ready, click to start
- **"Configuration Required"**: You need to set up your documentation repository first
- **"Select at least one scope"**: Choose at least one documentation type (User Facing, Internal, or SBOM)
- **"Checking credits..."**: The system is verifying you have available credits
- **"Upgrade Plan"**: You've reached your monthly credit limit and need to upgrade
- **"Loading configuration..."**: The system is checking your settings

### Starting Generation

When ready, click "Generate Documentation." A progress dialog will open showing:

1. The analysis phase (AI reading and understanding your code)
2. The generation phase (AI writing documentation)
3. The deployment phase (AI saving files to your repository)

This process can take several minutes depending on your codebase size and the amount of documentation being generated.

### What Happens During Generation

The AI:

1. **Analyzes your product**: Reads through the selected repositories to understand functionality, APIs, user flows, and code structure
2. **Generates content**: Creates documentation following the content structure you selected, using your custom instructions as guidance
3. **Organizes files**: Creates each documentation file with your custom filenames
4. **Commits to repository**: Saves all generated files to your configured documentation repository

### After Generation Completes

When finished, you'll see a success message. The documentation has been committed to your repository in the folder you configured in your settings.

You can:

- Review the generated files in your repository
- Edit them further if needed
- Publish them to your documentation site
- Share them with your team

## Example: Creating API Documentation

Let's walk through a complete example of creating documentation for a REST API.

### Step 1: Open the Creator
Navigate to Documentation and click "Create Documentation"

### Step 2: Choose Your Scope
Expand "Customize Scope & Content Structure" and ensure only "User Facing documentation" is checked

### Step 3: Select Content Types
For an API, check:
- Intro (for getting started with the API)
- Reference (for complete API endpoints)
- Troubleshooting (for common errors)
- Concepts (for authentication and rate limiting)

Uncheck Tutorials and How-To since this is a technical API.

### Step 4: Add Your Instructions
In the Additional Instructions box, type:
```
Create technical API documentation for developers. Include complete request/response examples using curl, Python, and JavaScript. Focus on authentication using API keys. Document all error codes with explanations. Include rate limiting information prominently.
```

### Step 5: Select Source Code
Expand "Select Code Scope" and ensure your API repository is selected with "Whole Repo" chosen.

### Step 6: Customize File Names
In the Configuration section, update the filenames:
- Change "intro" to "api-quickstart"
- Change "reference" to "api-endpoints"
- Change "troubleshooting" to "api-errors"
- Change "concepts" to "api-authentication"

### Step 7: Add Task Explanations
Check the box "Add documentation task explanation at the top of the file" so your team understands the purpose of each file.

### Step 8: Generate
Click "Generate Documentation" and wait for the process to complete.

The result will be four documentation files in your repository:
- api-quickstart.md (getting started guide)
- api-endpoints.md (complete API reference)
- api-errors.md (troubleshooting guide)
- api-authentication.md (authentication and security)

## Tips for Better Documentation

### Focus Your Scope
Generate only what you need for this particular update. You can always generate more documentation later with different settings.

### Be Specific in Instructions
Instead of "document the API," try "document the authentication endpoints with examples for OAuth2 and API key methods."

### Use Descriptive File Names
Names like "user-onboarding-tutorial" are better than generic names like "tutorial1."

### Review and Iterate
Generated documentation is a starting point. Review it, make edits, and regenerate with refined instructions if needed.

### Combine with Specific Commits
When documenting a new feature, use the specific commit option to focus documentation on just what changed, keeping other docs stable.

### Save Credit by Being Selective
Generating less documentation with focused instructions uses fewer credits than regenerating everything. Think about what really needs documentation right now.

## Understanding Credit Usage

Each documentation generation run uses credits from your workspace. The amount depends on:

- Size of your codebase
- Number of documentation types selected
- Amount of content being generated

You can see your current credit status at the top of the panel. If you're running low, the system will warn you before you start generation.

Owners and admins can upgrade the workspace plan to get more credits if needed. The upgrade button appears directly in the panel when you've reached your limit.

## Troubleshooting Common Issues

**"Configuration Required" button**
- Go to Organization Information
- Set your documentation repository and folder
- Return to the Documentation page

**"Select at least one scope" button**
- Open the "Customize Scope & Content Structure" section
- Check at least one box (User Facing, Internal, or SBOM)

**No repositories showing in Code Scope**
- Go to your repository settings
- Enable OrchestrAI for at least one repository
- Return to the Documentation page

**Generation taking a long time**
- Large codebases take longer to analyze
- Multiple documentation types take longer to generate
- Check the progress dialog for current status

**Generated content needs improvement**
- Add more specific instructions about what to emphasize
- Try generating smaller pieces with focused instructions
- Review and edit the markdown files directly after generation

## Next Steps

After creating your documentation:

1. **Review the files**: Check the generated markdown in your repository
2. **Make manual edits**: Adjust any sections that need refinement
3. **Set up auto-updates**: Consider using specific commit documentation for keeping docs current
4. **Share with your team**: Let others know where the new documentation lives
5. **Publish if ready**: Deploy to your documentation site or wiki

The AI Documentation Specialist gets smarter with each use. The more specific your instructions, the better your results will be over time.