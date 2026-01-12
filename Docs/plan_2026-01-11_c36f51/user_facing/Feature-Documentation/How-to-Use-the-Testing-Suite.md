I'll read the critical source files first to understand the testing suite functionality.# How to Use the Testing Suite

## Overview

The Testing Suite is your AI-powered assistant for maintaining code quality through automated test generation. The system analyzes your codebase and creates comprehensive test suites, including unit tests, integration tests, and edge case scenarios, while continuously tracking coverage metrics to help you maintain high-quality, well-tested code.

## Getting Started

### What You Need

Before you begin testing:
- An active account with workspace access
- At least one repository connected to your workspace
- Proper permissions to manage testing activities

### Opening the Testing Dashboard

1. Sign into your account
2. Choose your workspace from the top menu
3. Click on Testing in the navigation

If you haven't connected any repositories yet, you'll see a message with a button to add your first Git connection. Click it to get started.

## Understanding Your Test Coverage

### Reading the Coverage Dashboard

When you open the Testing page, you'll see a dashboard showing all your connected repositories with their test coverage information:

- **Repository Name**: Which codebase is being tracked
- **Unit Test Coverage**: The percentage of your code covered by unit tests
- **Integration Test Coverage**: Integration test status (this feature is coming soon)
- **Last Updated**: When the coverage information was last refreshed

### What Coverage Percentages Mean

Coverage numbers tell you how well your code is protected by tests:

- **85% or higher**: Excellent protection with comprehensive test coverage
- **70-84%**: Good coverage with a solid foundation, some room for improvement
- **Below 70%**: Needs attention - there are significant gaps in test coverage

Higher coverage means more of your code is verified by automated tests, reducing the chance of bugs reaching production.

## Generating Tests Automatically

### How AI Creates Your Tests

The AI Test Engineer examines your code and automatically writes appropriate tests for you:

1. **Find Your Repository**: Look for the repository you want to improve in the dashboard
2. **Click the Coverage Number**: Click on the unit test percentage shown for that repository
3. **Review Current Status**: A panel opens showing your current coverage details
4. **Choose Your Target**: Set the coverage percentage you want to achieve
5. **Add Special Requirements** (Optional): Include any specific testing instructions or preferences
6. **Pick Your AI Provider**: Select which AI model should generate the tests
7. **Begin Generation**: Click to start creating your test suite

### What Tests You'll Get

The AI creates a complete testing package:

- **Unit Tests**: Tests for individual functions and methods, including edge cases
- **Integration Tests**: Tests for how components work together (coming soon)
- **Edge Case Testing**: Tests for unusual inputs, boundary conditions, and error scenarios
- **Mock Dependencies**: Proper test isolation so tests run reliably

### Languages and Frameworks Supported

Tests are generated for all major programming languages:
- React and TypeScript
- JavaScript
- Java
- C#
- C++
- Kotlin
- Python

The system detects your technology automatically and generates tests using the right testing framework for your project.

## Customizing Test Generation

### Adding Custom Instructions

You can guide how tests are created by providing instructions:

- **Testing Framework**: Specify which testing library you prefer
- **File Focus**: Target specific folders or files that need more coverage
- **Test Structure**: Describe how you want tests organized
- **Priority Areas**: Emphasize certain parts of your code over others
- **Special Requirements**: Include any unique testing needs for your project

### Choosing What to Test

Select the scope of test generation:
- Create tests for your entire repository
- Focus on specific files or folders
- Target only untested code
- Update coverage in areas with existing tests

## Tracking Test Generation Progress

### Watching Progress in Real-Time

While the AI generates your tests, you can see:

- **Current Status**: Which file is being processed right now
- **Files Processed**: How many files have been completed
- **Progress Bar**: Visual indicator showing how close you are to completion
- **Detailed Reports**: Full summary when generation finishes

### When Generation Completes

After test generation finishes, you'll receive:
- A summary of coverage improvements
- List of files where new tests were added
- Any warnings or issues that came up
- Your new, updated coverage percentage

## Managing Generated Tests

### How Tests Are Saved

Generated tests are automatically saved to your repository:
- Tests go into the appropriate test folders
- Commit messages clearly mark them as AI-generated
- File structure follows your repository's conventions
- Tests are ready to run immediately

### Updating Coverage Information

To see the latest coverage numbers:

1. Find the "Refresh" button at the top of the coverage dashboard
2. Click it to update all repository information
3. Wait a moment while the latest data loads
4. View your updated coverage percentages

Coverage automatically updates after each test generation, but you can manually refresh anytime you want current information.

## Integrating with Your Workflow

### Working with Your Development Process

The Testing Suite fits naturally into how you already work:

- **CI/CD Support**: Generated tests work with your continuous integration pipeline
- **Framework Matching**: Tests use the same testing frameworks you already use
- **Git Integration**: All changes flow through your normal Git workflow
- **Team Access**: Everyone on your team can immediately access the new tests

### Benefits for Quality Assurance

Automated testing helps you:
- **Find Bugs Early**: Catch problems before they reach production
- **Prevent Regressions**: Make sure new changes don't break existing features
- **Document Behavior**: Tests show how code is supposed to work
- **Ship with Confidence**: Know your features are thoroughly tested

## Managing Your Repositories

### Viewing All Your Repositories

The main testing dashboard displays all repositories in your workspace, showing:
- Current test coverage for each one
- Recent test generation activity
- Coverage trends over time
- Quick access to improve coverage

### Adding More Repositories

To enable testing for additional repositories:

1. Go to the Code page from the main menu
2. Click the "Connection Management" tab
3. Connect new repositories to your workspace
4. Return to the Testing page to see them appear in the dashboard

## Best Practices for Testing

### Building Good Coverage

To get the most from automated testing:

- **Start with Where You Are**: Generate initial tests to see your current coverage level
- **Set Achievable Goals**: Target 80-85% coverage as a practical goal
- **Improve Step by Step**: Increase coverage gradually rather than trying to reach 100% immediately
- **Review What's Generated**: Look at the AI-generated tests to make sure they fit your needs
- **Guide Complex Cases**: Use custom instructions for complicated testing scenarios

### Keeping Tests Effective

Maintain high-quality test suites by:
- **Updating Regularly**: Regenerate tests when your code changes significantly
- **Watching Trends**: Monitor coverage over time to spot quality issues
- **Running Tests Often**: Execute your test suite regularly to catch problems quickly
- **Fixing Failures**: Investigate and resolve failing tests promptly

## Troubleshooting Common Issues

### No Repositories Showing Up

If you don't see repositories in the testing dashboard:
- Make sure you've selected a workspace from the top menu
- Confirm your repositories are connected through the Code page
- Check that you have the right permissions for this workspace

### Coverage Numbers Not Changing

If coverage metrics appear outdated:
- Click the "Refresh" button to manually update
- Verify that test generation completed successfully
- Make sure your repository connection is still active

### Problems During Test Generation

If test generation runs into issues:
- Read any error messages in the completion notification
- Check that your repository is accessible
- Verify the files are in supported programming languages
- Try generating tests for a smaller number of files first

## Getting Support

If you need help with the Testing Suite:
- Check the pricing page to see which features are available in your plan
- Contact support through the main navigation menu
- Browse additional documentation for more detailed information
- Verify your workspace permissions if certain features aren't available