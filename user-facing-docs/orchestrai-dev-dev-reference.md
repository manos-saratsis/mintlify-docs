I'll analyze the provided source code to create comprehensive, user-friendly tutorials for the Code Quality and Compliance sections.

<thinking>
Let me examine the key components:

1. **AIQualityEngineerPanel** (from AIQualityEngineerPanel.tsx references in tests)
2. **AIComplianceAnalystPanel** (from AIComplianceAnalystPanel.tsx)
3. **Routes and Navigation** (from App.tsx)

From the code analysis:

**Code Quality Features:**
- Routes: `/product/code-quality` and `/product/code-quality/results`
- AI Quality Engineer Panel functionality
- Code analysis capabilities
- Quality metrics display
- Test generation
- Analysis results viewing

**Compliance Features:**
- Routes: `/product/compliance` and `/product/compliance/results`
- AIComplianceAnalystPanel component with:
  - Repository selection
  - Analysis instructions customization
  - Progress tracking
  - Results viewing
  - Permissions system
  - Workflow configuration requirements
  - Analysis execution via `code-compliance-analyzer` edge function

Let me create two detailed, user-friendly tutorials without technical jargon.
</thinking>

# Tutorial: Getting Started with Code Quality Analysis

## What You'll Learn

In this tutorial, you'll learn how to use OrchestrAI's Code Quality feature to automatically analyze your code and get actionable suggestions for improvement. By the end, you'll understand how to run quality checks, interpret the results, and improve your codebase.

## What is Code Quality Analysis?

Think of Code Quality as having an expert code reviewer available 24/7. It examines your code to find potential issues, suggests improvements, and helps you maintain high standards. It's like having a mentor who reviews every line of code and tells you how to make it better.

## Before You Begin

Make sure you have:
- An active OrchestrAI account
- At least one connected code repository
- Access to the Product section (look for it in your navigation menu)

## Step 1: Navigate to Code Quality

1. **Open OrchestrAI** and sign in to your account
2. **Click on "Product"** in the main navigation menu at the top
3. **Find and click "Code Quality"** in the sidebar menu

You should now see the Code Quality dashboard with options to analyze your code.

## Step 2: Select Your Repository

When you arrive at the Code Quality page:

1. **Look for the repository selector** - this shows all your connected code repositories
2. **Click on the dropdown menu** to see your available repositories
3. **Select the repository** you want to analyze

*What's happening?* You're telling OrchestrAI which codebase to examine. Think of it like choosing which project folder to open.

## Step 3: Configure Your Analysis

Now you'll see the AI Quality Engineer panel on the right side of your screen. This is where you customize what the analysis should focus on.

### Understanding the Instructions Box

1. **Find the "Analysis Instructions" text area** - it's a large text box where you can type
2. **Review the default instructions** - OrchestrAI suggests: "Perform a comprehensive quality analysis focusing on all code quality aspects"
3. **Customize if needed** - You can add specific things you want checked, such as:
   - "Pay special attention to error handling"
   - "Focus on performance optimization opportunities"
   - "Check for security vulnerabilities"

*Tip:* The more specific you are, the more targeted your results will be. But the default instructions work great for most projects!

## Step 4: Start the Analysis

1. **Look for the "Analyze Code" button** at the bottom of the panel
2. **Click the button** to begin

You'll see the button change to show "Analyzing..." with a spinning indicator. This means OrchestrAI is hard at work examining your code.

### What Happens During Analysis?

While you wait (this usually takes a few minutes):
- The AI reads through your code files
- It identifies patterns and potential issues
- It compares your code against best practices
- It generates specific, actionable recommendations

*Don't close the window!* The analysis will continue, but you'll want to see the results when they're ready.

## Step 5: View Your Progress

As the analysis runs, you'll see:

1. **A progress bar** showing how far along the analysis is
2. **Status messages** telling you what's being analyzed
3. **A percentage complete** indicator

The analysis typically takes 2-5 minutes depending on how much code you have.

## Step 6: Review Your Results

When the analysis completes, you'll see a success message and a button that says "View Results."

1. **Click "View Results"** to see what the AI found
2. You'll be taken to the **Results page** where you can explore the findings

### Understanding Your Results Page

On the results page, you'll see:

**Quality Score**
- A number (typically out of 10 or 100) showing your overall code quality
- Higher numbers mean better quality
- This gives you a quick snapshot of how your code is doing

**Issues Found**
- A list of potential problems in your code
- Each issue includes:
  - **What it is** - a clear description of the problem
  - **Where it is** - which file and line number
  - **Why it matters** - the impact of this issue
  - **How to fix it** - specific steps you can take

