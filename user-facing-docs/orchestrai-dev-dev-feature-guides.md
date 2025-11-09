I'll analyze the source code to create a user-friendly how-to guide for generating documentation from scratch in OrchestrAI.

<analysis>
Let me examine the key files:

1. **AIDocumentationSpecialistPanel.tsx** - This is the main component that handles documentation generation
2. The component shows:
   - Two action types: 'migrate' (existing docs) and 'create' (from scratch)
   - Scope selection: User Facing, Internal Developer, SBOM
   - Content Structure options (nested under User Facing): intro, tutorials, how-to, reference, concepts, troubleshooting, release notes
   - Repository selection with full repo or specific commit options
   - Custom filename editing for generated files
   - Instructions field for customization
   - Task explanation option

Key user flows I can identify:
1. Opening the AI Documentation Specialist panel
2. Selecting documentation scope
3. Customizing content structure
4. Adding custom instructions
5. Customizing file names
6. Generating documentation
</analysis>

# orchestrai-dev-creating-documentation-from-scratch.md

## How to Create Documentation from Scratch

This guide will walk you through creating comprehensive documentation for your product using OrchestrAI's AI Documentation Specialist. You'll learn how to customize the scope, structure, and content of your documentation to match your exact needs.

---

## Before You Begin

Make sure you have:
- Configured your documentation repository and folder in the Workflow settings
- At least one repository enabled for OrchestrAI
- Sufficient credits available in your workspace

If you see a message about "Configuration Required," click the button to set up your documentation location first.

---

## Step 1: Open the AI Documentation Specialist

1. Navigate to the Documentation page in your product
2. Look for the "Create New Documentation" option
3. Click to open the AI Documentation Specialist panel on the right side of your screen

The panel will appear with all the tools you need to customize your documentation.

---

## Step 2: Choose Your Documentation Scope

The AI can create three different types of documentation. By default, "User Facing documentation" is selected, which is perfect for most products.

### Available Scopes:

**User Facing Documentation** (Selected by default)
- Perfect for your end users and customers
- Includes tutorials, guides, and references
- This is what most people see when they visit your docs

**Internal Developer Documentation**
- For your development team
- Includes architecture and setup guides
- Keep this checked if you want docs for your engineers

**SBOM (Software Bill of Materials)**
- Technical inventory of your software components
- Required for compliance in some industries
- Generates both CycloneDX and SPDX formats

**How to select:**
1. Scroll down to the "Customize Scope & Content Structure" section
2. Click the arrow to expand it
3. Check or uncheck the boxes for each type you want

---

## Step 3: Customize Your Content Structure

When you have "User Facing documentation" selected, you can choose exactly what sections to include. Think of this as choosing which chapters go in your documentation book.

### Available Content Types:

**Quickstart / Introduction** (Recommended - Checked by default)
- The "start here" page for new users
- Gets people up and running quickly
- Every good documentation set needs this

**Tutorials** (Recommended - Checked by default)
- Step-by-step guides from start to finish
- Shows users how to accomplish real goals
- Great for learning

**How-To Guides**
- Short, task-focused instructions
- "How do I do X?" type questions
- Practical and to the point

**API Reference** (Checked by default)
- Technical details about your APIs and SDKs
- Automatically generated from your code
- Essential for developers

**Concepts**
- Explains how your product works
- Covers architecture and key ideas
- Helps users understand the "why"

**Troubleshooting**
- Common problems and solutions
- Error messages explained
- Helps users help themselves

**Release Notes**
- What's new in each version
- Automatically generated from your updates
- Keeps users informed

**How to customize:**
1. In the "Customize Scope & Content Structure" section
2. Look under "User Facing documentation"
3. Check or uncheck each content type you want
4. The AI will only create the sections you select

---

## Step 4: Select Which Code to Analyze

The AI needs to look at your code to understand what to document. You can choose which repositories to analyze and even focus on specific recent changes.

### Choosing Repositories:

1. Scroll to the "Select Code Scope" section
2. Click to expand it
3. You'll see all your OrchestrAI-enabled repositories
4. By default, all are selected - uncheck any you don't want included

### Whole Repo vs. Specific Commit:

For each repository, you can choose:

**Whole Repo** (Default)
- Analyzes the entire codebase
- Best for comprehensive documentation
- Takes longer but covers everything

