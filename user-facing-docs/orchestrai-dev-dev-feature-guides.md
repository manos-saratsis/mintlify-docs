I'll analyze the source code to create a comprehensive how-to guide for creating documentation from scratch in OrchestrAI.

Let me first examine the key components:

<js_run>
// Extract key information about the documentation creation process
const documentationPanel = `AIDocumentationSpecialistPanel component`;
const features = {
  scopes: ['userFacing', 'internal', 'sbom'],
  contentStructure: ['intro', 'tutorials', 'howTo', 'reference', 'concepts', 'troubleshooting', 'releaseNotes'],
  customization: ['instructions', 'fileName', 'repositorySelection']
};

console.log('Documentation Features:', JSON.stringify(features, null, 2));
</js_run>

<js_run>
// Extract the workflow from the source code
const workflow = {
  step1: "Select 'Create New Documentation' action",
  step2: "Choose documentation scope (User Facing, Internal Developer, or SBOM)",
  step3: "Select content structure types",
  step4: "Add custom instructions",
  step5: "Customize file names",
  step6: "Select code repositories",
  step7: "Generate documentation"
};

console.log('Documentation Creation Workflow:', JSON.stringify(workflow, null, 2));
</js_run>

Now I'll create the user-facing documentation:

<write_file>
<path>user-facing-docs/orchestrai-dev-create-documentation-guide.md</path>
<content>
# Creating Documentation from Scratch

Learn how to generate comprehensive documentation for your product using OrchestrAI's AI Documentation Specialist. This guide walks you through creating new documentation with customizable scopes, content structures, and focused instructions.

## Overview

The AI Documentation Specialist analyzes your product directly and creates professional documentation from the ground up. You can customize what types of documentation to generate, choose specific content structures, and even create specialized documentation files with custom instructions.

## Before You Start

Make sure you have:
- Configured your documentation repository and folder in Organization Information settings
- At least one repository enabled for OrchestrAI
- Sufficient credits in your workspace

## Step 1: Open the AI Documentation Specialist

1. Navigate to the Documentation page in your workspace
2. Look for the "AI Documentation Specialist" panel
3. Select the **Create New Documentation** option (not Migrate)

You'll see a message explaining that the AI will analyze your product directly and create comprehensive documentation from scratch.

## Step 2: Choose Your Documentation Scope

Expand the **Customize Scope & Content Structure** section to select what types of documentation you want to create.

### Available Scopes

**User Facing Documentation**
- Creates documentation for your end users
- Includes tutorials, guides, and reference materials
- Perfect for product documentation sites

**Internal Developer Documentation**
- Generates documentation for your development team
- Includes architecture details and development setup guides
- Helps onboard new team members

**SBOM (Software Bill of Materials)**
- Creates industry-standard software component inventories
- Generates both CycloneDX and SPDX formats
- Essential for security and compliance

### Choosing Multiple Scopes

You can select any combination of scopes. For example:
- Select only "User Facing" for customer documentation
- Select "User Facing" + "Internal Developer" for comprehensive docs
- Select all three for complete documentation coverage

## Step 3: Select Content Structure (User Facing Only)

When you enable User Facing documentation, you'll see content structure options. Each serves a specific purpose:

**Intro (Quickstart)**
- First thing users see
- Gets them up and running quickly
- File name: `intro.md`

**Tutorials**
- End-to-end learning experiences
- Outcome-driven lessons
- File name: `tutorials.md`

**How-To Guides**
- Task-focused instructions
- Quick, specific solutions
- File name: `how_to.md`

**API Reference**
- Technical API documentation
- Automatically generated from code
- File name: `reference.md`

**Concepts**
- Explains how things work
- Architecture and models
- File name: `concepts.md`

**Troubleshooting**
- Common problems and solutions
- Error catalog and debugging tips
- File name: `troubleshooting.md`

**Release Notes**
- What's new in each version
- Automatically generated from changes
- File name: `release_notes.md`

### Recommended Starting Point

For new documentation, we recommend starting with:
- ✅ Intro (Quickstart)
- ✅ Tutorials
- ✅ API Reference

You can add other types later as your documentation grows.

## Step 4: Select Source Code Repositories

The AI needs to analyze your code to create accurate documentation.

### Choosing Repositories

1. Expand the **Select Code Scope** section
2. You'll see all repositories enabled for OrchestrAI
3. By default, all repositories are selected

### Repository Scope Options

For each repository, choose:

**Whole Repo**
- Analyzes the entire repository
- Best for comprehensive documentation
- Recommended for initial documentation creation

**Specific Commit**
- Analyzes only changes in one commit
- Perfect for updating docs after specific changes
- Select from recent commits in the dropdown