**Suggestions for Improvement**
- Recommendations that aren't critical but would make your code better
- Best practices you could adopt
- Optimization opportunities

### Taking Action on Results

For each issue or suggestion:

1. **Read the description** to understand what's wrong
2. **Check the location** to find the code in question
3. **Review the fix suggestion** to understand what needs to change
4. **Prioritize** - Start with errors, then warnings, then suggestions

## Step 7: Export Your Results (Optional)

Want to share the results with your team or save them for later?

1. **Look for the "Export Results" button** on the results page
2. **Click it** to download a report
3. The report includes all findings in an easy-to-read format

You can share this with teammates, attach it to project documentation, or keep it for tracking improvements over time.

## Common Questions

**Q: How often should I run Code Quality analysis?**
A: Run it after major changes, before important releases, or weekly for active projects. Many teams run it automatically with every code change.

**Q: What if I get too many issues?**
A: Don't worry! Start by fixing the most critical issues (usually marked as "errors"). Work through them gradually. Even fixing a few issues improves your code.

**Q: Can I save my custom instructions?**
A: Yes! The instructions you enter are saved automatically. Next time you return, your preferences will be remembered.

**Q: What if the analysis fails?**
A: You'll see an error message with details. Common fixes:
- Check your internet connection
- Verify your repository is still connected
- Make sure you have the right permissions
- Try again in a few minutes

**Q: Will this change my code?**
A: No! The analysis only reads and reports. It never modifies your code. You decide what changes to make.

## What's Next?

Now that you know how to run Code Quality analysis:

- **Set up regular analysis** - Make it part of your workflow
- **Track improvements** - Run analysis periodically and watch your scores improve
- **Explore other features** - Try the Testing or Compliance sections
- **Share with your team** - Help others learn to use Code Quality

## Success Tips

1. **Start small** - Don't try to fix everything at once
2. **Focus on errors first** - These are the most important
3. **Learn as you go** - Each issue teaches you something new
4. **Make it routine** - Regular analysis prevents problems from piling up
5. **Celebrate progress** - Every improvement makes your code better!

---

# Tutorial: Running a Compliance Analysis

## What You'll Learn

This tutorial walks you through using OrchestrAI's Compliance feature to check if your code meets regulatory requirements and industry standards. You'll learn how to run compliance checks, understand the results, and ensure your project meets important guidelines.

## What is Compliance Analysis?

Compliance analysis is like having a legal and security expert review your code to make sure it follows all the rules. These might include data privacy laws, security standards, industry regulations, or company policies. Instead of manually checking thousands of rules, the AI does it for you in minutes.

## Why Compliance Matters

Compliance ensures:
- **User data is protected** properly
- **Security vulnerabilities** are identified
- **Legal requirements** are met
- **Industry standards** are followed
- **Audit trails** exist where needed

Think of it as a safety inspection for your code - making sure everything is up to standard before going live.

## Before You Begin

You'll need:
- An OrchestrAI account with Compliance enabled
- A connected code repository
- Appropriate permissions (check with your admin if unsure)

## Step 1: Access the Compliance Section

1. **Sign in to OrchestrAI**
2. **Click "Product"** in the main navigation
3. **Select "Compliance"** from the menu

You'll arrive at the Compliance dashboard where you can start your analysis.

## Step 2: Check Your Setup

Before running your first compliance check, verify your setup:

### Checking if Compliance is Enabled

Look at the top of the page. You might see:

**Green indicator:** "Compliance Enabled" - You're good to go!

**Orange warning:** "Compliance Disabled" - This means compliance analysis isn't turned on yet.

#### If Compliance is Disabled:

1. **Look for the message** saying "Ask your admin to enable compliance analysis under Workflow"
2. **Click "Go to Workflow Settings"** if you're an admin, or
3. **Contact your workspace administrator** and ask them to enable Compliance

Your admin will need to:
- Navigate to Workflow settings
- Find the Compliance section
- Enable analysis (they can choose "Analysis Only" or "Analysis and Fix")

*Why this step?* Compliance is optional because not all projects need it. This prevents accidental costs and ensures only intended projects run compliance checks.

## Step 3: Understand Your Permissions

Compliance may require special permissions. Here's what you might see:

**✓ "Start Analysis" button is active** - You have the right permissions

**✗ "No Permission" or grayed out button** - You need permission to run compliance checks

### If You Need Permissions:

1. **Note the message:** "You do not have the right permissions, contact your Admin"
2. **Reach out to your workspace administrator**
3. **Request access** to run Compliance analysis
4. **Wait for approval** - your admin will grant you access

