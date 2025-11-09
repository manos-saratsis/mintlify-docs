# Generating Documentation from Scratch

Learn how to create comprehensive documentation for your project using OrchestrAI's Documentation feature. The AI will analyze your code and generate organized, professional documentation automatically.

---

## What This Guide Covers

This guide walks you through:
- Creating brand new documentation from your codebase
- Choosing what types of documentation to generate
- Customizing the documentation structure
- Adding specific instructions for focused content
- Managing where your documentation files are saved

---

## Before You Start

Make sure you have:
1. **Selected a workspace** - Choose the workspace containing your project
2. **Connected your code repository** - Your repository should be connected and enabled in OrchestrAI
3. **Configured documentation settings** - Set up where you want your documentation to be stored (go to Product Information to configure the documentation repository and folder)

---

## Creating Documentation Step by Step

### 1. Open the Documentation Tool

1. Navigate to the Documentation section in your workspace
2. Click the **"Create New Documentation"** button
3. The AI Documentation Specialist panel will open on the right side of your screen

### 2. Choose Your Documentation Scope

The documentation scope determines what types of documentation will be generated. You have three main options:

#### **User Facing Documentation** (Selected by default)
This creates documentation for people who will use your product. When you select this, you can customize what sections to include:

- **Intro** - A quickstart guide to help users get started quickly
- **Tutorials** - Step-by-step lessons that guide users through complete workflows
- **How-To Guides** - Short, focused instructions for specific tasks
- **API Reference** - Technical details about your APIs and SDKs (auto-generated)
- **Concepts** - Explanations of how your product works, its architecture, and key ideas
- **Troubleshooting** - Solutions for common problems and error messages
- **Release Notes** - Automatically generated updates about what's new

**Tip:** Start with just Intro, Tutorials, and API Reference if you're creating documentation for the first time.

#### **Internal Developer Documentation**
This creates documentation for your development team:

- Architecture documentation explaining how your code is organized
- Development setup guides for new team members
- Developer overview with technical details

#### **SBOM - Software Bill of Materials**
This creates a detailed list of all software components in your project, useful for security and compliance:

- CycloneDX format
- SPDX format

**You can select multiple scopes** - For example, you might want both User Facing and Internal Developer documentation.

### 3. Select Your Code Repositories

Choose which parts of your codebase the AI should analyze:

1. Click on **"Select Code Scope"** to expand the repository section
2. You'll see all repositories that are enabled for OrchestrAI
3. Check the boxes next to the repositories you want to include
4. Use **"Select All"** to include everything, or pick specific repositories

For each selected repository, you can choose:

**Whole Repo** - Analyze everything in the repository
- Best for comprehensive documentation
- Takes longer but gives complete coverage

**Specific Commit** - Focus on recent changes
- Select this when you want to update documentation for new features
- Click to see a list of recent commits
- Choose the commit that contains the changes you want to document

### 4. Customize File Names (Optional)

By default, documentation files are named based on their type (like "intro.md" or "tutorials.md"). You can customize these:

1. Scroll down to **"Files to be generated"**
2. Click on any filename to edit it
3. Type your preferred name (without the .md extension)
4. The label on the right shows what type of content will be in that file

**Example:** You might rename "intro.md" to "getting-started.md" or "tutorials.md" to "learn-by-doing.md"

### 5. Add Custom Instructions

Want the AI to focus on something specific? Add additional instructions:

1. Find the **"Additional Instructions"** text box (marked with a "Priority" badge)
2. Type specific guidance for what you want documented

**Example Instructions:**
- "Focus on explaining the authentication flow in detail"
- "Include code examples for Python developers"
- "Emphasize security best practices throughout"
- "Make sure to document all command-line options"

These instructions take priority over any default settings, so the AI will pay special attention to what you write here.

### 6. Add Task Explanations (Optional)

If you want each documentation file to include a note at the top explaining what that file covers:

1. Check the box for **"Add documentation task explanation at the top of the file"**
2. This adds a helpful header to each file showing its purpose

This is useful when multiple people will be working with the documentation.

### 7. Start Generating

When you're ready:

1. Review your selections
2. Click the **"Generate Documentation"** button at the bottom of the panel
3. A progress window will appear showing what the AI is doing
4. Wait while the AI analyzes your code and creates the documentation

The process usually takes a few minutes depending on how much code you're documenting.

---

## Creating Focused Documentation Files

Sometimes you want to create a specific, focused piece of documentation. Here's how:

### Example: Creating a Security Guide

Let's say you want a dedicated security documentation file:

1. **In Documentation Scope**, select **User Facing**
2. **In Content Structure**, check **Concepts** (since security is a key concept)
3. **In Additional Instructions**, write:
   ```
   Create a comprehensive security guide covering authentication, 
   authorization, data encryption, and security best practices. 
   Include real code examples and common security pitfalls to avoid.
   ```
4. **In Files to be generated**, find the "concepts" file and rename it to:
   ```
   security-guide
   ```
5. Click **Generate Documentation**

The AI will create a file called "security-guide.md" focused entirely on security topics.

### Example: Creating an API Cookbook

For a collection of practical API examples:

1. **In Documentation Scope**, select **User Facing**
2. **In Content Structure**, check **How-To Guides** and **Reference**
3. **In Additional Instructions**, write:
   ```
   Create an API cookbook with practical, copy-paste ready examples 
   for every major API endpoint. Include request/response examples, 
   error handling, and rate limiting information.
   ```
4. Rename the "how_to" file to:
   ```
   api-cookbook
   ```
5. Click **Generate Documentation**

---

## What Happens Next

After you click Generate Documentation:

1. **Analysis Phase** - The AI reads through your code to understand what it does
2. **Generation Phase** - The AI writes documentation based on your selections and instructions
3. **Deployment Phase** - The documentation files are created in your configured repository and folder

When complete, you'll see a success message and can view your new documentation.

---

## Tips for Better Documentation

**Be Specific with Instructions**
- Instead of "document everything," try "document the user authentication flow with examples"
- Specific instructions produce more focused, useful documentation

**Start Small**
- On your first run, select just one or two content types
- See what the AI generates, then expand from there

**Use Meaningful File Names**
- Rename files to match what users will look for
- "getting-started.md" is clearer than "intro.md"

**Select Relevant Repositories**
- If creating user documentation, you might skip internal tool repositories
- For developer docs, include all repositories

**Review the Configuration**
- Make sure the documentation repository and folder are set correctly in Product Information
- This determines where your files will be saved

---

## Common Questions

**How long does generation take?**
Usually 3-10 minutes depending on code size and scope selections.

**Can I run it again?**
Yes! You can generate documentation as many times as needed. The AI will update existing files or create new ones based on your configuration.

**What if I want to change something?**
Simply open the Documentation panel again, adjust your selections or instructions, and click Generate Documentation to create updated files.

**Can I generate just one specific file?**
Yes! Select only the scope and content type for that file, add focused instructions, and name the file specifically.

**What format is the documentation?**
All documentation is created in Markdown (.md) format, which is readable as plain text and can be rendered beautifully by documentation platforms.

---

## Next Steps

After generating your documentation:
1. Review the created files in your repository
2. Share them with your team or users
3. Set up automated regeneration when code changes
4. Expand to additional documentation types as needed

Your documentation is now ready to help users and developers understand and work with your project!