**When to Use Each Option:**
- Use "Whole Repo" when creating documentation from scratch
- Use "Specific Commit" when updating docs after a feature addition

## Step 5: Customize File Names

Each documentation type will be saved as a separate file. You can customize these names to match your needs.

### Default File Names

The files section shows what will be created:
- `intro.md` → Quickstart / Introduction
- `tutorials.md` → Tutorials
- `how_to.md` → How-To Guides
- `reference.md` → API Reference
- And more based on your selections

### Changing File Names

1. Find the file in the "Files to be generated" section
2. Click in the filename field
3. Type your preferred name (without .md extension)
4. The AI will create the file with your custom name

**Example:**
- Change `intro.md` to `getting-started.md`
- Change `tutorials.md` to `learning-guide.md`
- Change `reference.md` to `api-docs.md`

## Step 6: Add Focused Instructions

This is where you create specialized documentation by providing specific guidance to the AI.

### The Instructions Field

At the top of the panel, you'll see "Additional Instructions" with a Priority badge. This field takes precedence over all default settings.

### Creating Focused Documentation

To create focused documentation for a specific purpose, write detailed instructions:

**Example 1: Security-Focused Documentation**
```
Focus on security features and best practices. Include:
- Authentication and authorization flows
- Data encryption methods
- Security compliance information
- Common security pitfalls and how to avoid them
```

**Example 2: Getting Started Guide**
```
Create a beginner-friendly getting started guide that:
- Assumes no prior knowledge
- Uses simple language and short sentences
- Includes step-by-step setup instructions
- Provides working code examples
- Explains what each step accomplishes
```

**Example 3: API Integration Guide**
```
Focus exclusively on API integration. Cover:
- Authentication setup
- All available endpoints
- Request/response examples
- Rate limiting and error handling
- Code samples in Python and JavaScript
```

**Example 4: Mobile App Documentation**
```
Create documentation specifically for mobile developers:
- Focus on iOS and Android integration
- Include mobile-specific code examples
- Cover push notifications and offline functionality
- Explain mobile-specific performance considerations
```

### Best Practices for Instructions

**Be Specific**
- Instead of "document authentication," write "explain OAuth 2.0 flow with code examples"
- Instead of "cover APIs," write "document all REST endpoints with curl examples"

**Set the Tone**
- "Write in a friendly, conversational tone for beginners"
- "Use formal, technical language for enterprise developers"
- "Explain complex concepts using simple analogies"

**Define Scope**
- "Focus only on version 2.0 features"
- "Include only web-related functionality"
- "Document admin features separately from user features"

**Request Specific Elements**
- "Include code examples in TypeScript"
- "Add diagrams for all workflows"
- "Provide troubleshooting tips for common errors"

## Step 7: Combine Custom Names and Instructions

The most powerful approach combines custom file names with focused instructions.

### Example Workflow

**Scenario:** You want to create separate documentation for different user types

**1. First Documentation File**
- Scope: User Facing
- Content: Intro + Tutorials
- File name: `admin-guide.md`
- Instructions:
```
Create documentation specifically for administrators. Focus on:
- User management and permissions
- Workspace configuration
- Billing and subscription management
- Security settings and compliance
Use clear section headers and include screenshots where helpful.
```

**2. Second Documentation File** (Run again)
- Scope: User Facing
- Content: Intro + Tutorials + How-To
- File name: `developer-guide.md`
- Instructions:
```
Create documentation for developers integrating our API. Include:
- Complete API reference with examples
- Authentication and authorization
- Webhook setup and handling
- SDKs and client libraries
- Code examples in Python, JavaScript, and Java
```

**3. Third Documentation File** (Run again)
- Scope: User Facing
- Content: Intro + How-To
- File name: `end-user-guide.md`
- Instructions:
```
Create simple, beginner-friendly documentation for end users. Focus on:
- Getting started in 5 minutes
- Common tasks with screenshots
- No technical jargon
- Step-by-step instructions
- Troubleshooting common issues
```

## Step 8: Configure Advanced Options (Optional)

### Task Explanation

Check "Add documentation task explanation at the top of the file" to include:
- What the documentation covers
- Who it's intended for
- How it was generated

This helps readers understand the context and purpose.

## Step 9: Generate Your Documentation

1. Review your selections:
   - Scopes chosen
   - Content structure types
   - Repository selections
   - Custom file names
   - Instructions provided

2. Click the **Generate Documentation** button

3. You'll see a progress dialog showing:
   - Analyzing repositories
   - Generating content
   - Creating documentation files
   - Committing to your repository

4. When complete, your documentation will be in your configured repository and folder

## Creating Multiple Specialized Guides

To create several focused documentation files:

**Run 1: Quick Start Guide**
- Select: Intro only
- File name: `quickstart.md`
- Instructions: "Create a 5-minute quick start that gets users to their first successful action"

