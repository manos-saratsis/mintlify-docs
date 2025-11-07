I'll analyze the source code and create a user-friendly feature guide on how to generate documentation with OrchestrAI.

<read_file>
<path>src/components/AIDocumentationSpecialistPanel.tsx</path>
</read_file>

<read_file>
<path>src/components/DocumentationProgressDialog.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductDocumentation.tsx</path>
</read_file>

Now I'll create the feature guide based on the actual implementation:

# user-facing-docs/orchestrai-dev-documentation-generation-guide.md

# How to Generate Documentation with OrchestrAI

## Overview

OrchestrAI's AI Documentation Specialist helps you create professional, comprehensive documentation for your product automatically. Whether you're starting from scratch or restructuring existing documentation, the AI analyzes your product and generates well-organized documentation following industry best practices.

## Before You Start

Before generating documentation, make sure you have:

1. **Configured Your Documentation Repository**: Set up where you want your documentation files to be stored
2. **Selected Your Workspace**: Choose the workspace containing the repositories you want to document
3. **Connected Your Repositories**: Ensure the code repositories you want to document are connected and enabled in OrchestrAI

## Creating Documentation from Scratch

### Step 1: Access the Documentation Feature

1. Log into your OrchestrAI account
2. Navigate to the Documentation section from the main menu
3. Click the **"Create New Documentation"** button

You'll see the AI Documentation Specialist panel open on the right side of your screen.

### Step 2: Choose What to Document

#### Select Your Documentation Scope

You can generate three types of documentation:

**User Facing Documentation** (Recommended for getting started)
- This creates documentation for your end users
- Helps users understand how to use your product
- Includes tutorials, guides, and reference materials

**Internal Developer Documentation**
- Technical documentation for your development team
- Covers architecture, development setup, and code structure
- Useful for onboarding new team members

**SBOM (Software Bill of Materials)**
- Generates a detailed list of all software components
- Available in CycloneDX and SPDX formats
- Important for security and compliance tracking

**To select your scope:**
1. Look for the "Customize Scope & Content Structure" section
2. Click to expand it
3. Check the boxes next to the types of documentation you want to create
4. Start with "User Facing documentation" if this is your first time

### Step 3: Choose Your Content Structure

When you select User Facing documentation, you can choose which sections to include:

**Quickstart / Introduction** (Recommended - Always start with this)
- Gets users up and running quickly
- Provides a friendly welcome to your product
- Shows the fastest path to success

**Tutorials**
- Step-by-step guides that teach by doing
- Takes users through complete workflows
- Best for learning by example

**How-To Guides**
- Short, focused task instructions
- Answers "How do I...?" questions
- Perfect for specific problems

**API Reference**
- Technical details about your APIs
- Auto-generated from your code
- Essential for developers integrating with your product

**Concepts**
- Explains how things work behind the scenes
- Covers architecture and key ideas
- Helps users understand the "why"

**Troubleshooting**
- Common problems and solutions
- Error messages explained
- Helps users fix issues independently

**Release Notes**
- What's new in each version
- Automatically generated from changes
- Keeps users informed of updates

**Recommended starting combination:**
- ✅ Quickstart / Introduction
- ✅ Tutorials
- ✅ API Reference

You can always generate more sections later!

### Step 4: Select Which Code to Document

If you have multiple repositories, choose which ones the AI should analyze:

1. Expand the "Select Code Scope" section
2. You'll see all your connected repositories
3. Check the boxes next to the repositories you want to document

**Choose between:**

**Whole Repo** (Recommended)
- The AI analyzes your entire codebase
- Creates comprehensive documentation
- Best for complete documentation

**Specific Commit**
- Updates documentation based on specific changes
- Useful for documenting new features
- Select this if you only want to document recent updates

For most cases, start with "Whole Repo" to get complete documentation.

### Step 5: Add Custom Instructions (Optional but Powerful)

This is where you can guide the AI to create exactly what you need:

1. Find the "Additional Instructions" text box
2. Type specific requests for your documentation

**Example instructions you can use:**

```
Focus heavily on getting started quickly. Include code examples 
for the most common use cases. Use a friendly, conversational tone.
```

```
Create detailed API documentation with request/response examples. 
Include authentication requirements and rate limits.
```

```
Generate tutorials for three key workflows: user onboarding, 
creating a project, and sharing with team members.
```

```
Document our Python SDK with emphasis on error handling and 
best practices. Include examples for each major function.
```

**Custom File Creation:**

Want to create specific documentation files? Include requests like:

```
Create a "quickstart.md" file with a 5-minute setup guide.
Create a "common-errors.md" file listing the top 10 errors users encounter.
Create an "advanced-features.md" file for power users.
```

The AI will generate these files with the exact names you specify!

**Tips for great instructions:**
- Be specific about what you want
- Mention the audience (beginners, developers, etc.)
- Request specific examples or use cases
- Specify the tone (formal, friendly, technical)
- List any specific topics to emphasize

### Step 6: Review Your Configuration

Before generating, check the Configuration section at the bottom:

- **Repository**: Where your documentation will be stored
- **Folder**: The folder path for your documentation files
- **Files to be generated**: Preview of what will be created

You can even rename the files before generating:
1. Click on any filename in the list
2. Type your preferred name
3. The file will be created with your custom name

### Step 7: Generate Your Documentation

When everything looks good:

1. Click the **"Generate Documentation"** button at the bottom
2. A progress window will appear showing the AI's work
3. You'll see updates as the AI:
   - Analyzes your product
   - Generates documentation sections
   - Creates the files
   - Commits them to your repository

**This typically takes 3-5 minutes** depending on your codebase size.

### Step 8: Review and Deploy

Once generation is complete:

1. **Check Your Repository**: Your new documentation files are now in your repository
2. **Review the Content**: Open the files and review what the AI created
3. **Make Adjustments**: Edit any sections that need refinement
4. **Deploy**: Push your documentation live using your preferred hosting (GitHub Pages, Netlify, etc.)

## Deploying Your Documentation

Your documentation is created as Markdown (.md) files in your repository. Here's how to make it available to users:

### Option 1: GitHub Pages (Simplest)
1. Go to your repository settings on GitHub
2. Navigate to "Pages" in the sidebar
3. Select your documentation branch and folder
4. Click "Save"
5. Your documentation is now live at: `https://yourname.github.io/your-repo/`

### Option 2: Documentation Hosting Platforms
Your generated Markdown works perfectly with:
- **GitBook**: Import your repository for automatic updates
- **ReadTheDocs**: Connect your repo for professional hosting
- **Docusaurus**: Use the generated files as your content source
- **MkDocs**: Drop the files into your docs folder

### Option 3: Custom Website
- Copy the Markdown files to your documentation website
- Convert to HTML using any Markdown processor
- Style with your brand guidelines

## Tips for Best Results

### First Time Generating?
Start simple:
1. Select only "User Facing" documentation
2. Choose just Quickstart + Tutorials + API Reference
3. Document one repository
4. Review the results before expanding

### Generating Again?
- You can generate additional sections anytime
- Each generation adds to or updates existing files
- The AI remembers your structure and style

### Need Help?
- Use very specific custom instructions
- Generate in stages (e.g., first user guides, then API docs)
- Review and refine after each generation
- The AI learns from the feedback in your instructions

### Making Changes
If the generated documentation needs adjustments:
1. Edit the files directly in your repository
2. Regenerate specific sections with updated instructions
3. The AI can update existing files without losing your manual edits

## Common Use Cases

### Documenting a New API
Custom instruction:
```
Create comprehensive API documentation including authentication, 
all endpoints with request/response examples, error codes, and 
rate limiting information. Use curl examples.
```

### Creating a User Guide
Custom instruction:
```
Generate a beginner-friendly user guide with screenshots placeholders. 
Focus on the top 5 tasks users perform. Include step-by-step instructions 
with clear headings.
```

### Internal Team Documentation
Select "Internal developer documentation" and add:
```
Document our architecture decisions, development setup process, and 
coding standards. Include environment setup for Mac and Windows developers.
```

### Quick Reference Guide
Custom instruction:
```
Create a single-page quick reference guide with common commands, 
keyboard shortcuts, and frequently used code snippets.
```

## Frequently Asked Questions

**Q: Can I edit the generated documentation?**
Yes! All documentation is created in your repository as standard Markdown files. Edit them directly anytime.

**Q: What if I don't like what was generated?**
Regenerate with more specific instructions. The AI will create new versions based on your guidance.

**Q: How do I add images to my documentation?**
The AI creates placeholder references for images. Add your actual images to the repository and update the file paths.

**Q: Can I generate documentation in multiple languages?**
Not automatically, but you can request specific language in your custom instructions, or translate the generated files afterward.

**Q: Will regenerating overwrite my changes?**
The AI is smart about updates - it can refresh content while preserving manual edits. Always review the changes before accepting them.

**Q: How often should I regenerate documentation?**
Generate new documentation when you:
- Release major features
- Update your API
- Receive user feedback about unclear sections
- Restructure your product

## What Happens Behind the Scenes

When you click "Generate Documentation," here's what the AI does:

1. **Accesses Your Product**: The AI reviews your connected repositories to understand what your product does
2. **Analyzes Structure**: It examines your code, APIs, and features
3. **Plans Content**: Based on your selections and instructions, it creates an outline
4. **Writes Documentation**: It generates each section with appropriate examples and explanations
5. **Formats Files**: Creates properly structured Markdown files with headers, links, and formatting
6. **Deploys to Repository**: Commits all files to your specified repository and folder

All of this happens automatically - you just wait for completion!

## Next Steps

Once you've generated your documentation:

1. **Share with your team** for review and feedback
2. **Set up automatic hosting** so users can access it
3. **Add to your workflow** - regenerate after major releases
4. **Gather user feedback** on what additional documentation would help
5. **Generate more sections** as your product evolves

---

**Need more help?** Contact OrchestrAI support or visit our documentation for advanced features and tips.