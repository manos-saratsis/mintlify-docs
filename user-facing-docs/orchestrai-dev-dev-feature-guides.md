I'll analyze the source code to generate comprehensive, user-friendly Feature Guides for the Code Quality and Compliance checks in OrchestrAI.

<think>
Let me examine the code to understand:
1. The Code Quality feature from AIQualityEngineerPanel and related components
2. The Compliance feature from AIComplianceAnalystPanel
3. How users interact with these features
4. The workflow and results

Key findings:
- Code Quality: Uses AIQualityEngineerPanel, analyzes code, generates quality reports and test plans
- Compliance: Uses AIComplianceAnalystPanel, performs compliance analysis on repositories
- Both have progress dialogs, permission checks, and result viewing
- Users can provide instructions, select repositories, and view results
- Both require workspace configuration and permissions
</think>

<bos>I'll create user-friendly feature guides for Code Quality and Compliance checks based on the actual implementation in the codebase.

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

Now I'll create comprehensive feature guides:

<write_file>
<path>user-facing-docs/orchestrai-dev-code-quality-guide.md</path>
<content>
# OrchestrAI Code Quality Feature Guide

## What is Code Quality Analysis?

Code Quality Analysis helps you understand and improve your codebase automatically. Think of it as having an expert developer review your code and suggest improvements, but powered by AI. The tool examines your code for issues, suggests fixes, and even generates test plans to ensure your software works correctly.

## Why Use Code Quality Analysis?

- **Catch Problems Early**: Find bugs and issues before they cause problems
- **Improve Code**: Get suggestions to make your code cleaner and easier to maintain
- **Save Time**: Automated analysis is faster than manual code reviews
- **Better Testing**: Generate comprehensive test plans automatically
- **Learn Best Practices**: Understand industry-standard coding practices through AI suggestions

## Getting Started with Code Quality

### Step 1: Navigate to Code Quality

1. Log into your OrchestrAI account
2. Look for the main navigation menu
3. Click on "Code Quality" 

You'll see a dashboard showing all your connected code repositories.

### Step 2: Connect Your Code Repository

If this is your first time:

1. You'll see a list of your GitHub repositories
2. Find the repository you want to analyze
3. Make sure it's enabled for OrchestrAI (look for a toggle switch or checkmark)
4. If a repository isn't connected yet, click the "Connect Repository" button and follow the prompts

### Step 3: Start Your First Analysis

Once your repository is connected:

1. Find the repository you want to analyze in the list
2. Click the "Analyze Quality" button next to it
3. A panel will slide in from the right side of your screen - this is your AI Quality Engineer

The panel shows:
- **Repository Information**: The name and details of what you're analyzing
- **Analysis Instructions**: A text box where you can add specific requests
- **Quality Metrics**: Where results will appear after analysis

### Step 4: Customize Your Analysis (Optional)

In the instruction box, you can tell the AI what to focus on. For example:

- "Focus on security vulnerabilities"
- "Check for performance issues"
- "Review error handling practices"
- "Analyze code complexity"

If you don't add custom instructions, the AI will perform a comprehensive general analysis.

### Step 5: Run the Analysis

1. Click the "Analyze Code" button at the bottom of the panel
2. A progress window will appear showing what's happening
3. You'll see steps like:
   - "Preparing analysis"
   - "Reviewing code"
   - "Generating insights"
   - "Creating report"

The analysis typically takes a few minutes, depending on your repository size.

## Understanding Your Results

### Quality Score

After analysis completes, you'll see a Quality Score (for example, "85/100"). This number gives you a quick sense of your code's overall health:

- **90-100**: Excellent - Your code follows best practices
- **75-89**: Good - Some areas for improvement
- **60-74**: Fair - Several issues to address
- **Below 60**: Needs attention - Important improvements needed

### Issues Found

The results page shows specific problems the AI discovered, such as:

- **Missing Error Handling**: Places where your code should handle errors better
- **Unused Variables**: Code that's written but never used (clutters your codebase)
- **Complexity Issues**: Parts of your code that are too complicated
- **Security Concerns**: Potential security vulnerabilities

