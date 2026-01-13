# How to Use the Testing Suite

## Overview

OrchestrAI's Testing Suite automatically generates comprehensive test coverage for your codebase using advanced AI. The system analyzes your repository structure, identifies untested code, and creates unit tests tailored to your programming languages and frameworks—eliminating manual test writing while ensuring code reliability.

## Getting Started

### Prerequisites

Before using the Testing Suite, you need:

1. An active OrchestrAI account
2. A connected repository (GitHub, GitLab, or Bitbucket)
3. Sufficient credits in your workspace

### Accessing the Testing Suite

1. Sign in to your OrchestrAI account
2. Select your workspace from the top navigation bar
3. Navigate to the Testing page from the product menu
4. If no repositories are connected, you'll see an empty state with an option to add a Git connection

## Connecting Your First Repository

If you haven't connected a repository yet:

1. Click the button to add a Git connection
2. You'll be redirected to the connection management page
3. Authorize OrchestrAI to access your repositories
4. Select which repositories to enable for testing
5. Return to the Testing page to see your connected repositories

## Understanding Test Coverage

The Testing Suite displays all your connected repositories in a coverage table showing:

- **Repository Name**: The full name of your repository
- **Unit Test Percentage**: Current test coverage percentage (clickable to improve)
- **Status**: Current testing status (pending, processing, completed, or failed)
- **Last Updated**: When coverage was last measured

## Generating Tests

### Starting Test Generation

1. Locate your repository in the coverage table
2. Click on the unit test percentage for that repository
3. An AI Test Engineer panel opens on the right side

### Configuring Test Generation

The AI Test Engineer panel provides several configuration options:

**Target Coverage Percentage**
- Set your desired test coverage goal (0-100%)
- The AI will generate tests to reach this target
- Higher percentages may take longer to complete

**Custom Instructions (Optional)**
- Specify testing frameworks you prefer (e.g., "Use Jest for testing")
- Indicate which files or areas to focus on
- Define test organization preferences
- Add any custom testing requirements

**AI Model Selection**
- Choose between different AI models based on your needs:
  - **Claude Sonnet 4.5**: Most capable, best for complex codebases
  - **GPT-5**: High-quality test generation
  - **GPT-4o Mini**: Faster, cost-effective option
  - **Claude Haiku**: Budget-friendly choice
  - **Claude 3.5 Haiku**: Balanced speed and quality

**Execution Mode**
- **Now**: Real-time processing with immediate results
- **Batch**: Cost-saving mode (50% discount) with asynchronous processing

### Applying Changes

Once you've configured your preferences:

1. Review your settings in the panel
2. Click the "Apply" or "Generate Tests" button
3. The panel closes and test generation begins
4. Your repository status updates to show progress

## Monitoring Test Generation Progress

### Real-Time Status Updates

The coverage table automatically updates to show:

- **Processing**: AI is analyzing your code and generating tests
- **Connectivity Check**: Verifying repository access
- **Analyzing**: Understanding your codebase structure
- **Generating**: Creating test files
- **Pushing**: Committing tests to your repository
- **Completed**: Tests successfully generated and committed
- **Failed**: An error occurred (hover for details)

### Progress Notifications

You'll receive:
- On-screen notifications when generation starts
- Status updates as different phases complete
- Email notification when generation finishes
- Links to view the generated tests

## Understanding Test Generation Process

The AI Test Engineer follows a multi-phase approach:

**Phase 1: Repository Analysis**
- Scans your codebase to understand structure
- Identifies programming languages and frameworks
- Detects existing test patterns
- Locates untested files and functions

**Phase 2: Test Generation**
- Creates comprehensive unit tests for identified code
- Generates edge case scenarios
- Ensures proper mocking and assertions
- Adapts to your testing framework

**Phase 3: Repository Integration**
- Commits generated tests to a new branch
- Organizes tests in appropriate folders
- Creates a pull request for review
- Provides links to view changes

## Viewing Generated Tests

After completion:

1. Check your email for the completion notification
2. Click the provided link to view the pull request or commit
3. Review the generated test files in your repository
4. Tests are organized in the configured output folder (default: `orchestrai/tests`)

## Supported Technologies

The Testing Suite automatically detects and generates tests for:

- **React**: Component testing with proper setup
- **TypeScript**: Type-safe test generation
- **JavaScript**: ES6+ test coverage
- **Java**: JUnit-style tests
- **C#**: NUnit/xUnit patterns
- **C++**: Google Test framework
- **Kotlin**: KotlinTest support
- **Python**: pytest-compatible tests

