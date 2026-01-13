# How to Set Up Application Monitoring

Track your application's performance, user behavior, and errors automatically without writing instrumentation code manually.

## Overview

Application monitoring helps you understand how users interact with your product, identify performance issues, and track errors in production. Instead of manually adding tracking code throughout your application, you can have monitoring automatically integrated into your codebase.

## What You Can Monitor

### Performance Tracking
Monitor how your application performs in real-world conditions:
- Page load times and response speeds
- API call latency
- Resource usage
- Throughput and error rates

### User Behavior Analytics
Understand how users navigate and interact with your application:
- Feature adoption and usage patterns
- User journeys and navigation flows
- Conversion tracking
- Custom business metrics

### Distributed Tracing
Track requests as they flow through your application:
- End-to-end request tracking across services
- Identify bottlenecks and slow components
- Debug complex multi-service interactions

## Supported Monitoring Platforms

The system integrates with industry-leading observability platforms:

- **Datadog** - Full-stack observability with APM and monitoring
- **New Relic** - Application performance monitoring
- **Dynatrace** - AI-powered observability across your entire stack
- **Elastic APM** - Open source application performance monitoring
- **Grafana** - Metrics visualization and monitoring
- **Custom Solutions** - Any OpenTelemetry-compatible platform

You can also configure custom tracking for business-specific metrics alongside standard performance monitoring.

## How Automatic Instrumentation Works

### Step 1: Choose Your Monitoring Platform

Navigate to the Workflow page and configure your monitoring integration:

1. Select your preferred observability platform from the supported vendors
2. Configure what you want to track (metrics, traces, logs)
3. Provide your tracking code or configuration details
4. Set your preferences for where the monitoring code should be placed

### Step 2: Automatic Code Analysis

The system analyzes your codebase to determine the best instrumentation approach:

- **Framework Detection** - Identifies whether you're using React, Vue, Next.js, plain HTML, or other frameworks
- **Entry Point Discovery** - Locates the main files where monitoring should be initialized (like index.html, _app.tsx, or App.tsx)
- **Strategy Selection** - Determines the optimal way to add monitoring based on your framework and structure

### Step 3: Code Instrumentation

Monitoring code is automatically added to your application:

- **HTML Applications** - Tracking scripts are inserted in the appropriate location (head or body section)
- **React Applications** - Monitoring is initialized in your main HTML file, not in component code
- **Vue Applications** - Tracking is added to your entry point file
- **Next.js Applications** - Instrumentation is added to _app.tsx or using Next.js Script components

The instrumentation follows best practices for each platform to ensure optimal performance and accurate tracking.

## Platform-Specific Integration

Different monitoring platforms have specific requirements for how they should be integrated:

### Google Analytics 4
- Loads asynchronously to avoid blocking page rendering
- Initializes before any tracking calls are made
- Placed in the head section for early loading

### PostHog
- Initializes early in the application lifecycle
- Configured to track page views automatically in single-page applications
- Set up once at the application level, not in individual components

### Pendo
- Loads before any page content manipulation
- Connects user identity information for personalized tracking
- Positioned for optimal loading performance

### Mixpanel
- Initializes before any tracking events
- Set up in the main entry point for consistent tracking
- Supports event tracking, user identification, and analytics

### Segment
- Loads as early as possible for comprehensive tracking
- Supports multiple tracking methods (page views, events, user identification)
- Positioned at the beginning of the page for best performance

## Setting Up Monitoring

### From the Instrumentation Page

1. Navigate to the Instrumentation page
2. Click the "Configure Integration" button
3. Select your monitoring platform and provide configuration details
4. Review the repositories where monitoring will be added
5. Click "Instrument" to begin the setup

The system will:
- Analyze your code structure
- Determine which files need monitoring code
- Add instrumentation following best practices
- Commit the changes to your repository

### Monitoring Multiple Repositories

You can instrument all your connected repositories at once:

1. Click "Instrument" from the Instrumentation page
2. The system will analyze each enabled repository
3. Choose specific repositories or apply to all
4. Review and approve the changes

### Tracking Progress

While instrumentation is running, you can track its progress:

- **Initializing** - Setting up the instrumentation process
- **Analyzing** - Examining your code structure and identifying files
- **Fetching** - Retrieving file contents that need instrumentation
- **Instrumenting** - Adding monitoring code to your files
- **Committing** - Saving changes to your repository

## How Changes Are Applied

### Direct Commit
By default, instrumented code is committed directly to your main branch, making monitoring immediately available.

### Pull Request (Recommended)
For safer deployment, changes can be created as pull requests instead:

1. A new branch is created with the instrumentation changes
2. A pull request is opened with details about what was modified
3. You can review the changes before merging
4. Once approved, merge the pull request to activate monitoring

To use pull requests, configure this setting in your Workflow page under the Instrumentation function settings.

## Best Practices

### Single Initialization
Monitoring platforms should initialize once when your application loads, not every time a component renders. The system automatically places initialization code in the correct location for your framework.

### Framework-Appropriate Placement
- **React/Vue** - Monitoring code goes in your main HTML file (public/index.html), not in component files
- **Next.js** - Uses the _app.tsx file or Next.js Script components with appropriate loading strategies
- **HTML Applications** - Scripts are placed consistently across all pages

### Performance Considerations
Monitoring code is placed to minimize impact on page load performance:
- Scripts load asynchronously when possible
- Initialization happens at the optimal time for each platform
- Tracking doesn't block page rendering

## Viewing Results

After instrumentation completes:

1. Navigate to the Instrumentation page
2. See which files were modified in each repository
3. Click on a repository to view the commit or pull request
4. Access your monitoring platform to start viewing data

## Custom Metrics and Events

Beyond standard monitoring, you can track custom business metrics:

1. During configuration, add custom instructions for specific events or metrics
2. The system incorporates these into the instrumentation process
3. Custom tracking is added alongside standard monitoring

Examples of custom metrics:
- Feature usage tracking (e.g., "user clicked upgrade button")
- Business conversion events (e.g., "user completed onboarding")
- Custom performance markers (e.g., "search query completed")

## Troubleshooting

### No Files Were Instrumented
If no files match the instrumentation criteria:
- Verify your file patterns include the correct file types
- Check that exclude patterns aren't too broad
- Ensure the repository has the expected framework structure

### Partial Success
If some files were instrumented but others failed:
- Review the execution details to see which files had issues
- Check that failed files have the correct syntax and structure
- Re-run instrumentation to retry failed files

### Framework Not Detected Correctly
The system automatically detects frameworks, but you can verify:
- Your framework's typical entry point files exist
- File extensions match standard patterns (.tsx for React, .vue for Vue, etc.)

## Security and Privacy

### Access Token Usage
Your GitHub access token is securely stored and used only to read and write code in your repositories. Tokens are never exposed in logs or responses.

### Monitoring Platform Credentials
Configuration details for monitoring platforms (like tracking IDs) are stored securely in your workspace settings and only accessible to workspace members.

### Data Collection
The monitoring code added to your application collects data according to your chosen platform's configuration. Review your monitoring platform's settings to control what data is collected.

## Next Steps

After setting up monitoring:

1. Deploy your instrumented application to production
2. Log into your monitoring platform to view incoming data
3. Set up dashboards and alerts for key metrics
4. Use the insights to improve your application's performance and user experience

The monitoring continues to work automatically as users interact with your application, providing ongoing visibility into performance and behavior.