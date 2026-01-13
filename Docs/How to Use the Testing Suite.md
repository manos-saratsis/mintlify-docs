# How to Use the Testing Suite

## Overview

The Testing Suite automatically generates comprehensive test coverage for your code repositories using AI. The system analyzes your codebase, creates unit and integration tests, and pushes them directly to your repository—helping you ship with confidence.

## Getting Started

### Prerequisites

Before using the Testing Suite, you need:

1. **An Active Workspace** - Select your workspace from the top navigation bar
2. **Connected Repository** - Your code repository must be connected through the Connection Management area
3. **Sufficient Credits** - Test generation consumes workspace credits based on the AI model used

### Accessing the Testing Suite

1. Log into your OrchestrAI account
2. Select your workspace from the workspace dropdown
3. Navigate to the Testing page from the main menu
4. Click on any repository with unit test coverage to begin

## Understanding Test Coverage

### Coverage Metrics

The Testing Suite tracks two types of test coverage:

**Unit Test Coverage**: Tests individual functions, methods, and components in isolation. The system displays the current percentage of your code covered by unit tests.

**Integration Test Coverage**: Tests how different parts of your application work together, including API endpoints and service interactions.

### Reading the Repository Table

Each repository displays:

- **Repository Name**: The name and owner of your connected repository
- **Unit Test %**: Current unit test coverage percentage (click to improve)
- **Integration Status**: Current state of integration testing
- **Last Measured**: When coverage was most recently calculated

## Generating Tests

### Opening the AI Test Engineer

To generate tests for a repository:

1. Find your repository in the Repository Test Coverage table
2. Click the unit test percentage number for that repository
3. The AI Test Engineer panel opens on the right side

### Configuring Test Generation

The AI Test Engineer panel offers several configuration options:

**Target Coverage Percentage**
- Set your desired test coverage goal (0-100%)
- The AI generates enough tests to reach this target
- Higher percentages require more time and credits

**Custom Instructions**
- Specify testing frameworks to use (Jest, Pytest, JUnit, etc.)
- Indicate which files or directories to focus on
- Define test organization preferences
- Add any special requirements or constraints

**AI Model Selection**

Choose from available AI models based on your needs:

- **Claude Sonnet 4.5**: Most capable model for complex codebases with multiple languages and frameworks
- **GPT-5**: Advanced reasoning for sophisticated test scenarios
- **GPT-4o Mini**: Faster processing for straightforward testing needs
- **Claude Haiku 4.5**: Cost-effective option with good performance
- **Claude 3.5 Haiku**: Balanced performance and cost

**Processing Mode**

Select how tests are generated:

- **Now (Real-time)**: Tests generate immediately with live progress updates. Best for smaller codebases or urgent needs.
- **Batch**: Tests generate in the background at 50% cost savings. Results delivered when complete (typically within 24 hours). Only available with Claude Haiku 4.5.

### Starting Test Generation

After configuring your preferences:

1. Review your settings in the AI Test Engineer panel
2. Click the "Start Test Engineer" button
3. The panel closes and generation begins
4. Monitor progress in the repository table

## Monitoring Test Generation

### Real-Time Processing Status

When using "Now" mode, you'll see:

- **Processing**: The AI is analyzing your code structure
- **Analyzing**: Identifying what tests are needed
- **Generating**: Creating test files
- **Pushing**: Committing tests to your repository
- **Completed**: All tests successfully generated and pushed

### Batch Processing Status

When using "Batch" mode:

- **Processing**: Your request is queued
- Tests generate in the background
- You'll receive an email notification when complete
- Check back later to see results

### Progress Updates

The system provides real-time updates including:

- Current phase of test generation
- Number of test files created
- Time elapsed
- Any issues encountered

## Understanding Test Generation

### How the AI Analyzes Your Code

The AI Test Engineer follows a multi-phase process:

**Phase 1: Connectivity Check**
- Verifies access to your repository
- Confirms all necessary permissions
- Tests API connections

**Phase 2: Repository Analysis**
- Examines your code structure and dependencies
- Identifies programming languages and frameworks
- Detects existing test patterns
- Creates a strategic plan for test generation

**Phase 3: Test Generation**
- Generates test files based on the analysis
- Creates unit tests for functions and components
- Develops integration tests for interactions
- Includes edge cases and error scenarios

**Phase 4: Push to Repository**
- Commits generated tests to a new branch
- Creates a pull request (if configured)
- Or pushes directly to your default branch
- Updates coverage metrics

### Supported Technologies

The AI automatically detects and generates tests for:

- **Languages**: JavaScript, TypeScript, Python, Java, C#, C++, Kotlin
- **Frameworks**: React, Node.js, Django, Flask, Spring Boot, .NET, and more
- **Test Frameworks**: Jest, Mocha, Pytest, JUnit, NUnit, Google Test, and others

### Test Output Location

Generated tests are saved to your repository in:
- Default location: `orchestrai/tests/` directory
- You can customize this location in Workflow Settings

## Working with Generated Tests

### Reviewing Tests

After generation completes:

1. Open the pull request link shown in the execution results (if using PR mode)
2. Review the generated test files in your repository
3. Check that tests match your code's functionality
4. Run the tests locally to verify they pass

