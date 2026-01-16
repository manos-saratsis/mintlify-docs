I'll retrieve the key source files to document the GitHub repository connection process.# How to Connect GitHub Repositories

## Overview

Connect your GitHub account to OrchestrAI to enable automated code analysis, test engineering, and documentation generation for your repositories. This comprehensive guide covers the complete GitHub integration process, from initial setup through troubleshooting and account management.

## Before You Begin

### What You'll Need

- An active OrchestrAI account
- A GitHub account with access to repositories you want to analyze
- Admin or manager permissions in your OrchestrAI workspace
- Pop-ups enabled in your browser

### Understanding the Integration

When you connect GitHub to OrchestrAI:

- Your GitHub account links securely to your workspace
- OrchestrAI can read repository contents to perform analysis
- Repository metadata (names, descriptions, branches) becomes accessible
- All connections use encrypted OAuth tokens for security

**Important:** GitHub connections are workspace-specific. Each workspace maintains separate connections, so you can use different GitHub accounts across workspaces.

### What OrchestrAI Can Access

The integration allows OrchestrAI to:

- Read repository code for analysis and test generation
- View repository structure to understand your codebase
- Access commit history to track relevant changes
- Read file contents to identify testing opportunities

### What OrchestrAI Cannot Do

The GitHub connection does **not** allow OrchestrAI to:

- Modify your code or make commits
- Delete files or repositories
- Change repository settings or configurations
- Access private information beyond explicitly granted repositories

## Connecting Your GitHub Account

### Step 1: Verify Your Permissions

Before starting, confirm you have the right workspace permissions:

- **Workspace Admins and Managers:** Can add GitHub connections
- **Workspace Members:** Cannot add connections (you'll need to ask an administrator)

If you see the message "Members cannot add a git integration, contact your admin," reach out to your workspace administrator.

### Step 2: Access Code Management

1. Log in to your OrchestrAI account
2. Select your workspace from the top navigation bar
3. Navigate to the Code page from your dashboard

**Note:** If you don't see the workspace selector, you may need to create or join a workspace first.

### Step 3: Initiate the Connection

1. On the Code page, click the **Connect GitHub** button (or **+ GitHub** if you already have connections)
2. A modal window will appear
3. Click **Connect to GitHub** to start the authorization process
4. A new browser window opens, taking you to GitHub's authorization page

### Step 4: Authorize OrchestrAI on GitHub

In the GitHub authorization window:

1. Review the permissions OrchestrAI is requesting:
   - Repository access (read permissions)
   - Repository metadata access
2. Choose your authorization scope:
   - **All repositories:** Grants access to all current and future repositories
   - **Only select repositories:** Choose specific repositories from the list
3. Click **Authorize** to complete the connection

**Security Note:** OrchestrAI uses GitHub's OAuth 2.0 protocol for secure authentication. Your GitHub credentials are never stored by OrchestrAI. All tokens are encrypted and stored securely within your workspace.

### Step 5: Connection Confirmation

After successful authorization:

1. You'll see a confirmation page displaying: "Your GitHub account has been successfully connected to OrchestrAI"
2. Your GitHub username appears on the confirmation
3. The GitHub authorization window closes automatically (or you can close it manually)
4. You're returned to the Code page in OrchestrAI

Your connected GitHub account now displays with your username and the GitHub icon.

## Understanding Connection Scope

### Personal Account vs Organization Access

Your GitHub connection can access:

- **Personal repositories:** All repositories under your personal GitHub account
- **Organization repositories:** Repositories from organizations you're a member of
- **Collaborator access:** Repositories where you have collaborator permissions

OrchestrAI automatically detects all repositories you can access based on your GitHub permissions.

### Repository Permissions Required

The integration requests these specific permissions:

- **Read access:** View repository contents and metadata
- **Repository scope:** Access to public and private repositories you own or collaborate on

These permissions enable OrchestrAI to analyze your code and generate automated tests and documentation.

## Working with Multiple Accounts and Organizations

### Organization Selection

If you belong to multiple GitHub organizations:

1. After connecting, you'll see all available organizations listed
2. Each organization displays with its avatar and name
3. Select the organization or personal account you want to use for this workspace
4. Your selection is saved automatically for the current workspace

### Switching Between Accounts

To change which GitHub account or organization is active in your workspace:

1. Navigate to the Code page
2. Look for the organization selector in the Connection Management tab
3. Choose a different account from the dropdown menu
4. Your repository list updates automatically to reflect the new selection

**Remember:** Each workspace can maintain its own GitHub connection. To use multiple GitHub accounts simultaneously, create separate workspaces.

## Managing Repository Access

### Viewing Your Repositories

Once connected, you can:

1. Navigate to the **Repository Management** tab on the Code page
2. See all repositories from your selected account
3. View repository names, descriptions, and last update times
4. Browse repository details before enabling analysis features

The system automatically syncs your repository list and displays the last sync time.

### Enabling Repositories for Analysis

To activate OrchestrAI features for specific repositories:

1. Go to the Repository Management tab
2. Browse your available repositories
3. Use the toggle switches next to each repository to enable or disable analysis
4. Enabled repositories will begin syncing with OrchestrAI's analysis tools

### Refreshing Your Repository List

If you've recently added repositories to GitHub:

1. Navigate to the Repository Management tab
2. Click the **refresh button** to sync the latest repository list
3. The last synced time updates to show when the refresh occurred
4. New repositories appear in the list automatically

## GitHub App Installation (Advanced Features)

### Installing the OrchestrAI Bot

For advanced features like automated pull requests and deeper code analysis:

1. Install the OrchestrAI GitHub App on your account or organization
2. Select which repositories the app can access
3. The app appears in your list of available installations
4. Choose the installation to activate for your workspace

### Bot Capabilities

When installed, the OrchestrAI Bot can:

- Create automated pull requests with test code
- Analyze repository structure and dependencies in detail
- Monitor code changes for documentation updates
- Provide real-time integration status
- Generate automated workflow improvements

### Managing Bot Permissions

To modify or remove bot access:

1. Visit your GitHub account settings
2. Navigate to **Applications** → **Installed GitHub Apps**
3. Find **OrchestrAI** in the list
4. Adjust repository access settings or uninstall the app
5. Changes take effect immediately in OrchestrAI

### Selecting the Correct Bot Installation

If you have multiple bot installations across different organizations:

1. Navigate to the Code page in OrchestrAI
2. Look for the bot installation selector
3. Choose the installation that matches your current workspace needs
4. The system saves your selection for this workspace

## Understanding Rate Limits

### GitHub Rate Limits Explained

GitHub limits how many requests authenticated applications can make per hour:

- **Standard limit:** 5,000 requests per hour for authenticated users
- **Rate limit tracking:** OrchestrAI displays your remaining requests
- **Reset schedule:** Limits reset hourly at a specific time

### Monitoring Your Usage

The system shows you:

- Current number of remaining API requests
- Percentage of your limit still available
- Exact time when your limit will reset
- Which GitHub account is being tracked

### What Happens When Limits Are Reached

If you hit the GitHub rate limit:

- You'll see an error message: "Rate limit reached for the GitHub API"
- The message displays when your limit will reset
- Repository operations will be temporarily unavailable
- You can continue working once the reset time arrives
- Consider GitHub Enterprise for higher limits if you regularly hit this ceiling

### Avoiding Rate Limit Issues

To minimize rate limit problems:

- Avoid rapid, repeated refresh operations
- Batch repository operations when possible
- Schedule intensive analysis during off-peak hours
- Monitor your usage through OrchestrAI's tracking display

## Maintaining Your Connection

### Connection Status and Duration

Your GitHub connection remains active until:

- You manually disconnect from OrchestrAI
- Your GitHub authorization token expires or is revoked
- You change your GitHub password (requires reauthorization)
- You revoke OrchestrAI's access through GitHub settings

### Checking Connection Health

To verify your GitHub connection is working:

1. Navigate to the Code page
2. Select the **Connection Management** tab
3. View your connected GitHub account status
4. Look for "Connected as: [Your GitHub Username]" with a green indicator

### Reconnecting After Disconnection

If your connection is lost or expired:

1. You'll see a notification that reconnection is needed
2. Navigate to the Code page
3. Click the **Reconnect GitHub** button
4. Complete the authorization flow again
5. Your repositories and settings are preserved after reconnection

### Security Best Practices

To keep your GitHub connection secure:

- Review OrchestrAI's access periodically in GitHub settings
- Enable two-factor authentication on your GitHub account
- Monitor GitHub's activity log for unexpected repository access
- Revoke access immediately if you suspect unauthorized use
- Use different GitHub accounts for different security contexts across workspaces

## Disconnecting GitHub

### When to Disconnect

You might want to disconnect GitHub if you:

- No longer need OrchestrAI to access your repositories
- Want to switch to a different GitHub account
- Are leaving a workspace or organization
- Need to refresh your connection completely

### How to Disconnect

To remove a GitHub connection:

1. Go to the Code page
2. Navigate to the **Connection Management** tab
3. Locate your connected GitHub account
4. Click **Delete Connection** or **Disconnect**
5. Confirm the disconnection when prompted

**Warning:** Disconnecting will disable automated test engineering and analysis for all repositories in this workspace. Your historical analysis data remains available, but new updates require reconnection.

## Troubleshooting Connection Issues

### Authorization Cancelled

**What happened:** You clicked "Cancel" or closed the authorization window before completing the connection.

**Solution:**
1. Navigate back to the Code page
2. Click **Try Again** on the error page
3. Complete the GitHub authorization process without closing the window
4. Click **Authorize** when prompted

### Session Expired

**What happened:** The connection process took too long, and your session timed out after 10 minutes.

**Solution:**
1. Click **Try Again** on the error page
2. Complete the authorization process more quickly
3. Ensure you don't leave the authorization window open too long
4. If the issue persists, log out and log back in to OrchestrAI

### Connection Failed

**What happened:** The system couldn't complete the connection to GitHub due to a technical issue.

**Solution:**
1. Click **Try Again** to retry the connection
2. Verify your internet connection is stable
3. Make sure you're logged into GitHub
4. Try disabling browser extensions that might block authentication
5. Wait a few minutes and try again if GitHub is experiencing service issues

### User Not Found

**What happened:** OrchestrAI couldn't locate your user account during the connection process.

**Solution:**
1. Verify you're logged in to OrchestrAI
2. Log out and log back in to refresh your session
3. Try connecting GitHub again
4. Contact support with your workspace ID if the issue persists

### Storage Error

**What happened:** Your authorization succeeded, but OrchestrAI couldn't save your connection details.

**Solution:**
1. Check your internet connection
2. Navigate back to the Code page
3. Click **Try Again** to reconnect
4. If multiple attempts fail, contact support with the error details

### Pop-up Blocked

**What happened:** Your browser blocked the GitHub authorization window from opening.

**Solution:**
1. Look for the pop-up blocked notification in your browser's address bar
2. Click to allow pop-ups for OrchestrAI
3. Click **Connect GitHub** again to restart the connection
4. Consider adding OrchestrAI to your browser's allowed sites list

### No Repositories Showing

**What happened:** Your repository list appears empty after successfully connecting.

**Possible causes and solutions:**

1. **Repositories not authorized during setup:**
   - Return to GitHub settings
   - Grant OrchestrAI access to more repositories
   - Reconnect from the Code page

2. **Loading in progress:**
   - Wait a few moments for the repository list to populate
   - Large organizations may take longer to load

3. **Cache or sync issue:**
   - Click the refresh button in Repository Management
   - Log out and back in to clear your session
   - Try accessing from a different browser

4. **Organization access not granted:**
   - Contact your organization administrator
   - Ask them to approve OrchestrAI for organization use
   - Reconnect after approval is granted

### Token or Permission Errors

**What happened:** Your authorization expired or you lack sufficient permissions.

**Common scenarios and solutions:**

1. **"Token is invalid" or "Authentication failed":**
   - Your connection has expired
   - Navigate to the Code page
   - Disconnect your current connection
   - Connect again to refresh your authorization

2. **"Permission denied" or "Access forbidden":**
   - You don't have the required permissions for specific repositories
   - Ask the repository owner to grant you read access
   - For organization repositories, ensure you're a member
   - You may need admin permissions for certain operations

### Organization Access Issues

**What happened:** You can't access repositories belonging to an organization.

**Solutions:**

1. **Not a member of the organization:**
   - Ask the organization owner to add you as a member
   - After being added, reconnect from the Code page

2. **Organization hasn't approved OrchestrAI:**
   - Contact your organization administrator
   - Ask them to approve OrchestrAI for organization use
   - Once approved, reconnect to see organization repositories

3. **Need to select the correct installation:**
   - Navigate to Connection Management on the Code page
   - Use the organization selector to choose the correct account
   - Ensure you've selected the right installation if you belong to multiple organizations

### Connection Timeout

**What happened:** The connection took too long and timed out.

**Solutions:**

1. **Internet connection issues:**
   - Ensure you have a stable internet connection
   - Try connecting from a different network if possible
   - Avoid using VPNs that might slow authentication

2. **GitHub service issues:**
   - Check GitHub's status page for outages
   - Wait for service to be restored
   - Try again after any platform maintenance completes

3. **Browser issues:**
   - Clear your browser cache and cookies
   - Try using a different browser
   - Disable browser extensions that might interfere with authentication
   - Update your browser to the latest version

## Working Across Multiple Workspaces

### Workspace-Specific Connections

Each workspace in OrchestrAI maintains its own separate GitHub connection:

- Connecting in one workspace doesn't affect others
- You can use different GitHub accounts per workspace
- Repository selections are workspace-specific
- Bot installations apply to the selected account or organization

This isolation allows you to:

- Separate work and personal repositories across workspaces
- Use different GitHub accounts for different teams
- Maintain distinct repository sets per project

### Switching Workspaces

When you switch between workspaces:

1. Your GitHub connection for the new workspace loads automatically
2. You see only the repositories available in that workspace
3. Settings and preferences are workspace-specific
4. You may need to connect GitHub if it's a new workspace without an existing connection

## Security and Permissions Model

### How OrchestrAI Stores Your Connection

When you connect GitHub:

- OrchestrAI receives an OAuth token from GitHub
- The token is encrypted and stored in a secure vault
- Your GitHub username is linked to your workspace
- All token access is logged for security auditing

### Data Encryption

All GitHub connection data uses:

- Industry-standard encryption at rest
- Secure HTTPS transmission
- Isolated storage per workspace
- Regular security audits

### Revoking Access

You can revoke OrchestrAI's access at any time through:

1. **OrchestrAI:** Disconnect from the Code page
2. **GitHub:** Revoke in Settings → Applications → Authorized OAuth Apps

Both methods immediately terminate OrchestrAI's access to your repositories.

## Permission Requirements Summary

| Action | Workspace Admin | Workspace Manager | Workspace Member |
|--------|----------------|-------------------|------------------|
| Connect GitHub | ✓ Yes | ✓ Yes | ✗ No |
| View repositories | ✓ Yes | ✓ Yes | ✓ Yes |
| Enable/disable repositories | ✓ Yes | ✓ Yes | ✗ No |
| Delete connection | ✓ Yes | ✓ Yes | ✗ No |
| Install GitHub bot | ✓ Yes | ✓ Yes | ✗ No |
| Switch organizations | ✓ Yes | ✓ Yes | ✗ No |

## Getting Help

### When to Contact Support

Reach out to OrchestrAI support if:

- You've tried troubleshooting steps without success
- Error messages don't match the scenarios described here
- You need help with organization-level setup
- You suspect a security issue with your connection

### What to Include in Support Requests

When contacting support, provide:

- The specific error message you're seeing
- Your workspace ID (found in workspace settings)
- Your GitHub username (never share tokens or passwords)
- Steps you've already tried to resolve the issue
- Screenshots of error pages (ensure no sensitive information is visible)

## Next Steps

After successfully connecting GitHub:

1. **Enable repositories:** Toggle on repositories you want OrchestrAI to analyze
2. **Explore analysis features:** View code quality insights for your repositories
3. **Configure preferences:** Set up test generation and documentation settings
4. **Install the bot (optional):** Enable advanced features with the GitHub App
5. **Invite team members:** Add collaborators to your workspace to share access

## Success Indicators

You know your GitHub integration is working correctly when you see:

- "Connected as: [Your GitHub Username]" with a green indicator on the Code page
- Your repository list populating in the Repository Management tab
- The ability to enable/disable repositories with toggle switches
- The last synced time updating when you refresh your repository list
- No error messages or warnings on the Code page

Your GitHub integration is now ready to power automated testing and documentation generation for your repositories.