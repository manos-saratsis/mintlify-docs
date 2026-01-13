I'll read the specified files first to understand the GitHub integration implementation.# How to Use GitHub Integration

Connect your documentation to GitHub to enable automatic publishing, version control, and seamless content management. This guide walks you through connecting GitHub to your documentation site and managing that connection.

## What You Get with GitHub Integration

When you connect GitHub to your documentation, you'll have:

- **Automatic Publishing**: Changes you push to GitHub appear on your live site within minutes
- **Version Control**: Track all changes to your documentation over time
- **Team Collaboration**: Multiple people can contribute through GitHub
- **Branch Management**: Choose which branch (like main or production) triggers updates
- **No Manual Deployment**: Just save files and push to GitHub - no commands needed

## Before You Begin

Make sure you have:

- A GitHub account (free or paid)
- A repository containing your documentation files
- Write access to that repository (you need to be able to install apps)
- The `docs.json` file and your content files in the repository

## Connecting GitHub to Your Documentation

### Step 1: Access the Dashboard

1. Open your web browser and go to `dashboard.mintlify.com`
2. Sign in with your account credentials
3. Look for the Settings or Organization section in the menu

### Step 2: Install the GitHub App

1. Navigate to the GitHub App settings page at `dashboard.mintlify.com/settings/organization/github-app`
2. Click the button to install the GitHub app
3. You'll be redirected to GitHub to authorize the connection

### Step 3: Authorize on GitHub

When GitHub opens:

1. Choose whether to install the app for:
   - All repositories in your account (easiest if you have multiple documentation projects)
   - Only specific repositories (more secure if you only want to connect certain projects)

2. Review the permissions the app requests:
   - Read access to your repository contents (to read your documentation files)
   - Read access to metadata (to understand your repository structure)
   - Write access to checks (to report publishing status)

3. Click "Install" or "Authorize" to complete the connection

### Step 4: Select Your Repository

After authorization, you'll return to the dashboard:

1. Select your documentation repository from the list
2. Choose which branch should trigger automatic updates (typically "main" or "master")
3. Save your settings

## Understanding GitHub Permissions

### What Access the Integration Needs

The GitHub integration requires specific permissions to work correctly:

**Repository Contents** (Read): 
- Reads your documentation files when you push changes
- Accesses the `docs.json` configuration
- Retrieves images and other assets

**Repository Metadata** (Read):
- Understands your repository structure
- Tracks which branch you're working on
- Monitors for updates

**Checks** (Write):
- Reports whether publishing succeeded or failed
- Shows status updates in your GitHub commits
- Provides feedback on build progress

### Managing Access for Organizations

If your repository belongs to a GitHub organization:

1. Organization owners need to approve the app installation
2. You may need to request access if you're not an owner
3. Some organizations require administrator approval for new apps

**To request approval:**
1. Start the installation process
2. GitHub shows a message that approval is required
3. The organization owner receives a notification
4. Once approved, you can complete the setup

## How Automatic Publishing Works

### The Publishing Process

After connecting GitHub, publishing happens automatically:

1. **Make Changes**: Edit your documentation files locally or on GitHub
2. **Commit**: Save your changes with a commit message describing what you changed
3. **Push to GitHub**: Send your changes to the repository
4. **Automatic Build**: The system detects your changes and starts building
5. **Live Update**: Your changes appear on the live site in 2-5 minutes

### Monitoring Publishing Status

**Check Build Status:**
- Visit your repository on GitHub
- Look at your recent commits
- You'll see a checkmark (success) or X (failure) next to each commit
- Click the status icon for details about the build

**Build Success Indicators:**
- Green checkmark next to your commit
- Changes visible on your live documentation within minutes
- No error messages in the dashboard

**Build Failure Indicators:**
- Red X next to your commit
- Changes don't appear on your live site
- Error details available when you click the status icon

## Troubleshooting GitHub Connection Issues

### The Connection Won't Authorize

**If you're redirected back without connecting:**

1. Check that you have permission to install apps in the repository:
   - Repository settings → Applications
   - Verify you can manage GitHub Apps
   - Organization owners may need to approve the installation

2. Try removing and reinstalling:
   - Go to your GitHub settings
   - Navigate to Applications → Installed GitHub Apps
   - Remove the documentation app
   - Return to the dashboard and install again

