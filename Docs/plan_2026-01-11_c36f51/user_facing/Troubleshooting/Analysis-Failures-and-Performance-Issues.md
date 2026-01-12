# Analysis Failures and Performance Issues

## Understanding Analysis Problems

When you run quality, security, or compliance analyses on your code, you may occasionally encounter issues that prevent the analysis from completing successfully. This guide helps you identify and resolve common problems.

## Common Issues and Solutions

### Analysis Appears Stuck

**What it looks like:**
- The progress dialog shows the same status for more than 15 minutes
- No new chunks are being processed
- The elapsed time keeps increasing but progress stays the same

**Why this happens:**
Your analysis may have encountered a temporary processing delay or lost connection to the analysis service.

**How to fix it:**

1. **Check for stuck chunks:** Look in the progress dialog for a yellow warning box that says "X chunks appear stuck" with no activity for 5+ minutes.

2. **Click the Retry button** in the yellow warning box to reset the stuck chunks and restart their processing.

3. **Wait a few minutes** after clicking Retry to allow the system to resume processing.

4. **Use the refresh button** (circular arrow icon) next to the time remaining to manually check for status updates.

### Analysis Shows Failed Chunks

**What it looks like:**
- The progress dialog shows "X chunks failed" or "X errors"
- Some chunks have a red error indicator
- Analysis may complete but with partial results

**Why this happens:**
Individual code sections may fail analysis due to:
- Complex code patterns that exceed processing limits
- Temporary connectivity issues
- Large file sizes in specific chunks

**How to fix it:**

1. **Review the completion summary:** When analysis finishes with errors, you'll see a count of failed chunks.

2. **Click "Retry Failed"** in either:
   - The red warning box during analysis
   - The completion card that shows failed chunk count

3. **Review results if mostly complete:** If only 1-2 chunks failed out of many, you may choose to view the results without retrying, as most of your code has been analyzed.

4. **Contact support** if the same chunks fail repeatedly after 2-3 retry attempts.

### Analysis Times Out

**What it looks like:**
- Analysis stops completely after 45 minutes or more
- Status changes to "failed" or "timeout"
- Error message mentions "timed out" or "stalled"

**Why this happens:**
The system automatically stops analyses that show no progress for extended periods to prevent resource waste. This typically occurs when:
- The repository is extremely large
- Network connectivity was interrupted
- Processing resources were unavailable

**How to fix it:**

1. **Check your internet connection** and ensure it's stable.

2. **Start a new analysis** by returning to the Dashboard and clicking the analysis button again.

3. **For very large repositories:** The system automatically breaks your code into smaller chunks. If timeouts persist, some chunks may be too complex.

4. **Review completed work:** Even when an analysis times out, any completed chunks are saved. Starting a new analysis will focus on the remaining code.

### Batch Processing Queued for Long Time

**What it looks like:**
- Yellow "Batch Queued" message appears for several minutes
- Status says "waiting in queue to start processing"
- No progress bars moving

**Why this happens:**
Your analysis has been submitted successfully but is waiting for available processing capacity. This is normal during peak usage times.

**What to do:**

1. **Wait patiently:** Queued analyses typically start within 5-10 minutes.

2. **Close the dialog:** Click "Continue in Background" to let the analysis run while you work on other tasks.

3. **Check back later:** Return to the Dashboard to view your results when the analysis completes.

4. **Do not start multiple analyses:** Starting additional analyses while one is queued will only add to the queue length.

### Progress Dialog Not Updating

**What it looks like:**
- Numbers and percentages don't change
- Time elapsed is frozen
- Status appears outdated

**Why this happens:**
The progress dialog updates automatically every few seconds, but display updates may pause if:
- Your browser tab is in the background
- Your device went to sleep
- Network connectivity briefly dropped

**How to fix it:**

1. **Bring the browser tab to the foreground** and wait 5-10 seconds for automatic refresh.

2. **Click the refresh button** (circular arrow) next to the time remaining to force an immediate status check.

3. **Close and reopen the progress dialog:** 
   - Click "Continue in Background"
   - Navigate to the Dashboard
   - The analysis status will show current progress

### Analysis Starts But Shows No Phases

**What it looks like:**
- Progress dialog opens but shows "Loading status..."
- Phase indicators remain gray or show clock icons
- Nothing appears to be happening

**Why this happens:**
The analysis is initializing and the progress information hasn't loaded yet.

**What to do:**

1. **Wait 10-15 seconds** for the initial status to load.

2. **Check your connection:** Ensure you have active internet connectivity.

3. **Refresh if stuck:** If "Loading status..." persists for more than 30 seconds, close the dialog and reopen it from the Dashboard.

### Memory or Performance Issues

**What it looks like:**
- Your browser becomes slow or unresponsive
- Other tabs or applications slow down
- Analysis fails with memory-related errors

