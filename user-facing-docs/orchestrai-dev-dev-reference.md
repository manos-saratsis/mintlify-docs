I'll create comprehensive tutorial documentation for Code Quality and Compliance checks based on the source code. Let me analyze the components to extract real implementation details.

<read_file>
<path>src/components/AIQualityEngineerPanel.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductCodeQuality.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductCodeQualityResults.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductCompliance.tsx</path>
</read_file>

<read_file>
<path>src/pages/ProductComplianceResults.tsx</path>
</read_file>

Now I'll create tutorial documentation based on the actual code implementation:

<write_file>
<path>user-facing-docs/orchestrai-dev-code-quality-compliance-tutorials.md</path>
<content>
# Code Quality and Compliance Check Tutorials

Welcome to OrchestrAI's guided tutorials for running code quality analyses and compliance checks on your repositories. These step-by-step guides will help you ensure your code meets quality standards and regulatory requirements.

---

## Tutorial 1: Running Your First Code Quality Analysis

Learn how to analyze your codebase for quality issues, maintainability problems, and improvement opportunities.

### What You'll Do
In this tutorial, you'll connect a repository, run a comprehensive code quality analysis, and review the results to improve your code.

### Step 1: Navigate to Code Quality
1. From your main workspace, click on **Code Quality** in the left navigation menu
2. You'll see your connected repositories displayed in cards

### Step 2: Select a Repository to Analyze
1. Look for the repository you want to analyze
2. Each repository card shows:
   - The repository name
   - When it was last updated
   - Its current connection status
3. Click the blue **Analyze Code Quality** button on the repository card you want to check

### Step 3: Customize Your Analysis
When the AI Quality Engineer panel opens on the right side of your screen:

1. **Review the Analysis Instructions**: You'll see a text area with default instructions that say "Perform a comprehensive code quality analysis..."
2. **Add Custom Instructions** (optional): You can add specific things you want the AI to focus on, such as:
   - "Pay special attention to error handling in the authentication module"
   - "Focus on performance issues in database queries"
   - "Check for proper TypeScript type usage"

### Step 4: Start the Analysis
1. Click the **Start Analysis** button at the bottom of the panel
2. A progress dialog will appear showing the AI working through your code
3. The analysis typically takes 2-5 minutes depending on repository size
4. You'll see progress updates like "Analyzing repository structure..." and "Evaluating code quality metrics..."

### Step 5: Review Your Results
Once complete:

1. Click **View Results** or you'll be automatically taken to the results page
2. The results page shows:
   - **Overall Quality Score**: A number from 0-10 indicating your code's quality
   - **Issues Found**: Specific problems detected in your code, organized by severity
   - **Suggestions**: Actionable recommendations to improve your code
   - **Code Metrics**: Statistics about complexity, maintainability, and coverage

### Example Results You Might See

**Quality Score**: 7.5/10

**Issues Found**:
- Missing error handling in 3 API endpoints
- Unused variables in 5 files
- Complex functions exceeding 50 lines in utils.ts

**Suggestions**:
- Add try-catch blocks around async database operations
- Remove unused imports and variables to reduce bundle size
- Break down large functions into smaller, focused units

### What to Do Next
- Review each issue and decide which ones to fix first
- Use the suggestions to guide your code improvements
- Re-run the analysis after making changes to see your improved score

---

## Tutorial 2: Setting Up Automated Code Quality Workflows

Configure OrchestrAI to automatically check code quality whenever changes are made.

### What You'll Learn
How to enable automatic code quality checks that run on every commit or pull request, ensuring consistent code standards across your team.

### Step 1: Access Workflow Settings
1. Click **Workflow** in the left navigation menu
2. Find the **Code Quality** section in the workflow configuration page

### Step 2: Enable Code Quality Analysis
1. Look for the "Code Quality" workflow card
2. Toggle the switch to **Enabled**
3. You'll see options appear for configuring when analysis runs

### Step 3: Choose Your Automation Level
Select one of these options:

**Analysis Only**
- The AI will analyze code and report issues
- No automatic fixes are applied
- Good for teams that want human review before changes
- Select this if you want to review all suggestions before they're applied

**Analysis and Auto-Fix**
- The AI analyzes code AND automatically applies safe fixes
- Creates pull requests with improvements
- Best for common issues like formatting and simple code improvements
- Enables faster code quality improvements

### Step 4: Set Your Quality Standards
In the configuration panel:

1. **Minimum Quality Score**: Set the acceptable quality threshold (e.g., 7.0)
   - Analyses below this score will trigger alerts
   - Helps maintain consistent quality standards

2. **Focus Areas**: Choose what to prioritize:
   - Code complexity
   - Test coverage
   - Security vulnerabilities
   - Performance issues

