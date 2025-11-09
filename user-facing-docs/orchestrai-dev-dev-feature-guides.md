# orchestrai-dev-creating-new-documentation.md

## Creating New Documentation from Your Product

Learn how to generate fresh, comprehensive documentation for your product using AI analysis.

---

## What You'll Do

Generate complete documentation by having the AI analyze your product directly. No existing documentation needed - the AI will explore your product, understand how it works, and create professional documentation from scratch.

---

## Before You Start

Make sure you have:
- Configured a repository and folder where documentation will be saved
- At least one repository connected and enabled in your workspace

---

## Choosing What to Document

When you open the AI Documentation Specialist panel, you'll see three main types of documentation you can generate:

### User Facing Documentation
Documentation designed for people who will use your product. This includes:
- **Quickstart / Introduction** - Get users started quickly with the basics
- **Tutorials** - Step-by-step guides that walk users through complete tasks
- **How-To Guides** - Short, focused instructions for specific tasks
- **API Reference** - Technical details about your product's API (generated automatically)
- **Concepts** - Explanations of how your product works and key ideas
- **Troubleshooting** - Help for when things go wrong
- **Release Notes** - What's new in each version (generated automatically)

By default, the most essential sections (Introduction, Tutorials, and Reference) are selected for you.

### Internal Developer Documentation
Documentation for your team members who work on the product:
- Architecture overview
- Development setup instructions
- Technical implementation details

### Software Bill of Materials (SBOM)
Technical inventory documents in standard formats (CycloneDX and SPDX) that list all components in your product.

---

## Step-by-Step: Creating Your Documentation

### Step 1: Open the Documentation Panel
Click the "Create from Scratch" button on your Documentation page.

### Step 2: Add Special Instructions (Optional)
You'll see a text box labeled "Additional Instructions" at the top of the panel. Use this to tell the AI anything specific you want:
- Special topics to focus on
- Particular features to highlight
- Writing style preferences
- Target audience details

**Important:** These instructions take priority over any default settings.

### Step 3: Choose Documentation Scope
Click on "Customize Scope & Content Structure" to expand your options:

1. **Select Documentation Types**
   - Check "User Facing documentation" for end-user docs
   - Check "Internal developer documentation" for team docs
   - Check "SBOM" for software component lists

2. **Pick Content Structure** (for User Facing)
   - Choose which sections you want created
   - The most important ones (Introduction, Tutorials, Reference) are selected by default
   - Add or remove sections based on what your users need

### Step 4: Select Code to Analyze
If you have multiple repositories, choose which ones the AI should examine:
- Click "Select Code Scope" to see your repositories
- Use "Select All" or pick specific ones
- For each repository, choose:
  - **Whole Repo** - Analyze the entire codebase
  - **Specific Commit** - Focus on changes from one update (useful for release notes or targeted updates)

### Step 5: Customize File Names (Optional)
Each document will have a default filename. You can change these if needed:
- Scroll down to see the list of files that will be created
- Click on any filename to edit it
- The file extension (.md) is added automatically

### Step 6: Start Generation
Click the "Generate Documentation" button at the bottom. You'll see a progress dialog showing:
- Current step in the process
- What the AI is working on
- Estimated time remaining

---

## Creating Focused Documentation for Specific Topics

Sometimes you want documentation about just one feature or aspect of your product. Here's how:

### Use Targeted Instructions
In the "Additional Instructions" box, be very specific:
- "Focus only on the payment processing feature"
- "Document just the authentication system"
- "Create a guide for the reporting dashboard"

### Customize Your File Name
1. Scroll to the files section
2. Click on the filename you want to change
3. Give it a descriptive name like "payment-processing-guide" or "authentication-setup"

### Select Specific Content Types
1. Open "Customize Scope & Content Structure"
2. Uncheck sections you don't need
3. Keep only relevant sections (for example, just "How-To Guides" for a feature tutorial)

### Choose Targeted Code Scope
If your feature is in a specific repository:
1. Open "Select Code Scope"
2. Uncheck "Select All"
3. Check only the repository containing your feature
4. If the feature was recently added, use "Specific Commit" to focus on those changes

---

## Understanding File Generation Options

### Task Explanation at Top of File
You can choose to include or exclude an explanation at the beginning of each documentation file:
- **Checked**: Each file starts with a note explaining what it covers and how it was created
- **Unchecked**: Files start directly with the documentation content

This option appears as a checkbox labeled "Add documentation task explanation at the top of the file"

---

## What Happens During Generation

The AI will:
1. **Analyze Your Product** - Examines the code and features in your selected repositories
2. **Create Structure** - Builds a logical organization based on your chosen content structure
3. **Write Documentation** - Generates clear, comprehensive content for each section
4. **Save to Repository** - Commits all files to your configured documentation location

You'll receive a notification when it's complete, and you can view your new documentation right away.

---

## Tips for Best Results

- **Be specific in your instructions** - The more detail you provide, the better the AI understands what you need
- **Start with essential sections** - You can always generate additional sections later
- **Review and iterate** - If the first version isn't perfect, generate again with refined instructions
- **Use descriptive file names** - Make it easy to find specific documentation later
- **Select the right code scope** - Whole repository for comprehensive docs, specific commit for updates

---

## Need Different Documentation?

You can run the documentation generation as many times as you need:
- Create different versions for different audiences
- Generate focused guides for specific features
- Update documentation as your product evolves

Each generation is independent, so you can experiment with different scopes, instructions, and file structures until you get exactly what you need.