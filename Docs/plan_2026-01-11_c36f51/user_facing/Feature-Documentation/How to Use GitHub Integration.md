# How to Use GitHub Integration

## Overview

Connect your GitHub account to OrchestrAI to enable automated test engineering, repository management, and code analysis for your projects. This guide walks you through the complete GitHub integration process.

## Connecting Your GitHub Account

### Starting the Connection

1. Navigate to the Code page in your workspace
2. Click the **Connect GitHub** button
3. You'll be redirected to GitHub's authorization page
4. Review the permissions being requested (repository access)
5. Click **Authorize** to grant OrchestrAI access to your repositories

### What Happens During Connection

When you authorize the connection:

- OrchestrAI securely stores your GitHub credentials
- Your GitHub username is linked to your workspace
- All repositories you have access to become available for selection
- Your account information is encrypted and stored in a secure vault

### Successful Connection

After authorization, you'll see a success page displaying:

- A confirmation message that your account is connected
- Your GitHub username
- Information about next steps for managing repositories

You can now close this page and return to OrchestrAI to start working with your repositories.

## Understanding Connection Scope

### Personal Account vs Organization Access

Your GitHub connection can access:

- **Personal repositories**: All repos under your personal account
- **Organization repositories**: Repos from organizations you belong to
- **Collaborator access**: Repositories where you have collaborator permissions

The system automatically detects all repositories you can access based on your GitHub permissions.

## Working with Multiple Accounts

### Organization Selection

If you belong to multiple GitHub organizations:

1. After connecting, you'll see all available organizations
2. Each organization shows its avatar and name
3. Select the organization or personal account you want to use
4. The system saves your selection for this workspace

### Switching Between Accounts

To change which GitHub account or organization is active:

1. Navigate to the Code page
2. Look for the organization selector
3. Choose a different account from the dropdown
4. Your repository list will update automatically

## Managing Repository Access

### Viewing Your Repositories

Once connected, you can:

- See all repositories from your selected account
- View repository names and descriptions
- Check when each repository was last updated
- Browse repository details before enabling features

### Repository Permissions

The integration requests these permissions:

- **Read access**: View repository contents and metadata
- **Repository scope**: Access to public and private repositories you own or collaborate on

OrchestrAI uses these permissions to analyze your code and enable automated testing features.

## GitHub App Installation

### Installing the OrchestrAI Bot

For advanced features like automated pull requests and code analysis:

1. Install the OrchestrAI GitHub App on your account or organization
2. Select which repositories the app can access
3. The app appears in your list of available installations
4. Choose the installation to activate for your workspace

### Bot Capabilities

When installed, the OrchestrAI Bot can:

- Create automated pull requests with test code
- Analyze repository structure and dependencies
- Monitor code changes for documentation updates
- Provide real-time integration status

### Managing Bot Access

To modify bot permissions:

1. Visit your GitHub account settings
2. Navigate to Applications → Installed GitHub Apps
3. Find OrchestrAI in the list
4. Adjust repository access or remove the installation

## Rate Limits and Usage

### Understanding GitHub Rate Limits

GitHub limits how many requests can be made per hour:

- **Standard limit**: 5,000 requests per hour for authenticated users
- **Rate limit tracking**: OrchestrAI displays your remaining requests
- **Reset time**: Limits reset hourly at a specific time

### Monitoring Your Usage

The system shows:

- Current number of remaining requests
- Percentage of your limit still available
- When your limit will reset
- Which account is being tracked

### What Happens When Limits Are Reached

If you hit the rate limit:

- You'll see an error message explaining the situation
- The system will display when your limit resets
- You can continue once the reset time arrives
- Consider upgrading to GitHub Enterprise for higher limits

## Troubleshooting Connection Issues

### Authorization Cancelled

**What it means**: You clicked "Cancel" during GitHub authorization

**Solution**: Try connecting again and complete the authorization process

### Session Expired

**What it means**: Too much time passed between starting and completing authorization

**Solution**: Start the connection process again from the Code page

### Connection Failed

**What it means**: The system couldn't complete the connection to GitHub

**Possible causes**:
- Temporary GitHub service issues
- Network connectivity problems
- Invalid credentials

**Solution**: Wait a moment and try reconnecting

### User Not Found

**What it means**: The system couldn't locate your OrchestrAI account during connection

**Solution**: 
- Ensure you're logged into OrchestrAI
- Try logging out and back in
- Contact support if the issue persists

### Storage Error

**What it means**: The system couldn't save your GitHub connection

**Solution**: 
- Check your internet connection
- Try connecting again
- Contact support if repeated attempts fail

## Maintaining Your Connection

### Connection Status

Your GitHub connection remains active until:

- You manually disconnect
- Your GitHub token expires or is revoked
- You change your GitHub password
- You revoke OrchestrAI's access on GitHub

### Reconnecting After Disconnection

If your connection is lost:

1. You'll see a notification that reconnection is needed
2. Click the **Reconnect GitHub** button
3. Follow the authorization flow again
4. Your repositories and settings are preserved

### Security Best Practices

To keep your connection secure:

- Review OrchestrAI's access periodically in GitHub settings
- Use GitHub's security features like two-factor authentication
- Monitor the activity log for unexpected repository access
- Revoke access immediately if you suspect unauthorized use

## Working Across Workspaces

### Workspace-Specific Connections

Each workspace maintains its own GitHub connection:

- Connecting in one workspace doesn't affect others
- You can use different GitHub accounts per workspace
- Repository selections are workspace-specific
- Bot installations apply to the selected account/organization

### Switching Workspaces

When you switch workspaces:

- Your GitHub connection for the new workspace loads automatically
- You'll see the repositories available in that workspace
- Settings and preferences are workspace-specific
- You may need to connect GitHub if it's a new workspace

## Getting Help

### Common Questions

**Can I connect multiple GitHub accounts?**
Yes, by using different workspaces. Each workspace can have its own GitHub connection.

**Will this give OrchestrAI access to all my code?**
You control which repositories are accessible. During installation, you select specific repositories or allow access to all.

**Can I disconnect anytime?**
Yes, either through OrchestrAI settings or by revoking access in your GitHub account settings.

**What happens to my data if I disconnect?**
Your repository analysis and documentation remain available. New updates require reconnection.

### Support Resources

If you encounter issues:

- Check the error message for specific guidance
- Try the suggested solutions in this guide
- Contact OrchestrAI support with details about the error
- Include your workspace ID and GitHub username (but never share tokens or passwords)

## Next Steps

After connecting GitHub:

1. Browse your available repositories
2. Select repositories for test engineering
3. Enable automated documentation generation
4. Configure bot settings for your workflow
5. Start analyzing and improving your code

Your GitHub integration is now ready to help automate testing and documentation for your projects.