3. Check for browser issues:
   - Clear your browser cache and cookies
   - Try a different browser
   - Disable browser extensions that might block authorization

### Changes Aren't Publishing

**If you push to GitHub but nothing updates:**

1. **Verify the correct branch is connected:**
   - Check dashboard settings
   - Make sure you're pushing to the branch you selected (usually "main")
   - Pushing to other branches won't trigger builds

2. **Check build status in GitHub:**
   - Look at your commit history
   - Find any error messages on failed builds
   - Common issues include:
     - Syntax errors in `docs.json`
     - Missing files referenced in navigation
     - Incorrect file paths

3. **Review your file structure:**
   - Make sure `docs.json` is in the root of your repository
   - Verify all pages in navigation actually exist
   - Check that file names match exactly (including capitalization)

4. **Wait a few minutes:**
   - Builds typically take 2-5 minutes
   - Heavy load may cause longer delays
   - Check again after 10 minutes before troubleshooting further

### Repository Not Appearing in Dashboard

**If your repository doesn't show up when connecting:**

1. **Verify GitHub App installation:**
   - Go to GitHub settings → Applications → Installed GitHub Apps
   - Confirm the documentation app is installed
   - Check it has access to your repository

2. **Check repository access:**
   - Make sure you have write access to the repository
   - Private repositories require appropriate permissions
   - Organization repositories need organization-level app approval

3. **Refresh the connection:**
   - Remove the GitHub App installation
   - Clear your browser cache
   - Reinstall the app and authorize again

### Publishing Status Shows Errors

**Common error messages and solutions:**

**"Configuration Error":**
- Open your `docs.json` file
- Check for syntax errors (missing commas, brackets)
- Validate the JSON format using a JSON validator
- Fix any formatting issues and push again

**"Page Not Found":**
- Review your navigation in `docs.json`
- Verify all page names match actual file names (without .md extension)
- Check file paths match folder structure
- Fix references and push again

**"Build Timeout":**
- Your documentation may be very large
- Try breaking large files into smaller ones
- Remove unnecessary images or assets
- Push smaller changes more frequently

**"Authorization Failed":**
- Reauthorize the GitHub App
- Check that app permissions haven't been revoked
- Verify your GitHub account still has repository access
- Reinstall the app if necessary

## Managing Your GitHub Connection

### Checking Connection Status

To verify your GitHub connection is working:

1. Go to the dashboard at `dashboard.mintlify.com`
2. Navigate to Settings → GitHub
3. Look for:
   - Connected repository name
   - Connected branch
   - Last successful build time
   - Recent build history

### Changing Connected Repository

To switch to a different repository:

1. Go to Settings → GitHub in the dashboard
2. Click to disconnect the current repository
3. Follow the connection process again with the new repository
4. Select the new repository and branch

### Changing the Active Branch

To publish from a different branch:

1. Go to Settings → GitHub in the dashboard
2. Find the branch selection
3. Choose a different branch from the dropdown
4. Save your changes
5. Future pushes to the new branch will trigger builds

### Disconnecting GitHub

To remove the GitHub integration:

1. Go to Settings → GitHub in the dashboard
2. Click "Disconnect" or "Remove GitHub Integration"
3. Optionally, uninstall the GitHub App:
   - Go to GitHub settings → Applications
   - Find the documentation app
   - Click "Uninstall"

**After disconnecting:**
- Automatic publishing stops
- Your live site remains as-is
- You'll need to publish manually or reconnect to enable automatic updates

## Working with Multiple Team Members

### Collaborative Documentation Workflow

When multiple people contribute to documentation through GitHub:

**Recommended Workflow:**

1. Each team member clones the repository to their computer
2. Create a new branch for significant changes:
   - `git checkout -b update-api-docs`
3. Make and commit changes on the branch
4. Push the branch to GitHub
5. Open a pull request for review
6. After approval, merge to the main branch
7. Automatic publishing updates the live site

**Benefits of This Approach:**
- Changes are reviewed before going live
- Multiple people can work simultaneously without conflicts
- You maintain a clean history of all changes
- Mistakes can be caught before publishing

### Managing Permissions

**Who needs what access:**

**Documentation Writers:**
- Read and write access to the repository
- Ability to create branches
- Ability to open pull requests

