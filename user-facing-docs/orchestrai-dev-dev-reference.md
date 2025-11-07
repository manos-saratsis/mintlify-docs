I'll analyze the source code to create a comprehensive, user-friendly how-to guide for generating documentation with OrchestrAI.

<readme>

<think>
Let me analyze the provided source code to understand how documentation generation works in OrchestrAI:

1. From `AIDocumentationSpecialistPanel.tsx`:
   - Two modes: 'migrate' (existing docs) and 'create' (from scratch)
   - Requires documentation URL for migration
   - User can select scopes: user-facing, internal developer, SBOM
   - User-facing content structure options: intro, tutorials, how-to, reference, concepts, troubleshooting, release notes
   - Custom instructions take priority over default settings
   - Repository selection with full repo or specific commit scope
   - Files generated as markdown (.md)
   - Configuration needed: repository and folder settings
   - Process: Product Analysis → Documentation Review (if migrate) → Structured Generation → Code Deployment

2. From the workflow and panel logic:
   - Uses AI Documentation Specialist
   - Generates documentation in configured repository folder
   - For migration, creates docs in "migrated-docs" folder
   - Requires workspace credits
   - Progress tracked with checkpoints
   - Results deployed to repository

3. Key user actions:
   - Select documentation scope
   - Choose content structure
   - Provide custom instructions
   - Select source repositories
   - Generate and deploy

Now I'll create a user-friendly how-to guide without technical jargon.
</think>

</readme>

<artifact type="user-facing-docs" language="markdown" title="orchestrai-dev-generate-documentation-guide.md">
# How to Generate Documentation with OrchestrAI

This guide walks you through creating product documentation from scratch using OrchestrAI's AI Documentation Specialist.

## Before You Start

You'll need:
- A documentation repository configured (where your docs will be saved)
- At least one code repository enabled in your workspace
- Available credits in your account

> **Note:** If you haven't set up your documentation repository yet, visit the Product Information page first to configure where your documentation should be created.

## Step 1: Open the Documentation Specialist

1. Navigate to the Documentation section
2. Click the **"Create New Documentation"** button
3. The AI Documentation Specialist panel will open on the right side of your screen

## Step 2: Choose What Documentation to Create

### Select Your Documentation Scope

You can generate three types of documentation. Check the boxes for what you need:

**User Facing Documentation** (recommended to start)
- This creates documentation for your end users and customers
- Most commonly needed for product launches

**Internal Developer Documentation**
- Technical documentation for your development team
- Includes architecture and setup guides

**SBOM (Software Bill of Materials)**
- Automatically generates a list of all software components
- Available in CycloneDX and SPDX formats

> **Getting Started Tip:** If you're creating documentation for the first time, start with just "User Facing Documentation" selected. You can always generate the other types later.

## Step 3: Choose Your Content Structure (User Facing Only)

When you select User Facing Documentation, you'll see options to customize what pages get created. Here's what each section means:

### Essential Pages (Recommended)

**Quickstart / Introduction**
- The first page users see
- Explains what your product does and how to get started quickly
- **File created:** `intro.md`

**Tutorials**
- Complete, step-by-step walkthroughs
- Shows users how to accomplish real goals with your product
- **File created:** `tutorials.md`

**API Reference**
- Technical reference for developers using your product
- Automatically generated from your code
- **File created:** `reference.md`

### Optional Pages

**How-To Guides**
- Short, task-focused instructions
- Answers specific "how do I...?" questions
- **File created:** `how_to.md`

**Concepts**
- Explains how your product works under the hood
- Describes architecture, models, and key ideas
- **File created:** `concepts.md`

**Troubleshooting**
- Common errors and how to fix them
- Helpful for reducing support requests
- **File created:** `troubleshooting.md`

**Release Notes**
- Automatically tracks what's new in each version
- **File created:** `release_notes.md`

> **Recommendation:** For a complete documentation set, select at minimum: Quickstart, Tutorials, and API Reference. You can always add more sections later.

## Step 4: Write Custom Instructions

In the "Additional Instructions" box, tell the AI what's special about your documentation needs.

### Examples of Good Instructions

**For a developer tool:**
```
Focus on code examples and API usage. Include authentication steps 
in the quickstart. Make tutorials show real-world integration scenarios.
```

**For a SaaS product:**
```
Write for non-technical users. Use simple language. Include screenshots 
descriptions. Focus on business benefits in the intro.
```

**For a specific feature launch:**
```
Emphasize the new payment processing feature. Include migration 
steps for existing users. Add troubleshooting for common payment errors.
```

> **Pro Tip:** These custom instructions take priority over your default workspace settings. Be specific about what makes your product unique and what your users need to know.

## Step 5: Customize Filenames (Optional)

The AI will create markdown files with default names. You can change these:

1. Expand the "Configuration" section
2. Find the "Files to be generated" list
3. Click on any filename to edit it
4. The `.md` extension is added automatically

**Example:** Change `intro` to `getting-started` if that fits your style better.

## Step 6: Select Which Code to Document

### Choose Your Source Repositories

Expand the "Select Code Scope" section to see your available repositories.

You have two options for each repository:

