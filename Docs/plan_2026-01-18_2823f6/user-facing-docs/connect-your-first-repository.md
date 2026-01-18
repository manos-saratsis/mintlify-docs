# Connect Your First Repository

## Overview

Connecting your GitHub repositories to OrchestrAI enables automated test engineering for your projects. This guide walks you through the complete process of authorizing GitHub access, selecting repositories, and verifying your connection.

## Prerequisites

Before you begin, make sure you have:

- An active OrchestrAI account
- A workspace created in OrchestrAI
- A GitHub account with access to the repositories you want to connect
- Administrative access to your workspace (standard members cannot add GitHub integrations)

## Step 1: Access Code Management

1. Log in to your OrchestrAI account
2. Select your workspace from the workspace selector in the top navigation bar
3. Navigate to the Code Management page from your dashboard

**Important:** You must select a workspace before connecting to GitHub. If you see a message asking you to select a workspace, use the workspace selector in the top bar.

## Step 2: Initiate GitHub Connection

1. On the Code Management page, locate the **"+ GitHub"** button near the page title
2. Click the **"+ GitHub"** button to open the GitHub connection modal

**Permission Note:** If you see a message stating "Members cannot add a git integration, contact your admin," you need to have your workspace administrator connect GitHub for you. Only administrators and managers can add GitHub integrations.

## Step 3: Authorize GitHub Access

When you click to connect GitHub:

1. A modal will appear asking you to confirm the connection
2. Click **"Authorize & Connect GitHub"** to proceed
3. A new popup window will open with GitHub's authorization screen
4. Review the permissions being requested by OrchestrAI
5. Click **"Authorize"** on the GitHub page to grant access

**Troubleshooting Popup Blockers:**
- If the authorization window doesn't open, check that your browser allows popups from OrchestrAI
- Look for a popup blocker icon in your browser's address bar
- Allow popups for the OrchestrAI domain and try again

## Step 4: Complete Authorization

After authorizing on GitHub:

1. You'll see a success screen showing your connected GitHub username
2. The popup window will automatically close
3. You'll be returned to OrchestrAI's Code Management page
4. Your GitHub connection status will update to "Connected"

## Step 5: Manage Your Repositories

Once connected, you can access two management tabs:

### Repository Management Tab

This is where you control which repositories OrchestrAI can access:

1. Switch to the **"Repository Management"** tab
2. View all repositories available from your connected GitHub account
3. Enable or disable specific repositories using the toggle switches
4. Click **"Refresh Repositories"** to sync the latest changes from GitHub

**What You'll See:**
- Repository name and owner
- Current enablement status
- Last sync time
- GitHub rate limit information (if applicable)

### Connection Management Tab

This tab displays your GitHub connection details:

1. Switch to the **"Connection Management"** tab
2. View your connected GitHub account information
3. See the list of repositories associated with your workspace
4. Disconnect GitHub if needed (requires confirmation)

## Understanding Permissions

OrchestrAI uses GitHub App authentication, which provides:

- **Repository Access:** Read access to code and repository structure
- **Webhook Access:** Notifications about code changes and pull requests
- **Secure Token Management:** Your credentials are encrypted and stored securely
- **Granular Control:** You can enable/disable access for individual repositories

## Verification Steps

To verify your connection is working correctly:

1. Check that the **"+ GitHub"** button is no longer visible (it appears only when not connected)
2. Confirm you can see your repositories listed in the Repository Management tab
3. Verify the "Last Synced" timestamp shows a recent time
4. Try toggling a repository on/off to ensure changes are saved

## Common Connection Issues

### "Popup was blocked" Error

**Solution:** Enable popups for OrchestrAI in your browser settings, then try connecting again.

### "Session Expired" Error

**What happened:** Your connection session timed out during authorization.

**Solution:** Return to the Code Management page and start the connection process again. The authorization must be completed within a few minutes of starting.

### "Authorization Cancelled" Error

**What happened:** You clicked "Cancel" on the GitHub authorization screen.

**Solution:** Click the **"Try Again"** button to restart the authorization process. This time, click "Authorize" on the GitHub screen.

### "User Not Found" Error

**What happened:** OrchestrAI couldn't verify your logged-in status.

**Solution:** 
1. Log out of OrchestrAI
2. Log back in
3. Try connecting to GitHub again

### "Connection Storage" Error

**What happened:** The connection was authorized but couldn't be saved to your workspace.

**Solution:** 
1. Verify you selected a workspace before connecting
2. Ensure you have the correct permissions in the workspace
3. Try connecting again

### "Select a Workspace" Warning

**What happened:** You tried to connect GitHub without selecting a workspace.

**Solution:** Use the workspace selector in the top navigation bar to choose a workspace, then try connecting again.

## Disconnecting GitHub

If you need to disconnect your GitHub account:

1. Go to the Connection Management tab
2. Locate the disconnect or delete connection option
3. Confirm the disconnection when prompted
4. All repository access will be revoked immediately

**Warning:** Disconnecting will disable all OrchestrAI features that depend on GitHub access for this workspace.

## Rate Limits and Caching

GitHub enforces rate limits on API requests. OrchestrAI handles this intelligently:

- **Automatic Caching:** Repository information is cached to reduce API calls
- **Cache Indicator:** You'll see an indicator when viewing cached data
- **Manual Refresh:** Use the "Refresh Repositories" button to force an update
- **Rate Limit Display:** Current rate limit status is shown when approaching limits

## Next Steps

After successfully connecting your first repository:

1. Enable the repositories you want OrchestrAI to monitor
2. Configure test engineering settings for each repository
3. Set up notifications for test results
4. Invite team members to your workspace to collaborate

## Security Notes

- Your GitHub credentials are never stored by OrchestrAI
- Only OAuth tokens are used, which can be revoked at any time
- All connections are workspace-specific and isolated
- You can review and revoke OrchestrAI's access anytime through your GitHub settings

## Getting Help

If you continue to experience issues connecting GitHub:

1. Check that you have administrative access to your workspace
2. Verify your GitHub account has access to the repositories you want to connect
3. Try clearing your browser cache and cookies
4. Contact OrchestrAI support with details about the error message you received

---

**Success Checklist:**
- ✅ Workspace selected
- ✅ GitHub authorization completed
- ✅ Connection shows as "Connected"
- ✅ Repositories visible in Repository Management tab
- ✅ At least one repository enabled

You're now ready to use OrchestrAI's test engineering features with your connected repositories!