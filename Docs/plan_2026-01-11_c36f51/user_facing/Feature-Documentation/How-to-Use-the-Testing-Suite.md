# How to Use the Testing Suite

## Overview

The Testing Suite automatically generates comprehensive test coverage for your codebase using AI technology. Simply connect your repository, set your target coverage percentage, and let the AI Test Engineer analyze your code and create appropriate tests for all supported languages and frameworks.

## Getting Started

### Prerequisites

Before using the Testing Suite, you need:

1. **A Connected Repository**: Your GitHub, GitLab, or Bitbucket repository must be connected to OrchestrAI
2. **An Active Workspace**: Select a workspace from the top navigation bar
3. **Repository Access**: Ensure OrchestrAI has permission to read your code and commit changes

### Initial Setup

1. Navigate to the Testing page from your product dashboard
2. If you don't see any repositories listed, click the button to add a Git connection
3. Select the repositories you want to enable for automated testing
4. Your repositories will appear in the test coverage table with their current coverage percentages

## Understanding Test Coverage

### Coverage Metrics

The testing dashboard displays coverage information for each repository:

- **Unit Test Percentage**: Shows the current percentage of your code covered by unit tests (target: 85%)
- **Integration Test Status**: Indicates whether integration tests are available (currently in development)
- **Status Indicators**: Color-coded bars show your progress toward coverage goals

### Supported Technologies

The AI Test Engineer automatically detects and generates tests for:

- **Frontend**: React, TypeScript, JavaScript
- **Backend**: Java, C#, C++, Kotlin, Python
- **Test Frameworks**: Automatically detects the appropriate testing framework for your project

## Generating Tests

### Basic Test Generation

1. **Select a Repository**: Click on the unit test percentage for any repository in the coverage table
2. **Set Your Target**: Choose your desired test coverage percentage (up to 100%)
3. **Provide Instructions** (optional): Add specific requirements such as:
   - Preferred testing framework
   - Files or folders to focus on
   - Test organization preferences
   - Edge cases to cover
4. **Choose Processing Mode**:
   - **Now**: Generate tests immediately (faster results, standard cost)
   - **Batch**: Process when capacity is available (50% cost savings, completed within 24 hours)
5. **Start Generation**: Click to begin the automated test generation process

### Custom Instructions Examples

You can guide the AI Test Engineer with specific instructions:

- "Focus on testing the authentication module"
- "Use Jest for all JavaScript tests"
- "Prioritize edge case coverage for API endpoints"
- "Organize tests by feature rather than file structure"
- "Include integration tests for database operations"

### Scope Options

Choose what to test:

- **Full Repository**: Analyze and generate tests for the entire codebase
- **Specific Commits**: Focus on testing only the files changed in particular commits (useful for incremental testing)

## How Test Generation Works

### Phase 1: Repository Analysis

The AI examines your codebase to understand:

- Code structure and organization
- Programming languages and frameworks in use
- Existing test patterns and conventions
- Dependencies and interactions between components
- Coverage gaps that need attention

This analysis takes a few minutes and provides a comprehensive understanding of your testing needs.

### Phase 2: Intelligent Test Creation

Based on the analysis, the AI generates:

- **Unit Tests**: Comprehensive tests for individual functions and methods
- **Edge Case Coverage**: Tests for boundary conditions and error scenarios
- **Dependency Mocking**: Appropriate mocks and stubs for external dependencies
- **Assertion Validation**: Proper verification of expected behavior

The AI creates tests that follow your project's conventions and use the appropriate testing framework automatically.

### Phase 3: Results Delivery

Once generation completes:

- Test files are organized in a dedicated folder (default: `orchestrai/tests`)
- Tests are committed to your repository based on your workspace settings
- You receive a notification when the process completes
- Coverage metrics update automatically

## Tracking Progress

### Real-Time Status Updates

Monitor test generation progress through:

- **Status Column**: Shows current phase (analyzing, generating, pushing, completed)
- **Progress Indicators**: Visual feedback on generation status
- **File Counts**: Number of test files created
- **Completion Notifications**: Email alerts when generation finishes

### Execution History

View past test generation runs:

- Click on any repository to see its execution history
- Review previous coverage improvements
- Check commit links for generated tests
- View pull request URLs if your workspace uses PR-based delivery

## Test Execution Modes