### Running Tests

To execute the generated tests:

1. Pull the test branch to your local environment
2. Install any required testing dependencies
3. Run your standard test commands (npm test, pytest, mvn test, etc.)
4. Review test results and coverage reports

### Merging Tests

When you're satisfied with the tests:

1. Approve the pull request (if using PR mode)
2. Merge into your main branch
3. Your CI/CD pipeline can now run these tests automatically
4. Coverage metrics update in OrchestrAI

## Advanced Features

### Commit-Based Test Generation

Generate tests only for specific changes:

1. The system can analyze specific commits
2. Tests are created only for modified files
3. Reduces generation time and costs
4. Ideal for continuous testing workflows

### Custom Test Instructions

Provide detailed guidance to the AI:

- "Use Jest with React Testing Library"
- "Focus on the src/components directory"
- "Include async operation tests"
- "Mock external API calls"
- "Follow our existing test structure in tests/examples"

### Progress Tracking

Monitor your testing journey:

- View historical test executions
- Track coverage improvements over time
- See which files have been tested
- Identify coverage gaps

### Continuous Testing Workflow

Integrate testing into your development process:

1. Connect your repository to OrchestrAI
2. Set target coverage goals
3. Generate initial test suite
4. Generate additional tests for new features
5. Maintain high coverage as code evolves

## Configuration Options

### Code Push Behavior

Control how tests are committed:

- **Pull Request**: Creates a new branch and pull request for review
- **Direct Push**: Commits tests directly to your default branch
- Configure this in Workflow Settings under Management

### Ignored Folders

Exclude directories from test generation:

1. Navigate to Management > Workflow Settings
2. Add folders to ignore (node_modules, build, dist, etc.)
3. These folders are skipped during analysis
4. Reduces processing time and focuses on relevant code

### Output Folder Configuration

Customize where tests are saved:

1. Go to Management > Workflow Settings
2. Set your preferred test output location
3. Default: `orchestrai/tests/`
4. Tests organize automatically by source file structure

## Troubleshooting

### No Repositories Showing

If you don't see any repositories:

- Verify a workspace is selected in the top navigation
- Check that you've connected repositories in Connection Management
- Ensure your GitHub/GitLab connection is active
- Refresh the page to reload repository data

### Test Generation Failed

If test generation encounters issues:

- Check that your repository still exists and is accessible
- Verify your GitHub token has sufficient permissions
- Review error messages in the execution history
- Try reconnecting your repository in Connection Management

### Coverage Not Updating

If coverage metrics don't update after tests are generated:

- Wait a few minutes for the system to process results
- Refresh the Testing page
- Check that tests were successfully pushed to your repository
- Verify the execution completed without errors

### Authentication Issues

If you see authentication errors:

- Your GitHub token may have expired
- Reconnect your GitHub account in Connection Management
- Ensure your token has repo access permissions
- Try disconnecting and reconnecting the repository

## Billing and Credits

### Understanding Costs

Test generation consumes workspace credits based on:

- **AI Model Used**: Different models have different costs
- **Code Complexity**: Larger, more complex codebases cost more
- **Target Coverage**: Higher coverage goals require more generation
- **Processing Mode**: Batch mode offers 50% savings over real-time

### Cost Optimization Tips

Reduce credit consumption:

- Use Batch mode when possible (50% savings)
- Select more efficient AI models for simpler codebases
- Exclude unnecessary folders in Workflow Settings
- Generate tests incrementally rather than all at once
- Use commit-based generation for new features only

### Monitoring Usage

Track your credit usage:

- View credit balance in your workspace dashboard
- Check consumption per test generation execution
- Review historical usage patterns
- Set up low-credit notifications

## Best Practices

### Setting Realistic Coverage Goals

- Start with 70-80% coverage for most projects
- 100% coverage may not be necessary or cost-effective
- Focus on critical business logic first
- Increase coverage incrementally over time

### Providing Clear Instructions

Help the AI generate better tests:

- Specify exact testing frameworks and tools
- Mention any mocking or stubbing requirements
- Indicate files or features to prioritize
- Reference existing test patterns to follow

### Reviewing Generated Tests

Always review tests before merging:

- Verify tests match your code's intent
- Check for proper assertions and expectations
- Ensure edge cases are covered appropriately
- Run tests locally to confirm they pass

### Integrating with CI/CD

Make testing automatic:

- Add generated tests to your CI/CD pipeline
- Run tests on every pull request
- Block merges if tests fail
- Track coverage metrics over time

### Maintaining Test Quality

Keep your test suite healthy:

- Update tests when code changes
- Remove outdated or irrelevant tests
- Regenerate tests for refactored code
- Monitor test execution times

## Getting Help

If you need assistance:

- Check error messages in the execution history for specific guidance
- Review repository connection settings in Connection Management
- Verify your workspace has sufficient credits
- Contact support if issues persist

## Next Steps

After generating your initial test suite:

1. Review and merge the generated tests
2. Run tests in your CI/CD pipeline
3. Generate additional tests for new features
4. Set up automated testing workflows
5. Monitor and maintain coverage over time

The Testing Suite helps you build confidence in your code with comprehensive, AI-generated tests that catch bugs before they reach production.