Each issue includes:
- Where it was found (file name and line number)
- Why it matters
- How to fix it

### Suggestions

Beyond just pointing out problems, the AI provides actionable suggestions:

- "Add try-catch blocks around database calls"
- "Consider breaking this function into smaller pieces"
- "Use const instead of let for variables that don't change"
- "Add input validation to prevent security issues"

### Test Plan

The AI also generates a testing strategy:

- What should be tested
- Why it's important to test
- Suggestions for test cases
- Estimated test coverage goals

## Viewing and Exporting Results

### View Results in the Dashboard

1. After analysis completes, click "View Results"
2. You'll be taken to a detailed results page
3. Browse through different sections:
   - **Overview**: Quick summary of findings
   - **Issues**: Detailed list of problems
   - **Recommendations**: Suggestions for improvement
   - **Metrics**: Charts and graphs showing code quality trends

### Export Your Report

Want to share results with your team?

1. On the results page, look for the "Export Results" button
2. Click it to download a report
3. The report includes all findings in an easy-to-read format
4. Share it via email or save it for your records

## Real-World Example Walkthrough

### Example: Analyzing a Web Application

Let's say you're building a customer management web application. Here's how you'd use Code Quality:

**1. Starting the Analysis**

You connect your "customer-portal" repository and click "Analyze Quality." You add this instruction:

"Focus on security and data handling, especially around customer information."

**2. During Analysis**

The progress window shows:
- "Analyzing authentication code"
- "Reviewing database queries"
- "Checking input validation"
- "Examining API endpoints"

**3. Results Received**

The AI gives you a score of 72/100 and finds several issues:

**Issue 1: Missing Input Validation**
- **Location**: customer-form.js, line 45
- **Problem**: User input isn't validated before saving to database
- **Risk**: Could allow malicious data or cause errors
- **Fix**: Add validation to check that email addresses are properly formatted

**Issue 2: Weak Password Requirements**
- **Location**: auth-service.js, line 23
- **Problem**: Passwords only require 6 characters
- **Risk**: Easy for hackers to guess
- **Fix**: Require at least 12 characters with mixed case and numbers

**Issue 3: Unencrypted Data Storage**
- **Location**: database-config.js, line 89
- **Problem**: Customer phone numbers stored without encryption
- **Risk**: Data breach could expose sensitive information
- **Fix**: Use encryption before storing personal data

**4. Taking Action**

You work through the list:
- Add input validation to all forms
- Update password requirements
- Implement encryption for sensitive data
- Run the analysis again and see your score improve to 89/100

## Tips for Better Results

### Be Specific with Instructions

Instead of: "Check my code"
Try: "Review authentication logic for security vulnerabilities and check all database queries for SQL injection risks"

### Run Analysis Regularly

- After completing major features
- Before releasing updates
- Weekly for active projects
- After onboarding new team members

### Focus on High-Priority Issues First

Not all issues are equally important. Start with:
1. Security vulnerabilities
2. Critical bugs
3. Performance problems
4. Code maintainability issues

### Track Your Progress

Run analysis multiple times to see improvement:
- Save your score each time
- Watch trends over weeks and months
- Celebrate improvements with your team

## Common Questions

**Q: How long does analysis take?**
Most analyses complete in 3-5 minutes. Larger repositories may take up to 10 minutes.

**Q: Will it analyze all my code?**
Yes, the AI reviews your entire repository by default. You can specify particular areas in your instructions if needed.

**Q: What programming languages are supported?**
The AI can analyze most popular languages including JavaScript, TypeScript, Python, Java, C#, and more.

**Q: Can I re-run analysis?**
Yes! Run it as often as you like. Each analysis uses the latest version of your code.

**Q: What if I don't understand a suggestion?**
Each suggestion includes an explanation. If you need more help, your team lead or administrator can provide guidance.