### Real-Time Processing

Best for:
- Urgent testing needs
- Small to medium repositories
- When you need results quickly

How it works:
- Processes immediately upon request
- Completes within minutes to hours depending on repository size
- Uses premium AI models for fastest results
- Standard credit usage applies

### Batch Processing

Best for:
- Large repositories
- Cost-conscious projects
- When you can wait up to 24 hours

How it works:
- Queued for processing during off-peak times
- Uses efficient batch API for 50% cost savings
- Automatically processes when capacity is available
- Same quality results at lower cost

## Delivery Options

### Direct Commit

Tests are committed directly to your repository's main branch:
- Immediate integration with your codebase
- No review process required
- Fastest path to improved coverage

### Pull Request Workflow

Tests are submitted via pull request:
- Review generated tests before merging
- Add comments or request changes
- Maintain team approval processes
- Better for collaborative environments

Configure your preferred delivery method in Workspace Settings under Code Push Behavior.

## Understanding Test Output

### Test File Organization

Generated tests are organized logically:

- Tests mirror your source code structure
- Each source file gets corresponding test files
- Tests are grouped by feature or module
- Clear naming conventions for easy navigation

### Test File Location

By default, tests are saved to `orchestrai/tests/`, but you can customize this location in Workflow Settings under Output Folders.

## Coverage Goals and Progress

### Setting Targets

Choose coverage percentages based on your needs:

- **70-80%**: Basic coverage for most projects
- **85%**: Recommended enterprise standard
- **90-100%**: Comprehensive coverage for critical systems

### Monitoring Improvement

Track your progress over time:

- Coverage percentages update after each generation
- Compare current coverage to target goals
- Identify remaining gaps
- Plan incremental improvements

## Best Practices

### Starting with Test Generation

1. **Begin Small**: Start with one repository to understand the process
2. **Review Results**: Check the first batch of generated tests before scaling up
3. **Provide Feedback**: Use custom instructions to guide future generations
4. **Set Realistic Targets**: Aim for 85% coverage initially, then increase if needed

### Optimizing Test Quality

- **Be Specific**: Detailed instructions produce more relevant tests
- **Incremental Approach**: Generate tests for new code as it's written using commit-scope
- **Regular Updates**: Run generation periodically to maintain coverage as code evolves
- **Review and Refine**: Examine generated tests to ensure they meet your standards

### Managing Costs

- **Use Batch Mode**: Save 50% on large repositories when time permits
- **Scope Wisely**: Use commit-based scope for incremental testing
- **Set Appropriate Targets**: Higher coverage percentages require more generation time
- **Monitor Usage**: Check your workspace credit consumption regularly

## Troubleshooting

### No Repositories Showing

If you don't see repositories:
- Ensure you've connected a Git provider in Connection Management
- Verify your workspace is selected in the top navigation
- Check that repositories are enabled for OrchestrAI

### Generation Failures

If test generation fails:
- Verify repository access permissions
- Check that your GitHub token is still valid
- Review error messages for specific issues
- Try reconnecting your Git provider

### Incomplete Coverage

If coverage doesn't reach your target:
- Review custom instructions for clarity
- Check for complex code that may need manual testing
- Consider running generation multiple times
- Examine which files were skipped and why

## Integration with Development Workflow

### Continuous Testing

Incorporate automated test generation into your workflow:

1. **New Features**: Generate tests for newly committed code using commit scope
2. **Code Reviews**: Include test coverage in your review criteria
3. **Pre-Deployment**: Ensure adequate test coverage before releases
4. **Maintenance**: Update tests when refactoring existing code

### CI/CD Integration

While OrchestrAI generates tests, you run them using your existing tools:

- Generated tests work with your current test runners
- Integrate test execution into your CI/CD pipeline
- Monitor test results alongside your other quality metrics
- Use generated tests in automated deployment gates

## Getting Help

If you need assistance:

- Check execution history for detailed error messages
- Review repository settings for configuration issues
- Contact support with specific execution IDs for faster resolution
- Consult workspace members with management permissions for settings changes

## Next Steps

After setting up automated testing:

1. Explore other OrchestrAI features like documentation generation and code review
2. Configure workspace-level settings for consistent behavior across repositories
3. Set up notifications to stay informed of test generation completion
4. Establish team processes for reviewing and maintaining generated tests