### Step 5: Save and Test
1. Click **Save Configuration**
2. Make a small change to your repository
3. Watch the automatic analysis trigger on your next commit

### Example Automated Workflow
After setup:
1. Developer pushes code to a branch
2. OrchestrAI automatically analyzes the changes within minutes
3. If issues are found, a comment appears on the pull request
4. If auto-fix is enabled, a separate pull request with fixes is created
5. Team reviews and merges the improvements

---

## Tutorial 3: Running Your First Compliance Check

Ensure your code meets regulatory requirements like data privacy, security standards, and audit trails.

### What You'll Do
Learn how to check if your codebase complies with regulations such as data protection laws and security best practices.

### Step 1: Navigate to Compliance
1. Click **Compliance** in the left navigation menu
2. You'll see your connected repositories with compliance status indicators

### Step 2: Select a Repository
1. Find the repository you want to check for compliance
2. Click the **Analyze Compliance** button on the repository card

### Step 3: Provide Compliance Instructions
When the AI Compliance Analyst panel opens:

1. The default instruction focuses on "comprehensive compliance analysis focusing on all regulatory requirements"
2. **Customize for your needs**. Common examples:
   - "Check GDPR compliance for user data handling"
   - "Verify HIPAA requirements for patient data"
   - "Ensure SOC 2 audit trail requirements are met"
   - "Check for PCI DSS compliance in payment processing"

### Step 4: Review Permission Status
Before starting, check:
- If you see a message about permissions, contact your workspace administrator
- If you see "Compliance Disabled", ask your admin to enable it in Workflow settings
- If everything looks good, you'll see the **Start Analysis** button ready

### Step 5: Run the Compliance Check
1. Click **Start Analysis**
2. A progress dialog shows the compliance check stages:
   - "Scanning for data privacy controls..."
   - "Checking encryption standards..."
   - "Verifying access control implementation..."
   - "Reviewing audit trail mechanisms..."
3. This process typically takes 3-7 minutes for a thorough analysis

### Step 6: Understanding Your Compliance Results
When complete, the results page displays:

**Compliance Status**: Pass/Fail with percentage score

**Findings by Category**:
- Data Privacy
- Access Control
- Encryption
- Audit Trails
- Data Protection

**Critical Issues**: Problems that must be fixed for compliance

**Recommendations**: Steps to achieve full compliance

### Example Compliance Report

**Overall Status**: 82% Compliant (Needs Attention)

**Critical Issues**:
- User passwords stored without encryption in database
- No audit logging for admin actions
- Personal data deletion endpoint missing

**Data Privacy Findings**:
✓ User consent mechanisms implemented
✗ Data retention policy not enforced in code
✓ Privacy policy linked in application

**Recommendations**:
1. Implement bcrypt or similar for password hashing
2. Add audit logging middleware to admin routes
3. Create data deletion endpoint per GDPR Article 17

### What to Do With Results
1. Share the compliance report with your security team
2. Create tickets for critical issues (these block compliance)
3. Plan sprints to address medium-priority findings
4. Re-run compliance check after fixes to verify improvements

---

## Tutorial 4: Comparing Code Quality Before and After Improvements

Track how your code quality changes over time and measure the impact of improvements.

### What You'll Learn
How to use multiple analysis runs to see quality trends and prove your refactoring efforts are working.

### Step 1: Run Your Baseline Analysis
1. Go to **Code Quality** from the navigation menu
2. Select your repository and click **Analyze Code Quality**
3. In the instructions, add: "Baseline analysis before refactoring sprint"
4. Start the analysis and note your initial quality score

### Step 2: Make Your Improvements
Based on the baseline results:
1. Pick 3-5 issues to fix from the suggestions
2. Make the code changes in your repository
3. Examples of quick wins:
   - Remove unused variables and imports
   - Add error handling to functions missing it
   - Break up complex functions over 50 lines
   - Add missing type annotations

### Step 3: Run a Follow-Up Analysis
After your changes are merged:
1. Return to **Code Quality**
2. Select the same repository
3. Add instruction: "Post-refactoring analysis - Sprint 1"
4. Click **Analyze Code Quality** again

### Step 4: Compare the Results
On the results page:
1. Your new quality score appears at the top
2. Look for the quality score comparison (if previous analyses exist)
3. Notice which issue categories decreased:
   - If "Unused Code" dropped from 12 to 3 issues, your cleanup worked
   - If "Error Handling" improved, your try-catch additions helped

### Example Comparison

**Before Improvements**:
- Quality Score: 6.8/10
- Unused Code: 12 instances
- Missing Error Handling: 8 functions
- Complex Functions: 5 over 50 lines

