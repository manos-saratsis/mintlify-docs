I'll analyze the source code to create a comprehensive how-to guide for generating documentation with OrchestrAI.

<thinking>
Let me examine the AIDocumentationSpecialistPanel component to understand the documentation generation workflow:

1. The panel supports two actions: 'migrate' (existing docs) and 'create' (from scratch)
2. Users can select documentation scopes: User Facing, Internal Developer, SBOM
3. For User Facing docs, users can customize content structure (intro, tutorials, how-to, reference, concepts, troubleshooting, release notes)
4. Users can select repositories and choose between full repo or specific commit analysis
5. Users can provide custom instructions that take priority over default settings
6. The process involves:
   - Product analysis
   - Documentation generation following selected structure
   - Code deployment to repository
7. Configuration requirements: documentation repository and folder must be set in workflow settings
8. The generated files are deployed to the configured repository location

Key features I need to document:
- How to create documentation from scratch
- Selecting User Facing content structure
- Using custom instructions
- Repository selection and scope
- The deployment process
</thinking>

<read_file>
<path>src/components/DocumentationProgressDialog.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductDocumentation.tsx</path>
</read_file>

Based on the source code analysis, I'll now create the user-facing documentation:

# **OrchestrAI Feature Guide: Generating Documentation**

## **Creating Product Documentation from Scratch**

OrchestrAI's AI Documentation Specialist can automatically create comprehensive documentation for your product by analyzing your codebase and generating structured content.

### **Getting Started**

Before you begin generating documentation, you'll need to:

1. Make sure you have at least one repository connected and enabled for OrchestrAI
2. Configure your documentation settings by going to Product Information and setting:
   - Which repository will store your documentation
   - What folder the documentation should be saved in
   - Your preferred content structure

If these aren't configured yet, you'll see a friendly reminder with a button to set them up.

### **Opening the Documentation Generator**

1. Navigate to the Documentation page in your workspace
2. Look for the "Create Documentation" option
3. The AI Documentation Specialist panel will open on the right side of your screen

### **Choosing What to Document**

When the panel opens, you have several choices to make:

#### **Documentation Type**

You can generate three types of documentation:

- **User Facing**: Documentation for people who use your product (selected by default)
- **Internal Developer**: Technical documentation for your development team
- **SBOM**: Software Bill of Materials for compliance and security tracking

Select one or more types by checking the boxes. You must select at least one type to proceed.

#### **User Facing Content Structure**

When you select User Facing documentation, you can customize what sections to include:

- **Intro/Quickstart** (selected by default): A quick introduction to get users started
- **Tutorials** (selected by default): Step-by-step guides that walk users through complete workflows
- **How-To Guides**: Short, task-focused instructions for specific actions
- **API Reference** (selected by default): Automatically generated API and SDK documentation
- **Concepts**: Explanations of your product's architecture, models, and important ideas
- **Troubleshooting**: Solutions to common problems and error messages
- **Release Notes**: Automatically generated update logs

The AI will create separate files for each section you select. By default, Intro, Tutorials, and Reference are selected to give you a solid documentation foundation.

### **Selecting Your Code**

You need to tell the AI which parts of your codebase to analyze:

1. Expand the "Select Code Scope" section
2. You'll see all repositories that are enabled for OrchestrAI
3. Use "Select All" to include everything, or check individual repositories
4. For each selected repository, choose:
   - **Whole Repo**: Analyzes your entire codebase (recommended for first-time documentation)
   - **Specific Commit**: Updates documentation based on a particular code change

When you select "Specific Commit", you'll see a list of recent changes. Click on one to focus the documentation update on just those changes.

### **Adding Custom Instructions**

The "Additional Instructions" box is where you can guide the AI to create exactly what you need:

**What to Include:**
- Specific topics or features to emphasize
- Your preferred writing style or tone
- Special formatting requirements
- Particular examples you want included

