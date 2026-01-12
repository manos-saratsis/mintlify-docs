# How to Use GitHub Integration

## Overview

Connect your GitHub account to OrchestrAI to enable automated testing, code analysis, and repository management. The GitHub integration allows you to access your repositories, manage permissions, and leverage GitHub-specific features within the platform.

## Connecting Your GitHub Account

### Starting the Connection

1. Navigate to the Code page in your workspace
2. Click the "Connect GitHub" button
3. You will be redirected to GitHub's authorization page
4. Review the requested permissions (repository access)
5. Click "Authorize" to grant access

### What Happens During Connection

When you authorize the connection:
- OrchestrAI securely stores your GitHub access token
- Your GitHub username is linked to your workspace
- You gain access to all repositories you have permissions for
- The connection is associated with your current workspace

### Success Confirmation

After successful authorization, you'll see:
- A confirmation page displaying "GitHub Connected Successfully!"
- Your connected GitHub username
- A message confirming you can now manage repositories

## Understanding Connection Errors

If something goes wrong during the connection process, you'll be redirected to an error page with details about what happened.

### Common Error Types

**Authorization Cancelled**
- Occurs when you click "Cancel" during GitHub authorization
- Solution: Try connecting again and click "Authorize"

**Session Expired**
- Your connection attempt took too long or the session timed out
- Solution: Start the connection process again from the beginning

**Connection Failed**
- The system couldn't complete the connection to GitHub
- Solution: Try again, and contact support if the problem continues

**User Not Found**
- Your user account couldn't be located in the system
- Solution: Make sure you're logged in before connecting GitHub

**Storage Error**
- The system couldn't save your GitHub connection details
- Solution: Try connecting again, and contact support if it fails repeatedly

### Error Recovery

When you encounter an error:
1. Review the error message and details provided
2. Click "Try Again" to restart the connection process
3. Click "Back to Product" to return without connecting
4. Contact support if the same error occurs multiple times

## Managing Repository Access

### Viewing Your Repositories

Once connected, you can:
- See all repositories you have access to
- View repositories from multiple GitHub accounts (if you're a member of organizations)
- Access both personal and organization repositories

### Organization Access

If you're a member of GitHub organizations:
- All organization repositories you have access to will be available
- Your permissions are respected (read, write, admin)
- Organization-level settings apply to all members

## GitHub Bot Installation

### Understanding the Bot

OrchestrAI uses a GitHub Bot (GitHub App) for advanced features like:
- Automated code analysis
- Webhook event handling
- Repository-level operations
- Enhanced security with fine-grained permissions

### Installing the Bot

1. Navigate to your Code page
2. Look for the bot installation prompt
3. Select which account to install the bot on:
   - Your personal GitHub account
   - An organization you belong to
4. Choose which repositories the bot can access
5. Confirm the installation

### Managing Bot Installations

You can:
- View all accounts where the bot is installed
- See which installation is currently selected
- Switch between different installations
- Check installation status for your workspace

### Multiple Installations

If you belong to multiple GitHub organizations:
- The bot can be installed on multiple accounts
- Each installation is managed independently
- Select the appropriate installation for your current workspace
- Switch installations as needed for different projects

## Rate Limits and Usage

### Understanding GitHub Rate Limits

GitHub restricts the number of API requests you can make:
- Standard limit: 5,000 requests per hour
- Rate limits are per-user or per-installation
- Limits reset every hour

### Checking Your Rate Limit

The system automatically monitors your GitHub rate limit:
- View remaining requests
- See when your limit resets
- Get warnings when approaching the limit

### When You Hit the Limit

If you exceed the rate limit:
- You'll see an error message indicating the limit was reached
- The system will show when the limit resets
- Wait until the reset time to resume operations
- Consider which operations consume the most requests

## Security and Permissions

### Token Storage

Your GitHub access token is:
- Encrypted and stored securely in a vault system
- Never displayed in the user interface
- Associated with your specific workspace
- Used only for authorized operations

### Permission Scopes

The GitHub integration requests:
- Repository access (read and write)
- Ability to view your repositories
- Access to repository contents and metadata

### Workspace Isolation

Each workspace connection is independent:
- Tokens are tied to specific workspaces
- Different team members can connect their own GitHub accounts
- Workspace-level permissions control who can use the integration

## Troubleshooting Connection Issues

### Connection Not Working

If your GitHub connection isn't functioning:

1. **Verify Connection Status**
   - Check if your GitHub account is still connected
   - Look for connection status indicators
   - Confirm your username is displayed correctly

2. **Check Permissions**
   - Ensure you granted all required permissions during authorization
   - Verify you have access to the repositories you're trying to use
   - Confirm organization permissions if accessing org repositories

3. **Token Validity**
   - GitHub tokens can expire or be revoked
   - Reconnect your GitHub account to refresh the token
   - Check if you've revoked access in GitHub settings

4. **Workspace Membership**
   - Confirm you're a member of the workspace
   - Verify your membership status is "active"
   - Check with workspace administrators about access

### Repository Not Appearing

If expected repositories aren't showing up:

1. **Verify GitHub Access**
   - Confirm you have access to the repository on GitHub
   - Check if the repository is private (requires appropriate permissions)
   - Ensure the repository owner hasn't restricted access

2. **Refresh Repository List**
   - Disconnect and reconnect your GitHub account
   - Wait a few moments for the system to sync
   - Check if the repository appears after refreshing

3. **Organization Repositories**
   - Verify you're a member of the organization
   - Check that the organization has granted third-party app access
   - Confirm OrchestrAI is authorized for the organization

### Bot Installation Issues

If the GitHub Bot isn't working:

1. **Installation Status**
   - Verify the bot is installed on your account or organization
   - Check which repositories the bot has access to
   - Confirm the installation is active in GitHub settings

2. **Select Correct Installation**
   - If you have multiple installations, ensure the right one is selected
   - Match the installation to the repository you're working with
   - Switch installations if needed

3. **Repository Access**
   - The bot needs explicit access to repositories
   - Check GitHub App settings for repository permissions
   - Grant access to specific repositories or all repositories

### Rate Limit Problems

If you're hitting rate limits frequently:

1. **Monitor Usage**
   - Check your rate limit status regularly
   - Identify which operations consume the most requests
   - Plan operations during off-peak times

2. **Optimize Operations**
   - Batch repository operations when possible
   - Avoid unnecessary repository refreshes
   - Wait for rate limit resets before retrying

3. **Contact Support**
   - If legitimate usage consistently hits limits
   - To discuss enterprise options with higher limits
   - For help optimizing your workflow

## Maintaining Your Connection

### Regular Maintenance

To keep your GitHub integration working smoothly:
- Periodically verify your connection is active
- Update permissions if you join new organizations
- Reinstall the bot if you add new repositories
- Monitor rate limit usage during heavy operations

### Updating Connection

If you need to update your connection:
1. Disconnect your current GitHub account
2. Reconnect following the standard connection process
3. Reselect bot installations if needed
4. Verify repository access is restored

### Multiple GitHub Accounts

If you need to connect a different GitHub account:
- Disconnect the current account first
- Connect the new account through the standard process
- Note that only one GitHub account can be connected per workspace at a time
- Consider using different workspaces for different GitHub accounts

## Getting Help

If you continue to experience issues:
- Review error messages carefully for specific guidance
- Check the error details section for technical information
- Contact support with error codes and descriptions
- Provide your workspace ID for faster assistance

The GitHub integration is designed to work seamlessly, but if you encounter persistent problems, our support team can help diagnose and resolve connection issues specific to your account and workspace setup.