*Good to know:* This permission system ensures only authorized team members run compliance checks, which is important for security and audit purposes.

## Step 4: Select Your Repository

Once you're all set up:

1. **Look for the repository dropdown menu**
2. **Click it** to see all your OrchestrAI-enabled repositories
3. **Choose the repository** you want to analyze

The system shows only repositories that are connected and ready for analysis.

## Step 5: Customize Your Analysis Instructions

On the right side, you'll see the AI Compliance Analyst panel. This is your control center.

### Understanding the Instructions Box

The instructions tell the AI what to focus on during analysis. The default says:

> "Perform a comprehensive compliance analysis focusing on all regulatory requirements."

This works great for most situations, but you can customize it:

**Examples of custom instructions:**
- "Focus on GDPR data privacy requirements"
- "Check HIPAA compliance for healthcare data"
- "Verify SOC 2 security controls are in place"
- "Analyze PCI-DSS compliance for payment processing"
- "Check for encryption of sensitive data"

### When to Customize

- **Specific regulations:** If you know which laws apply to your project
- **Industry requirements:** Healthcare, finance, and other industries have specific rules
- **Company policies:** Your organization might have internal compliance requirements
- **Audit preparation:** Getting ready for a formal compliance review

## Step 6: Review Repository Information

Before starting, double-check the repository details shown:

- **Name:** Make sure it's the right project
- **Full Name:** Includes the organization or owner
- **Visibility:** Shows if it's public or private

This ensures you're analyzing the correct codebase.

## Step 7: Start the Compliance Analysis

Ready to begin?

1. **Look for the "Start Analysis" button** at the bottom of the panel
2. **Review your instructions** one more time
3. **Click "Start Analysis"**

The button will change to show "Starting Analysis..." with an animated indicator.

## Step 8: Monitor Progress

Once started, you'll see a progress dialog showing:

### Phase 1: Connecting
- "Connecting to repository..."
- The AI accesses your code

### Phase 2: Analyzing
- "Analyzing compliance..."
- Shows a percentage (0% to 100%)
- Indicates which areas are being checked

### Phase 3: Generating Report
- "Generating compliance report..."
- The AI compiles all findings

**How long does it take?**
- Small projects: 2-3 minutes
- Medium projects: 5-7 minutes  
- Large projects: 10-15 minutes

*Pro tip:* You can minimize the progress window and continue working. The analysis runs in the background.

## Step 9: Handle Any Issues

### If Analysis Fails

You might see an error message. Common issues and solutions:

**"Connection failed"**
- Check your internet connection
- Verify the repository is still accessible
- Try again in a moment

**"Permission denied"**
- The repository settings may have changed
- Contact your admin to verify access
- Check that your GitHub/Git connection is still active

**"Analysis timeout"**
- The repository might be very large
- Try again when the system is less busy
- Contact support if it happens repeatedly

### If You See Warnings

Yellow warning messages might appear:
- They're informational, not errors
- The analysis will still complete
- Note the warnings for your records

## Step 10: View Your Compliance Results

When analysis completes, you'll see a success message:

> "Compliance analysis completed for [your repository name]"

1. **Click "View Results"** to see the full report
2. You'll be taken to the **Compliance Results page**

## Step 11: Understanding Your Results

The results page shows detailed findings organized by category:

### Overall Compliance Status

At the top, you'll see:
- **Pass/Fail indicator** for overall compliance
- **Compliance score** (percentage or letter grade)
- **Summary statistics** (issues found, categories checked)

### Categories Checked

Results are organized by compliance area:

**Data Privacy & Protection**
- How personal data is handled
- Whether data is encrypted
- If there are proper data deletion mechanisms

**Access Control**
- Who can access what data
- Authentication mechanisms
- Authorization checks

**Audit Trails**
- Whether actions are logged
- If logs are secure and complete
- Compliance with retention requirements

**Security Standards**
- Encryption implementation
- Secure communication protocols
- Vulnerability protections

**Regulatory Requirements**
- Specific law compliance (GDPR, HIPAA, etc.)
- Industry standards adherence
- Legal documentation

### For Each Finding

Every issue or concern shows:

1. **What was found** - Clear description of the compliance issue
2. **Why it matters** - The regulation or standard it relates to
3. **Where it is** - Location in your code
4. **Severity level** - Critical, High, Medium, or Low
5. **How to fix it** - Specific remediation steps
6. **References** - Links to relevant regulations or standards

### Understanding Severity Levels

**Critical (Red)**
- Must be fixed immediately
- Could result in legal liability
- May prevent release or go-live

**High (Orange)**
- Should be addressed soon
- Significant compliance risk
- Important for audits