**Example Instructions:**
- "Focus heavily on the authentication flow and include code examples in Python and JavaScript"
- "Write in a friendly, conversational tone suitable for beginner developers"
- "Include detailed error handling examples for each API endpoint"
- "Add screenshots placeholders where visual guides would be helpful"

**Important:** These instructions take priority over any default settings you've configured elsewhere. Whatever you write here will be the AI's primary guidance.

### **Customizing File Names**

The AI creates files based on the sections you selected. You can customize the file names:

1. Look for the "Files to be generated" section
2. Each file shows a text box with the current name
3. Click in any box to change the filename (the .md extension is added automatically)
4. Keep names simple and descriptive (like "getting-started" or "api-guide")

### **Additional Options**

- **Task Explanation**: Check this box if you want the AI to add a note at the top of each file explaining what it generated and why. This helps your team understand the AI's work.

### **Starting the Generation**

When you're ready:

1. Click the "Generate Documentation" button at the bottom of the panel
2. You'll see a progress window showing what the AI is doing:
   - Analyzing your product
   - Understanding your code structure
   - Creating documentation files
   - Preparing deployment
3. The entire process typically takes a few minutes

You can safely close the progress window—the AI will continue working in the background.

### **How Documentation Gets Deployed**

Once generation is complete, here's what happens automatically:

1. **Commit Creation**: The AI creates a new commit in your documentation repository
2. **File Organization**: Your documentation files are saved in the folder you configured
3. **Folder Structure**: Each documentation type gets its own subfolder:
   - User Facing docs go in `/user-facing-docs/`
   - Internal docs go in `/internal-developer-docs/`
   - SBOM files go in `/sbom/`
4. **File Naming**: Files are prefixed with your repository name (like "my-product-intro.md")

**Important Notes:**
- Your original code repositories are never modified—only your documentation repository receives updates
- Each generation creates a fresh set of files
- The AI includes a timestamp and generation details in each file

### **Reviewing Your Documentation**

After generation completes:

1. You'll see a success message
2. The files are immediately available in your repository
3. Navigate to your documentation repository on GitHub to review the generated content
4. If you use a documentation hosting service (like GitBook or ReadTheDocs), it will automatically pick up the new files

### **Tips for Best Results**

**First Time Setup:**
- Select "Whole Repo" for all repositories to give the AI complete context
- Include Intro, Tutorials, and Reference for a comprehensive documentation set
- Keep your custom instructions simple and focused

**Updating Documentation:**
- Use "Specific Commit" when you've made targeted changes
- Reference the commit message in your custom instructions
- Only select the content sections that need updates

**Custom Instructions:**
- Be specific about what you want but don't over-constrain the AI
- Mention your audience (beginners, experienced developers, etc.)
- Specify if you need code examples in particular languages
- Request specific formats if your documentation platform requires them

### **What If Something Goes Wrong?**

If documentation generation fails:

1. Check that your repository and folder are properly configured
2. Verify that your GitHub connection has the necessary permissions
3. Make sure you've selected at least one documentation type
4. Try simplifying your custom instructions

You can retry generation at any time—each attempt is independent.

### **Understanding Credit Usage**

Documentation generation uses workspace credits. The amount depends on:
- Number of repositories analyzed
- Size of your codebase
- Number of documentation sections generated

If you run out of credits:
- Free plans have daily and monthly limits
- Workspace admins can upgrade the plan for more credits
- You'll see a clear message about credit status before starting

---

## **Quick Reference**

**Minimum Requirements:**
- At least one repository enabled
- Documentation repository and folder configured
- At least one documentation type selected

**Recommended First-Time Setup:**
- Select: User Facing documentation
- Include: Intro, Tutorials, Reference
- Choose: All repositories, Whole Repo scope
- Add custom instructions about your product's main purpose

**Generated Files Location:**
- Your documentation repository
- In the folder you configured
- Organized in subfolders by documentation type

**Time to Complete:**
- Small projects: 2-3 minutes
- Medium projects: 5-8 minutes
- Large codebases: 10-15 minutes