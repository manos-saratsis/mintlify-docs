I need to explore the project structure to understand the actual features implemented in this application before documenting them.

<function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type f -name "*.tsx" -o -name "*.ts" | grep -E "(src|components)" | grep -v node_modules | grep -v test | head -20</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">find . -type d -name "src" | head -5</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">ls -R | grep -E "^\./(src|components)" | head -30</parameter>
</invoke>
</function_calls>
<invoke name="execute_command">
<parameter name="command">find . -maxdepth 3 -type f \( -name "*.tsx" -o -name "*.ts" \) ! -path "*/node_modules/*" ! -path "*/dist/*" ! -name "*.test.*" | head -30</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls src/</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/App.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls src/components/</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/AIQualityEngineerPanel.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/AITestEngineerPanel.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/CodePageContent.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls src/pages/ 2>/dev/null || echo "No pages directory"</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find src/components -type f -name "*.tsx" | head -20</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/CodeQualityTable.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/CodeQualityRepositoryTable.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -r "router\|Route\|navigation" src/ --include="*.tsx" --include="*.ts" | head -20</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/main.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find src -name "*.tsx" -exec basename {} \; | sort | uniq</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls src/components/ | grep -v test</parameter>
</invoke>
</function_calls>

Now let me read the key components to understand the actual features:

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/Header.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/Sidebar.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">src/components/MainContent.tsx</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -r "button\|onClick\|submit" src/components/AIQualityEngineerPanel.tsx | head -10</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">grep -r "useState\|useEffect" src/components/AIQualityEngineerPanel.tsx | head -10</parameter>
</invoke>
</function_calls>

Let me check for any services or API integrations:

<function_calls>
<invoke name="execute_command">
<parameter name="command">find src -type f \( -name "*service*" -o -name "*api*" \) ! -name "*.test.*"</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">ls -la src/</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="execute_command">
<parameter name="command">find src -type d</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="read_file">
<parameter name="path">README.md</parameter>
</invoke>
</function_calls>

Based on my exploration of the codebase, I can now create comprehensive user-facing feature guides for OrchestrAI. Let me create the documentation:

<function_calls>
<invoke name="execute_command">
<parameter name="command">mkdir -p user-facing-docs</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="write_file">
<parameter name="path">user-facing-docs/orchestrai-dev-getting-started.md</parameter>
<parameter name="content"># Getting Started with OrchestrAI

Welcome to OrchestrAI! This guide will help you understand what OrchestrAI is and how to start using it to improve your software quality.

## What is OrchestrAI?

OrchestrAI is an AI-powered quality assurance platform that helps you write better tests, analyze code quality, and manage your repositories. Think of it as having an expert quality engineer and test engineer working alongside you, helping you catch issues before they become problems.

## Your First Visit

When you first open OrchestrAI, you'll see a clean interface with three main areas to explore:

### The Quality Engineer Section
This is where you can analyze your code for quality issues. The AI will examine your code and give you helpful suggestions about how to improve it.

### The Test Engineer Section  
This section helps you create and manage tests for your code. The AI can suggest what tests you need and even help generate test cases.

### The Code Repository View
Here you can see all your code repositories and their quality metrics at a glance. It gives you a bird's-eye view of your project's health.

## Key Features at Your Fingertips

**Smart Code Analysis**: Upload or paste your code, and the AI will review it for potential problems, complexity issues, and areas that need improvement.

**Automated Test Suggestions**: Not sure what to test? The AI can analyze your code and suggest what test cases you should write.

**Repository Dashboard**: See how all your projects are doing in one place, with easy-to-understand quality scores and metrics.

**Real-time Quality Metrics**: Watch your code quality improve as you make changes, with instant feedback on coverage, maintainability, and complexity.

## What You Can Do

With OrchestrAI, you can:

- **Analyze code quality** without being a quality assurance expert
- **Get suggestions** for what tests to write
- **Track improvements** over time across all your projects
- **Identify problems** before they reach production
- **Understand complex code** with AI-powered explanations
- **Compare repositories** to see which projects need attention

## Next Steps

Ready to dive in? Check out our other guides:
- How to Analyze Your First Code File
- Understanding Your Quality Report
- Creating Tests with AI Assistance
- Managing Multiple Repositories

Let's get started making your code better!
</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="write_file">
<parameter name="path">user-facing-docs/orchestrai-dev-analyzing-code-quality.md</parameter>
<parameter name="content"># How to Analyze Your Code Quality

Learn how to use OrchestrAI's AI Quality Engineer to understand and improve your code quality.

## What is Code Quality Analysis?

Code quality analysis is like having an experienced developer review your code and point out areas that could be better. OrchestrAI's AI looks at things like:

- How complex your code is (simpler is usually better!)
- How easy it will be to maintain in the future
- Potential bugs or issues
- Whether you're following best practices

## Starting Your First Analysis

### Step 1: Open the Quality Engineer Panel

When you first open OrchestrAI, you'll see the AI Quality Engineer section. This is your starting point for code analysis.

### Step 2: Add Your Code

You have a few ways to get your code into the system:

**Option 1: Paste Your Code**
Simply copy your code from your editor and paste it into the input area. This works great for quick checks of individual files or functions.

**Option 2: Upload a File**  
Click the upload button to select a code file from your computer. OrchestrAI supports many programming languages including JavaScript, TypeScript, Python, and more.

**Option 3: Connect a Repository**
Link your code repository to analyze entire projects at once.

### Step 3: Run the Analysis

Once your code is loaded, click the "Analyze Code" button. The AI will get to work examining your code. You'll see a progress indicator while it's working.

## Understanding Your Results

After the analysis completes, you'll see several sections:

### Quality Score
A number that represents overall code quality. Higher is better! Scores range from 0 to 10.

- **8-10**: Excellent! Your code is in great shape
- **6-7**: Good, with some room for improvement  
- **4-5**: Needs attention in several areas
- **0-3**: Significant issues that should be addressed

### Complexity Rating
This tells you how complicated your code is to understand and modify:

- **Low**: Easy to understand and maintain
- **Medium**: Somewhat complex, may need simplification
- **High**: Very complex, likely needs refactoring

### Maintainability Score
How easy will it be for you (or someone else) to work with this code in the future? Higher scores mean it's easier to maintain.

### Issues Found
A list of specific problems the AI discovered. Each issue includes:
- What the problem is
- Where it's located in your code
- Why it matters
- Suggestions for fixing it

### Recommendations
Practical advice from the AI about how to improve your code. These are prioritized from most to least important.

## What to Do With Your Results

### Address Critical Issues First
If the AI found any critical issues (usually marked in red), tackle these first. They're typically bugs or security concerns.

### Review Suggestions
Read through the AI's recommendations. They're designed to help you write better code, not criticize what you've done.

### Track Your Progress
After making improvements, run the analysis again to see how your score improved. It's satisfying to watch those numbers go up!

### Save Your Reports
You can export your analysis results to share with your team or keep for your records.

## Tips for Better Results

**Start Small**: If you have a large project, begin by analyzing individual files or modules rather than everything at once.

**Run Regular Checks**: Make it a habit to analyze your code before considering it "done." Catching issues early saves time later.

**Don't Aim for Perfection**: A score of 7 or 8 is usually excellent. Chasing a perfect 10 might not be worth the time.

**Learn from Patterns**: If the AI keeps pointing out the same types of issues, take time to learn about those patterns so you can avoid them in the future.

## Common Questions

**How long does analysis take?**
Most analyses complete in seconds to a few minutes, depending on how much code you're analyzing.

**What languages are supported?**
OrchestrAI works with JavaScript, TypeScript, Python, Java, and many other popular languages.

**Will this work on old code?**
Yes! OrchestrAI can analyze any code, regardless of when it was written. It's actually a great tool for understanding legacy code.

