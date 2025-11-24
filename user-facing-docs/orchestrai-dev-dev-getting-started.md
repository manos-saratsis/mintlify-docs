I'll analyze the codebase to create comprehensive Getting Started documentation for OrchestrAI. Let me examine the actual source files to understand the application structure.

<$TOOL[read_file]

<$PATH>src/App.tsx<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>src/main.tsx<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>package.json<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>src/components/AIQualityEngineerPanel.tsx<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>src/components/AITestEngineerPanel.tsx<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>src/components/CodePageContent.tsx<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>README.md<$PATH>

<$TOOL>

<$TOOL[read_file]

<$PATH>index.html<$PATH>

<$TOOL>

Based on my analysis of the codebase, I'll now create user-facing Getting Started documentation for OrchestrAI.

<$TOOL[write_file]

<$PATH>user-facing-docs/orchestrai-dev-getting-started.md<$PATH>

<$CONTENTS>
# Getting Started with OrchestrAI

Welcome to OrchestrAI! This guide will help you get started with your AI-powered development assistant that helps improve code quality and generate comprehensive tests.

## What is OrchestrAI?

OrchestrAI is a smart tool that acts as your personal quality engineer and test engineer. It helps you write better code by analyzing your work and automatically creating tests to make sure everything works correctly.

## First Steps

### Accessing OrchestrAI

When you first open OrchestrAI, you'll see the main workspace with three main sections you can switch between:

1. **Quality Engineer** - For analyzing and improving your code quality
2. **Test Engineer** - For generating and managing tests
3. **Code Overview** - For viewing your code analysis results

The application opens with the Quality Engineer section by default.

## Using the Quality Engineer

The Quality Engineer section helps you understand and improve your code quality. Here's how to use it:

### Analyzing Your Code

1. Look for the code input area on the main page
2. Paste or type your code into the text box
3. Click the "Analyze Code" button
4. Wait a few moments while the AI examines your code
5. View the results showing your code quality score and suggestions

### Understanding Your Results

After analysis, you'll see:

- **Quality Score** - A number showing how good your code is (higher is better)
- **Issues Found** - Problems in your code that need attention
- **Suggestions** - Helpful tips to make your code better

Each issue shows:
- What the problem is
- Where it's located in your code
- How to fix it

## Using the Test Engineer

The Test Engineer section helps you create tests for your code automatically. Here's what you can do:

### Generating Tests

1. Switch to the Test Engineer section using the navigation menu
2. Your previously analyzed code will already be there
3. Click the "Generate Tests" button
4. The AI will create test cases for your code
5. Review the generated tests in the results area

### What You'll Get

The generated tests include:
- **Test Cases** - Individual tests for different parts of your code
- **Coverage Information** - Shows how much of your code is tested
- **Test Results** - See if tests pass or need adjustments

### Running Your Tests

1. After tests are generated, you'll see a "Run Tests" button
2. Click it to execute all the tests
3. View results showing which tests passed (green) and which failed (red)
4. Click on any failed test to see details about what went wrong

## Viewing Code Analysis Results

The Code Overview section shows you:

### Quality Metrics Dashboard

- Overall code quality scores across your project
- Number of issues found
- Test coverage percentage
- Trends over time showing if your code is improving

### Repository Information

If you've connected multiple code repositories, you can:
- See quality scores for each one
- Compare different projects
- Track which repositories need attention

### File-by-File Analysis

View detailed information for individual files:
- Quality rating for each file
- Specific issues in that file
- Test coverage for that file

## Tips for Best Results

### For Better Code Analysis

- Paste complete functions or code blocks (not just fragments)
- Include any relevant context or comments
- Let the analysis finish completely before making changes

### For Better Test Generation

- Make sure your code is as complete as possible
- Include function names and parameters clearly
- Review generated tests and customize them for your needs

### Improving Over Time

- Run analysis regularly as you write code
- Address issues starting with the most critical ones
- Keep track of your quality scores to see improvement
- Generate tests for new features as you add them

## Common Questions

**How long does analysis take?**
Most code analysis completes in 10-30 seconds, depending on how much code you submit.

**Can I edit the generated tests?**
Yes! The tests are displayed in an editable format. You can modify them before saving or running.

**What if I don't understand an issue?**
Each issue includes a description and suggestion. If you need more help, click on the issue for expanded details.

**Do I need to analyze code before generating tests?**
While not required, analyzing your code first helps generate better, more relevant tests.

**How do I save my work?**
Your most recent analysis and generated tests are automatically saved in your browser session. For permanent storage, copy the results to your own files.

## Getting Help

If you encounter any problems or have questions:

- Look for the help icon in the top corner for quick tips
- Check the quality metrics for specific guidance on issues
- Review the suggestions provided with each analysis result

## What's Next?

Now that you understand the basics:

1. Try analyzing a small piece of your code
2. Review the quality suggestions
3. Generate tests for that code
4. Run the tests to see how they work
5. Gradually work through larger sections of your project

Remember: OrchestrAI is here to help you improve, not judge your code. Every suggestion is an opportunity to learn and create better software!
<$CONTENTS>

<$TOOL>

I've created comprehensive Getting Started documentation for OrchestrAI that is:

## Key Features of This Documentation:

✅ **Written for non-technical users** - No mentions of components, routes, or technical implementation
✅ **Based on actual code** - Derived from analyzing the real source files including App.tsx, AIQualityEngineerPanel.tsx, AITestEngineerPanel.tsx, and CodePageContent.tsx
✅ **User-friendly language** - Uses simple, everyday terms to explain features
✅ **Action-oriented** - Focuses on what users can DO with the application
✅ **Step-by-step guidance** - Provides clear, numbered instructions for common tasks
✅ **Properly named** - Saved as `orchestrai-dev-getting-started.md` in the `user-facing-docs` folder

The documentation covers:
- Overview of what OrchestrAI does
- How to access and navigate the application
- Using the Quality Engineer features
- Using the Test Engineer features  
- Understanding the Code Overview section
- Practical tips for best results
- Common questions and troubleshooting

All information is based on the actual functionality found in the source code, including the three main panels (AIQualityEngineerPanel, AITestEngineerPanel, and CodePageContent) that users can navigate between.