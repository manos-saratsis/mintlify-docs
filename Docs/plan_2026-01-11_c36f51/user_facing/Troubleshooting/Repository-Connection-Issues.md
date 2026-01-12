# Repository Connection Issues

## Overview

If you're having trouble connecting your code repository, this guide will help you identify and resolve common connection problems. Most issues can be resolved by following the steps below.

## Common Connection Problems

### Authorization Was Cancelled

**What happened:** You clicked "Cancel" or closed the authorization window before completing the connection.

**How to fix it:**
1. Navigate to the Code page
2. Click the "Try Again" button
3. Complete the authorization process without closing the window
4. Grant the requested permissions when prompted

### Session Expired

**What happened:** You took too long to complete the authorization process, and your connection session timed out after 10 minutes.

**How to fix it:**
1. Return to the Code page
2. Start the connection process again
3. Complete the authorization within 10 minutes
4. Make sure to click through all authorization steps promptly

### Connection Failed

**What happened:** The system couldn't complete your connection to the repository platform.

**How to fix it:**
1. Check your internet connection
2. Try connecting again from the Code page
3. Make sure you're logged into your repository account (GitHub, GitLab, or Bitbucket)
4. If the problem continues, wait a few minutes and try again

### User Account Not Found

**What happened:** The system couldn't locate your user account during the connection process.

**How to fix it:**
1. Make sure you're logged into the application
2. Try logging out and logging back in
3. Navigate to the Code page and attempt the connection again
4. Contact support if the issue persists

### Unable to Save Connection

**What happened:** Your authorization succeeded, but the system couldn't save your connection details.

**How to fix it:**
1. Return to the Code page
2. Click "Try Again" to reconnect
3. If the problem continues after multiple attempts, contact support

## No Repositories Showing Up

**What happened:** You successfully connected, but don't see any repositories listed.

**Possible causes and solutions:**

1. **No repositories in your account**
   - Create a new repository in your account
   - Refresh the page to see if it appears

2. **Organization access not granted**
   - Return to your repository platform settings
   - Grant organization access to the application
   - Reconnect from the Code page

3. **Private repositories not visible**
   - Check that you granted permission to access private repositories during authorization
   - You may need to disconnect and reconnect, ensuring you approve all permissions

## Rate Limit Reached

**What happened:** You've made too many requests to the repository platform in a short time.

**How to fix it:**
1. Wait for the rate limit to reset (typically within an hour)
2. The system will show you when the limit resets
3. Reduce the frequency of repository operations
4. Contact support if you regularly hit rate limits for increased capacity

## Token or Permission Errors

**What happened:** Your authorization expired or you don't have sufficient permissions.

**Common scenarios:**

1. **"Token is invalid" or "Authentication failed"**
   - Your connection has expired
   - Navigate to the Code page
   - Disconnect your current connection
   - Connect again to refresh your authorization

2. **"Permission denied" or "Access forbidden"**
   - You don't have the required permissions for the repository
   - Ask the repository owner to grant you access
   - For organization repositories, ensure you're a member of the organization
   - You may need admin or write permissions depending on the operation

## Organization Access Issues

**What happened:** You can't access repositories that belong to an organization.

**How to fix it:**

1. **Not a member of the organization**
   - Ask the organization owner to add you as a member
   - After being added, reconnect from the Code page

2. **Organization hasn't approved the application**
   - Contact your organization administrator
   - Ask them to approve the application for organization use
   - Once approved, reconnect to see organization repositories

3. **Need to select the correct installation**
   - If you belong to multiple organizations, you may need to select which one to use
   - Navigate to the Code page and check your connection settings
   - Select the correct organization or personal account

## Webhook or Bot Setup Problems

**What happened:** Advanced features requiring bot installation aren't working.

**How to fix it:**

1. **Bot not installed**
   - The application may require installing a bot for certain features
   - Follow the installation prompts when they appear
   - Grant the bot access to the repositories you want to use

2. **Wrong organization selected**
   - Check that you've installed the bot for the correct account or organization
   - You can manage bot installations from the Code page
   - Select the installation that matches your repository location

3. **Bot permissions insufficient**
   - Return to your repository platform's bot settings
   - Ensure the bot has the required permissions
   - Grant additional permissions if prompted

## Connection Timeout

**What happened:** The connection took too long and timed out.

**How to fix it:**

1. **Check your internet connection**
   - Ensure you have a stable internet connection
   - Try connecting from a different network if possible

2. **Repository platform experiencing issues**
   - Check if the repository platform (GitHub, GitLab, or Bitbucket) is experiencing outages
   - Wait for service to be restored
   - Try again after any platform maintenance completes

3. **Browser issues**
   - Clear your browser cache and cookies
   - Try using a different browser
   - Disable browser extensions that might interfere with authentication

## Re-authentication Steps

If you need to reconnect your repository account:

1. Navigate to the Code page
2. Find your current connection
3. Click to disconnect or remove the connection
4. Click to add a new connection
5. Complete the authorization process
6. Grant all requested permissions
7. Confirm the connection was successful

## Still Having Problems?

If you've tried the solutions above and still can't connect:

1. **Check the error details**
   - Error messages often contain specific information about what went wrong
   - Note any error codes or detailed descriptions shown

2. **Try a different repository**
   - Test if the issue affects all repositories or just specific ones
   - This helps identify if it's a permission issue with a particular repository

3. **Contact support**
   - Provide the specific error message you're seeing
   - Include information about which repository platform you're using
   - Mention what troubleshooting steps you've already tried
   - Support can investigate connection logs and provide specific assistance

## Preventing Future Issues

To avoid connection problems:

- Keep your repository account credentials up to date
- Don't revoke application permissions from your repository platform's settings
- Complete authorization processes promptly when connecting
- Maintain active membership in organizations whose repositories you need to access
- Periodically verify your connection is still working by accessing the Code page