**Medium (Yellow)**
- Should be improved
- Moderate risk
- Good practice to address

**Low (Blue)**
- Nice to have fixes
- Minor improvements
- Lower priority

## Step 12: Take Action on Results

Now that you have your results:

### Prioritize Your Work

1. **Start with Critical issues** - These must be fixed
2. **Move to High severity** - Important for compliance
3. **Address Medium items** - Improve your compliance posture
4. **Consider Low priority** - Time permitting

### For Each Issue:

1. **Click on the issue** to see full details
2. **Read the explanation** carefully
3. **Review the fix suggestion**
4. **Locate the code** using the file path provided
5. **Implement the fix** according to recommendations
6. **Document what you changed** for audit purposes

### Get Help if Needed

- **Technical questions:** Consult with your development team
- **Compliance questions:** Speak with your compliance officer or legal team
- **OrchestrAI questions:** Contact support or your workspace admin

## Step 13: Export and Share Results

Want to share findings with your team or save for records?

1. **Look for "Export Results"** button on the results page
2. **Click it** to download a comprehensive report
3. **Choose your format** (usually PDF or detailed spreadsheet)

**Uses for exported results:**
- Share with compliance team
- Include in audit documentation
- Attach to project reports
- Track progress over time
- Present to stakeholders

## Step 14: Track Progress

After addressing issues:

1. **Run the analysis again** to verify fixes
2. **Compare before and after scores**
3. **Document improvements** for your records
4. **Keep audit trail** of compliance work

Many teams run compliance checks:
- Before major releases
- Monthly for active projects
- After significant code changes
- Before compliance audits

## Common Questions

**Q: Will this analysis actually fix compliance issues?**
A: No, the analysis identifies problems and tells you how to fix them. Your team implements the actual fixes. (Some plans may offer automated fixing as an add-on feature.)

**Q: How accurate is the compliance analysis?**
A: Very accurate for standard requirements. However, always consult with legal and compliance professionals for final sign-off, especially for regulated industries.

**Q: Can I run this before every code change?**
A: Yes! Many teams integrate compliance checks into their regular workflow. Running it frequently catches issues early.

**Q: What if I don't understand a compliance issue?**
A: Each issue includes explanations and references. You can also consult with your compliance team or contact OrchestrAI support for clarification.

**Q: How much does compliance analysis cost?**
A: Costs vary by plan. Check with your workspace administrator or review your subscription details. Some plans include a certain number of free analyses per month.

**Q: Can I analyze multiple repositories at once?**
A: You analyze one repository at a time, but you can queue multiple analyses. Results are generated separately for each repository.

**Q: What regulations does OrchestrAI check?**
A: The system checks common regulations like GDPR, HIPAA, SOC 2, PCI-DSS, and others. The specific checks depend on your custom instructions and detected patterns in your code.

## Important Reminders

### Compliance is Ongoing

- **Run regular checks** - Don't just check once
- **Update as regulations change** - Laws and standards evolve
- **Train your team** - Everyone should understand compliance
- **Document everything** - Keep records of checks and fixes

### Always Verify Critical Compliance

While OrchestrAI is powerful:
- **Consult legal professionals** for important compliance decisions
- **Have compliance team review** critical findings
- **Don't rely solely on automation** for regulated industries
- **Keep human oversight** in the compliance process

## What's Next?

Now that you've run your first compliance analysis:

1. **Create a compliance schedule** - Decide how often to run checks
2. **Assign responsibilities** - Who handles which types of issues?
3. **Set up notifications** - Get alerted to new compliance concerns
4. **Explore other features** - Try Code Quality or Testing analysis
5. **Train your team** - Help others learn compliance analysis

## Success Checklist

You've successfully used Compliance analysis when you can:

- ✓ Access the Compliance section
- ✓ Verify compliance is enabled for your workspace
- ✓ Select and analyze a repository
- ✓ Understand the progress indicators
- ✓ Interpret the results page
- ✓ Prioritize issues by severity
- ✓ Export results for sharing
- ✓ Know when to run compliance checks

## Getting Help

If you encounter any issues:

1. **Check permissions** - Ensure you have the right access
2. **Verify configuration** - Compliance must be enabled
3. **Contact your admin** - For permission or setup issues
4. **Review documentation** - Check for updated guidance
5. **Reach out to support** - OrchestrAI team is here to help

---

**Congratulations!** You now know how to use both Code Quality and Compliance features in OrchestrAI. These powerful tools help you maintain high-quality, compliant code with minimal effort. Keep running regular analyses, and you'll see continuous improvements in your codebase quality and compliance posture.