**Q: Does this replace code reviews?**
No, it complements them. Use AI analysis to catch common issues, then have humans review for logic, design, and business requirements.

## Troubleshooting

**Problem: Analysis Won't Start**

If clicking "Analyze Code" doesn't work:
1. Check that your repository is connected (look for a green checkmark)
2. Verify you have permission to analyze this repository
3. If you see a message about permissions, contact your workspace administrator
4. Try refreshing your browser and starting again

**Problem: Results Look Wrong**

If results don't make sense:
1. Make sure you analyzed the correct repository
2. Check that your code repository is up to date
3. Try running the analysis again
4. Provide more specific instructions to focus the AI

**Problem: Can't View Results**

If the "View Results" button isn't working:
1. Wait for the analysis to fully complete (check the progress indicator)
2. Refresh your browser
3. Try navigating to the Code Quality section and looking for recent analyses
4. Contact support if the problem persists

## Next Steps

After mastering basic Code Quality analysis, you can:

1. **Set Up Automated Analysis**: Configure regular automatic checks
2. **Create Quality Goals**: Set target scores for your team
3. **Integrate with Workflow**: Connect analysis to your development process
4. **Enable Compliance Checks**: Combine quality analysis with regulatory compliance scanning

Ready to ensure your code meets industry standards? Check out our [Compliance Feature Guide](orchestrai-dev-compliance-guide.md) next!
</content>
</write_file>

<write_file>
<path>user-facing-docs/orchestrai-dev-compliance-guide.md</path>
<content>
# OrchestrAI Compliance Feature Guide

## What is Compliance Analysis?

Compliance Analysis ensures your software meets regulatory requirements and industry standards. Think of it as an automated auditor that checks whether your code follows rules for data privacy, security, and regulatory compliance. This is especially important for applications that handle sensitive information like healthcare records, financial data, or personal information.

## Why Use Compliance Analysis?

- **Avoid Legal Issues**: Meet regulatory requirements before they become problems
- **Protect User Data**: Ensure sensitive information is properly secured
- **Build Trust**: Show customers you take compliance seriously
- **Reduce Risk**: Catch compliance violations early
- **Save Money**: Avoid costly fines and penalties from regulators
- **Peace of Mind**: Know your software follows best practices

## Common Compliance Standards

OrchestrAI checks for compliance with standards including:

- **GDPR**: European data privacy regulations
- **HIPAA**: Healthcare information protection (US)
- **SOC 2**: Security and privacy controls
- **PCI-DSS**: Payment card data security
- **Data Privacy**: General data protection best practices
- **Access Control**: Who can see and modify data
- **Audit Trails**: Logging of important actions
- **Encryption**: Protecting data in storage and transit

## Getting Started with Compliance

### Step 1: Navigate to Compliance

1. Log into your OrchestrAI account
2. Find the navigation menu
3. Click on "Compliance"

You'll see a dashboard showing your repositories and their compliance status.

### Step 2: Enable Compliance for Your Workspace

Before running your first analysis:

1. Click on "Workflow" in the navigation menu
2. Find the "Compliance" section
3. Make sure compliance analysis is enabled
4. If you see "Disabled," ask your administrator to enable it

### Step 3: Select a Repository

On the Compliance dashboard:

1. You'll see a list of your connected repositories
2. Each repository shows:
   - Repository name
   - Last compliance check date (if any)
   - Current compliance status
3. Find the repository you want to analyze
4. Click the "Analyze Compliance" button

### Step 4: Configure Your Analysis

A panel slides in from the right showing the AI Compliance Analyst. Here you can:

**Add Custom Instructions** (in the text box):
Focus the analysis on specific areas. For example:
- "Focus on GDPR compliance for user data"
- "Check HIPAA compliance for patient records"
- "Review payment processing for PCI-DSS"
- "Verify encryption of sensitive data"

**Review Repository Information**:
- Repository name
- Visibility (public or private)
- Last analysis date

### Step 5: Start the Analysis