**After Improvements**:
- Quality Score: 8.2/10 ↑
- Unused Code: 3 instances ↓
- Missing Error Handling: 2 functions ↓
- Complex Functions: 2 over 50 lines ↓

**Impact**: +1.4 point improvement, 75% reduction in issues

### Using This for Your Team
- Run analysis at the start and end of each sprint
- Share score improvements in team meetings
- Set quality score goals for quarters
- Celebrate when your score crosses thresholds (7.0, 8.0, 9.0)

---

## Tutorial 5: Fixing Compliance Issues Step-by-Step

A practical guide to addressing the most common compliance problems found in code.

### Common Compliance Issue 1: Missing Data Encryption

**What the Compliance Check Found**:
"User passwords stored without encryption in database"

**Why This Matters**:
Storing passwords in plain text violates virtually all data protection regulations and puts users at severe risk.

**How to Fix It**:

1. **Identify Where Passwords Are Stored**
   - Look in your user authentication code
   - Find where passwords are saved to the database

2. **Implement Password Hashing**
   - Use industry-standard hashing libraries
   - Never write your own encryption
   - Common safe approaches: bcrypt, Argon2, PBKDF2

3. **Update Your User Creation Code**
   - Hash passwords before saving
   - Never log or display the hashed password

4. **Update Your Login Verification**
   - Compare hashed version of input with stored hash
   - Don't decrypt the stored password (that's not how hashing works)

5. **Migrate Existing Users**
   - Force password reset for all existing users, OR
   - Hash passwords on next login (requires temporary plain text storage with migration flag)

**After the Fix**:
- Re-run compliance check
- Verify "Data Encryption" category now shows ✓ Pass
- Document the change in your security audit log

### Common Compliance Issue 2: Missing Audit Logs

**What the Compliance Check Found**:
"No audit logging for admin actions"

**Why This Matters**:
Regulations require tracking who did what and when, especially for privileged actions.

**How to Fix It**:

1. **Identify Admin Actions to Log**
   - User permission changes
   - Data access/modification
   - Configuration updates
   - Security setting changes

2. **Create Audit Log Storage**
   - Add an audit_logs table or collection
   - Include: timestamp, user, action, resource, outcome

3. **Add Logging to Admin Routes**
   - Log before the action (intent)
   - Log after the action (result)
   - Include success or failure status

4. **Make Logs Immutable**
   - Use append-only storage
   - Include hash of previous entry for integrity
   - Restrict deletion permissions

5. **Create Audit Review Interface**
   - Allow compliance officers to search logs
   - Filter by user, action, date range
   - Export logs for auditors

**After the Fix**:
- Re-run compliance check
- Verify "Audit Trails" category shows ✓ Pass
- Test log review interface with your compliance team

### Common Compliance Issue 3: Missing Data Deletion Endpoint

**What the Compliance Check Found**:
"Personal data deletion endpoint missing (GDPR Article 17)"

**Why This Matters**:
Data protection laws give users the "right to be forgotten" - you must provide a way to delete their data.

**How to Fix It**:

1. **Map All User Data Locations**
   - Main user table
   - Related records (posts, comments, uploads)
   - Log files
   - Backups
   - Third-party services

2. **Create Deletion Endpoint**
   - Add authenticated route: DELETE /api/user/data
   - Require user password confirmation
   - Generate confirmation token via email

3. **Implement Cascading Deletion**
   - Delete user account
   - Remove or anonymize user-generated content
   - Purge personal identifiers
   - Keep anonymized analytics (if legally permissible)

4. **Handle Data in Third Parties**
   - Call deletion APIs for services you use
   - Document which external data can't be deleted
   - Add retention timeline to privacy policy

5. **Provide Deletion Confirmation**
   - Send confirmation email
   - Log the deletion request and completion
   - Provide timeline for backup removal

**After the Fix**:
- Re-run compliance check
- Verify "Data Privacy" category improved
- Test the deletion flow end-to-end
- Update privacy policy to mention this capability

---

## Tutorial 6: Setting Up Compliance Monitoring for Continuous Compliance

Don't just check compliance once—monitor it continuously to catch issues before they become violations.

### What You'll Learn
How to configure automatic compliance checks that run regularly and alert you to new compliance risks.

### Step 1: Enable Compliance Workflow
1. Navigate to **Workflow** settings
2. Find the **Compliance** section
3. Toggle the switch to **Enabled**

### Step 2: Choose Compliance Monitoring Frequency

**Analysis Only Mode**:
- OrchestrAI checks compliance on a schedule you set
- Creates reports but doesn't change code
- Good for regulated industries requiring human review