**Can I analyze private/confidential code?**
Your code is processed securely and not stored or shared. Check your organization's security policies before analyzing proprietary code.

## Next Steps

Now that you know how to analyze code quality, learn about:
- Generating Test Plans
- Understanding Code Metrics
- Setting Up Repository Monitoring
</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="write_file">
<parameter name="path">user-facing-docs/orchestrai-dev-generating-tests.md</parameter>
<parameter name="content"># How to Generate Tests with AI

Learn how to use OrchestrAI's AI Test Engineer to create comprehensive test suites for your code.

## What is Test Generation?

Test generation is the process of creating automated tests that verify your code works correctly. OrchestrAI's AI can analyze your code and suggest what tests you need, or even write complete test cases for you.

Think of it like having a testing expert who reads your code and thinks "What could go wrong here? What scenarios should we verify?"

## Why Testing Matters

Good tests help you:
- Catch bugs before your users do
- Make changes confidently, knowing tests will catch problems
- Document how your code is supposed to work
- Sleep better at night knowing your code is verified

## Getting Started with Test Generation

### Step 1: Navigate to the Test Engineer Section

From the main screen, select the AI Test Engineer panel. This is your command center for everything testing-related.

### Step 2: Load Your Code

Just like with quality analysis, you can:
- Paste code directly
- Upload a file
- Select code from a connected repository

### Step 3: Choose Your Test Framework

Tell OrchestrAI what testing tools you use. Common options include:
- Jest (for JavaScript/TypeScript projects)
- Mocha
- Pytest (for Python)
- JUnit (for Java)

Don't see your framework? The AI can generate tests in a general format you can adapt.

### Step 4: Generate Your Tests

Click the "Generate Tests" button. The AI will:
1. Analyze your code to understand what it does
2. Identify edge cases and scenarios to test
3. Write test cases for those scenarios
4. Organize the tests logically

## Understanding Generated Tests

The AI creates different types of tests:

### Happy Path Tests
These verify your code works when everything goes right. They test the main functionality with valid inputs.

### Error Handling Tests  
These check what happens when things go wrong - invalid inputs, network errors, missing data, etc.

### Edge Case Tests
These test boundary conditions - empty arrays, maximum values, null values, and other unusual but valid scenarios.

### Integration Tests
When applicable, these verify that different parts of your code work together correctly.

## Using Your Generated Tests

### Review the Tests
Always review AI-generated tests before using them. The AI is smart, but you know your requirements best. Look for:
- Are all important scenarios covered?
- Do the test descriptions make sense?
- Are the assertions checking the right things?

### Copy and Customize
Once you're happy with the tests, copy them into your test files. You can modify them as needed - add more assertions, change test data, or split complex tests into smaller ones.

### Run the Tests
Execute your new tests in your development environment. They should pass if your code is working correctly, or help you find issues if they fail.

### Build On Them
Use the AI-generated tests as a foundation. Add more tests as you think of additional scenarios or as your code changes.

## Getting Better Test Suggestions

### Provide Context
The more the AI knows about your code, the better tests it can generate. If your code connects to a database or calls external services, mention that.

### Specify Coverage Goals
Tell the AI if you need comprehensive testing or just basic coverage. Different projects have different testing needs.

### Indicate Critical Paths
Point out which parts of your code are most important or risky. The AI can focus on generating more thorough tests for those areas.

### Request Specific Test Types
If you need specific kinds of tests (like performance tests or security tests), let the AI know.

## Test Coverage Insights

After generating tests, you'll see:

### Coverage Percentage
What portion of your code will be tested by these tests. Higher is generally better, but 100% isn't always necessary.

### Uncovered Areas
Parts of your code that don't have tests yet. You can generate additional tests for these areas.

### Test Quality Score
How comprehensive and effective the generated tests are.

## Common Scenarios

