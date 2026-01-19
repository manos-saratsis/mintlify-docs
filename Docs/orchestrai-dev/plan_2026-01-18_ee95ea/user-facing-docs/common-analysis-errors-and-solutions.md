I'll retrieve the specified files first to understand the error handling patterns.# Common Analysis Errors and Solutions

## Understanding Analysis Errors

When you run analyses on your code—whether for quality, security, or compliance—you may encounter errors that prevent completion or affect results. This guide helps you understand what went wrong and how to fix it.

## Connection and Authentication Issues

### Authorization Was Cancelled

**What you'll see:**
- Error message saying "Authorization cancelled"
- Connection process stops before completing
- Unable to access repositories

**What happened:**
You closed the authorization window or clicked "Cancel" before finishing the connection to your repository.

**How to fix it:**
1. Go to the Code page in your account
2. Click "Try Again" to restart the connection
3. Keep the authorization window open until completion
4. Approve all requested permissions when asked

### Session Expired

**What you'll see:**
- "Session expired" error message
- Connection process fails after taking several minutes
- Need to restart authorization from the beginning

**What happened:**
The connection process took longer than 10 minutes, causing your authorization session to expire.

**How to fix it:**
1. Return to the Code page
2. Begin the connection process again
3. Complete all authorization steps within 10 minutes
4. Click through each step promptly without long delays

### Authentication Failed

**What you'll see:**
- "Token is invalid" error
- "Authentication failed" message
- Can't access previously connected repositories

**What happened:**
Your authorization expired or was revoked from your repository platform.

**How to fix it:**
1. Navigate to the Code page
2. Disconnect your current repository connection
3. Connect again to create a fresh authorization
4. Approve all permissions during reconnection

### Permission Denied

**What you'll see:**
- "Access forbidden" error
- "Permission denied" message
- Unable to run analyses on specific repositories

**What happened:**
You don't have the necessary permissions to access or analyze the repository.

**How to fix it:**
1. Ask the repository owner to grant you access
2. For organization repositories, verify you're a member
3. Some operations require admin or write permissions—check your access level
4. After permissions are granted, try the analysis again

## Analysis Process Errors

### Analysis Appears Stuck

**What you'll see:**
- Progress stays at the same percentage for over 15 minutes
- No new sections being processed
- Time keeps increasing but nothing changes

**What happened:**
Your analysis encountered a processing delay or lost connection to the service.

**How to fix it:**
1. Look for a yellow warning box saying "chunks appear stuck"
2. Click the "Retry" button in that warning box
3. Wait a few minutes for processing to resume
4. Use the refresh button (circular arrow) to check for updates
5. If stuck for over 20 minutes, cancel and start a new analysis

### Analysis Times Out

**What you'll see:**
- Analysis stops after 45 minutes or more
- Status changes to "failed" or "timeout"
- Error message mentions "timed out" or "stalled"

**What happened:**
The system stopped your analysis because it showed no progress for an extended period. This prevents wasting processing resources.

**Why this happens:**
- Your repository is extremely large
- Network connection was interrupted
- Processing resources were temporarily unavailable

**How to fix it:**
1. Check your internet connection is stable
2. Start a new analysis from the Dashboard
3. For very large repositories, the system breaks code into smaller chunks automatically
4. Any completed work is saved—the new analysis focuses on remaining code

### Failed Chunks

**What you'll see:**
- "X chunks failed" or "X errors" in the progress display
- Some sections show red error indicators
- Analysis completes but with partial results

**What happened:**
Individual code sections couldn't be analyzed due to complexity, temporary connectivity issues, or file size limits.

**How to fix it:**
1. Review the completion summary showing failed chunk count
2. Click "Retry Failed" in the red warning box or completion card
3. If only 1-2 chunks failed out of many, you can view results without retrying
4. Contact support if the same chunks fail after 2-3 retry attempts

### Batch Processing Queued

**What you'll see:**
- Yellow "Batch Queued" message for several minutes
- Status says "waiting in queue to start processing"
- No progress bars moving

**What happened:**
Your analysis was submitted successfully but is waiting for available processing capacity. This is normal during busy times.