## Test Coverage Types

### Unit Tests
- Tests individual functions and methods
- Covers edge cases and error scenarios
- Validates input/output behavior
- Includes dependency mocking

### Integration Tests
- Tests component interactions (coming soon)
- Validates API endpoint behavior
- Checks database operations
- Verifies service communication

## Customizing Test Generation

### Setting Test Output Location

1. Navigate to Workflow Settings
2. Locate the Testing configuration section
3. Specify your preferred output folder
4. Default location is `orchestrai/tests`

### Configuring Ignored Folders

Prevent certain directories from test generation:

1. Go to Workflow Settings
2. Add folders to the ignored list
3. Common exclusions: `node_modules`, `dist`, `build`, `.git`

### Code Push Behavior

Control how tests are committed:

1. Access Workflow Settings
2. Find the "Code Push Behavior" option for Test Engineer
3. Choose your preference:
   - Create pull requests for review
   - Direct commit to branch
   - Custom branch naming

## Advanced Features

### Commit-Based Testing

Generate tests only for specific changes:

1. Enable commit-based scope in your configuration
2. Specify which commits to analyze
3. The AI focuses only on changed files
4. Useful for incremental test coverage improvements

### Batch Processing

Save costs with batch processing mode:

1. Select "Batch" execution mode
2. Tests generate asynchronously
3. Receive 50% cost savings
4. Ideal for large codebases or non-urgent testing

### Multi-Chunk Processing

For large repositories:
- The system automatically divides work into manageable chunks
- Each chunk processes independently
- Progress updates show chunk completion
- Ensures reliable processing of massive codebases

## Troubleshooting

### Repository Access Denied

If you see access errors:
1. Verify your GitHub token has correct permissions
2. Check that the repository exists and hasn't been deleted
3. Reconnect your GitHub account if needed
4. Ensure the repository URL is correct

### Test Generation Failed

Common solutions:
1. Check your workspace has sufficient credits
2. Verify the repository is accessible
3. Review any custom instructions for conflicts
4. Try again with a lower target percentage

### No Tests Generated

If no tests appear:
1. Confirm source files exist in the repository
2. Check ignored folders configuration
3. Verify supported languages are present
4. Review the execution log for details

### Billing Issues

If you receive billing errors:
1. Check your workspace credit balance
2. Verify your subscription is active
3. Review recent usage in billing dashboard
4. Contact support if charges seem incorrect

## Best Practices

### Optimal Coverage Targets

- Start with 70-80% for new projects
- Gradually increase to 85-90% over time
- 100% coverage may be excessive for some files
- Focus on critical business logic first

### Custom Instructions

Write clear, specific instructions:
- "Use Jest with React Testing Library"
- "Focus on API endpoint handlers in /src/api"
- "Mock external service calls"
- "Follow existing test file naming conventions"

### Regular Testing

- Generate tests after major feature additions
- Update coverage after refactoring
- Schedule periodic coverage improvements
- Review generated tests before merging

### Team Collaboration

- Share testing standards via custom instructions
- Review pull requests as a team
- Maintain consistent test organization
- Document framework preferences

## Credit Usage

Testing Suite operations consume credits based on:

- **AI Model Used**: Premium models cost more per operation
- **Repository Size**: Larger codebases require more analysis
- **Target Percentage**: Higher coverage goals use more credits
- **Execution Mode**: Batch mode provides 50% savings

Monitor usage:
1. Check the billing dashboard regularly
2. Review individual execution costs
3. Use batch mode for cost optimization
4. Choose appropriate AI models for your needs

## Email Notifications

You'll receive emails when:
- Test generation completes successfully
- A pull request is created with new tests
- Errors occur during generation
- Coverage targets are achieved

Email includes:
- Repository name
- Execution summary
- Direct link to results
- Next steps for review

## Getting Help

If you need assistance:

1. Check the status message in the coverage table
2. Review error details by hovering over failed status
3. Consult this documentation for common issues
4. Contact OrchestrAI support for complex problems

## Next Steps

After setting up your testing workflow:

1. Explore other OrchestrAI features like Documentation and Code Review
2. Configure additional repositories for testing
3. Set up automated testing in your CI/CD pipeline
4. Share testing results with your team

The Testing Suite helps you maintain high-quality, reliable code by automating the tedious process of test creation—letting you focus on building features while AI ensures comprehensive test coverage.