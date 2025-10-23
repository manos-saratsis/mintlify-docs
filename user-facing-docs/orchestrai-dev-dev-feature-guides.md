I'll analyze the provided source code to generate comprehensive, user-friendly feature guides for OrchestrAI.

<analysis>
The codebase shows:
1. AI Compliance Analyst Panel - for compliance analysis of repositories
2. AI Documentation Specialist Panel - for generating/migrating documentation
3. Various configuration options, permission checks, and workflow settings
4. Integration with GitHub repositories
5. Progress dialogs and checkpoint/resume functionality
</analysis>

# OrchestrAI Feature Guides

## Compliance Analysis

### Getting Started with Compliance Analysis

**What is Compliance Analysis?**

Compliance analysis helps ensure your code meets regulatory requirements and follows best practices for data privacy, security, and access control. The AI Compliance Analyst automatically reviews your repositories and identifies potential compliance issues.

**Before You Begin**

Make sure compliance analysis is enabled for your workspace. If you see a message saying "Compliance Disabled," ask your workspace administrator to enable it in the Workflow settings.

---

### Running a Compliance Analysis

**Step 1: Open the Compliance Panel**

When viewing your repositories, look for the Compliance option. Click on it to open the AI Compliance Analyst panel on the right side of your screen.

**Step 2: Select Your Repository**

The panel will show information about the repository you're analyzing, including:
- Repository name
- Full path
- Whether it's public or private

**Step 3: Add Custom Instructions (Optional)**

You'll see a text box with default instructions. You can customize these to focus on specific compliance areas:
- Data privacy requirements
- Access control policies
- Encryption standards
- Audit trail requirements

**Step 4: Start the Analysis**

Click the purple "Start Analysis" button at the bottom of the panel. The AI will begin examining your code for compliance issues.

**What Happens During Analysis**

The system will:
1. Review your code for compliance patterns
2. Check for data protection measures
3. Analyze access control implementations
4. Verify encryption usage
5. Generate a comprehensive report

You'll see a progress indicator showing the analysis is underway. This typically takes a few minutes depending on repository size.

**Step 5: View Results**

Once complete, you'll see a success message and a "View Results" button. Click it to see:
- Compliance score
- List of issues found
- Recommendations for improvements
- Detailed findings by category

---

### Understanding Your Results

**Compliance Score**

Your repository receives an overall compliance score. Higher scores indicate better compliance with standards.

**Issues and Recommendations**

The report categorizes findings into:
- **Critical**: Must be addressed immediately
- **Warnings**: Should be reviewed and fixed
- **Suggestions**: Optional improvements

Each issue includes:
- What was found
- Why it matters
- How to fix it
- Relevant code locations

---

### What to Do If Analysis Fails

**Permission Issues**

If you see "You do not have the right permissions," contact your workspace administrator to grant you compliance analysis permissions.

**Configuration Issues**

If compliance is disabled, your administrator needs to:
1. Go to Workflow settings
2. Find the Compliance section
3. Enable analysis

**Technical Errors**

If the analysis fails unexpectedly:
1. Check your internet connection
2. Verify the repository is accessible
3. Try again in a few minutes
4. Contact support if the issue persists

---

## Documentation Generation

### Understanding Documentation Generation

**Two Ways to Create Documentation**

OrchestrAI offers two approaches:

1. **Create New Documentation**: The AI analyzes your product directly and writes documentation from scratch
2. **Migrate Existing Documentation**: The AI reviews your current documentation and restructures it following best practices

---

### Creating New Documentation

**When to Use This**

Choose this option when:
- You're starting fresh with no existing documentation
- Your current documentation is incomplete
- You want the AI to analyze your product directly

**Step 1: Open the Documentation Panel**

From the Documentation page, click "Create Documentation." The AI Documentation Specialist panel opens on the right side.

**Step 2: Customize Your Instructions**

In the instructions box, describe what you want the documentation to cover. The AI will prioritize these instructions over default settings.

Example instructions:
- "Focus on getting started guides for new users"
- "Include detailed API reference sections"
- "Emphasize troubleshooting and common issues"

**Step 3: Choose Documentation Scope**

Click "Customize Scope & Content Structure" to select what types of documentation to generate:

**Documentation Types:**
- **User Facing**: Documentation for end users of your product
- **Internal Developer**: Technical documentation for your development team
- **SBOM**: Software Bill of Materials listing all components

**Content Structure (for User Facing):**
- **/intro**: Quick start guides to get users up and running
- **/tutorials**: Step-by-step walkthroughs for complete workflows
- **/how-to**: Short, task-focused guides
- **/reference**: Detailed API and SDK documentation
- **/concepts**: Explanations of architecture and key ideas
- **/troubleshooting**: Help for common problems
- **/release-notes**: What's new in each version

Select the sections most relevant to your needs.

**Step 4: Select Repositories**

If you have multiple code repositories, you can choose which ones to document:

**Whole Repository**: Document the entire codebase
**Specific Commit**: Document changes from a particular update

To select specific commits:
1. Choose a repository
2. Click "Specific Commit"
3. Pick from the list of recent updates
4. The AI will focus on changes in that commit

**Step 5: Generate Documentation**

Click the purple "Generate Documentation" button. The AI will:
1. Analyze your product functionality
2. Study your code repositories
3. Create structured documentation
4. Save it to your configured documentation repository