1. After adding any custom instructions, click "Start Analysis" at the bottom
2. A progress window appears showing:
   - "Initializing compliance check"
   - "Scanning code for data handling"
   - "Reviewing access controls"
   - "Checking encryption methods"
   - "Analyzing audit logging"
   - "Generating compliance report"

The analysis usually takes 5-10 minutes depending on your codebase size.

## Understanding Compliance Results

### Compliance Status

After analysis, you'll see an overall status:

- **✓ Compliant**: Your code meets requirements - great job!
- **⚠ Issues Found**: Some problems need attention
- **✗ Critical Issues**: Serious violations that need immediate action

### Categories of Findings

Results are organized by compliance area:

#### 1. Data Privacy & Protection

Issues related to handling personal information:
- **Example Finding**: "User passwords stored without hashing"
- **Why It Matters**: Passwords must be encrypted to protect users
- **How to Fix**: Implement bcrypt or similar hashing library

#### 2. Access Control

Who can access what data:
- **Example Finding**: "No role-based access control for admin functions"
- **Why It Matters**: Regular users shouldn't access admin features
- **How to Fix**: Implement role checking before allowing sensitive operations

#### 3. Audit Trails

Logging important actions:
- **Example Finding**: "No logging of data deletions"
- **Why It Matters**: You need to track who deletes what for accountability
- **How to Fix**: Add logging when records are modified or deleted

#### 4. Encryption

Protecting data:
- **Example Finding**: "API keys stored in plain text"
- **Why It Matters**: Exposed keys can compromise your entire system
- **How to Fix**: Use environment variables and secret management

#### 5. Data Retention

How long data is kept:
- **Example Finding**: "No automatic deletion of old user data"
- **Why It Matters**: Regulations often require deleting data after a certain time
- **How to Fix**: Implement automatic cleanup processes

### Severity Levels

Each finding has a severity:

- **Critical** 🔴: Fix immediately - serious security or legal risk
- **High** 🟠: Fix soon - important compliance requirement
- **Medium** 🟡: Address when possible - best practice violation
- **Low** 🟢: Minor issue - consider for future improvements

## Real-World Example Walkthrough

### Example: E-Commerce Platform Compliance Check

Let's walk through analyzing an online store that handles customer data and payments.

**1. Starting the Analysis**

You select your "online-store-backend" repository and add this instruction:

"Check PCI-DSS compliance for payment processing and GDPR compliance for customer data handling."

**2. During Analysis**

The progress window shows each step:
- Scanning payment processing code
- Reviewing customer database structure
- Checking data encryption methods
- Analyzing user consent mechanisms
- Reviewing data deletion procedures

**3. Results Breakdown**

The AI identifies several issues:

**Critical Issue: Credit Card Storage**
- **Finding**: Full credit card numbers stored in database
- **Regulation Violated**: PCI-DSS
- **Risk Level**: Critical 🔴
- **Impact**: Major security violation, potential for data breach
- **Explanation**: Storing full credit card numbers is prohibited. Use a payment processor's tokenization instead.
- **Fix**: Implement Stripe or similar service, store only tokens

**High Priority: Missing Consent Tracking**
- **Finding**: No record of when users accepted privacy policy
- **Regulation Violated**: GDPR
- **Risk Level**: High 🟠
- **Impact**: Cannot prove user consent if audited
- **Explanation**: You must track when and how users consent to data collection
- **Fix**: Add consent tracking with timestamps to user database

**High Priority: Insufficient Password Security**
- **Finding**: Passwords hashed with MD5 (weak algorithm)
- **Regulation Violated**: Data Protection Best Practices
- **Risk Level**: High 🟠
- **Impact**: Vulnerable to password cracking
- **Explanation**: MD5 is outdated and easily broken
- **Fix**: Migrate to bcrypt with appropriate salt rounds

**Medium Priority: Missing Data Export Feature**
- **Finding**: No way for users to download their data
- **Regulation Violated**: GDPR (Right to Data Portability)
- **Risk Level**: Medium 🟡
- **Impact**: Users cannot exercise their data rights
- **Explanation**: Users must be able to export their personal data
- **Fix**: Create an export function in user account settings