**Why this happens:**
Large repositories with thousands of files require significant processing resources. Most of the work happens on our servers, but the progress dialog and results display use your browser's memory.

**How to fix it:**

1. **Close unnecessary browser tabs** before starting an analysis.

2. **Use "Continue in Background":** This closes the progress dialog while analysis continues, freeing up browser resources.

3. **Check results later:** Navigate back to the Dashboard when the analysis completes rather than keeping the progress dialog open.

4. **For very large repositories:** Consider analyzing specific directories or file types rather than the entire codebase at once.

## When Analysis Cancellation Is Needed

### How to Cancel an Analysis

If you need to stop an analysis that's currently running:

1. **Open the progress dialog** if it's not already visible (check the Dashboard for running analyses).

2. **Click the red "Cancel" button** at the bottom of the dialog.

3. **Confirm your choice** if prompted.

4. **Wait for cancellation to complete:** The status will update to "Cancelled" within a few seconds.

**Note:** Cancelled analyses cannot be resumed. You'll need to start a new analysis if you want to analyze the code again.

### When to Cancel

Consider cancelling an analysis when:
- You selected the wrong repository or analysis type
- You need to update your code before analysis
- The analysis has been stuck for more than 20 minutes despite retry attempts
- You need to free up analysis capacity for a more urgent task

## Understanding Analysis Recovery

### Automatic Recovery

The system includes automatic recovery features that work without your intervention:

**Stale Detection:** Every 15 minutes, the system checks for chunks that haven't reported progress. These are automatically reset and retried.

**Timeout Protection:** Analyses that exceed 45 minutes without completing are automatically finalized with whatever results were gathered.

**Failed Chunk Retry:** Chunks that fail are automatically retried up to 3 times before being marked as permanently failed.

### Manual Recovery Options

When automatic recovery isn't sufficient:

**Reset Stuck Chunks:** Use the "Retry" button in yellow warning boxes to manually reset processing that appears frozen.

**Retry Failed Chunks:** Use the "Retry Failed" button to reprocess chunks that encountered errors.

**Start Fresh:** Cancel the current analysis and start a new one if repeated retry attempts don't resolve the issue.

## Viewing Partial Results

Even when an analysis doesn't complete fully, you can often view useful results:

1. **Navigate to the Dashboard** after the analysis completes or is cancelled.

2. **Look for the analysis entry** in your repository's history.

3. **Click "View Results"** even if the analysis shows as "partially completed."

4. **Review completed sections:** The report will show findings from all successfully analyzed chunks.

5. **Note the coverage:** The report indicates which parts of your code were analyzed and which were not.

## Performance Optimization Tips

To ensure faster, more reliable analyses:

### Before Starting

- **Ensure stable internet connectivity** throughout the analysis
- **Close resource-intensive applications** on your device
- **Keep your browser tab active** (don't put your device to sleep)
- **Use a modern browser** (Chrome, Firefox, Edge, or Safari) with the latest updates

### During Analysis

- **Avoid starting multiple analyses** simultaneously on the same repository
- **Don't refresh the browser page** while analysis is running
- **Use "Continue in Background"** if you need to work on other tasks
- **Wait for completion** before making code changes that trigger new analysis

### For Large Repositories

- **Expect longer processing times** (30-60 minutes for repositories with 1000+ files)
- **Plan analysis during off-hours** to avoid peak processing times
- **Review results incrementally** rather than waiting for 100% completion
- **Consider excluding test files or vendor directories** if they're not needed for your analysis goals

## Getting Help

If you've tried the solutions above and still experience problems:

1. **Note the analysis ID:** Found in the Configuration section of the progress dialog (looks like "a1b2c3d4...").

2. **Document what happened:** 
   - What type of analysis you were running
   - How long it ran before the problem occurred
   - Any error messages you saw
   - Steps you took to try to resolve it

3. **Check the Dashboard:** Look for error details in the analysis history.

4. **Contact support:** Provide the analysis ID and problem description.

## Common Error Messages

**"Execution timed out or stalled"**
- The analysis stopped responding for an extended period
- Solution: Start a new analysis

**"Batch processing timed out"**
- Your queued analysis didn't complete within the expected timeframe
- Solution: Retry the analysis during off-peak hours

**"Chunk timed out after X attempts"**
- A specific code section failed multiple processing attempts
- Solution: Results for other sections are still available; contact support if this section is critical

**"No activity detected"**
- The progress system lost connection to the analysis
- Solution: Close and reopen the progress dialog, or check the Dashboard

**"Analysis cancelled by user"**
- You or another team member manually stopped the analysis
- Solution: Start a new analysis when ready

**"Could not verify workspace access"**
- Permission or authentication issue
- Solution: Refresh the page and ensure you're logged in; contact your workspace administrator if the problem persists