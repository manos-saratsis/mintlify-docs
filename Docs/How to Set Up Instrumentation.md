# How to Set Up Instrumentation

## Overview

Instrumentation lets you automatically add monitoring, tracing, and logging to your applications without manually writing code. Track performance, monitor errors, and gain insights into how your application behaves in production—all powered by AI that understands your codebase.

## What You Can Monitor

Once set up, instrumentation helps you:

- **Track Application Performance** - Monitor response times, throughput, error rates, and resource usage
- **Trace Requests** - Follow requests across different parts of your application to identify bottlenecks
- **Monitor Errors** - Automatically capture and track errors as they happen in production
- **Measure Custom Metrics** - Track business-specific metrics that matter to your team
- **Analyze User Behavior** - Understand feature adoption, user journeys, and conversion patterns

## Supported Platforms

Instrumentation works with leading observability platforms:

- **Datadog** - Full-stack observability platform
- **New Relic** - Application performance monitoring
- **Dynatrace** - AI-powered observability
- **Elastic APM** - Open source application performance monitoring
- **Grafana** - Metrics and visualization
- **Custom Solutions** - Any OpenTelemetry-compatible platform

## Getting Started

### Prerequisites

Before you can set up instrumentation:

1. **Connect Your Code Repository** - Your GitHub repository must be connected to OrchestrAI
2. **Enable OrchestrAI** - The repository must have OrchestrAI enabled
3. **Choose Your Platform** - Decide which observability platform you want to use

### Step 1: Configure Your Integration

1. Navigate to the Instrumentation page
2. Click the **Configure Integration** button in the top right
3. Select your preferred observability platform from the available options
4. Enter any required credentials or API keys for your chosen platform
5. Save your configuration

### Step 2: Select Repositories

You can instrument code in two ways:

**Option A: Instrument All Repositories**
1. Click the **Instrument** button in the top right
2. AI will analyze all your connected repositories
3. Select which repositories you want to instrument
4. Confirm to begin the process

**Option B: Instrument Individual Repository**
1. Find the repository in the list on the Instrumentation page
2. Click the instrument button next to that repository
3. AI will focus on just that codebase

### Step 3: AI Analysis

Once you start the instrumentation process:

1. AI analyzes your code structure and identifies the frameworks you're using
2. The system determines the best places to add monitoring code
3. AI selects the appropriate instrumentation strategy for your chosen platform
4. The analysis follows best practices specific to your observability vendor

### Step 4: Review and Deploy

After AI completes the analysis:

1. Review the proposed instrumentation changes
2. See what monitoring capabilities will be added
3. Approve the changes to apply them to your codebase
4. Deploy your updated code to start collecting data

## What Gets Monitored

Instrumentation automatically adds tracking for:

### Performance Metrics
- API response times
- Database query performance
- External service calls
- Resource utilization (CPU, memory)
- Request throughput

### Error Tracking
- Unhandled exceptions
- Failed requests
- Timeout errors
- Validation failures

### Distributed Tracing
- Request flow across services
- Service dependencies
- Latency breakdowns
- Bottleneck identification

### Custom Events
- Business-specific metrics
- User actions
- Feature usage
- Custom application events

## Monitoring Your Instrumentation

### View Execution Status

On the Instrumentation page, you can see:

- Which repositories have been instrumented
- Current instrumentation status for each repository
- When instrumentation was last updated
- Any errors or issues that occurred

### Check Results

After instrumentation completes:

1. Click **View Results** next to a repository
2. See detailed information about what was added
3. Review any warnings or recommendations
4. Access links to view data in your observability platform

## Managing Instrumentation

### Update Instrumentation

To refresh or update instrumentation for a repository:

1. Find the repository on the Instrumentation page
2. Click the instrument button again
3. AI will analyze any code changes and update accordingly

### Change Platforms

To switch to a different observability platform:

1. Click **Configure Integration**
2. Select a different platform
3. Re-run instrumentation on your repositories
4. The previous instrumentation will be replaced

### Disable Instrumentation

To remove instrumentation from a repository:

1. Access the repository settings
2. Disable OrchestrAI for that repository
3. The next deployment will not include instrumentation code

## Best Practices

### Start Small
Begin with one or two repositories to familiarize yourself with the process before instrumenting your entire codebase.

### Review Regularly
Check your instrumentation status regularly to ensure monitoring stays up-to-date as your code evolves.

### Monitor Key Services First
Prioritize instrumenting your most critical services and user-facing applications.

### Use Custom Metrics Wisely
Define custom metrics for business KPIs that matter to your team, not just technical metrics.

### Keep Credentials Secure
Store observability platform credentials securely and rotate them according to your security policies.

## Troubleshooting

### Instrumentation Fails

If instrumentation doesn't complete successfully:

- Verify your observability platform credentials are correct
- Check that the repository is properly connected and OrchestrAI is enabled
- Review any error messages in the execution results
- Ensure your code uses supported frameworks and languages

### No Data Appearing

If you don't see data in your observability platform:

- Confirm the instrumented code has been deployed
- Check that your platform API keys and configuration are correct
- Verify network connectivity from your application to the monitoring platform
- Review platform-specific setup requirements

### Integration Not Available

If you don't see the Configure Integration button:

- Verify you have the necessary permissions in your workspace
- Check that your workspace has access to the Instrumentation feature
- Contact your workspace administrator for access

## Need Help?

If you encounter issues or have questions about setting up instrumentation, check your execution results for detailed error messages or consult your observability platform's documentation for platform-specific requirements.