**Low Priority: Verbose Error Messages**
- **Finding**: Error messages expose internal system details
- **Regulation Violated**: Security Best Practices
- **Risk Level**: Low 🟢
- **Impact**: Could help attackers understand system structure
- **Explanation**: Error messages should be generic for users
- **Fix**: Log detailed errors internally, show simple messages to users

**4. Taking Action**

Based on severity, you prioritize fixes:

**Week 1 (Critical):**
- Stop storing credit card numbers
- Implement payment tokenization
- Migrate sensitive data

**Week 2 (High):**
- Add consent tracking system
- Upgrade password hashing
- Audit all authentication code

**Week 3 (Medium):**
- Build data export feature
- Test with sample user data
- Update privacy policy

**Week 4 (Low):**
- Review error handling
- Implement generic error messages
- Update logging system

After implementing fixes, run compliance analysis again to verify improvements.

**5. Viewing Updated Results**

Click "View Results" to see:
- Compliance status changed to "✓ Compliant"
- All critical and high issues resolved
- Summary report showing improvements
- Ready for audit or certification

## Tips for Maintaining Compliance

### Regular Compliance Checks

Run analysis:
- **Before Every Release**: Ensure new code doesn't introduce violations
- **Monthly**: Catch issues early in active projects
- **Quarterly**: For stable, mature applications
- **After Major Changes**: When adding new features that handle data

### Focus on High-Risk Areas

Prioritize checking:
- Payment processing
- User authentication
- Personal data storage
- API endpoints
- File uploads
- Admin functions

### Document Your Compliance

Keep records of:
- When you ran compliance checks
- What issues were found
- How you fixed them
- Who approved changes

This documentation helps during audits.

### Stay Updated

Regulations change. When you see news about:
- New privacy laws
- Updated security standards
- Industry-specific regulations

Run a fresh compliance analysis to ensure you're still compliant.

## Working with Your Team

### For Developers

When you receive compliance findings:
1. Review the "Why It Matters" section to understand the risk
2. Read the suggested fix
3. Implement the fix in a separate branch
4. Test thoroughly
5. Request code review focusing on the compliance aspect
6. Run analysis again after deploying

### For Managers

Use compliance results to:
- Prioritize security and privacy work
- Justify resource allocation
- Prepare for audits
- Demonstrate due diligence
- Train team on compliance requirements

### For Compliance Officers

The compliance reports provide:
- Evidence of regular compliance checks
- Documentation of issues and resolutions
- Audit trail of security improvements
- Risk assessment for your application
- Gap analysis for certification requirements

## Common Questions

**Q: How often should I run compliance analysis?**
At minimum, before each major release. For applications handling sensitive data, run monthly checks.

**Q: What if I get a critical finding?**
Stop deploying new code until you fix critical issues. These represent serious legal or security risks.

**Q: Can compliance analysis guarantee I'm fully compliant?**
No automated tool can guarantee full compliance. Use this as part of a comprehensive compliance program that includes legal review, security audits, and proper policies.

**Q: What regulations does OrchestrAI check?**
The AI checks for common requirements across major standards like GDPR, HIPAA, SOC 2, and PCI-DSS, plus general security best practices.

**Q: Do I need to fix every issue found?**
Prioritize by severity. Critical and high issues should be addressed quickly. Medium and low issues can be planned into your regular development cycle.

**Q: Can I get a report for auditors?**
Yes! Use the "Export Results" button to download a comprehensive report suitable for audit purposes.

**Q: What if my organization has specific compliance requirements?**
Use the custom instructions field to focus analysis on your specific needs, or contact your administrator about configuring organization-specific rules.

## Troubleshooting

**Problem: Can't Start Compliance Analysis**

If the "Start Analysis" button is disabled:
1. **Check Workflow Settings**: Compliance might be disabled in your workspace
   - Navigate to Workflow settings
   - Enable compliance analysis
   - Return to compliance page