### "I Need Tests for Existing Code"
This is perfect for OrchestrAI! Upload your code and the AI will create a complete test suite, which is especially helpful for legacy code that never had tests.

### "I'm Writing New Code"
Generate tests as you write! This helps you think about edge cases early and can even influence how you design your code.

### "My Tests Keep Failing"
If generated tests fail unexpectedly, they might have found bugs in your code. This is actually a good thing - better to find issues now than in production!

### "I Need More Tests"
Run the generator again and ask for additional scenarios. You can generate tests multiple times for the same code from different angles.

## Best Practices

**Generate Early and Often**: Create tests as you develop, not as an afterthought.

**Mix AI and Manual**: Use AI-generated tests as a foundation, then add your own specialized tests for business logic.

**Keep Tests Updated**: When you change your code, regenerate or update the tests to match.

**Test the Important Stuff**: Focus testing effort on critical functionality. Not every line of code needs exhaustive testing.

**Read the Tests**: Generated tests are also documentation - they show how your code is meant to be used.

## Tips for Success

- Start with simple functions before tackling complex ones
- Generate tests for one module or file at a time
- Compare generated tests with any existing tests you have
- Share generated tests with your team for review
- Use failed tests as debugging clues

## Troubleshooting

**Tests Look Wrong**
Make sure you selected the correct test framework and that your code was fully loaded.

**Missing Test Cases**  
Request additional tests or manually add tests for scenarios the AI might have missed.

**Tests Won't Run**
Check that the generated test format matches your project's setup. You may need to adjust imports or test structure slightly.

**Too Many Tests**
It's okay to remove redundant or unnecessary tests. More isn't always better.

## Next Steps

Learn more about:
- Understanding Test Coverage Reports
- Organizing Large Test Suites
- Running Tests Automatically
- Testing Best Practices
</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="write_file">
<parameter name="path">user-facing-docs/orchestrai-dev-repository-management.md</parameter>
<parameter name="content"># Managing Your Code Repositories

Learn how to use OrchestrAI to monitor and manage the quality of all your code repositories in one place.

## What is Repository Management?

Repository management in OrchestrAI gives you a dashboard view of all your code projects. Instead of checking each project individually, you can see the health of everything at once and identify which projects need attention.

Think of it like a fitness tracker, but for your code - you get a quick health check for all your projects.

## Accessing Your Repository Dashboard

Navigate to the Code Repository View from the main navigation. This shows all repositories you've connected to OrchestrAI.

## What You'll See

### Repository List
A table showing all your repositories with key information:

**Repository Name**: The project name, which you can click to see details

**Quality Score**: The overall health rating (0-10) based on code quality analysis

**Test Coverage**: What percentage of code has tests

**Last Updated**: When the repository was last analyzed

**Status**: Active, needs attention, or up-to-date

**Issues Count**: Number of quality issues found

### Visual Health Indicators

Color coding makes it easy to spot problems:
- **Green**: Healthy repositories doing well
- **Yellow**: Repositories that could use improvement  
- **Red**: Repositories with significant issues requiring attention

## Connecting a New Repository

### Step 1: Add Repository
Click the "Add Repository" or "Connect Repository" button.

### Step 2: Choose Your Source
Select where your code lives:
- GitHub
- GitLab  
- Bitbucket
- Other Git providers
- Direct upload

### Step 3: Authorize Access
If using a hosted service like GitHub, you'll need to grant OrchestrAI permission to access your repository. This is secure and you can revoke access anytime.

### Step 4: Select Repository
Choose which specific repository to connect from your account.

### Step 5: Initial Analysis
OrchestrAI will run its first analysis of your repository. This may take a few minutes depending on the size of your codebase.

## Understanding Repository Metrics

### Quality Score
Your repository's overall health score, calculated from:
- Code complexity
- Maintainability
- Issue count
- Test coverage
- Code organization

