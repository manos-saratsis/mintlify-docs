# Understanding OrchestrAI Workflow

OrchestrAI uses specialized AI agents to analyze and improve your code automatically. Each agent focuses on a specific aspect of software quality, working independently or together to provide comprehensive insights and improvements.

## The AI Agent Team

Your workspace includes six specialized AI agents, each designed to handle specific analysis tasks:

### Quality Engineer
The Quality Engineer examines your code to ensure it follows best practices and maintains high standards across multiple dimensions:

- **Readability** - Reviews naming conventions, comments, and code formatting
- **Maintainability** - Checks adherence to SOLID principles, DRY patterns, and modularity
- **Reliability** - Evaluates error handling and edge case coverage
- **Efficiency** - Analyzes performance characteristics and complexity
- **Testability** - Assesses test coverage and mocking capabilities

### Security Analyst
The Security Analyst identifies potential vulnerabilities and security risks in your codebase:

- **Injection Prevention** - Scans for SQL injection, XSS, and command injection risks
- **Authentication & Authorization** - Reviews authentication flows and session management
- **Secrets & Data Protection** - Detects hardcoded keys and personally identifiable information
- **Cryptography** - Identifies weak encryption algorithms
- **Configuration Security** - Checks security headers, CORS settings, and TLS configuration
- **Input Validation** - Ensures proper data sanitization

### Compliance Analyst
The Compliance Analyst ensures your code meets regulatory requirements and industry standards:

- **Data Privacy** - Validates GDPR, CCPA, and PII handling compliance
- **Data Protection** - Reviews storage practices and retention policies
- **Access Control** - Verifies role-based access and least privilege principles
- **Audit Trails** - Checks logging and traceability mechanisms
- **Encryption Standards** - Confirms data encryption at rest and in transit
- **Regulatory Compliance** - Assesses alignment with SOC2, HIPAA, and ISO 27001

### Test Engineer
The Test Engineer generates comprehensive test suites to improve code coverage:

- Creates unit tests for JavaScript, TypeScript, React, Java, C#, C++, Kotlin, and Python
- Generates tests targeting specific coverage levels (Basic 60%, Important 80%, Full 100%)
- Supports whole repository testing or commit-specific test generation
- Automatically detects testing frameworks in your codebase
- Organizes generated tests in an `orchestrai_tests` folder

### Documentation Specialist
The Documentation Specialist creates and maintains comprehensive documentation:

- **User-Facing Documentation** - Quickstart guides, tutorials, how-to guides, API references
- **Internal Developer Documentation** - Architecture overviews, development setup guides
- **Security Documentation** - SBOM files (CycloneDX and SPDX formats), security policies
- **Release Notes** - Commit-based documentation of changes
- Supports both creating new documentation and migrating existing documentation

### Instrumentation Engineer
The Instrumentation Engineer adds analytics and monitoring capabilities to your application:

- Automatically inserts JavaScript tracking tags
- Supports multiple analytics vendors (Google Analytics, Mixpanel, Segment, etc.)
- Smart placement in HTML, React, and Vue files
- Respects code structure and framework patterns
- Creates clean commits with instrumentation changes

## How Analysis Works

### Starting an Analysis

When you start an analysis:

1. **Select Your Repository** - Choose one or more repositories from your connected sources
2. **Configure the Analysis** - Select AI model tier (Haiku for speed, Sonnet for balance, Opus for depth)
3. **Choose Execution Mode** - Run immediately or schedule as a batch job
4. **Add Instructions** - Provide optional custom instructions to focus the analysis
5. **Start the Process** - The agent begins analyzing your code

### Processing Queue

Analyses are processed based on your chosen execution mode:

- **Immediate Execution** - The analysis starts right away and shows real-time progress
- **Batch Execution** - The analysis is queued and runs during off-peak hours

You can view the status of all executions on the Dashboard page, where each analysis shows:
- Current progress percentage
- Which files are being analyzed
- Any issues encountered
- Estimated time remaining

### Viewing Results

Once an analysis completes:

1. Navigate to the respective results page (Quality Results, Security Results, Compliance Results, etc.)
2. Review findings organized by severity or category
3. Access detailed explanations for each issue
4. Download reports or export data as needed

For Test Engineer results, generated tests appear in your repository's `orchestrai_tests` folder. For Documentation Specialist results, documentation files are committed to your configured documentation repository and folder.

## Credit System

OrchestrAI uses a credit-based system to manage usage across your workspace:

### How Credits Work