**What to do:**
1. Wait patiently—queued analyses typically start within 5-10 minutes
2. Click "Continue in Background" to work on other tasks
3. Check back later on the Dashboard for results
4. Don't start additional analyses—this only increases queue length

### Progress Not Updating

**What you'll see:**
- Numbers and percentages frozen
- Time elapsed doesn't change
- Status appears old or out of date

**What happened:**
The progress display updates every few seconds, but may pause if your browser tab is in the background, your device went to sleep, or connectivity briefly dropped.

**How to fix it:**
1. Bring the browser tab to the foreground
2. Wait 5-10 seconds for automatic refresh
3. Click the refresh button (circular arrow) to force an update
4. If frozen, close the progress dialog and reopen it from the Dashboard

### Analysis Shows No Phases

**What you'll see:**
- Progress dialog shows "Loading status..."
- Phase indicators remain gray or show clock icons
- Nothing appears to be happening

**What happened:**
The analysis is initializing and progress information hasn't loaded yet.

**What to do:**
1. Wait 10-15 seconds for the initial status to load
2. Check your internet connection
3. If "Loading status..." persists over 30 seconds, close and reopen from the Dashboard

## Repository Access Errors

### No Repositories Showing

**What you'll see:**
- Empty repository list after connecting
- "No repositories found" message
- Successful connection but nothing to select

**What happened:**
Either you have no repositories in your account, organization access wasn't granted, or private repository permissions weren't approved.

**How to fix it:**
1. Verify you have repositories in your account
2. Return to your repository platform settings
3. Grant organization access to the application
4. Disconnect and reconnect, approving all permissions including private repositories
5. Refresh the page after making changes

### Rate Limit Reached

**What you'll see:**
- "Rate limit exceeded" error
- Unable to access repositories temporarily
- Message about trying again later

**What happened:**
You made too many requests to the repository platform in a short time.

**How to fix it:**
1. Wait for the rate limit to reset (typically within one hour)
2. The system shows when the limit resets
3. Reduce frequency of repository operations
4. Contact support if you regularly hit limits

### Organization Access Issues

**What you'll see:**
- Can't see repositories that belong to an organization
- "Not a member" or "Access denied" errors
- Some team repositories missing from your list

**What happened:**
You're not a member of the organization, or the organization hasn't approved the application for use.

**How to fix it:**
1. Ask the organization owner to add you as a member
2. Have your organization administrator approve the application
3. After being added or approved, reconnect from the Code page
4. If you belong to multiple organizations, select the correct one

## Memory and Performance Errors

### Browser Becomes Slow

**What you'll see:**
- Browser becomes unresponsive during analysis
- Other tabs or applications slow down
- Analysis fails with memory errors

**What happened:**
Large repositories with thousands of files require significant resources. While most processing happens on servers, the progress display uses your browser's memory.

**How to fix it:**
1. Close unnecessary browser tabs before starting analysis
2. Use "Continue in Background" to free up browser resources
3. Check results later from the Dashboard instead of keeping progress open
4. For very large repositories, consider analyzing specific directories instead of the entire codebase

### Timeout on Large Repositories

**What you'll see:**
- Analysis takes over 30 minutes
- Frequent "checking status" messages
- Concerns about whether it's still working

**What happened:**
Large repositories legitimately require more time to analyze completely.

**What to expect:**
1. Repositories with 1000+ files may take 30-60 minutes
2. Progress may appear slow but is still working
3. The system automatically manages chunk processing
4. You can close the progress dialog and check back later

**Best practices:**
1. Plan analyses during off-hours to avoid peak times
2. Use "Continue in Background" for long analyses
3. Review results incrementally rather than waiting for 100%
4. Consider excluding test files or vendor directories if not needed

## Error Messages Explained

### "Execution timed out or stalled"

**What it means:** Your analysis stopped responding for an extended period.

**What to do:** Start a new analysis from the Dashboard.

### "Batch processing timed out"

**What it means:** Your queued analysis didn't complete within the expected timeframe.

**What to do:** Retry during off-peak hours when server load is lower.

### "Chunk timed out after X attempts"

**What it means:** A specific code section failed multiple processing attempts.

**What to do:** Results for other sections are still available. Contact support if this section is critical.

### "No activity detected"

