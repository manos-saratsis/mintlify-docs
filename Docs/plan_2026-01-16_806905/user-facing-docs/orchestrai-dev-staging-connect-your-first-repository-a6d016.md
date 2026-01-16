# Connect Your First Repository

## Overview

Connecting your repository to OrchestrAI enables automated test engineering and code analysis for your projects. This guide walks you through connecting your GitHub account and selecting repositories for analysis.

## Prerequisites

Before you begin, ensure you have:

- An active OrchestrAI account
- A workspace created and selected
- Admin or Management permissions in your workspace (Members cannot add git integrations)
- A GitHub account with access to the repositories you want to connect

## Understanding Workspace Permissions

Repository connections are workspace-specific. Only workspace administrators and users with management permissions can connect GitHub accounts. If you see a message stating "Members cannot add a git integration, contact your admin," you'll need to request access from your workspace administrator.

## Connecting Your GitHub Account

### Step 1: Access Code Management

1. Log in to OrchestrAI
2. Select your workspace from the top navigation bar
3. Navigate to the Code Management page
4. You'll see a **+ GitHub** button if no connection exists yet

### Step 2: Select Your Workspace

1. Click the **+ GitHub** button
2. A connection dialog will appear asking you to confirm your workspace selection
3. Verify the correct workspace is selected from the dropdown menu
4. This ensures your repositories are connected to the right workspace

### Step 3: Authorize GitHub Access

1. Click **Authorize & Connect GitHub**
2. A popup window will open directing you to GitHub
3. GitHub will request the following permissions:
   - Access to your repository information
   - Ability to read repository contents
   - Webhook creation for repository updates

4. Review the permissions and click **Authorize** on GitHub

**Important:** Make sure to allow popups in your browser for OrchestrAI. If the GitHub authorization window doesn't open, check your browser's popup blocker settings.

### Step 4: Complete the Connection

After authorizing on GitHub:

1. The popup window will automatically close
2. You'll be redirected back to OrchestrAI
3. A success confirmation will appear showing your connected GitHub username
4. Your repositories will automatically load in the Code Management page

## Managing Your Repositories

Once connected, you can manage which repositories OrchestrAI can access:

### Repository Management Tab

1. Navigate to the **Repository Management** tab in Code Management
2. You'll see a list of all repositories accessible through your GitHub connection
3. Each repository displays:
   - Repository name
   - Current enablement status
   - Last synchronization time

### Enabling Repositories for Analysis

1. Browse the list of available repositories
2. Toggle the switch next to any repository to enable or disable it
3. Enabled repositories will be analyzed by OrchestrAI's test engineering features
4. You can enable or disable repositories at any time

### Refreshing Your Repository List

If you've added new repositories to GitHub or modified permissions:

1. Look for the refresh option in the Repository Management section
2. Click refresh to synchronize your latest repository list
3. The last synchronization time will update to show when the list was refreshed

## Managing Your Connection

### Connection Management Tab

The **Connection Management** tab provides controls for your GitHub integration:

1. View your current connection status
2. See which GitHub account is connected
3. Access options to disconnect or modify your connection

### Disconnecting GitHub

If you need to disconnect your GitHub account:

1. Navigate to the **Connection Management** tab
2. Locate the disconnect option
3. Confirm the disconnection when prompted
4. All repository access will be removed from this workspace

**Note:** Disconnecting will stop OrchestrAI from accessing your repositories but won't delete any previously analyzed data.

## Troubleshooting Common Issues

### Connection Errors

If you encounter problems during connection:

**Authorization Cancelled**
- This means you clicked "Cancel" during the GitHub authorization process
- Simply try connecting again and complete the authorization

**Session Expired**
- Your connection session timed out during the process
- Return to Code Management and start the connection process again

**Connection Failed**
- The GitHub connection couldn't be completed
- Check your internet connection and try again
- Ensure you're logged into the correct GitHub account

**Popup Blocked**
- The GitHub authorization window was blocked by your browser
- Allow popups for OrchestrAI in your browser settings
- Try the connection process again

### Missing Repositories

If repositories don't appear after connecting:

1. Verify you granted OrchestrAI access to the repositories in GitHub
2. Check that you have the necessary permissions on GitHub for those repositories
3. Use the refresh option to reload your repository list
4. For organization repositories, ensure the OrchestrAI GitHub App is installed for your organization

### Storage Errors

If you see a "Storage Error" message:

1. Try disconnecting and reconnecting your GitHub account
2. Clear your browser cache and cookies
3. Contact support if the issue persists

### Workspace Not Selected

If you see a message about selecting a workspace:

1. Look at the top navigation bar
2. Click the workspace selector dropdown
3. Choose the workspace where you want to connect GitHub
4. Retry the connection process

## Managing Multiple Repositories

OrchestrAI supports connecting multiple repositories within a workspace:

### Adding More Repositories

1. After your initial connection, return to Repository Management
2. Browse the full list of accessible repositories
3. Enable additional repositories by toggling their switches
4. Each repository can be independently enabled or disabled

### Organization Access

For GitHub organization repositories:

1. When authorizing OrchestrAI, you'll be prompted to grant organization access
2. Select which organizations should allow OrchestrAI access
3. Organization owners may need to approve the installation
4. Once approved, organization repositories will appear in your list

### Repository Permissions

OrchestrAI respects your GitHub permissions:

- You'll only see repositories where you have at least read access
- Private repositories require explicit authorization during connection
- Organization repositories require organization-level approval

## Verifying Successful Connection

After connecting, confirm everything is working correctly:

### Check Connection Status

1. Navigate to Code Management
2. Look for the **Repository Management** tab (it should be accessible)
3. You should see a list of repositories instead of a connection button
4. The **Connection Management** tab should show your GitHub username

### Verify Repository Access

1. Check that your expected repositories appear in the list
2. The repository count should match what you have access to on GitHub
3. Enable at least one repository for analysis

### Review Synchronization

1. Note the "Last synced" timestamp near your repository list
2. This confirms OrchestrAI has successfully retrieved your repository information
3. If using cached data, you'll see an indicator showing the cache status

## Next Steps

Now that your repository is connected:

1. **Enable Repositories:** Toggle on the repositories you want OrchestrAI to analyze
2. **Explore Features:** Visit other sections to access test engineering features
3. **Set Up Webhooks:** Your repositories will automatically notify OrchestrAI of changes
4. **Review Analysis:** Check back for automated test recommendations and code insights

Your repository connection is now complete and ready for OrchestrAI's test engineering capabilities.

## Getting Help

If you encounter issues not covered in this guide:

- Ensure you have management permissions in your workspace
- Check that your GitHub account has access to the repositories you're trying to connect
- Verify your browser allows popups from OrchestrAI
- Contact your workspace administrator for permission-related issues
- Reach out to OrchestrAI support for technical problems