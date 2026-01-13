# How to Use the Testing Suite

## Overview

The Testing Suite automatically generates comprehensive test coverage for your code repositories using AI technology. The system analyzes your codebase, creates appropriate tests, and commits them directly to your repository—helping you maintain high-quality code without manual test writing.

## Getting Started

### Prerequisites

Before using the Testing Suite, you need:

1. **A Connected Repository**: Link your GitHub, GitLab, or Bitbucket repository through the Code Management section
2. **An Active Workspace**: Select a workspace from the top navigation bar
3. **Repository Access**: Ensure your connected account has write permissions to the repository

### Initial Setup

1. Navigate to the Testing page from the product dashboard
2. If you don't have any repositories connected yet, click the "Add Git Connection" button
3. Authorize OrchestrAI to access your repositories
4. Your connected repositories will appear in the Repository Test Coverage table

## Generating Tests

### Starting Test Generation

1. **Open the Test Engineer Panel**: Click the flask icon in the Repository Test Coverage section
2. **Select Your Repository**: The panel displays your available repositories with their current test coverage
3. **Set Your Coverage Target**: Use the slider to choose your desired test coverage percentage (0-100%)
4. **Choose AI Provider**: Select from available AI models:
   - **Claude Sonnet 4.5**: Premium quality, best for complex codebases
   - **GPT-5**: Advanced reasoning for intricate test scenarios
   - **GPT-4o Mini**: Fast and cost-effective for standard projects
   - **Claude Haiku**: Budget-friendly option with good performance
   - **Claude 3.5 Haiku**: Balanced quality and speed

5. **Select Execution Mode**:
   - **Real-time**: Tests generate immediately with live progress updates
   - **Batch**: Processes in the background with 50% cost savings (available with Claude 3.5 Haiku)

6. **Add Custom Instructions** (Optional): Provide specific requirements such as:
   - Preferred testing framework (Jest, PyTest, JUnit, etc.)
   - Specific files or folders to focus on
   - Special testing patterns or conventions
   - Edge cases to prioritize

7. **Start Generation**: Click "Generate Tests" to begin

### Monitoring Progress

Once generation starts, you can track progress through:

- **Status Updates**: Real-time status shows current phase (Connectivity Check, Analyzing, Generating, Pushing)
- **Progress Indicators**: Visual progress bars display completion percentage
- **File Counts**: See how many test files have been generated
- **Execution History**: View past test generation runs in the repository table

### Understanding Test Generation Phases

The system works through multiple phases automatically:

**Phase 1 - Repository Analysis**: The AI examines your codebase structure, identifies programming languages, detects frameworks, and creates a test generation plan divided into manageable chunks.

**Phase 2 - Test Creation**: For each chunk of your code, the AI generates appropriate tests including unit tests for individual functions, integration tests for component interactions, and comprehensive edge case coverage.

**Phase 3 - Code Delivery**: Generated tests are committed to your repository according to your configured push behavior (direct commit, pull request, or branch creation).

## Supported Technologies

The Testing Suite automatically detects and generates tests for:

- **Languages**: TypeScript, JavaScript, Java, C#, C++, Kotlin, Python, React
- **Frameworks**: Automatically identified from your codebase
- **Test Runners**: Jest, PyTest, JUnit, NUnit, and more (based on your project setup)

## Test Coverage Tracking

### Understanding Coverage Metrics

The repository table displays:

- **Unit Test Percentage**: Current coverage level for unit tests
- **Integration Test Status**: Availability of integration test coverage
- **Last Measured**: When coverage was last calculated
- **Commit Information**: Which code version was tested

### Improving Coverage

To increase test coverage:

1. Click on the current coverage percentage in the repository table
2. The Test Engineer panel opens with your repository pre-selected
3. Set a higher target percentage than current coverage
4. Generate tests to reach your new goal

## Working with Test Results

### Accessing Generated Tests

After generation completes, tests are available in your repository:

- **Default Location**: Tests are saved in the `orchestrai/tests` folder
- **Custom Location**: Configure output folder in Workflow Settings if needed
- **File Organization**: Tests mirror your source code structure for easy navigation

### Test File Naming

Generated test files follow standard naming conventions:
- JavaScript/TypeScript: `filename.test.ts` or `filename.spec.ts`
- Python: `test_filename.py`
- Java: `FilenameTest.java`
- C#: `FilenameTests.cs`

### Reviewing Results

Each completed execution provides:

- **Commit Link**: Direct link to view changes in your repository
- **Pull Request**: If configured, a PR is created for review
- **File Count**: Total number of test files generated
- **Execution Details**: Complete log of the generation process

## Advanced Features

### Commit-Based Testing

Generate tests for specific code changes:

1. Select "Commits" scope type when configuring generation
2. Specify commit SHAs to analyze
3. The AI focuses only on files changed in those commits

This is useful for:
- Adding tests to recent feature additions
- Improving coverage for specific pull requests
- Testing hotfix changes

### Custom Test Instructions