**Whole Repo** (recommended for initial documentation)
- Analyzes your entire codebase
- Creates comprehensive documentation
- Best for first-time documentation generation

**Specific Commit**
- Documents only changes in a particular commit
- Useful for updating docs after specific features
- Click to see recent commits and select one

> **Default Behavior:** All your enabled repositories are pre-selected with "Whole Repo" mode. This is perfect for getting started.

## Step 7: Generate Your Documentation

1. Review your selections:
   - Documentation scope (User Facing, Internal, SBOM)
   - Content structure (which pages)
   - Custom instructions
   - Source repositories

2. Click the **"Generate Documentation"** button at the bottom

3. A progress window will appear showing:
   - Current step being processed
   - Estimated time remaining
   - Real-time status updates

The generation process typically takes 5-15 minutes depending on your code size and selected documentation scope.

## Step 8: Monitor Progress

While the AI works, you'll see updates like:

- "Analyzing product functionality..."
- "Creating Quickstart documentation..."
- "Generating tutorials..."
- "Writing API reference..."
- "Preparing deployment..."

> **Can I Close the Window?** Yes! The generation continues in the background. You can check progress by reopening the Documentation Specialist panel.

## Step 9: Deploy Your Documentation

Once generation is complete:

1. You'll see a success notification
2. Click **"View Results"** to review your new documentation
3. Your documentation is automatically committed to your configured repository

Your documentation files will be in the folder you specified in your configuration settings.

## Understanding File Organization

Your generated documentation follows this structure:

```
/your-docs-folder/
  ├── intro.md              (Quickstart/Introduction)
  ├── tutorials.md          (Complete walkthroughs)
  ├── reference.md          (API documentation)
  ├── how_to.md            (Task guides)
  ├── concepts.md          (Technical explanations)
  ├── troubleshooting.md   (Error solutions)
  └── release_notes.md     (Version history)
```

If you selected Internal Developer documentation:
```
/your-docs-folder/
  ├── architecture.md       (System design)
  ├── development-setup.md  (Getting dev environment running)
  └── overview.md          (Developer onboarding)
```

## Creating Custom Documentation Files

Want to create documentation that doesn't fit the standard structure? Use custom instructions:

### Example: Adding a Security Documentation Page

In the Additional Instructions field, add:
```
Create an additional security.md file that documents:
- Authentication methods
- Authorization policies  
- Data encryption practices
- Security best practices for users
```

### Example: Creating Industry-Specific Documentation

```
Generate a compliance.md file covering:
- HIPAA compliance features
- Data privacy controls
- Audit trail capabilities
- Required configurations for healthcare use
```

The AI will create these custom files alongside your standard documentation.

## Tips for Great Documentation

### Write Clear Instructions

❌ **Too vague:** "Make it good"

✅ **Better:** "Focus on beginners. Include visual descriptions. Explain technical terms in simple language."

### Start Simple, Expand Later

Your first documentation run should focus on essentials:
- Quickstart (how to get started)
- Tutorials (accomplish key tasks)
- API Reference (technical details)

Add advanced sections like Concepts and Troubleshooting once you have the basics in place.

### Use Specific Examples in Instructions

Instead of: "Include code examples"

Try: "Include code examples in Python and JavaScript for all API endpoints. Show both successful responses and error handling."

### Update Documentation Regularly

When you make product changes:
1. Use "Specific Commit" mode
2. Select the commit with your changes
3. The AI updates only affected documentation sections

## Troubleshooting Common Issues

### "Configuration Required" Error

**Solution:** Visit the Product Information page and set up:
- Which repository should contain your documentation
- Which folder inside that repository

### "Select at Least One Scope" Error

**Solution:** Check at least one box under Documentation Scope (User Facing, Internal Developer, or SBOM)

### "No Permission" Message

**Solution:** Contact your workspace administrator to grant you documentation generation permissions

### Documentation Takes Too Long

**Expected:** 5-15 minutes is normal for comprehensive documentation

**If longer:** Check your code repository size. Very large repositories take more time to analyze.

### Generated Documentation Needs Changes

After generation, you can:
1. Edit files directly in your repository
2. Run generation again with more specific custom instructions
3. Generate additional sections to supplement existing docs

## Next Steps

After generating your documentation:

1. **Review the Content:** Read through the generated documentation to ensure accuracy

2. **Customize Further:** Make manual edits to add company-specific information, branding, or examples

3. **Set Up Hosting:** Deploy your documentation to your preferred hosting platform (your docs are standard markdown files)

4. **Keep It Updated:** Re-run documentation generation when you release new features or make significant changes

5. **Gather Feedback:** Share with your team and users, then refine with better custom instructions

## Need Help?

- **Credit Limits:** If you see a credit limit message, visit your Account page to upgrade your plan
- **Configuration Issues:** Check the Product Information page for documentation repository settings  
- **Permission Problems:** Contact your workspace administrator
- **Questions About Results:** Review your custom instructions and try being more specific about what you need

---

**Remember:** Good documentation takes iteration. Your first generation provides a solid foundation, and you can refine it over time with more specific instructions and manual edits.
</artifact>