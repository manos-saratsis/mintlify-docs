# How to Connect Code Repositories

Connect your GitHub repositories to start tracking code changes, managing pull requests, and automating your development workflow.

## Prerequisites

Before connecting repositories, ensure you have:

- An active account with access to a workspace
- Admin or management permissions in your workspace (regular members cannot add integrations)
- Access to the GitHub account or organization you want to connect

## Connecting GitHub

### Starting the Connection Process

1. Navigate to the Code Management page from your dashboard
2. If you haven't connected GitHub yet, you'll see a "+ GitHub" button next to the page title
3. Click the "+ GitHub" button to begin the connection process

**Note:** If you're a workspace member without management permissions, you'll see a message stating "Members cannot add a git integration, contact your admin" instead of the connection button.

### Selecting a Workspace

Before connecting GitHub, you must have a workspace selected:

1. Use the workspace selector in the top navigation bar
2. Choose the workspace where you want to add the GitHub connection
3. If no workspace is selected, you'll see a reminder to select one before proceeding

### Authorizing the Connection

After clicking the connection button:

1. A popup window will open directing you to GitHub
2. GitHub will ask you to authorize access to your repositories
3. Review the permissions being requested:
   - Read access to your repositories
   - Access to repository metadata
   - Ability to read repository contents
4. Click "Authorize" to grant access
5. The popup will close automatically after successful authorization

### What Happens During Connection

When you authorize the connection:

- Your GitHub account is linked to your workspace
- All repositories you have access to become available for selection
- The system securely stores your access credentials
- Repository information is synchronized automatically

## Managing Connected Repositories

### Viewing Your Repositories

Once connected, you can view all your repositories:

1. Go to the Code Management page
2. Select the "Repository Management" tab
3. View the complete list of repositories from your connected GitHub account

For each repository, you'll see:

- Repository name and full path
- Privacy status (public or private)
- Current enablement status for the platform
- Connection information (which GitHub account it belongs to)

### Enabling Repositories

To start using a repository with the platform:

1. Find the repository in the Repository Management list
2. Toggle the enable switch next to the repository name
3. The repository is now active and ready to use

### Refreshing Repository List

If you've added new repositories to GitHub or changed access permissions:

1. Navigate to the Repository Management tab
2. Look for the sync or refresh option
3. Click to update the repository list with the latest information from GitHub

The system shows when the repository list was last updated to help you know if a refresh is needed.

## Connection Management

### Viewing Connection Details

To see information about your GitHub connection:

1. Navigate to the Code Management page
2. Select the "Connection Management" tab
3. Review the connected account information

This page displays:

- The GitHub username or organization connected
- When the connection was established
- Number of repositories accessible through this connection
- Connection status and health

### Connecting Multiple Accounts

You can connect multiple GitHub accounts or organizations to the same workspace:

1. Each connection is managed independently
2. Repositories from all connections appear in the unified repository list
3. Each repository shows which connection it belongs to

### Managing Permissions

The GitHub connection requires specific permissions:

- **Repository Access**: Required to read repository contents and metadata
- **Repository Scope**: Access to both public and private repositories you own or have access to

If you need to modify permissions:

1. Visit your GitHub account settings
2. Navigate to Applications or Authorized OAuth Apps
3. Find the platform's application
4. Adjust permissions as needed

### Disconnecting GitHub

To remove a GitHub connection:

1. Go to the Connection Management tab
2. Find the connection you want to remove
3. Click the disconnect or delete option
4. Confirm the removal

**Important:** Disconnecting removes access to all repositories from that connection. Any enabled repositories will need to be re-enabled if you reconnect later.

## Connection Status and Indicators

### Active Connection Status

When your connection is working properly:

- The connection appears in the Connection Management tab
- Repositories load without errors
- Repository data updates successfully

### Checking Rate Limits

GitHub limits how frequently data can be accessed:

- The system monitors your usage automatically
- Rate limit information appears when viewing repositories
- If limits are reached, you'll see when access will be restored

### Reconnecting After Expiration

If your connection stops working:

1. You'll receive a notification about the connection issue
2. Navigate to the Connection Management tab
3. Click to reconnect or refresh the connection
4. Follow the authorization process again

## Understanding Repository Synchronization

### Automatic Sync

The platform automatically synchronizes repository information:

- New repositories you gain access to appear automatically
- Repository updates reflect within the synchronization period
- Removed repositories disappear from your list

### Cache and Performance

To improve performance:

- Repository lists are cached temporarily
- The last sync time is displayed on the Repository Management page
- You can manually refresh when you need the latest information

### Sync Timing

Repository information updates:

- Automatically at regular intervals
- When you manually trigger a refresh
- After reconnecting or updating your connection

## Troubleshooting Connection Issues

### Popup Blocked

If the authorization popup doesn't appear:

1. Check if your browser blocked the popup
2. Allow popups from the platform
3. Try clicking the connection button again

### Authorization Failed

If GitHub authorization fails:

1. Ensure you're logged into the correct GitHub account
2. Verify you have the necessary permissions
3. Check that you haven't exceeded GitHub's authorization limits
4. Try clearing your browser cache and attempting again

### No Repositories Showing

If repositories don't appear after connecting:

1. Verify the connection is active in Connection Management
2. Check that you have access to repositories in GitHub
3. Try refreshing the repository list
4. Ensure the correct workspace is selected

### Connection Expired

If your connection stops working:

1. Navigate to the Code Management page
2. Look for expiration notices
3. Follow the prompts to reconnect
4. Re-authorize access when prompted

### Rate Limit Reached

If you've hit GitHub's rate limits:

1. Check the rate limit information displayed
2. Note when the limit will reset
3. Wait for the reset time to pass
4. Consider reducing the frequency of operations

## Best Practices

### Workspace Organization

- Connect repositories to the appropriate workspace
- Group related repositories in the same workspace
- Keep personal and team repositories in separate workspaces

### Managing Multiple Connections

- Clearly identify which connection belongs to which GitHub account
- Regularly review connected accounts
- Remove unused connections to maintain clarity

### Security Considerations

- Only connect repositories you actively need
- Regularly review which repositories are enabled
- Disconnect accounts you no longer use
- Be mindful of private repository access

### Maintaining Connections

- Monitor connection status regularly
- Address expiration notices promptly
- Keep permissions up to date
- Refresh repository lists when making changes in GitHub

## Workspace Permissions and Access

### Who Can Connect Repositories

Only users with management permissions can:

- Add new GitHub connections
- Remove existing connections
- Connect additional GitHub accounts

### What Members Can Do

Regular workspace members can:

- View connected repositories
- See which repositories are enabled
- Access repository information
- Use enabled repositories for their work

Members cannot:
- Add new GitHub connections
- Remove connections
- Change connection settings

### Requesting Access

If you need to connect a repository but don't have permissions:

1. Contact your workspace administrator
2. Request management permissions if appropriate
3. Ask an admin to add the connection for you

## Next Steps

After connecting your repositories:

- Enable the repositories you want to work with
- Explore repository contents and history
- Set up automations and workflows
- Invite team members to collaborate
- Configure repository-specific settings

Your connected repositories are now ready to use throughout the platform for code analysis, pull request management, and development workflows.