Provide detailed requirements to shape test generation:

**Framework Preferences**:
```
Use Jest for all TypeScript tests
Follow React Testing Library patterns
```

**Coverage Focus**:
```
Prioritize API endpoint testing
Include database interaction tests
Focus on error handling scenarios
```

**Project Conventions**:
```
Place tests alongside source files
Use describe blocks for component organization
Mock external API calls
```

### Ignored Folders

Configure folders to skip during test generation:

1. Navigate to Workflow Settings
2. Find the "Ignored Folders" section
3. Add folders like `node_modules`, `build`, `dist`, or vendor directories
4. Tests won't be generated for code in these locations

### Output Folder Configuration

Customize where tests are saved:

1. Go to Workflow Settings
2. Locate "Output Folders" configuration
3. Set your preferred test directory path
4. All generated tests will be saved to this location

## Code Push Behavior

Control how tests are delivered to your repository:

### Direct Commit
Tests are committed directly to your default branch. Use this for:
- Personal projects
- Quick updates
- Trusted automated changes

### Pull Request
Tests are committed to a new branch with an automatic pull request. Use this for:
- Team projects requiring review
- Production codebases
- Environments with branch protection

### Branch Only
Tests are committed to a new branch without creating a pull request. Use this for:
- Manual review workflows
- Integration with custom CI/CD processes

Configure this setting in Workflow Settings under "Code Push Behavior."

## Execution History

### Viewing Past Executions

The repository table shows recent test generation runs:

- **Status**: Current state (Processing, Completed, Failed)
- **Timestamp**: When execution started
- **Progress**: Completion percentage for in-progress runs
- **Results**: Links to commits or pull requests

### Execution Details

Click on an execution to view:
- Complete generation log
- Files created
- Coverage achieved
- Any errors encountered
- AI model used
- Total processing time

## Troubleshooting

### Generation Fails to Start

**Repository Access Issues**:
- Verify your GitHub connection is active
- Check repository permissions allow write access
- Reconnect your GitHub account if token expired

**Configuration Problems**:
- Ensure a workspace is selected
- Confirm repository is properly connected
- Check that you have available credits

### Tests Don't Appear

**Check Output Location**:
- Verify output folder configuration in Workflow Settings
- Look for the `orchestrai/tests` folder by default
- Review commit or pull request for file locations

**Push Behavior Settings**:
- If set to "Pull Request," check for open PRs
- If set to "Branch Only," switch to the new branch
- Review execution logs for push errors

### Low Coverage Results

**Increase Target Percentage**:
- Set a higher coverage goal when generating
- Run generation multiple times to build up coverage
- Focus on specific files with custom instructions

**Provide Better Context**:
- Add detailed instructions about testing requirements
- Specify important files or features to prioritize
- Include examples of existing test patterns

## Best Practices

### Starting Small
Begin with a 50-60% coverage target for your first run. Review the generated tests, then increase gradually to reach higher coverage goals.

### Regular Updates
Run test generation after major features or refactoring to maintain coverage as your codebase evolves.

### Review Generated Tests
Even though tests are automatically created, review them to ensure they match your quality standards and testing philosophy.

### Custom Instructions
Provide clear, specific instructions about your testing preferences to get better results aligned with your project's needs.

### Scope Appropriately
For large repositories, consider using commit-based scoping to generate tests incrementally rather than all at once.

### Monitor Credits
Test generation consumes AI credits based on codebase size and chosen model. Check your workspace credits before starting large generation runs.

## Cost Management

### Execution Modes

**Real-time Mode**: 
- Processes immediately
- Live progress updates
- Full credit cost
- Best for urgent needs

**Batch Mode**:
- Processes in background
- 50% cost savings
- Available with Claude 3.5 Haiku
- Best for large codebases

### Model Selection Impact

Different AI models have different credit costs:
- **Premium models** (Sonnet 4.5, GPT-5): Higher quality, higher cost
- **Standard models** (GPT-4o Mini): Balanced performance and cost
- **Economy models** (Haiku variants): Budget-friendly with good results

Choose based on your quality requirements and budget.

## Email Notifications

After test generation completes, you'll receive an email notification containing:
- Generation status (success or failure)
- Repository name
- Link to results (commit or pull request)
- Summary of files generated

Configure notification preferences in your workspace settings.

## Integration with CI/CD

Generated tests integrate seamlessly with your existing development workflow:

1. **Tests Follow Conventions**: Generated tests use standard naming and structure recognized by test runners
2. **Framework Detection**: The AI identifies your testing framework and generates compatible tests
3. **Immediate Execution**: Run generated tests with your normal test commands
4. **Coverage Tools**: Generated tests work with coverage reporters like Jest coverage, Coverage.py, JaCoCo, etc.

No special configuration needed—tests work with your existing setup.

## Getting Help

If you encounter issues or have questions:

- Check execution logs for detailed error messages
- Review repository connection status
- Verify workspace permissions
- Contact support with execution ID for assistance