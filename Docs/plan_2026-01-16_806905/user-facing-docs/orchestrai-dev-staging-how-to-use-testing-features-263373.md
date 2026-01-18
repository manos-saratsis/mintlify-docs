# How to Use Testing Features

## Overview

The AI-Powered Testing feature automatically generates comprehensive test suites for your code repositories. Using advanced AI, it analyzes your codebase and creates unit tests, integration tests, and edge case scenarios to improve code reliability and coverage.

## Getting Started

### Prerequisites

Before using the Testing feature, ensure you have:

1. **Connected Repository**: A GitHub, GitLab, or Bitbucket repository linked to your workspace
2. **Active Workspace**: A workspace with appropriate permissions
3. **Available Credits**: Sufficient credits in your plan for AI test generation

### Accessing the Testing Dashboard

1. Navigate to the Testing page from the main product menu
2. Select your active workspace from the top navigation bar
3. View all connected repositories with their current test coverage metrics

## Understanding Test Coverage

### Coverage Metrics

Your dashboard displays coverage information for each repository:

- **Unit Test Percentage**: Shows current test coverage (0-100%)
- **Coverage Status**: Visual indicators showing progress toward testing goals
- **Repository Details**: Name, full path, and connection status

### Coverage Levels

The system offers three pre-configured coverage targets:

- **Full Coverage (100%)**: Comprehensive testing for all code paths
- **Most Important Tests (80%)**: Focus on critical functionality
- **Basic (60%)**: Essential test coverage for core features

## Generating Tests

### Starting Test Generation

1. **Locate Your Repository**: Find the repository in the Testing dashboard
2. **Click the Coverage Percentage**: Click on the unit test percentage to open the AI Test Engineer panel
3. **Configure Options**: Set your test generation preferences
4. **Start Generation**: Click "Create new Tests" to begin

### Configuration Options

#### Test Coverage Level

Choose your target coverage:
- Select from Full Coverage, Most Important Tests, or Basic
- The AI will analyze your code and generate tests to reach this target
- Current coverage is displayed for reference

#### Generation Scope

Select what to test:

**Whole Repository**
- Generates tests for all source files
- Provides comprehensive coverage across your codebase
- Ideal for new projects or major coverage improvements

**Selected Commits**
- Focus on recently changed files
- Select specific commits from the recent history
- More targeted and efficient for incremental updates
- Use "Select Last 5 Commits" for quick selection

#### Model Selection

Choose your AI model and execution mode:

**Model Options**
- **Haiku**: Fast, cost-effective for standard testing needs
- **Sonnet**: Advanced analysis for complex code patterns
- **Opus**: Premium model for sophisticated testing requirements

**Execution Mode**
- **Real-time**: Generate tests immediately with live progress updates
- **Batch**: Cost-saving mode (50% reduction) with asynchronous processing

#### Custom Instructions

Provide additional guidance for test generation:
- Specify testing frameworks (Jest, Mocha, PyTest, JUnit, etc.)
- Define file organization preferences
- Request specific test patterns or approaches
- Add any custom requirements

The AI automatically detects and supports: React, TypeScript, JavaScript, Java, C#, C++, Kotlin, and Python.

### Monitoring Progress

#### Progress Dialog

When test generation starts, a progress dialog displays:

1. **Current Phase**: Shows which stage is running
   - Connectivity Check: Verifying repository access
   - Repository Analysis: Analyzing code structure
   - Test Generation: Creating test files
   - Push to GitHub: Committing tests to repository

2. **Processing Status**: Real-time updates on chunks being processed
3. **File Count**: Number of test files generated
4. **Completion Percentage**: Overall progress indicator

#### Background Processing

You can continue work while tests generate:
- Close the progress dialog to return to other tasks
- Test generation continues in the background
- Return to the Testing dashboard to check status
- Receive notifications when generation completes

## Reviewing Generated Tests

### Accessing Test Results

After generation completes:

1. **View Summary**: Check the completion notification for overview
2. **Open Test Folder**: Click "Open test folder" to view generated tests in your repository
3. **Review Coverage**: Updated coverage percentage appears in the dashboard

### Test File Organization

Generated tests are organized in your repository:
- Default location: `orchestrai/tests` folder
- Tests mirror your source code structure
- Each source file has corresponding test files
- Clear naming conventions for easy identification

### Understanding Test Quality

The AI generates tests with:
- **Comprehensive Coverage**: Tests for all major code paths
- **Edge Cases**: Scenarios for boundary conditions and error states
- **Framework Compliance**: Tests follow your specified framework patterns
- **Best Practices**: Industry-standard test structure and assertions

## Integrating Tests

### Running Tests Locally

