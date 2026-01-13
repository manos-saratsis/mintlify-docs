# How to Use GitHub Integration

## Overview

Connect your GitHub account to OrchestrAI to manage repositories, enable automated testing, and collaborate on your projects. The GitHub integration allows you to access your repositories, configure automated workflows, and maintain continuous integration with your codebase.

## Getting Started

### Connecting Your GitHub Account

1. Navigate to the Code page from your workspace
2. Look for the GitHub connection option
3. Click **Connect GitHub** to begin the authorization process
4. You will be redirected to GitHub's authorization page
5. Review the permissions requested and click **Authorize** to grant access
6. Upon successful authorization, you'll be redirected back to OrchestrAI with a confirmation message

**What Happens During Connection:**
- OrchestrAI requests permission to access your repositories
- Your GitHub username is linked to your workspace
- A secure connection is established for repository access
- You can now browse and select repositories within OrchestrAI

### Understanding Permission Scopes

When you connect GitHub, OrchestrAI requests the following permissions:

- **Repository Access**: Read and write access to your code repositories
- **User Information**: Access to your GitHub username and profile
- **Organization Access**: Ability to view organizations you belong to

These permissions enable OrchestrAI to fetch repository contents, analyze code structure, and manage test engineering configurations.

## Managing Your Connection

### Viewing Connection Status

Your GitHub connection status is displayed in the Code section of your workspace. You'll see:

- Your connected GitHub username
- The account type (personal or organization)
- Connection health status
- Last sync timestamp

### Checking API Rate Limits

GitHub enforces API rate limits on all integrations. To monitor your usage:

1. Go to your Code page
2. View the rate limit indicator showing remaining API calls
3. Check when the rate limit resets
4. Plan repository operations accordingly

**Rate Limit Details:**
- Standard limit: 5,000 requests per hour for authenticated users
- Remaining requests shown as a percentage
- Automatic reset time displayed
- Usage tracking per workspace

### Multiple GitHub Accounts

If you belong to multiple GitHub organizations or have access to different accounts:

1. Connect your primary GitHub account first
2. The system will automatically detect available organizations
3. Select which organization's repositories you want to access
4. Switch between organizations as needed from the workspace settings

## Working with Repositories

### Accessing Your Repositories

Once connected, you can view all accessible repositories:

1. Navigate to the Code page
2. Browse the list of repositories from your connected account
3. Repositories include both personal repos and organization repos you have access to
4. Each repository shows its name, visibility status, and last update time

### Repository Information Display

For each repository, you'll see:

- **Repository Name**: Full name including owner/organization
- **Visibility**: Public or private status
- **Connection**: Which GitHub account owns this repository
- **Last Updated**: Most recent activity timestamp

### Handling Multiple Connections

If you've connected multiple GitHub accounts to your workspace:

- All repositories from all connections appear in a unified list
- Each repository is tagged with its source connection
- Filter or search across all connected accounts
- Manage connections independently without affecting others

## GitHub Bot Installation

### Installing the OrchestrAI Bot

For advanced features like automated pull requests and continuous testing, install the OrchestrAI GitHub Bot:

1. Navigate to the Bot Installation section
2. Click **Install Bot** to proceed to GitHub
3. Select which account (personal or organization) to install on
4. Choose whether to grant access to all repositories or select specific ones
5. Complete the installation on GitHub's website
6. Return to OrchestrAI to confirm the installation

### Managing Bot Installations

View and manage your bot installations:

1. Go to the Code page
2. View the list of accounts where the bot is installed
3. Each installation shows:
   - Account name (personal or organization)
   - Account avatar
   - Installation status
   - Repository access scope

### Selecting Active Installation

If the bot is installed on multiple accounts:

1. View all available installations
2. Select which installation to use for the current workspace
3. The selected installation determines which repositories can use automated features
4. Switch between installations as needed

## Troubleshooting

### Authorization Issues

**If authorization is cancelled:**
- You'll see a message explaining the cancellation
- Click **Try Again** to restart the authorization process
- No changes are made to your account

**If your session expires:**
- The connection attempt times out after 10 minutes
- You'll be notified that the session expired
- Start a new connection attempt from the Code page

### Connection Failures

**Common connection errors and solutions:**

**Token Exchange Failed:**
- This occurs when GitHub cannot complete the authorization
- Return to the Code page and try connecting again
- Ensure you're logged into the correct GitHub account

**User Not Found:**
- Make sure you're logged into OrchestrAI
- Refresh your session by logging out and back in
- Verify your account is active

**Storage Error:**
- The connection couldn't be saved to your workspace
- Check your internet connection
- Try again after a few moments
- Contact support if the issue persists

### Rate Limit Issues

**If you hit GitHub's rate limit:**
- You'll see a notification about the rate limit
- The reset time is displayed
- Wait until the reset time to resume operations
- Plan large operations during off-peak hours

**Managing rate limits:**
- Monitor your usage regularly
- Batch repository operations when possible
- Avoid unnecessary API calls
- Consider the number of repositories being accessed

### Repository Access Problems

**If repositories aren't showing:**
- Verify your GitHub connection is active
- Check that you have permission to access the repositories
- Ensure the repositories aren't archived or deleted
- Refresh the repository list

**If specific repositories are missing:**
- Confirm the repository exists on GitHub
- Check organization permissions if it's an org repository
- Verify the bot installation includes that repository
- Review GitHub App installation settings

### Bot Installation Issues

**Bot not showing as installed:**
- Verify the installation completed on GitHub's side
- Return to GitHub's settings and confirm the app is listed
- Check that the installation wasn't revoked
- Try reinstalling the bot

**Cannot select installation:**
- Ensure you're a member of the organization
- Verify the bot is installed on that account
- Check that you have admin permissions for the installation
- Confirm the installation hasn't been suspended

## Security and Privacy

### Token Storage

Your GitHub access tokens are stored securely:
- Tokens are encrypted and stored in a secure vault
- Database records contain only references, not actual tokens
- Token access is restricted to authorized operations
- Tokens are automatically refreshed as needed

### Connection Privacy

- Connections are specific to your workspace
- Other workspace members cannot see your personal tokens
- Organization connections follow GitHub's permission model
- You can revoke access at any time from GitHub's settings

### Revoking Access

To disconnect GitHub:

1. Go to your GitHub account settings
2. Navigate to Applications → Authorized OAuth Apps
3. Find OrchestrAI in the list
4. Click **Revoke** to remove access
5. Return to OrchestrAI and reconnect if needed

## Best Practices

### Connection Management

- Keep your GitHub connection active for seamless repository access
- Review connected accounts periodically
- Update connections if you change organizations
- Monitor rate limit usage to avoid interruptions

### Organization Setup

- Install the bot at the organization level for team projects
- Grant appropriate repository access during installation
- Coordinate with team members on which installation to use
- Review bot permissions regularly

### Repository Operations

- Sync repository lists regularly to see new repositories
- Use specific repository selection for focused work
- Batch operations when working with multiple repositories
- Monitor API usage during large-scale operations

### Troubleshooting Steps

1. Check connection status first
2. Verify GitHub account permissions
3. Review rate limit availability
4. Confirm bot installation if using automated features
5. Try reconnecting if issues persist
6. Contact support with specific error messages

## Getting Help

If you encounter issues not covered in this guide:

- Check the connection status indicator for specific error messages
- Review GitHub's authorization settings for OrchestrAI
- Verify your workspace membership and permissions
- Contact OrchestrAI support with details about the error
- Include your GitHub username and workspace information when reporting issues