**Monitoring Progress**

A progress window shows what's happening:
- "Analyzing product..." - Understanding your product
- "Generating content..." - Writing documentation
- "Creating files..." - Saving documentation

This process can take 10-30 minutes depending on complexity.

---

### Migrating Existing Documentation

**When to Use This**

Choose this option when:
- You have existing documentation that needs reorganization
- You want to adopt a standard documentation structure
- Your current documentation is scattered or inconsistent

**Requirements**

Before migrating, make sure you've added your documentation URL in Product Information settings.

**The Migration Process**

1. Open the Documentation Specialist panel
2. Select "Migrate Documentation"
3. The AI will:
   - Review your existing documentation
   - Understand its structure and content
   - Reorganize it according to best practices
   - Apply your selected content structure
   - Preserve all important information

**What Gets Preserved**

The AI maintains:
- All technical accuracy
- Code examples
- Screenshots and images
- Important warnings and notes

**What Changes**

The AI improves:
- Document organization and hierarchy
- Navigation between topics
- Consistency in style and formatting
- Completeness of coverage

---

### Resuming Interrupted Documentation

If documentation generation stops unexpectedly, OrchestrAI can resume where it left off.

**When You See the Resume Option**

You'll notice a green notice saying "Resuming from checkpoint" - this means:
- Your previous progress was saved
- The AI will continue from that point
- Your original settings are preserved

**What's Preserved**

When resuming:
- Selected documentation scopes
- Content structure choices
- Custom instructions
- Repository selections

Simply click "Generate Documentation" again to continue.

---

### Understanding Configuration

**Repository and Folder Setup**

Documentation must be saved somewhere. Your administrator configures:
- Which repository stores documentation
- What folder within that repository
- What content structure to follow

If you see "Configuration Required," ask your administrator to set this up in Workflow settings.

**Priority of Instructions**

Instructions work in layers:
1. **Your run-specific instructions** (highest priority) - what you type in the panel
2. **Workspace configuration** - defaults set by your administrator
3. **System defaults** - OrchestrAI's built-in best practices

This means your custom instructions always take precedence.

---

### Tips for Great Documentation

**Be Specific in Instructions**

Instead of: "Create documentation"
Try: "Create beginner-friendly guides with lots of examples"

**Choose Relevant Sections**

Don't select everything - focus on what your users actually need. New products might need more tutorials; mature products might need better reference documentation.

**Use Specific Commits for Updates**

When documenting new features, select the specific commit that added them. This creates targeted, accurate documentation for just those changes.

**Review and Refine**

After generation:
1. Review the created documentation
2. Test the examples
3. Have team members read it
4. Generate again with refined instructions if needed

---

### Common Questions

**How long does documentation generation take?**

Typically 10-30 minutes, depending on:
- How much code you're documenting
- How many sections you selected
- Whether you're creating or migrating

**Can I edit the documentation after generation?**

Yes! The documentation is saved as regular files in your repository. You can edit them like any other code files.

**What if I don't like the result?**

You can:
- Run generation again with different instructions
- Select different content sections
- Edit the files directly
- Mix AI-generated and manually-written documentation

**Do I need to select all content types?**

No - select only what makes sense for your product. A simple tool might only need Intro and Reference documentation.

---

### Troubleshooting

**"Configuration Required" Message**

**Problem**: No documentation repository is set up
**Solution**: Ask your administrator to configure the documentation repository in Workflow settings

**"Documentation URL Required" Message**

**Problem**: Trying to migrate without providing the current documentation location
**Solution**: Add your documentation URL in Product Information settings before migrating

**"Select at least one scope" Message**

**Problem**: No documentation types selected
**Solution**: Choose at least one type: User Facing, Internal Developer, or SBOM

**"Repository Selection Required" Message**

**Problem**: No repositories selected when repositories are available
**Solution**: Select at least one repository from the list to document

**Generation Takes Too Long**

**What's Normal**: 10-30 minutes
**If Longer**: 
- Check your internet connection
- Wait a bit longer for large projects
- Contact support if it exceeds an hour

**Generated Documentation is Incomplete**

**Possible Causes**:
- Instructions were too narrow
- Not all relevant repositories selected
- Some content sections weren't chosen

**Solutions**:
- Broaden your instructions
- Select additional repositories
- Enable more content structure sections
- Run generation again

---

## General Tips

### Making the Most of AI Features

**Start Small**

When trying these features for the first time:
1. Start with one small repository
2. Review the results carefully
3. Adjust your approach
4. Scale up to larger projects

**Iterate and Improve**

Don't expect perfection on the first try:
- Run analysis or generation
- Review what worked and what didn't
- Refine your instructions
- Try again with improvements

**Collaborate with Your Team**

These tools work best when:
- Multiple team members review results
- You discuss findings together
- Everyone contributes to improving instructions
- You share what works well

### Getting Help

**Permission Issues**

Contact your workspace administrator to:
- Grant you access to features
- Enable functions in workflow settings
- Configure repositories and folders

**Technical Problems**

If something isn't working:
1. Check this guide for troubleshooting steps
2. Verify your permissions
3. Ensure settings are configured
4. Contact OrchestrAI support with specific details about what you tried

**Best Practices Questions**

For advice on how to best use these features:
- Review the tips in each section
- Experiment with different approaches
- Share experiences with your team
- Reach out to support for guidance

---