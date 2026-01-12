# Connecting Your First Repository

## Overview

OrchestrAI integrates with your GitHub repositories to enable automated test engineering and code analysis. This guide walks you through connecting your first repository, from initial authentication through repository selection and troubleshooting.

## Prerequisites

Before connecting a repository, ensure you have:

- An active OrchestrAI account
- A GitHub account with access to the repositories you want to connect
- Admin or management permissions in your OrchestrAI workspace
- Pop-ups enabled in your browser for OrchestrAI

## Understanding Repository Connections

When you connect a repository to OrchestrAI, the platform:

- Accesses your repository code to analyze test coverage
- Reads repository metadata (name, description, branches)
- Monitors repository activity for automated test generation
- Stores connection details securely within your workspace

**Important:** Repository connections are workspace-specific. Each workspace maintains its own separate GitHub connections.

## Step-by-Step Connection Process

### Step 1: Access Code Management

1. Log in to your OrchestrAI account
2. Select your workspace from the top navigation bar
3. Navigate to the Code Management section from your dashboard

**Note:** If you don't see the workspace selector, you may need to create or join a workspace first.

### Step 2: Verify Your Permissions

Before connecting GitHub, confirm you have the right permissions:

- **Workspace Admins/Managers:** Can add new GitHub connections
- **Workspace Members:** Cannot add connections (you'll see a message: "Members cannot add a git integration, contact your admin")

If you're a member without management access, ask your workspace administrator to add the GitHub connection.

### Step 3: Initiate GitHub Connection

1. On the Code Management page, look for the **"+ GitHub"** button
2. Click the button to open the GitHub connection modal
3. Click **"Connect to GitHub"** to start the authorization process

A new browser window will open, taking you to GitHub's authorization page.

### Step 4: Authorize OrchestrAI on GitHub

In the GitHub authorization window:

1. Review the permissions OrchestrAI is requesting
2. Select which repositories you want to grant access to:
   - **All repositories:** Grants access to all current and future repositories
   - **Only select repositories:** Choose specific repositories from the list
3. Click **"Authorize"** or **"Install"** to complete the connection

**Security Note:** OrchestrAI uses GitHub's OAuth 2.0 protocol for secure authentication. Your GitHub credentials are never stored by OrchestrAI.

### Step 5: Connection Confirmation

After successful authorization:

1. The GitHub window will close automatically
2. You'll see a success confirmation showing your GitHub username
3. The message "Your GitHub account has been successfully connected to OrchestrAI" confirms the connection
4. You'll be returned to the Code Management page

Your connected GitHub account is now displayed with your username preceded by the GitHub icon.

### Step 6: View and Manage Repositories

Once connected:

1. Navigate to the **"Repository Management"** tab
2. Your available repositories will load automatically
3. Each repository displays with its name and current status
4. Use the toggle switches to enable or disable specific repositories for OrchestrAI analysis

The system automatically syncs your repository list and displays the last sync time.

## Managing Your Connection

### Viewing Connection Status

To check your current GitHub connection:

1. Go to Code Management
2. Select the **"Connection Management"** tab
3. View your connected GitHub account details

### Refreshing Repository List

If you've recently added repositories to GitHub:

1. Navigate to the Repository Management tab
2. Click the **refresh button** to sync the latest repository list
3. The last synced time updates to show when the refresh occurred

### Disconnecting GitHub

To remove a GitHub connection:

1. Go to the Connection Management tab
2. Locate your connected GitHub account
3. Click **"Delete Connection"**
4. Confirm the disconnection when prompted

**Warning:** Disconnecting will disable test engineering for all repositories in this workspace.

## Troubleshooting Common Issues

### "Authorization Cancelled" Error

**What happened:** You closed the GitHub authorization window or clicked "Cancel" during the OAuth process.

**Solution:** 
1. Return to Code Management
2. Click **"Try Again"** on the error page
3. Complete the GitHub authorization process

### "Session Expired" Error

**What happened:** The connection process took too long, and your session timed out.

**Solution:**
1. Click **"Try Again"** on the error page
2. Complete the authorization process more quickly
3. If the issue persists, log out and log back in to OrchestrAI

### "Connection Failed" Error

**What happened:** The connection couldn't be completed due to a technical issue.

**Solution:**
1. Click **"Try Again"** to retry the connection
2. Verify your internet connection is stable
3. Try disabling browser extensions that might block pop-ups
4. If the problem continues, contact support

### "User Not Found" Error

**What happened:** OrchestrAI couldn't verify your account during the connection process.

**Solution:**
1. Verify you're logged in to OrchestrAI
2. Log out and log back in
3. Try connecting GitHub again
4. If the issue persists, contact support

### Pop-up Blocked

**What happened:** Your browser blocked the GitHub authorization window.

**Solution:**
1. Look for the pop-up blocked notification in your browser's address bar
2. Click to allow pop-ups for OrchestrAI
3. Click **"+ GitHub"** again to restart the connection

### "Select a Workspace" Warning

**What happened:** You attempted to connect GitHub without selecting a workspace.

**Solution:**
1. Use the workspace selector in the top navigation bar
2. Choose the workspace where you want to add the connection
3. Click **"+ GitHub"** again

### No Repositories Showing

**What happened:** Your repository list appears empty after connecting.

**Possible causes and solutions:**
- **Repositories not authorized:** Return to GitHub and grant access to more repositories
- **Loading in progress:** Wait a few moments for the list to populate
- **Cache issue:** Click the refresh button to reload the repository list

### "Storage Error"

**What happened:** OrchestrAI couldn't save your connection details.

**Solution:**
1. Check your internet connection
2. Try connecting again
3. If the error persists, contact support with the error details

## Understanding GitHub Integration

### What OrchestrAI Accesses

When you connect a repository, OrchestrAI can:

- **Read repository code:** To analyze test coverage and generate tests
- **View repository structure:** To understand your codebase organization
- **Access commit history:** To track changes relevant to testing
- **Read file contents:** To analyze code and identify testing opportunities

### What OrchestrAI Cannot Do

OrchestrAI's GitHub connection does **not** allow the platform to:

- Modify your code or commit changes
- Delete files or repositories
- Change repository settings
- Access private information beyond granted repositories

### Data Security

- All connections use encrypted OAuth tokens
- Tokens are stored securely within your workspace
- Each workspace has isolated access controls
- You can revoke access at any time through GitHub settings

## Re-authentication

If your GitHub connection expires or is revoked:

1. You'll see a notification in Code Management
2. Click **"+ GitHub"** to reconnect
3. Complete the authorization process again
4. Your previously enabled repositories will need to be re-enabled

## Next Steps

After successfully connecting your first repository:

1. **Enable repositories:** Toggle on the repositories you want OrchestrAI to analyze
2. **Explore the Dashboard:** View test coverage insights for your connected repositories
3. **Configure settings:** Set up test generation preferences for each repository
4. **Invite team members:** Add collaborators to your workspace to share repository access

## Getting Help

If you encounter issues not covered in this guide:

- Click **"Back to Product"** to return to the main dashboard
- Contact your workspace administrator if you need permission changes
- Reach out to OrchestrAI support with specific error messages

## Permission Requirements Summary

| Action | Workspace Admin | Workspace Manager | Workspace Member |
|--------|----------------|-------------------|------------------|
| Connect GitHub | ✓ Yes | ✓ Yes | ✗ No |
| View repositories | ✓ Yes | ✓ Yes | ✓ Yes |
| Enable/disable repositories | ✓ Yes | ✓ Yes | ✗ No |
| Delete connection | ✓ Yes | ✓ Yes | ✗ No |

---

**Success Indicator:** When you see "Connected as: [Your GitHub Username]" with a green checkmark, your repository is successfully connected and ready for test engineering.