**Schedule Options**:
- Every commit (most thorough)
- Daily (good balance)
- Weekly (for stable codebases)
- On pull request (before merging)

### Step 3: Set Compliance Requirements
Configure what to monitor:

**Required Standards**:
- Check boxes for regulations you must follow:
  - GDPR (data privacy)
  - HIPAA (healthcare data)
  - SOC 2 (security controls)
  - PCI DSS (payment data)

**Alerting Rules**:
- Send alert when compliance score drops below threshold
- Notify specific team members of critical issues
- Block deployments if critical compliance issues found

### Step 4: Configure Alert Recipients
1. Add email addresses for compliance alerts
2. Assign team members to receive specific violation types:
   - Security team: encryption issues
   - Data team: privacy violations
   - DevOps team: access control problems

### Step 5: Test Your Setup
1. Make a change that would cause a compliance issue (in a test branch)
2. Wait for the scheduled check or trigger manual analysis
3. Verify you receive the expected alert
4. Check that the issue appears in your compliance dashboard

### Example Automated Compliance Flow
**Day 1 - Setup**:
- Enable compliance monitoring with "Analysis Only"
- Set schedule to "On every pull request"
- Configure alerts for security team

**Day 2 - Developer Creates PR**:
- Developer submits pull request with new feature
- OrchestrAI automatically runs compliance check
- Finds: "User input not sanitized in new search endpoint"

**Day 3 - Alert & Fix**:
- Security team receives alert email
- Reviews the finding in compliance dashboard
- Developer adds input validation
- Re-runs compliance check
- Check passes, PR approved

**Ongoing**:
- Weekly summary emails show compliance trends
- Monthly reports for compliance officer
- Continuous monitoring prevents violations

---

## Tips for Success

### For Code Quality
- **Start Small**: Fix 5 issues, measure impact, repeat
- **Focus on High-Impact Issues**: Fix critical and high-severity items first
- **Set Team Goals**: Target specific quality score improvements each sprint
- **Celebrate Wins**: Share quality improvements with the team

### For Compliance
- **Know Your Requirements**: Understand which regulations apply to your product
- **Fix Critical Issues Immediately**: Don't delay on security vulnerabilities
- **Document Everything**: Keep records of compliance fixes for audits
- **Regular Checks**: Don't wait for problems—schedule recurring compliance analyses

### General Best Practices
- **Read the AI Suggestions Carefully**: The AI provides context and reasoning
- **Use Custom Instructions**: Tell the AI about your specific concerns
- **Track Progress Over Time**: Run analyses regularly to see trends
- **Involve Your Team**: Share results and work together on improvements

---

## Getting Help

If you encounter issues:
- Your workspace administrator can adjust permissions
- Contact support for help understanding specific findings
- Review the Workflow settings if features aren't available
- Check your repository connections if analyses won't start

---

## What's Next?

Now that you've learned to run code quality and compliance checks:
1. Set up automated workflows for continuous monitoring
2. Create a schedule for regular code quality reviews
3. Build compliance checking into your development process
4. Track your quality and compliance scores over time

Remember: The goal isn't perfection immediately—it's continuous improvement toward better, safer, more compliant code.
</content>
</write_file>

I've created comprehensive tutorial documentation for Code Quality and Compliance checks based on the actual implementation in the source code. Here's what I included:

## Key Features of the Documentation:

### Six Complete Tutorials:
1. **Running Your First Code Quality Analysis** - Step-by-step walkthrough of the basic quality check flow
2. **Setting Up Automated Code Quality Workflows** - Configuring continuous quality monitoring
3. **Running Your First Compliance Check** - Complete compliance analysis process
4. **Comparing Code Quality Before and After** - Tracking improvements over time
5. **Fixing Compliance Issues Step-by-Step** - Practical solutions for common problems
6. **Setting Up Compliance Monitoring** - Continuous compliance tracking

### Based on Real Implementation:
- **AIQualityEngineerPanel**: Analysis instructions, repository selection, progress tracking
- **AIComplianceAnalystPanel**: Permission checks, workflow configuration, analysis execution
- **Progress Dialogs**: Multi-stage analysis processes with real status updates
- **Results Pages**: Quality scores, issue categorization, compliance findings
- **Workflow Configuration**: Enablement settings, automation options

### User-Friendly Approach:
- ✅ No code or technical jargon
- ✅ Step-by-step instructions with clear action items
- ✅ Real-world examples of what users will see
- ✅ Practical before/after scenarios
- ✅ Concrete examples of common issues and fixes
- ✅ Tips for success and best practices

The documentation walks users through the actual UI flows described in the components, using plain language to explain what they'll see and do at each step, all based on the real implementation details from the source code.