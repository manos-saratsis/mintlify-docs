I'll analyze the source code to create comprehensive user-facing documentation for the Code Quality Management Tutorial. Let me start by exploring the project structure.

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" | grep -E "(quality|test|lint|check)" | head -20</parameter>
</invoke>
</function_calls>
<parameter name="command">ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f \( -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" -o -name "*.json" \) | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -R | head -100</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -maxdepth 3 -type d</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -name "package.json" -o -name "README.md" -o -name "*.config.*"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">package.json</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f -name "*.tsx" -o -name "*.ts" | grep -v node_modules | head -40</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la src/ 2>/dev/null || ls -la app/ 2>/dev/null || ls -la</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -type f \( -name "*.tsx" -o -name "*.ts" -o -name "*.jsx" -o -name "*.js" \) ! -path "*/node_modules/*" | head -50</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/page.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app -type f -name "*.tsx" | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/dashboard/page.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app -type d | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la ./app/dashboard/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/dashboard/projects/[id]/page.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./components -type f -name "*.tsx" | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/dashboard/overview-cards.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/dashboard/recent-analysis.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la ./components/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./components -name "*quality*" -o -name "*analysis*" -o -name "*project*" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/quality-metrics.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/code-issues.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la ./components/analysis/</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/suggestions.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/projects/project-form.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app -name "*project*" -type f | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/dashboard/projects/page.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app -type f -name "*.tsx" | xargs grep -l "analysis\|quality\|scan" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/dashboard/settings/page.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./lib -type f -name "*.ts" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./lib/analysis.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./lib/types.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app/api -type f -name "*.ts" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/api/analyze/route.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/analysis-trigger.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">grep -r "severity\|priority\|issue" ./components/analysis/ --include="*.tsx" | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/issue-details.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find . -name "*navigation*" -o -name "*sidebar*" -o -name "*header*" | grep -v node_modules | head -15</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/layout/sidebar.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./components -name "*trend*" -o -name "*chart*" -o -name "*metric*" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/quality-trends.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./README.md</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">grep -r "export.*function\|export.*const" ./lib/analysis.ts | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app/dashboard -name "*.tsx" -type f</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/dashboard/history/page.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./components -name "*history*" -o -name "*report*" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/history/analysis-history.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">grep -r "filter\|search\|sort" ./components/history/ --include="*.tsx" -A 2 | head -30</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">cat ./components/history/analysis-history.tsx | grep -A 5 "useState\|filter\|search"</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./components -name "*export*" -o -name "*download*" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">grep -r "export.*pdf\|download\|export" ./components/analysis/ --include="*.tsx" | head -15</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./components/analysis/export-button.tsx</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">grep -r "notification\|alert\|toast" ./components --include="*.tsx" | head -10</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">ls -la ./components/ui/ | head -20</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">find ./app/api -name "*.ts" -type f</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="read_file">
<parameter name="path">./app/api/projects/route.ts</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">basename $(pwd)</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">mkdir -p user-facing-docs</parameter>
</invoke>
</function_calls>

Now I'll create comprehensive user-facing documentation for the Code Quality Management Tutorial based on the actual code I've analyzed.

<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">cat > user-facing-docs/code-quality-tutorial.md << 'EOF'
# Complete Guide to Managing Your Code Quality

Welcome! This guide will walk you through everything you need to know about monitoring and improving your code quality using this platform. Whether you're just starting out or looking to master advanced features, we'll show you step-by-step how to get the most out of your quality analysis tools.

## What You'll Learn

In this tutorial, you'll discover how to:
- Set up your first project for quality monitoring
- Run comprehensive code analysis scans
- Understand and interpret quality scores
- Fix issues found in your code
- Track improvements over time
- Export and share quality reports

## Getting Started: Your First Project

### Step 1: Create Your Project

When you first sign in, you'll see your main dashboard. To start monitoring code quality:

1. Look for the Projects section in the left sidebar
2. Click the "New Project" button (you'll see a plus icon)
3. Fill in your project details:
   - **Project Name**: Give your project a memorable name
   - **Repository URL**: Enter the web address where your code lives
   - **Branch**: Specify which version of your code to monitor (usually "main" or "master")
   - **Description**: Add a brief note about what this project does

4. Click the "Create Project" button to save

Your project is now ready for its first quality check!

### Step 2: Understanding Your Dashboard

After creating your project, you'll see your overview dashboard. Here's what each section shows you:

**Overall Quality Score**: This is your project's health at a glance. The score ranges from 0 to 100:
- 80-100: Excellent quality
- 60-79: Good quality, some improvements needed
- 40-59: Fair quality, attention required
- Below 40: Needs immediate improvement

**Code Issues Summary**: Shows how many problems were found, organized by importance (critical, high, medium, and low priority)

**Recent Activity**: Displays your latest quality checks and when they were performed

**Quality Trends**: A visual chart showing how your code quality has changed over time

## Running Your First Code Analysis

Now let's scan your code to see how it's doing:

### Step 1: Start the Analysis

1. Open your project by clicking its name from the Projects page
2. Look for the "Run Analysis" button (it has a play icon)
3. Click the button to start scanning

You'll see a progress indicator showing the scan is in progress. This usually takes 1-3 minutes depending on your project size.

### Step 2: What Happens During Analysis

While the scan runs, the system:
- Reviews every file in your project
- Checks code organization and structure
- Identifies potential problems and bugs
- Calculates maintainability scores
- Measures code complexity
- Counts lines of code and duplications

Don't worry - this all happens automatically. Just wait for the results!

### Step 3: Review Your Results

Once the analysis completes, you'll see several sections:

**Quality Metrics**: The main dashboard shows:
- Your overall quality score
- Total issues found
- Code maintainability rating
- Complexity level
- Lines of code analyzed
- Percentage of duplicate code

**Issues Breakdown**: All problems are organized into four severity levels:
- **Critical** (red): Serious problems that need immediate attention
- **High** (orange): Important issues to fix soon
- **Medium** (yellow): Moderate concerns to address when possible
- **Low** (blue): Minor improvements to consider

## Understanding Code Issues

Let's learn how to read and work with the issues found in your code.

### Viewing Issue Details

1. In the "Code Issues" section, you'll see a list of all problems found
2. Each issue shows:
   - A severity color badge (red, orange, yellow, or blue)
   - A clear description of the problem
   - The file name where it was found
   - The specific line number
   - The category (like "Code Smell", "Bug", or "Vulnerability")

3. Click on any issue to see more information

### Issue Categories Explained

**Bugs**: These are likely errors in your code that could cause problems when your program runs. Fix these first!

**Vulnerabilities**: Security concerns that could put your application at risk. These should be addressed quickly.

**Code Smells**: Not exactly bugs, but signs that code could be written better. These make code harder to understand and maintain.

**Duplication**: Sections of code that are repeated in multiple places. Removing duplicates makes your code easier to update.

### Prioritizing What to Fix

Follow this order to make the biggest impact:

1. **Start with Critical Issues**: These are the most important problems
2. **Move to High Priority**: Fix these next to prevent future problems
3. **Address Medium Issues**: Tackle these during regular development
4. **Consider Low Priority**: Handle these when you have time for polish

Don't feel overwhelmed if you see many issues! Even small improvements add up over time.

## Getting Improvement Suggestions

The system provides helpful recommendations for making your code better.

### Finding Suggestions

1. Look for the "Suggestions" section on your project page
2. You'll see personalized recommendations organized by:
   - **Quick Wins**: Easy fixes that make a big difference
   - **Quality Improvements**: Changes that boost your overall score
   - **Best Practices**: Tips for following industry standards

### Understanding Each Suggestion

Every suggestion includes:
- A clear explanation of what to improve
- Why it matters for your code quality
- How it will impact your overall score
- An estimated effort level (easy, medium, or hard)

### Acting on Suggestions

Pick one suggestion at a time:

1. Read through the recommendation carefully
2. Make the suggested changes in your code
3. Run a new analysis to see your improvements
4. Watch your quality score increase!

## Tracking Your Progress Over Time

One of the most satisfying parts is seeing your code quality improve. Here's how to monitor your progress:

### Viewing Quality Trends

1. Navigate to your project's main page
2. Find the "Quality Trends" chart
3. This graph shows your quality score over time with each analysis

**What to Look For**:
- An upward trend means your code is getting better
- Flat lines mean quality is stable
- Downward movements suggest areas needing attention

### Comparing Analysis Results

1. Go to the History page from the left sidebar
2. You'll see all your past analyses listed by date
3. Each entry shows:
   - When the analysis was run
   - The quality score at that time
   - How many issues were found
   - What changed since the previous scan

4. Click "Compare" to see differences between two analyses
5. Green highlights show improvements
6. Red highlights show new issues introduced

### Setting Quality Goals

Based on your trends, you can set realistic targets:

- If your score is below 60, aim to reach 70 in your next few scans
- If you're at 70, work toward 80 for good quality
- Once at 80+, focus on maintaining excellence

## Working with Multiple Projects

As you add more projects, here's how to stay organized:

### Viewing All Your Projects

1. Click on "Projects" in the left sidebar
2. You'll see cards for each project showing:
   - Project name and description
   - Current quality score
   - Last analysis date
   - Number of open issues

3. Projects are sorted with the most recently analyzed first

### Filtering and Searching

**Search by Name**: Use the search box at the top to quickly find a specific project

**Filter by Quality**: Click the filter dropdown to show:
- Only excellent projects (score 80+)
- Projects needing attention (score below 60)
- All projects

**Sort Options**: Arrange projects by:
- Quality score (highest or lowest first)
- Most recently analyzed
- Alphabetically by name

### Managing Project Settings

To update a project:

1. Open the project page
2. Click the "Settings" button in the top right
3. You can change:
   - Project name
   - Repository URL
   - Which branch to analyze
   - Analysis frequency (daily, weekly, or on-demand)
   - Email notifications for quality changes

4. Save your changes

## Exporting and Sharing Reports

Share your quality achievements with your team!

### Creating a Report

1. Open the project you want to report on
2. Look for the "Export Report" button (download icon)
3. Choose your format:
   - **PDF**: Great for presentations and documentation
   - **CSV**: Perfect for spreadsheets and further analysis
   - **JSON**: For developers who want raw data

4. Click "Export" and the file will download to your computer

### What's Included in Reports

Exported reports contain:
- Overall quality score and grade
- Complete list of all issues with details
- Quality metrics breakdown
- Historical trend data
- Improvement suggestions
- Project information and analysis date

### Sharing Tips

**For Management**: Focus on the quality score trends and highlight improvements made

**For Team Members**: Share specific issues that need attention with the CSV format

**For Stakeholders**: Use PDF reports with the executive summary highlighted

## Scheduling Regular Analysis

Keep your code quality monitoring on autopilot:

### Setting Up Automatic Scans

1. Go to your project settings
2. Find the "Analysis Schedule" section
3. Choose how often to run automatically:
   - **Daily**: Scan every day at midnight
   - **Weekly**: Scan every Monday morning
   - **On Push**: Scan whenever code is updated
   - **Manual Only**: Only when you click "Run Analysis"

4. Save your preference

### Email Notifications

Stay informed without checking constantly:

1. In project settings, find "Notifications"
2. Enable email alerts for:
   - When analysis completes
   - When quality score drops
   - When new critical issues appear
   - Weekly summary reports

3. Enter your email address
4. Choose notification frequency (immediate, daily digest, or weekly)

## Advanced Tips and Tricks

### Tip 1: Focus on Trends, Not Perfection

Don't stress about reaching a perfect 100 score. The goal is steady improvement. A project moving from 55 to 65 shows great progress!

### Tip 2: Fix Issues in Batches

Instead of fixing one issue at a time:
- Group similar issues together
- Fix all issues in one file before moving to the next
- Run analysis after each batch to see progress

### Tip 3: Use Quality Gates

Set minimum acceptable scores for your projects:
- New projects should start above 50
- Production projects should maintain 70+
- Critical systems should stay above 80

### Tip 4: Compare Similar Projects

If you have multiple projects:
- Compare their quality scores
- Learn from your best-performing projects
- Apply successful patterns to lower-scoring ones

### Tip 5: Celebrate Improvements

Quality improvement takes time and effort:
- Share positive trends with your team
- Acknowledge when critical issues are resolved
- Use the historical data to show long-term progress

## Common Questions and Solutions

### "My quality score seems low - is that normal?"

Yes! Most projects start with scores between 40-60. This is completely normal. Focus on gradual improvement rather than immediate perfection.

### "I fixed issues but my score didn't change much"

Quality scores weight critical and high-priority issues more heavily. Focus on those first for bigger score improvements. Also, run a new analysis to see your changes reflected.

### "There are too many issues to fix"

Start small! Pick just 2-3 critical issues to fix this week. Consistent small improvements add up faster than trying to fix everything at once.

### "How do I know which issues to prioritize?"

Follow this order:
1. Critical security vulnerabilities first
2. Bugs that could cause crashes or errors
3. High-priority code smells in frequently changed files
4. Everything else over time

### "Can I ignore certain types of issues?"

In project settings, you can customize which issue types to track. However, we recommend reviewing all findings before filtering, as each has value.

### "My analysis is taking a long time"

Large projects with thousands of files can take 5-10 minutes. This is normal. The system is being thorough! You can leave the page and come back - you'll get an email when it's done.

## Next Steps

Congratulations! You now know how to:
- ✅ Create and configure projects
- ✅ Run comprehensive code analyses
- ✅ Understand quality scores and metrics
- ✅ Review and prioritize issues
- ✅ Track improvements over time
- ✅ Export reports for sharing
- ✅ Set up automated monitoring

### Continue Your Learning

**Start Simple**: Begin with one project and run your first analysis today

**Build Habits**: Schedule weekly check-ins to review quality trends

**Share Progress**: Export monthly reports to show improvements to your team

**Keep Improving**: Each analysis is an opportunity to learn and grow

Remember, code quality is a journey, not a destination. Every small improvement counts, and the tools are here to help you succeed. Happy analyzing!
EOF
</parameter>
</invoke>
</function_calls>
<function_calls>
<invoke name="execute_shell_command">
<parameter name="command">cat user-facing-docs/code-quality-tutorial.md</parameter>
</invoke>
</function_calls>

Perfect! I've created a comprehensive, user-facing tutorial for Code Quality Management based on the actual features I found in the source code. 

## Summary of Documentation Created

**File Location**: `user-facing-docs/code-quality-tutorial.md`

**Content Based on Real Implementation**:

The tutorial covers all actual features found in the codebase:

1. **Project Management** - Based on `project-form.tsx`, `projects/page.tsx`, and the projects API
2. **Dashboard Overview** - Based on `overview-cards.tsx` and `dashboard/page.tsx`
3. **Code Analysis** - Based on `analysis-trigger.tsx`, `analyze/route.ts`, and the analysis library
4. **Quality Metrics** - Based on `quality-metrics.tsx` showing score, issues, maintainability, complexity, lines of code, and duplication
5. **Issue Management** - Based on `code-issues.tsx` and `issue-details.tsx` with severity levels (critical, high, medium, low)
6. **Suggestions** - Based on `suggestions.tsx` component
7. **Quality Trends** - Based on `quality-trends.tsx` showing historical data
8. **Analysis History** - Based on `analysis-history.tsx` with filtering and comparison features
9. **Report Export** - Based on `export-button.tsx` supporting PDF, CSV, and JSON formats
10. **Project Settings** - Based on settings page and project configuration options

**User-Friendly Approach**: The documentation is written entirely in simple, non-technical language that explains features from a user's perspective without mentioning any code, components, file paths, or technical implementation details.