**Specific Commit**
- Focuses on recent changes
- Perfect for updating docs after a specific feature
- Much faster for targeted updates

**To use specific commits:**
1. Click the "Specific Commit" button for a repository
2. Wait for the list of recent commits to load
3. Click on the commit you want to focus on
4. You'll see it highlighted in blue

---

## Step 5: Add Custom Instructions

This is where you can tell the AI exactly what you want. These instructions are incredibly powerful and take priority over everything else.

### What to Include in Your Instructions:

**Be Specific About:**
- Special terminology your product uses
- The tone you want (friendly, technical, formal)
- Specific features to emphasize or skip
- Your target audience (beginners, experts, etc.)

**Example Instructions:**

*For a friendly approach:*
"Use a conversational, welcoming tone. Explain technical concepts in simple terms. Include lots of examples and assume users are new to this type of product."

*For technical documentation:*
"Write for experienced developers. Include code examples in Python and JavaScript. Focus on advanced features and best practices."

*For specific features:*
"Emphasize our new payment integration feature. Include step-by-step setup instructions and common troubleshooting tips. Use real-world e-commerce examples."

**How to add instructions:**
1. Find the "Additional Instructions" box
2. Type or paste your instructions
3. You'll see a purple "Priority" badge - this means your instructions override defaults

### Optional: Task Explanation

If you want to see notes about what the AI did at the top of each file:
1. Check the box "Add documentation task explanation at the top of the file"
2. This helps you understand the AI's approach
3. You can remove these notes before publishing

---

## Step 6: Customize File Names (Optional)

Each documentation file gets a default name, but you can change them to match your preferences.

**Default file naming:**
- intro → intro.md
- tutorials → tutorials.md
- how_to → how_to.md
- reference → reference.md

**How to change file names:**
1. Scroll to the "Configuration" section
2. Look for "Files to be generated"
3. Click on any filename
4. Type your preferred name
5. The ".md" extension is added automatically

**Example customizations:**
- Change "intro" to "getting-started"
- Change "tutorials" to "learn"
- Change "reference" to "api-docs"

---

## Step 7: Generate Your Documentation

Once you've customized everything, you're ready to create your documentation!

**What happens when you click Generate:**
1. The AI analyzes your selected repositories
2. It reviews your product to understand functionality
3. It creates documentation following your structure
4. The files are committed to your documentation repository

**To start generation:**
1. Review your selections one more time
2. Make sure you have enough credits (check the top of the panel)
3. Click the purple "Generate Documentation" button at the bottom
4. A progress dialog will appear showing the AI's work

**During generation:**
- Don't close your browser
- You'll see status updates as the AI works
- This can take several minutes depending on your code size
- Checkpoints are saved automatically in case of interruption

**When it's complete:**
- You'll see a success message
- Your documentation is committed to your repository
- You can view the results immediately

---

## Tips for Best Results

**Start Simple:**
- For your first time, use the default selections
- Add customizations as you learn what works

**Be Clear in Instructions:**
- The more specific you are, the better the results
- Include examples of what you want
- Mention what to avoid

**Use Specific Commits for Updates:**
- When you add a new feature, use "Specific Commit"
- This updates only the relevant documentation
- Saves time and credits

**Choose the Right Content Structure:**
- Not sure? Start with just Intro, Tutorials, and Reference
- You can always generate more sections later

**Review Generated Files:**
- The AI does great work, but always review before publishing
- Make minor adjustments to match your voice
- Add any missing details you notice

---

## Common Questions

**Can I generate documentation multiple times?**
Yes! You can run the AI as many times as you want. Each run creates fresh documentation based on your current settings.

**What if I only want to add one new section?**
Uncheck all content types except the one you want, then generate. The AI will only create that specific section.

**Do I need to select all my repositories?**
No - only select repositories that are relevant to your documentation. For example, if documenting your API, just select the API repository.

**Can I edit the documentation after it's generated?**
Absolutely! The generated files are markdown files in your repository. Edit them however you like.

**What happens if generation is interrupted?**
The AI saves checkpoints automatically. You can resume from where it left off without starting over.

---

## Next Steps

After generating your documentation:
1. Review the files in your documentation repository
2. Make any minor edits needed
3. Set up your documentation site to display the new files
4. Share with your users!

Remember: You can always regenerate or add new sections as your product evolves. The AI Documentation Specialist grows with your product.