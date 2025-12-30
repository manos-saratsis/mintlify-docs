# How to Connect and Manage Code Repositories

## Overview

Connect your GitHub repositories to enable code analysis and management capabilities. This guide walks you through connecting your GitHub account, managing repository access, and configuring your code analysis settings.

## Prerequisites

Before connecting repositories, you need:

- An active account and workspace selected
- Owner or Admin role in your workspace (Members cannot add git integrations)
- A GitHub account with access to the repositories you want to connect

## Connecting Your GitHub Account

### Initial Connection

1. **Select Your Workspace**
   - Choose your workspace from the workspace selector at the top of the page
   - You must have a workspace selected before connecting to GitHub

2. **Access Code Management**
   - Navigate to the Code Management page from the product menu
   - Look for the "+ GitHub" button in the top section

3. **Start the Connection Process**
   - Click the "+ GitHub" button
   - A GitHub account connection modal will appear
   - Review the connection information and click the connect button

4. **Authorize Access**
   - A popup window will open displaying GitHub's authorization page
   - If the popup is blocked, allow popups for this site in your browser settings
   - Sign in to your GitHub account if prompted
   - Review the permissions being requested
   - Click "Authorize" to grant access

5. **Connection Confirmation**
   - The popup will close automatically upon successful connection
   - A success message will appear showing your GitHub username and the number of repositories found
   - Your repositories will begin loading automatically

### What Happens During Connection

When you connect your GitHub account:
- Your GitHub username and account information are linked to your workspace
- All repositories you have access to are discovered and listed
- Repository metadata (name, privacy status, access level) is synchronized
- Connection status is saved for future sessions

## Managing Your Repositories

### Viewing Your Repositories

After connecting, you can view all your repositories in the Repository Management tab:

1. Navigate to the **Repository Management** tab
2. View the complete list of your repositories with the following information:
   - Repository name and full path
   - Privacy status (Public or Private)
   - Current enablement status
   - Last synchronization time

### Understanding Repository Status

Each repository displays its current state:
- **Not Enabled**: Repository is connected but not actively being analyzed
- **Enabled**: Repository is actively being monitored and analyzed
- **Private/Public**: Indicates repository visibility settings from GitHub

### Enabling Repositories for Analysis

To activate analysis on specific repositories:

1. Locate the repository in your list
2. Find the enablement toggle or activation control for that repository
3. Switch the toggle to enable analysis
4. The repository will begin synchronizing and analyzing code
5. Changes are saved automatically

### Disabling Repositories

To stop analysis on a repository:

1. Find the enabled repository in your list
2. Toggle the enablement control to the off position
3. Analysis will stop, but the repository remains connected
4. You can re-enable it at any time

### Refreshing Repository Data

To sync the latest information from GitHub:

1. Look for the refresh or sync button near your repository list
2. Click to trigger a manual synchronization
3. New repositories will be discovered
4. Existing repository information will be updated
5. Check the "Last synced" timestamp to confirm the update

### Rate Limit Information

The system displays GitHub API rate limit information:
- Remaining API calls available
- Time until rate limit resets
- Cached data usage to minimize API calls

## Managing Your Connection

### Viewing Connection Details

Access connection information in the Connection Management tab:

1. Click on the **Connection Management** tab
2. View your connected GitHub account details
3. See connection status and account information
4. Review the list of repositories associated with this connection

### Disconnecting Your GitHub Account

If you need to disconnect your GitHub account:

1. Navigate to the **Connection Management** tab
2. Locate the disconnect or delete connection option
3. Confirm you want to remove the connection
4. All repository enablements will be deactivated
5. You can reconnect the same or different account later

**Important**: Disconnecting will:
- Remove access to all connected repositories
- Disable any active analysis on those repositories
- Preserve historical data from previous analyses
- Require re-enabling repositories if you reconnect

## Troubleshooting

### Connection Issues

**Problem**: Popup window is blocked
- **Solution**: Allow popups for this site in your browser settings and try again

**Problem**: "Select a Workspace" message appears
- **Solution**: Choose a workspace from the workspace selector before attempting to connect

**Problem**: "User Email Required" error
- **Solution**: Ensure your account has a verified email address and try logging in again

**Problem**: "Authentication Required" message
- **Solution**: Log out and log back in to refresh your session, then retry the connection

### Repository Loading Issues

**Problem**: Repositories not appearing after connection
- **Solution**: Wait a few moments for synchronization to complete, then use the refresh button

**Problem**: "No repositories found" message
- **Solution**: Verify you have repositories in your GitHub account and that you granted proper permissions during authorization

**Problem**: Missing repositories in the list
- **Solution**: Use the refresh button to resync with GitHub and discover newly added repositories

**Problem**: Rate limit warnings appearing
- **Solution**: Wait for the indicated reset time before performing additional operations. The system uses caching to minimize this issue.

### Permission Issues

**Problem**: "Members cannot add a git integration" message appears
- **Solution**: Contact your workspace Owner or Admin to add the GitHub connection. Only users with Owner or Admin roles can connect repositories.

**Problem**: Cannot enable/disable repositories
- **Solution**: Verify you have management permissions in your workspace. Members with restricted access cannot modify repository settings.

## Best Practices

### Workspace Organization

- Connect GitHub at the workspace level to share repository access with your team
- Use separate workspaces for different projects or teams
- Ensure workspace roles are properly assigned before connecting repositories

### Repository Management

- Enable only the repositories you actively need to analyze to conserve resources
- Regularly refresh repository lists to stay current with your GitHub account
- Review and update enabled repositories as your projects evolve

### Connection Maintenance

- Check the last synchronized timestamp periodically to ensure data is current
- Use the manual refresh when you've added new repositories or made significant changes
- Monitor rate limit information if performing frequent operations

## Data Synchronization

### Automatic Sync

The system automatically synchronizes:
- Repository lists when you first connect
- Repository metadata when accessing the management page
- Connection status when navigating between pages

### Manual Sync

Use manual synchronization when:
- You've added new repositories to your GitHub account
- Repository settings have changed in GitHub
- You want to ensure you have the latest information
- Automatic sync hasn't run recently

### Sync Timing

- Initial connection sync occurs immediately after authorization
- Cached data is used when possible to avoid rate limits
- Manual refresh always fetches fresh data from GitHub
- Last sync timestamp displays when data was last updated

## Security and Permissions

### What Access is Granted

When you connect GitHub:
- Read access to repository information and metadata
- Ability to list repositories you have access to
- No write access to your code or repository settings
- Connection is scoped to the selected workspace

### Protecting Your Connection

- Only workspace Owners and Admins can add or remove connections
- Each workspace maintains its own separate connection
- Disconnecting removes all access immediately
- Re-authorization is required if you disconnect and reconnect

### Privacy Considerations

- Both public and private repositories can be connected
- Privacy settings from GitHub are respected and displayed
- Repository data is isolated within your workspace
- Only workspace members can view connected repositories

## Next Steps

After connecting your repositories:
- Navigate to analysis features to begin reviewing your code
- Configure specific analysis settings for individual repositories
- Set up notifications for code quality changes
- Explore insights and metrics from your connected repositories

---

**Need Help?**

If you encounter issues not covered in this guide:
- Check that your workspace and permissions are properly configured
- Verify your GitHub account has access to the repositories you're trying to connect
- Try disconnecting and reconnecting if experiencing persistent issues
- Contact your workspace administrator for permission-related problems