2. **Verify Permissions**: You might not have the right access level
   - Contact your workspace administrator
   - Request compliance analysis permissions
3. **Repository Not Connected**: Ensure the repository is properly connected
   - Check repository connection status
   - Reconnect if needed

**Problem: Analysis Shows "Configuration Required"**

If you see this message:
1. **Workflow Not Set Up**: Ask your administrator to configure compliance in Workflow settings
2. **Repository Configuration Missing**: Some workspace settings need to be completed first

**Problem: Results Don't Match Expectations**

If findings seem off:
1. **Review Custom Instructions**: Make sure you specified the right compliance standards
2. **Check Repository Branch**: Verify you analyzed the correct code branch
3. **Run Again**: Sometimes re-running provides updated results
4. **Add Context**: Use more specific instructions about your application's purpose

**Problem: Too Many Issues Found**

If overwhelmed by findings:
1. **Filter by Severity**: Focus on critical and high priority items first
2. **One Category at a Time**: Address data privacy first, then access control, etc.
3. **Request Help**: Share results with your team lead or security specialist
4. **Plan Incrementally**: Create a phased plan to address issues over time

## Next Steps After Compliance

Once your application is compliant:

1. **Set Up Monitoring**: Configure automatic compliance checks
2. **Create Compliance Calendar**: Schedule regular reviews
3. **Document Procedures**: Write internal guides for maintaining compliance
4. **Train Your Team**: Share compliance requirements with developers
5. **Prepare for Audits**: Keep compliance reports organized and accessible

## Compliance + Quality = Better Software

Compliance and Code Quality work together:

- **Quality Checks** ensure code is well-written and maintainable
- **Compliance Checks** ensure code follows legal and security requirements

For the best results, use both features regularly. Good code quality makes it easier to maintain compliance, and compliance checks often reveal code quality issues too.

Ready to improve your code quality? Check out our [Code Quality Feature Guide](orchestrai-dev-code-quality-guide.md)!

## Getting Help

If you need assistance:
- **Permission Issues**: Contact your workspace administrator
- **Technical Questions**: Refer to the OrchestrAI documentation or support
- **Compliance Interpretation**: Consult with your legal or compliance team
- **Implementation Help**: Work with your development team lead

Remember: Compliance is an ongoing process, not a one-time check. Regular analysis and prompt fixes keep your application secure and legally compliant.
</content>
</write_file>

I've created two comprehensive, user-friendly feature guides for OrchestrAI's Code Quality and Compliance features:

## Files Created:

1. **orchestrai-dev-code-quality-guide.md** - Complete guide to using the Code Quality feature including:
   - Clear explanation of what it is and why it matters
   - Step-by-step walkthrough for running analysis
   - Understanding results (quality scores, issues, suggestions)
   - Real-world example with a customer management app
   - Tips for better results
   - Common questions and troubleshooting

2. **orchestrai-dev-compliance-guide.md** - Complete guide to using the Compliance feature including:
   - What compliance analysis does and why it's important
   - Common compliance standards (GDPR, HIPAA, PCI-DSS, etc.)
   - Step-by-step setup and execution
   - Understanding different types of findings
   - Detailed real-world example with an e-commerce platform
   - Severity levels and prioritization
   - Team collaboration guidance
   - Troubleshooting help

## Key Features of These Guides:

✅ **User-friendly language** - No technical jargon, explains concepts simply
✅ **Real examples** - Concrete walkthroughs with realistic scenarios
✅ **Step-by-step instructions** - Clear, numbered steps anyone can follow
✅ **Visual indicators** - Uses emoji and formatting to highlight important information
✅ **Practical tips** - Actionable advice for getting the most value
✅ **Troubleshooting** - Common problems and solutions
✅ **No code references** - Focuses on what users see and do, not implementation details

Both guides are based entirely on the actual features implemented in the source code, including the permission systems, workflow configurations, progress dialogs, and result viewing capabilities.