**What it means:** The progress system lost connection to the analysis process.

**What to do:** Close and reopen the progress dialog, or check the Dashboard for current status.

### "Analysis cancelled by user"

**What it means:** You or another team member manually stopped the analysis.

**What to do:** Start a new analysis when ready.

### "Could not verify workspace access"

**What it means:** Permission or authentication issue with your workspace.

**What to do:** Refresh the page and verify you're logged in. Contact your workspace administrator if the problem persists.

### "Connection failed"

**What it means:** The system couldn't complete connection to your repository platform.

**What to do:**
1. Check your internet connection
2. Verify you're logged into your repository account
3. Try again from the Code page
4. Wait a few minutes if the platform is experiencing issues

### "Unable to save connection"

**What it means:** Authorization succeeded but the system couldn't save your connection details.

**What to do:** Return to the Code page and click "Try Again" to reconnect.

### "User account not found"

**What it means:** The system couldn't locate your user account during connection.

**What to do:**
1. Verify you're logged into the application
2. Try logging out and back in
3. Attempt the connection again from the Code page
4. Contact support if the issue continues

## Analysis Recovery Features

### Automatic Recovery

The system includes built-in recovery that works without your action:

- **Stale Detection:** Every 15 minutes, the system checks for stuck chunks and automatically resets them
- **Timeout Protection:** Analyses over 45 minutes without progress are finalized with gathered results
- **Failed Chunk Retry:** Failed chunks are automatically retried up to 3 times

### Manual Recovery Options

When automatic recovery isn't enough:

- **Reset Stuck Chunks:** Click "Retry" in yellow warning boxes to manually reset frozen processing
- **Retry Failed Chunks:** Click "Retry Failed" to reprocess chunks with errors
- **Start Fresh:** Cancel and start a new analysis if repeated retries don't help

## Viewing Partial Results

Even when analysis doesn't complete fully, you can often see useful results:

1. Go to the Dashboard after analysis completes or is cancelled
2. Find the analysis entry in your repository's history
3. Click "View Results" even if showing "partially completed"
4. Review findings from successfully analyzed sections
5. Check the coverage indicator showing which parts were analyzed

## Preventing Analysis Errors

### Before Starting Analysis

- Ensure stable internet connectivity
- Close resource-intensive applications
- Keep your browser tab active (don't let device sleep)
- Use a modern, updated browser (Chrome, Firefox, Edge, or Safari)

### During Analysis

- Avoid starting multiple analyses simultaneously on the same repository
- Don't refresh the browser page while analysis is running
- Use "Continue in Background" if you need to work on other tasks
- Wait for completion before making code changes

### For Large Repositories

- Expect longer processing times (30-60 minutes for 1000+ files)
- Plan analyses during off-hours
- Review results incrementally
- Consider excluding test files or vendor directories if not needed

### Maintaining Connection Health

- Keep repository account credentials up to date
- Don't revoke application permissions from your repository platform
- Complete authorization promptly when connecting
- Maintain active membership in organizations you need to access
- Periodically verify connections work by visiting the Code page

## When to Cancel Analysis

Consider cancelling a running analysis when:

- You selected the wrong repository or analysis type
- You need to update your code before analyzing
- Analysis has been stuck over 20 minutes despite retry attempts
- You need to free up capacity for a more urgent task

**How to cancel:**
1. Open the progress dialog (check Dashboard if closed)
2. Click the red "Cancel" button at the bottom
3. Confirm your choice if prompted
4. Wait for status to update to "Cancelled"

**Important:** Cancelled analyses cannot be resumed. Start a new analysis if you want to analyze the code again.

## Getting Additional Help

If you've tried these solutions and still experience problems:

1. **Note the analysis ID** found in the Configuration section of the progress dialog (looks like "a1b2c3d4...")

2. **Document what happened:**
   - Type of analysis you were running
   - How long it ran before the problem
   - Any error messages you saw
   - Troubleshooting steps you tried

3. **Check the Dashboard** for error details in analysis history

4. **Try a different repository** to see if the issue is specific to one repository

5. **Contact support** with the analysis ID, error details, and problem description for investigation

Support can review connection logs and processing history to provide specific assistance for your situation.