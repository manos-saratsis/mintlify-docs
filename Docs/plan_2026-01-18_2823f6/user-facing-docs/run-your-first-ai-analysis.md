# Run Your First AI Analysis

Get started with OrchestrAI by running your first code quality analysis. This guide walks you through selecting a repository, starting an analysis, and understanding your results.

## Before You Begin

To run your first analysis, you'll need:

- An active workspace selected
- At least one repository connected to OrchestrAI
- The repository enabled for analysis (toggle switched on)

If you haven't connected a repository yet, you'll see helpful guidance to get started.

## Starting Your Analysis

### Step 1: Navigate to Code Quality

From your product dashboard, click on **Code Quality** in the sidebar. This opens the analysis center where you can view all your code quality assessments.

### Step 2: Find Your Repository

In the "Recent Code Quality Analyses" table, you'll see all repositories that are enabled for analysis. Each repository shows:

- Repository name
- Current status
- Previous analysis results (if any)
- Action button to start new analysis

### Step 3: Launch the Analysis

Click the **Run Analysis** button next to your chosen repository. This opens the AI Quality Engineer dialog that guides you through the entire process.

## Understanding the Analysis Process

Your analysis runs through four distinct phases. You'll see real-time progress for each stage:

### Phase 0: Connectivity Check

The system verifies connection to your Git provider (GitHub, GitLab, or Bitbucket). This typically takes a few seconds.

**What you'll see:** A progress indicator showing "Connecting to Git provider..."

### Phase 1: Analyzing Repository

The AI scans your codebase structure and creates an intelligent analysis plan. It identifies all code files and organizes them into logical chunks for efficient processing.

**What you'll see:** 
- "Scanning codebase structure and creating analysis plan..."
- When complete: "Found X quality chunks to analyze"

**Time estimate:** 30 seconds to 2 minutes, depending on repository size

### Phase 2: Running Quality Analysis

This is where the AI Quality Engineer examines your code. The system processes multiple chunks simultaneously for faster results.

**What you'll see:**
- Real-time chunk counter: "15 / 50 chunks analyzed"
- Percentage complete
- Estimated time remaining
- Live elapsed time
- Individual chunk status with color coding:
  - Green background: Completed successfully
  - Blue background with spinning icon: Currently processing
  - Gray background: Waiting to start
  - Red background: Encountered an error

**Time estimate:** 5-20 minutes for typical repositories. Larger codebases may take longer.

**Batch Processing:** Your analysis is submitted to Anthropic's Claude AI. You may see a "Batch Queued" status briefly while waiting in the processing queue.

### Phase 3: Generating Quality Report

The system compiles all findings into a comprehensive, easy-to-understand report.

**What you'll see:** "Compiling quality findings into report..."

**Time estimate:** 30 seconds to 1 minute

## Monitoring Progress

### Live Status Updates

The progress dialog refreshes automatically every 3 seconds, showing:

- Current phase and completion status
- Chunk-by-chunk progress with visual indicators
- Elapsed time (updates every second)
- Estimated completion time

### Reading Chunk Status

Each chunk in the list shows:

- **Spinning blue icon:** Currently being analyzed
- **Green checkmark:** Analysis complete
- **Clock icon:** Waiting to start
- **Red alert icon:** Failed (can be retried)

Quality scores appear next to completed chunks when available.

### Background Processing

Don't want to wait? Click **Continue in Background** to close the dialog. Your analysis keeps running, and you can:

- Navigate to other pages
- Start analyses on other repositories
- Return anytime to check progress

When you return to the Code Quality page, any running analyses show their current status in the table.

## When Analysis Completes

### Success!

When analysis finishes successfully, you'll see:

- Green success message: "Code quality analysis completed successfully!"
- **View Results** button to see your report

Click **View Results** to explore your findings, including:

- Overall quality score
- Detailed metrics by category
- Specific code issues and recommendations
- File-by-file breakdown

### Handling Issues

**Stuck Chunks:** If a chunk shows no progress for 5+ minutes, you'll see a warning with a **Retry** button. Click it to restart those specific chunks without rerunning the entire analysis.

**Failed Chunks:** If some chunks fail (shown with red error icons), you have options:

- **Retry Failed:** Reprocess only the failed chunks
- **View Results Anyway:** See findings from successful chunks

The system shows exactly how many chunks succeeded and failed, so you can make informed decisions.

**Complete Failure:** If the entire analysis fails, you'll see an error message explaining what went wrong. Common issues include:

- Connection problems with your Git provider
- Repository access permissions
- Temporary service interruptions

Simply click the **Run Analysis** button again to retry.

## Managing Running Analyses

### Cancel an Analysis

If you need to stop an analysis in progress:

1. Click the **Cancel** button in the progress dialog
2. Confirm you want to stop

The system immediately halts processing. Cancelled analyses don't count against your credits for work not performed.

### Configuration Details

Expand the **Configuration** section at the top of the progress dialog to view:

- Repository name
- Analysis type
- AI model used (typically Claude 3.5 Haiku or Claude 3.5 Sonnet)
- Processing mode (Batch or Sync)
- Unique analysis ID for reference

## Tips for Your First Analysis

**Start Small:** For your first analysis, choose a smaller repository (under 50 files) to see results quickly and understand the process.

**Check Enablement:** Make sure the repository toggle is switched on. Disabled repositories won't appear in the analysis list.

**Credit Awareness:** Each analysis consumes credits from your workspace. The banner at the top shows your current credit balance.

**Resume Capability:** If you accidentally close the progress dialog, don't worry! The analysis continues running, and reopening it shows current progress exactly where it left off.

**Recent History:** The table shows your last 5 analyses per repository, making it easy to track changes over time or compare results after code improvements.

## What Happens Next

After your first successful analysis, you'll have:

- A baseline quality score for your codebase
- Specific, actionable recommendations
- Understanding of your code's strengths and weaknesses
- Foundation for tracking improvements over time

From the results page, you can:

- Dive into detailed findings
- Export reports
- Share results with your team
- Run follow-up analyses to track progress

## Need Help?

**No Repositories Showing?** 
Navigate to the Code page using the sidebar to connect and enable repositories.

**Analysis Not Starting?**
Check that you've selected a workspace and have sufficient credits available.

**Want to See Past Results?**
Click the **View Results** button at the top of the Code Quality page when you have completed analyses.

Your first analysis typically completes within 10-20 minutes, giving you immediate insights into your code quality. Each subsequent analysis builds on this foundation, helping you maintain and improve your codebase over time.