### Test Coverage Percentage
Shows how much of your code has automated tests:
- **80%+**: Excellent coverage
- **60-80%**: Good coverage
- **40-60%**: Needs improvement
- **Below 40%**: Significant gaps in testing

### Code Complexity
Indicates how difficult the code is to understand and maintain:
- **Low**: Simple, easy to work with
- **Medium**: Moderate complexity
- **High**: Complex, may need refactoring

### Issue Density
The number of issues per 1000 lines of code. Lower is better.

### Maintainability Index
A score indicating how easy the code will be to maintain over time.

## Viewing Repository Details

Click any repository name to see detailed information:

### File-by-File Analysis
See quality metrics for individual files so you know exactly where to focus your efforts.

### Issue Breakdown
Detailed list of all issues found, organized by severity and type.

### Trend Charts
Visual graphs showing how your repository's health has changed over time.

### Test Coverage Map
Visual representation of which files and functions have test coverage.

### Recent Changes
List of recent commits or changes and their impact on quality metrics.

## Comparing Repositories

### Side-by-Side View
Select multiple repositories to compare them directly. This helps you:
- Identify which projects need the most work
- Spot patterns across projects
- Allocate development resources effectively
- Set consistent quality standards

### Team Performance
If you manage multiple developers or teams, compare repositories to understand which teams might need additional support or training.

## Taking Action

### Prioritize by Impact
OrchestrAI helps you decide what to work on first by showing which issues will have the biggest impact on quality if fixed.

### Set Quality Goals
For each repository, you can set target metrics:
- Desired quality score
- Target test coverage
- Maximum acceptable complexity

The dashboard will show progress toward these goals.

### Schedule Regular Reviews
Set reminders to review repositories regularly. Consistent attention prevents small issues from becoming big problems.

## Filtering and Searching

### Filter by Status
Show only repositories that:
- Need attention
- Have recent changes
- Meet quality standards
- Are below target metrics

### Search by Name
Quickly find specific repositories when you have many connected.

### Sort by Metrics
Order repositories by quality score, coverage, issue count, or last update date.

## Keeping Repositories Up to Date

### Automatic Updates
Enable automatic analysis whenever code is pushed to your repository. This keeps metrics current without manual effort.

### Manual Refresh
Click the refresh button on any repository to run a new analysis immediately.

### Change Notifications
Get alerted when a repository's quality score drops significantly or when critical issues are introduced.

## Team Collaboration

### Share Reports
Generate shareable reports showing repository health to share with teammates, managers, or stakeholders.

### Comment and Discuss
Add notes or comments to specific issues to collaborate with team members on solutions.

### Track Assignments
Assign issues to specific team members and track their progress.

## Best Practices

**Regular Monitoring**: Check your dashboard at least weekly to catch issues early.

**Focus on Trends**: Pay attention to whether repositories are improving or declining over time, not just current scores.

**Balance Quality and Delivery**: Don't let perfect be the enemy of good. Sometimes "good enough" is the right choice.

**Set Realistic Goals**: Improve gradually. Trying to fix everything at once is overwhelming.

**Celebrate Improvements**: When a repository's metrics improve, acknowledge the good work!

## Common Use Cases

### New Project Setup
Connect new repositories immediately to establish a quality baseline from day one.

### Code Review Preparation
Check repository metrics before code reviews to focus on areas needing attention.

### Technical Debt Planning
Use the repository dashboard to identify and prioritize technical debt paydown efforts.

### Onboarding New Team Members
Show new developers the repository dashboard so they understand project health and priorities.

### Sprint Planning
Review repository metrics during sprint planning to inform which quality improvements to schedule.

## Troubleshooting

**Repository Won't Connect**
Check that you've granted necessary permissions and that the repository URL is correct.

**Metrics Seem Wrong**
Refresh the analysis or check when it was last run. Stale data can be misleading.

**Too Many Repositories**
Use folders or tags to organize repositories into logical groups for easier management.

**Analysis Takes Too Long**  
Very large repositories may take time to analyze initially. Subsequent analyses are usually faster.