**Run 2: Comprehensive Tutorial**
- Select: Tutorials only
- File name: `complete-tutorial.md`
- Instructions: "Create an end-to-end tutorial covering all major features with working examples"

**Run 3: API Reference**
- Select: Reference only
- File name: `api-reference.md`
- Instructions: "Generate complete API documentation with request/response examples for every endpoint"

**Run 4: Troubleshooting Guide**
- Select: Troubleshooting only
- File name: `troubleshooting.md`
- Instructions: "Create a troubleshooting guide covering the top 20 most common issues with solutions"

## Tips for Success

**Start Small**
- Begin with just Intro and Reference
- Add more content types as needed
- Generate focused guides one at a time

**Use Clear Instructions**
- Be specific about what you want
- Mention the target audience
- Specify the level of technical detail

**Iterate and Refine**
- Generate initial documentation
- Review what was created
- Run again with refined instructions for improvement

**Organize by Audience**
- Create separate files for different user types
- Use custom names that indicate the audience
- Write instructions tailored to each audience's needs

**Leverage Repository Scope**
- Use "Whole Repo" for comprehensive docs
- Use "Specific Commit" to document new features added in recent changes

## What Happens Next

After generation completes:

1. **Files Created**: Your documentation files appear in the configured repository folder
2. **Git Commit**: Changes are committed automatically with a descriptive message
3. **Review**: Check your repository to see the new documentation
4. **Publish**: Deploy your documentation site if you have one configured

## Common Scenarios

**Scenario: First-Time Documentation**
- Select all scopes for complete coverage
- Use default content structure (Intro, Tutorials, Reference)
- Provide general instructions about your product
- Let the AI analyze all repositories

**Scenario: Feature-Specific Docs**
- Select only User Facing scope
- Choose Intro and How-To
- Custom file name: `new-feature-guide.md`
- Provide detailed instructions about the specific feature

**Scenario: Developer Onboarding**
- Select Internal Developer scope
- Let it generate architecture and setup docs
- Add instructions about team conventions and practices

**Scenario: Compliance Documentation**
- Select SBOM scope
- Let it generate standard compliance formats
- Use for security audits and vendor requirements

## Troubleshooting

**"Configuration Required" Error**
- Go to Organization Information settings
- Set your documentation repository and folder
- Return to generate documentation

**"Repository Selection Required" Error**
- Expand the Select Code Scope section
- Select at least one repository
- Ensure repositories are enabled for OrchestrAI

**Documentation Doesn't Match Expectations**
- Refine your instructions to be more specific
- Run generation again with updated instructions
- Consider breaking into smaller, focused files

**Need to Update Documentation**
- Use the same scopes and file names
- Update instructions with what changed
- The AI will refresh the existing files

## Next Steps

After creating your documentation:

1. **Review Generated Content**: Read through the documentation to ensure accuracy
2. **Deploy Documentation**: Publish to your documentation site
3. **Iterate**: Run again with refined instructions if needed
4. **Maintain**: Use "Specific Commit" scope to update docs as code changes
5. **Expand**: Add more content types as your product grows

---

**Need Help?**

If you encounter issues or need guidance:
- Check that your repository and folder are configured
- Verify you have sufficient credits
- Ensure repositories are enabled for OrchestrAI
- Contact your workspace administrator for permissions issues
</content>
</write_file>

I've created a comprehensive how-to guide titled "Creating Documentation from Scratch" that covers everything users need to know about generating documentation in OrchestrAI. Here's what the guide includes:

## Key Features Documented

**1. Complete Workflow**
- Step-by-step process from opening the panel to generating documentation
- Clear progression through all configuration options

**2. Documentation Scopes**
- User Facing (with detailed content structure options)
- Internal Developer
- SBOM
- When to use each scope

**3. Content Structure Types**
- Detailed explanation of all 7 content types
- Purpose and file name for each
- Recommended starting configuration

**4. Custom Instructions**
- How to write effective, focused instructions
- 4 detailed examples (Security, Getting Started, API Integration, Mobile)
- Best practices for specificity and tone

**5. Custom File Names**
- How to rename documentation files
- Examples of effective naming conventions
- Combining custom names with focused instructions

**6. Advanced Scenarios**
- Creating multiple specialized guides
- Organizing by audience
- Feature-specific documentation
- Compliance documentation

**7. Practical Examples**
- Complete workflow for creating admin, developer, and end-user guides
- Multiple specialized guide examples
- Real-world scenario solutions

The guide uses simple, friendly language without any technical jargon or code references, focusing entirely on what users can DO with the feature and how it benefits them. Each section provides clear actions and outcomes, making it easy for anyone to create comprehensive, focused documentation for their product.