**Reviewers:**
- Read access to the repository
- Ability to review and approve pull requests
- Ability to merge approved changes

**GitHub App Managers:**
- Organization owner or admin status
- Ability to manage GitHub App installations
- Access to the documentation dashboard

## Understanding the Build Process

### What Happens After You Push

When you push changes to GitHub:

1. **Detection** (immediate):
   - GitHub notifies the documentation system
   - The system queues your build

2. **Validation** (5-10 seconds):
   - Checks that `docs.json` is valid
   - Verifies all referenced files exist
   - Confirms navigation structure is correct

3. **Building** (1-3 minutes):
   - Processes all markdown files
   - Generates navigation
   - Applies your styling and branding
   - Creates optimized versions of images

4. **Deployment** (30-60 seconds):
   - Uploads the new version
   - Updates the live site
   - Clears caches so changes appear immediately

5. **Verification** (5-10 seconds):
   - Confirms the new version is live
   - Reports success status to GitHub
   - Updates the dashboard

**Total Time:** Typically 2-5 minutes from push to live site

### Viewing Build Logs

To see detailed information about a build:

1. Go to your GitHub repository
2. Click on the "Commits" section
3. Find your recent commit
4. Click the status icon (checkmark or X)
5. View the detailed build log

The log shows:
- Which files were processed
- Any warnings or errors encountered
- Build duration
- Success or failure status

## Best Practices for GitHub Integration

### Commit Messages

Write clear commit messages that explain what changed:

**Good examples:**
- "Add OAuth integration guide"
- "Update API endpoint documentation"
- "Fix typo in getting started guide"

**Avoid:**
- "Update"
- "Changes"
- "Fix stuff"

Clear messages help you track changes and understand what each build includes.

### Testing Before Pushing

Before pushing to the branch connected to your live site:

1. Preview changes locally using `mint dev`
2. Check that all links work
3. Verify images display correctly
4. Test code examples
5. Review for typos and formatting

This prevents publishing broken or incomplete content.

### Branch Strategy

**Recommended approach:**

- **Main branch**: Connected to live site, always deployable
- **Development branch**: For testing and staging changes
- **Feature branches**: For specific updates or new content

Make changes on feature branches, test on development, then merge to main for publishing.

### Handling Urgent Fixes

For critical errors on your live site:

1. Make the fix on a new branch
2. Test quickly but thoroughly
3. Open a pull request
4. Review (even if brief)
5. Merge to main
6. Changes go live in 2-5 minutes

The automatic publishing enables quick fixes when needed.

## Repository Organization Tips

### Recommended Folder Structure

Organize your repository for easy management:

```
your-documentation-repo/
├── docs.json (configuration)
├── favicon.svg (site icon)
├── logo/
│   ├── light.svg
│   └── dark.svg
├── getting-started/
│   ├── introduction.md
│   └── quickstart.md
├── guides/
│   ├── feature-one.md
│   └── feature-two.md
├── api-reference/
│   ├── openapi.json
│   └── authentication.md
└── images/
    ├── screenshot-1.png
    └── diagram-1.svg
```

### File Naming Conventions

**Use consistent naming:**
- Lowercase file names: `getting-started.md` not `Getting-Started.md`
- Hyphens instead of spaces: `api-guide.md` not `api guide.md`
- Descriptive names: `oauth-setup.md` not `doc3.md`

This prevents issues with case sensitivity and makes files easier to find.

### Managing Images and Assets

**Store images efficiently:**
- Keep images in an `images` folder
- Use descriptive file names
- Reference them consistently: `![Description](/images/screenshot-1.png)`
- Optimize image sizes before committing (keep under 200KB when possible)

## Getting Help

### If You're Still Having Issues

**Check these resources:**

1. **Build status in GitHub**: Most helpful for diagnosing why builds fail
2. **Dashboard notifications**: Shows recent activity and any alerts
3. **Your commit history**: Compare working builds to failing builds

**Getting Support:**

If you can't resolve an issue:

1. Note the specific error message
2. Identify when the problem started
3. Check if recent changes might have caused it
4. Contact support with:
   - Your repository name
   - The commit SHA where the problem occurs
   - Any error messages you see
   - What you've already tried

The GitHub integration makes publishing documentation automatic and reliable. Once connected, you can focus on writing great documentation while the system handles deployment.