1. **Pull Latest Changes**: Get the generated tests from your repository
2. **Install Dependencies**: Ensure testing frameworks are installed
3. **Run Test Suite**: Execute tests using your project's test command
4. **Review Results**: Check for any failures or warnings

### CI/CD Integration

Generated tests work with existing pipelines:
- Tests appear as standard files in your repository
- Compatible with GitHub Actions, GitLab CI, Jenkins, and other platforms
- No special configuration needed
- Run alongside your existing test suite

### Modifying Generated Tests

You can customize generated tests:
- Edit test files like any other code
- Add additional test cases as needed
- Adjust assertions for specific requirements
- Update as your code evolves

## Maintaining Tests

### Updating Tests for Code Changes

When you modify code:

1. **Use Commit-Based Generation**: Select recent commits to update related tests
2. **Target Specific Areas**: Focus on changed files rather than full repository
3. **Incremental Updates**: Generate new tests only for modified functionality
4. **Merge with Existing**: New tests integrate with previously generated ones

### Coverage Tracking

Monitor test coverage over time:
- Dashboard shows current coverage percentage
- Track improvements after each generation
- Identify areas needing additional testing
- Set goals for coverage targets

### Best Practices

**Regular Updates**
- Generate tests for new features immediately
- Update tests when refactoring code
- Review and maintain test quality periodically

**Efficient Generation**
- Use commit-based scope for incremental changes
- Reserve full repository generation for major updates
- Choose appropriate coverage levels for your needs

**Quality Assurance**
- Review generated tests before deploying
- Run tests locally to verify functionality
- Address any test failures promptly
- Keep test instructions updated for consistency

## Understanding Test Results

### Execution Records

The Testing dashboard tracks all test generations:
- View history of past executions
- Check status (completed, in progress, failed)
- See which commits were tested
- Access generated pull requests or commits

### Result Notifications

You receive notifications when:
- Test generation completes successfully
- Errors occur during generation
- Tests are committed to your repository
- Pull requests are created with new tests

### Troubleshooting

If test generation fails:

1. **Check Repository Access**: Verify connection is active
2. **Review Error Message**: Read the specific error details
3. **Verify Permissions**: Ensure your GitHub token has write access
4. **Try Again**: Use "Try Again" button with adjusted settings

Common issues:
- **Repository Not Found**: Repository may be deleted or access revoked
- **Insufficient Permissions**: GitHub token needs additional scopes
- **No Tests Generated**: Repository structure may not contain testable code
- **API Limits**: Wait and retry, or upgrade your plan

## Advanced Features

### Multi-Language Support

The AI automatically handles:
- Mixed-language repositories
- Framework-specific patterns
- Language-appropriate test structures
- Technology-specific best practices

### Test Strategy Analysis

For repositories at 100% coverage:
- Generate advanced test strategies
- Review comprehensive test recommendations
- Identify testing improvements
- Plan future testing enhancements

### Workspace Settings

Administrators can configure:
- Enable or disable testing for the workspace
- Set default testing preferences
- Configure output folder locations
- Manage ignored folders for test generation

Navigate to Workflow settings to adjust these configurations.

## Credit Usage

### Understanding Costs

Test generation consumes workspace credits:
- **Real-time Mode**: Standard credit usage
- **Batch Mode**: 50% cost reduction (Haiku model only)
- **Model Selection**: Different models have different credit costs

### Managing Credits

Monitor your credit balance:
- Check available credits before generation
- View usage in workspace settings
- Upgrade plan if monthly limit reached
- Daily limits reset automatically

### Cost Optimization

Reduce credit usage by:
- Using commit-based scope for smaller changes
- Selecting Batch mode when available
- Choosing Haiku model for standard testing
- Setting appropriate coverage targets

## Permissions and Access

### User Permissions

Access to testing features depends on:
- **Free Plans**: Full access to all users
- **Paid Plans**: Permission-based access controlled by administrators

If you see "No Permission" message, contact your workspace administrator.

### Repository Permissions

Your GitHub connection needs:
- Read access to repository content
- Write access to commit generated tests
- Permission to create pull requests (depending on settings)

Reconnect your GitHub account if permission errors occur.

## Getting Help

### Support Resources

If you need assistance:
- Review error messages for specific guidance
- Check repository connection status
- Verify workspace credit balance
- Contact support for persistent issues

### Tips for Success

**First-Time Users**
- Start with a small repository to understand the process
- Use Basic coverage (60%) initially
- Review generated tests to learn patterns
- Gradually increase coverage targets

**Experienced Users**
- Leverage commit-based generation for efficiency
- Use custom instructions for specific requirements
- Integrate into development workflow
- Maintain tests alongside code changes

The AI-Powered Testing feature helps you build comprehensive test suites quickly, improving code quality and reliability across your entire codebase.