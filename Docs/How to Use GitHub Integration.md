# How to Use GitHub Integration

## Overview

Connect your GitHub account to OrchestrAI to access your repositories, enable automated testing, and streamline your development workflow. This guide walks you through connecting GitHub, managing permissions, and troubleshooting common issues.

## Connecting Your GitHub Account

### Initial Setup

1. **Start the Connection Process**
   - Navigate to the Code page in your workspace
   - Click the "Connect GitHub" button
   - You'll be redirected to GitHub's authorization page

2. **Authorize Access**
   - Review the permissions OrchestrAI is requesting
   - Click "Authorize" to grant access to your repositories
   - GitHub will redirect you back to OrchestrAI

3. **Confirmation**
   - Upon successful connection, you'll see a success page showing your GitHub username
   - Your account is now connected and ready to use

### What You're Authorizing

When you connect GitHub, OrchestrAI requests access to:
- **Repository Access**: View and interact with your repositories
- **Read/Write Permissions**: Enable automated testing and code analysis
- **Organization Access** (optional): Access repositories from organizations you belong to

## Managing Multiple Accounts

### Organization Access

If you belong to GitHub organizations, you can grant OrchestrAI access to organizational repositories:

1. During the authorization process, GitHub will ask which organizations you want to grant access to
2. Select the organizations where you want to use OrchestrAI
3. Organization administrators may need to approve the installation

### Switching Between Accounts

Each workspace can have one active GitHub connection:
- Your personal GitHub account is linked to your user profile
- You can view all repositories you have access to, including those from organizations
- All repositories from connected organizations appear in your repository list

## Using the OrchestrAI Bot

### Installing the Bot

The OrchestrAI Bot provides enhanced automation capabilities:

1. **Check Bot Status**
   - Navigate to your workspace settings
   - Look for the GitHub Bot section to see if it's installed

2. **Install the Bot**
   - If not installed, click "Install OrchestrAI Bot"
   - Choose whether to install on your personal account or an organization
   - Select which repositories the bot can access (all repositories or specific ones)

3. **Select Active Installation**
   - If you have multiple bot installations (personal + organizations), choose which one to use
   - The selected installation determines which repositories can use automated features

### Bot Capabilities

The OrchestrAI Bot can:
- Automatically run tests on your repositories
- Create pull requests with test results
- Monitor repository changes
- Generate documentation from your code

## Working With Repositories

### Viewing Your Repositories

Once connected, you can:
- See all repositories you have access to
- View repositories from your personal account
- Access repositories from organizations where the bot is installed
- Filter and search through your repository list

### Repository Information

For each repository, you can see:
- Repository name and description
- Owner (your account or organization name)
- Access level and permissions
- Last update time
- Primary programming language

## Understanding Connection Status

### Success Indicators

When GitHub is properly connected:
- Your GitHub username appears in your profile settings
- You can view your repository list
- The connection status shows as "Active"
- Your account avatar displays next to the connection

### Checking Rate Limits

GitHub limits how many requests can be made per hour:
- The system automatically monitors your rate limit status
- You'll see a percentage showing how much of your quota remains
- Rate limits reset automatically every hour
- If you hit the limit, wait for the reset time shown

## Troubleshooting Connection Issues

### Authorization Cancelled

**What happened**: You clicked "Cancel" during the GitHub authorization process.

**Solution**: Try connecting again and complete the authorization process.

### Session Expired

**What happened**: Your connection attempt took too long, and the security token expired.

**Solution**: Start the connection process again. Complete authorization within 10 minutes.

### Connection Failed

**What happened**: The system couldn't complete the GitHub connection.

**Possible causes**:
- Temporary GitHub service issues
- Network connectivity problems
- Browser blocking the redirect

**Solutions**:
- Try again in a few moments
- Check your internet connection
- Ensure pop-ups aren't blocked
- Try a different browser if the issue persists

### Storage Error

**What happened**: Your GitHub connection couldn't be saved to your workspace.

**Solution**: This usually resolves itself on retry. If it continues, contact support.

### User Not Found

**What happened**: The system couldn't locate your user account during connection.

**Solution**: Make sure you're logged into OrchestrAI before connecting GitHub.

### Rate Limit Reached

**What happens**: GitHub restricts how many actions you can perform per hour.

**What to do**:
- Wait for the rate limit to reset (shown on your dashboard)
- Limits typically reset within an hour
- Authenticated users have higher limits (5,000 requests/hour)
- The system shows when your quota will refresh

### Token Retrieval Failed

**What happened**: The system couldn't access your stored GitHub credentials.

**Solution**: Disconnect and reconnect your GitHub account to refresh the authentication.

## Maintaining Your Connection

### Connection Security

Your GitHub access is secured through:
- Encrypted storage of authentication tokens
- Automatic token refresh when needed
- Workspace-level isolation of credentials
- Secure vault storage for sensitive data

### Updating Permissions

If you need to change what OrchestrAI can access:

1. Go to your GitHub account settings
2. Navigate to "Applications" → "Authorized OAuth Apps"
3. Find "OrchestrAI" in the list
4. Click to modify permissions or revoke access
5. Reconnect in OrchestrAI if you revoked access

### Disconnecting GitHub

To remove the GitHub connection:

1. Navigate to your workspace settings
2. Find the GitHub connection section
3. Click "Disconnect GitHub"
4. Confirm the disconnection
5. Your repositories will no longer be accessible until you reconnect

## Best Practices

### Organization Setup

For teams using organizations:
- Install the OrchestrAI Bot at the organization level
- Grant access only to repositories that need automated testing
- Ensure team members have appropriate permissions in GitHub
- Designate an administrator to manage the bot installation

### Security Tips

- Review requested permissions before authorizing
- Regularly audit which applications have access to your GitHub account
- Use organization-level controls for sensitive repositories
- Revoke access immediately if you suspect any security issues

### Optimal Usage

- Connect once per workspace for seamless access
- Keep your GitHub connection active for continuous integration
- Monitor rate limits if you're working with many repositories
- Select the appropriate bot installation for your current project

## Getting Help

### Common Questions

**Q: Can I connect multiple GitHub accounts?**
A: Each workspace connects to one GitHub account, but that account can access multiple organizations.

**Q: Will OrchestrAI modify my code?**
A: OrchestrAI only reads your code unless you explicitly enable features that create pull requests.

**Q: What happens if I change my GitHub password?**
A: Your OrchestrAI connection remains active. OAuth tokens are independent of your password.

**Q: Can I use OrchestrAI with private repositories?**
A: Yes, OrchestrAI works with both public and private repositories you have access to.

### Support Resources

If you encounter issues not covered in this guide:
- Check the error message for specific guidance
- Review your GitHub permissions and settings
- Contact OrchestrAI support with details about the error
- Include your GitHub username (not password) when requesting help

## Next Steps

After connecting GitHub:
1. Browse your repository list
2. Select repositories for automated testing
3. Configure test engineering settings
4. Enable continuous integration features
5. Review generated documentation and test results

Your GitHub integration is now complete and ready to enhance your development workflow.