## Next Steps

Explore more features:
- Setting Up Automatic Quality Checks
- Creating Custom Quality Reports
- Integrating with Your Development Workflow
- Understanding Advanced Metrics
</parameter>
</invoke>
</function_calls>

<function_calls>
<invoke name="write_file">
<parameter name="path">user-facing-docs/orchestrai-dev-understanding-metrics.md</parameter>
<parameter name="content"># Understanding Quality Metrics

A friendly guide to understanding what all those numbers and scores mean in OrchestrAI.

## Why Metrics Matter

Metrics are like a health checkup for your code. Just as a doctor uses blood pressure and heart rate to understand your physical health, OrchestrAI uses various metrics to understand your code's health.

The good news? You don't need to be an expert to understand them. This guide explains each metric in plain language.

## Core Quality Metrics

### Quality Score (0-10)

**What it is**: Your code's overall health rating

**What it means**:
- **9-10**: Exceptional - This code is a joy to work with
- **7-8**: Very Good - Minor improvements possible
- **5-6**: Adequate - Several areas need attention
- **3-4**: Concerning - Significant issues present
- **0-2**: Critical - Serious problems that should be addressed immediately

**What affects it**:
- How complex your code is
- Whether it follows best practices
- How many issues were found
- How easy it will be to maintain
- Test coverage

**Why it matters**: A higher score means your code is easier to work with, has fewer bugs, and will cause fewer headaches in the future.

### Test Coverage (Percentage)

**What it is**: How much of your code is verified by automated tests

**What it means**:
- **90-100%**: Excellent - Nearly everything is tested
- **70-89%**: Good - Most important code is tested
- **50-69%**: Fair - Significant gaps in testing
- **Below 50%**: Poor - Many parts untested

**Common misconception**: 100% coverage doesn't mean zero bugs, but it does mean you'll catch more problems before users do.

**What to aim for**: 
- Critical code: 90%+ coverage
- Normal business logic: 70-80% coverage
- Simple utilities: 60-70% coverage

**Why it matters**: Tests catch bugs before they reach users and give you confidence when making changes.

### Code Complexity

**What it is**: How difficult your code is to understand and modify

**Levels**:

**Low Complexity**
- Code is straightforward and easy to follow
- Few nested conditions or loops
- Functions do one thing well
- Easy for anyone to understand and modify

**Medium Complexity**
- Some intricate logic
- Multiple conditions or paths
- May take time to fully understand
- Should be manageable with good documentation

**High Complexity**  
- Many nested conditions and logic paths
- Difficult to follow without deep concentration
- High risk of bugs when modifying
- Good candidate for simplification

**Why it matters**: Complex code is expensive. It takes longer to understand, is more likely to contain bugs, and is harder to modify safely.

### Maintainability Index (0-100)

**What it is**: A prediction of how easy your code will be to maintain over time

**What it means**:
- **85-100**: Highly maintainable - Easy to work with
- **65-84**: Moderately maintainable - Acceptable
- **50-64**: Difficult to maintain - Consider improvements
- **Below 50**: Very difficult to maintain - Needs refactoring

**What affects it**:
- Code complexity
- Size of functions and files
- How well code is organized
- Quality of naming and documentation

**Why it matters**: Maintainable code saves time and money. Changes that take hours in maintainable code can take days in unmaintainable code.

## Issue Metrics

### Issue Count

**What it is**: Total number of problems found in your code

**Categories**:

**Critical**: Serious problems that could cause crashes or security issues
**Important**: Significant issues that should be fixed soon
**Moderate**: Problems that reduce quality but aren't urgent
**Minor**: Small improvements that would be nice to have

**Why it matters**: More issues mean more potential bugs, slower development, and harder maintenance.

### Issue Density

**What it is**: Number of issues per 1000 lines of code

**Why this matters more than total count**: A 100-line file with 5 issues is worse than a 10,000-line file with 20 issues.