- Each analysis consumes credits based on the AI model selected and repository size
- Haiku models use fewer credits but provide faster, lighter analysis
- Sonnet models balance credit usage with analysis depth
- Opus models use more credits but deliver the most thorough analysis
- Your subscription plan determines monthly credit allocation

### Monitoring Credits

The system tracks your credit usage in real-time:

- **Low Credit Warning** - Appears when only 20% of monthly credits remain
- **Credit Exhausted** - Running analyses pause automatically when credits run out
- **Daily Limits** - Free plans have daily credit limits that reset every 24 hours
- **Monthly Limits** - Paid plans have monthly limits that reset on your billing date

When credits run low, workspace owners and administrators see an option to upgrade their plan for additional credits.

### Usage Across Analysis Types

Different analysis types consume credits at different rates:

- **Quality Analysis** - Moderate credit usage, analyzes all code files
- **Security Analysis** - Higher credit usage due to deep vulnerability scanning
- **Compliance Analysis** - Moderate credit usage, focuses on regulatory patterns
- **Test Generation** - Variable usage based on target coverage and scope
- **Documentation Generation** - Variable usage based on number of sections and repositories
- **Instrumentation** - Lower credit usage, focused on specific file modifications

## Workspace Organization

### Repository Management

Organize your repositories by enabling OrchestrAI for specific projects:

1. Navigate to the Repositories page
2. Connect your GitHub, GitLab, or other Git provider accounts
3. Enable OrchestrAI for repositories you want to analyze
4. Assign repositories to products for better organization

### Product Organization

Group related repositories into products:

- Create products representing your applications or services
- Assign repositories to products for logical grouping
- Generate product-wide documentation across multiple repositories
- Track analysis results by product

### Team Collaboration

Control who can perform different actions:

- **Workspace Owners** - Full control over all settings and analyses
- **Administrators** - Manage workflow settings and permissions
- **Members** - Run analyses based on assigned permissions
- **Function Permissions** - Grant or restrict access to specific AI agents

Configure permissions by navigating to Settings and selecting Team Management. Assign function-specific permissions for Quality, Security, Compliance, Testing, Documentation, and Instrumentation.

## Workflow Configuration

### Enabling Functions

Control which AI agents are available in your workspace:

1. Navigate to the Workflow Settings page
2. Enable or disable specific functions (Quality, Security, Compliance, Testing, Documentation, Instrumentation)
3. Configure default settings for each enabled function
4. Set analysis-only or analysis-and-fix modes where applicable

### Analysis Preferences

Set default preferences for how analyses run:

- **Default Model Selection** - Choose which AI model tier to use by default
- **Execution Mode** - Set whether analyses run immediately or as batch jobs
- **Notification Settings** - Configure alerts for completed analyses or errors
- **Auto-Run Settings** - Enable automatic analysis on code commits or pull requests

### Documentation Configuration

For the Documentation Specialist, configure:

- **Target Repository** - Where documentation files will be committed
- **Folder Structure** - Where different documentation types are organized
- **Content Structure** - Which documentation sections to generate by default
- **Documentation URL** - Link to existing documentation for migration scenarios

### Instrumentation Configuration

For the Instrumentation Engineer, configure:

- **Integrations** - Enable analytics vendors and custom JavaScript tags
- **File Targets** - Specify which file types to instrument (HTML, React, Vue)
- **Placement Rules** - Control where tags are inserted in your code
- **Exclusion Patterns** - Prevent instrumentation in specific directories

## Integration with Development Workflows

### GitHub Integration

OrchestrAI integrates seamlessly with your GitHub workflow:

- Analyses access your repository code through secure GitHub connections
- Results can trigger GitHub Actions for automated responses
- Generated tests and documentation are committed directly to your repositories
- Pull requests can include analysis results as comments

### CI/CD Pipeline Integration

Connect OrchestrAI to your continuous integration pipeline:

- Trigger analyses automatically on commits or pull requests
- Block deployments if critical security issues are found
- Generate test coverage reports as part of your build process
- Update documentation automatically with each release

### Result Notifications

Stay informed about analysis completion:

- Email notifications when analyses complete or encounter errors
- In-app notifications accessible from the Dashboard
- Webhook support for custom integrations with your tools
- Slack integration for team-wide visibility (when configured)

### Background Execution

Long-running analyses can continue in the background:

- Close progress dialogs without canceling the analysis
- Return to the Dashboard to see all running executions
- Resume viewing progress by clicking on any active execution
- Receive notifications when background analyses complete

This workflow ensures your team can analyze and improve code quality continuously without disrupting your development process. Each AI agent works independently but shares insights through a unified platform, making it easy to maintain high standards across your entire codebase.