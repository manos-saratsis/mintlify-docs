I'll start by reading the key source files to understand the cost monitoring and usage features.Let me explore the repository structure to find the correct paths.Let me read the existing cost monitoring documentation to understand what's already been documented.Now let me check related files to understand the credit billing system and analysis costs better.# How to Monitor Costs and Usage

## Overview

Monitor your credit consumption, track subscription status, and manage your billing in real-time. The Cost Analysis page provides complete visibility into how your workspace uses credits, helping you optimize spending while maintaining access to AI-powered code analysis and automation.

## Accessing Your Cost Dashboard

1. Sign in to your workspace
2. Select **Cost Analysis** from your workspace navigation menu
3. View your subscription status, credit usage, and billing information

The dashboard displays all billing information in one place, including usage meters, subscription details, and plan management options.

## Understanding the Credit System

OrchestrAI uses credits as the currency for all AI operations. Credits are consumed when AI agents analyze code, generate documentation, write tests, or perform automated workflows.

### Credit Consumption

Different operations consume different amounts of credits:
- **Simple operations:** Less than 1 credit (quick checks, small file analysis)
- **Standard analyses:** 1-3 credits (code quality reviews, documentation generation)
- **Complex workflows:** Several credits (comprehensive security audits, multi-file processing)

The exact cost depends on the complexity of your codebase and the scope of the analysis.

## Monitoring Credit Usage

### Free Plan Usage Display

If you're on the Free plan, your dashboard shows:

**Monthly Credit Usage**
- Total monthly allocation: 50 credits
- Credits consumed this month
- Credits remaining until the next billing cycle
- Visual progress bar showing usage percentage

**Key Information:**
- No daily restrictions—use all 50 credits whenever needed
- Credits reset at the beginning of each month
- Approximately 3-4 complete AI workflows per month
- Access to 1 public repository with 5 collaborators

### Pro Plan Usage Display

Pro subscribers see:

**Monthly Credit Allocation**
- Total credits purchased (100 to 5,000+ credits)
- Credits used in the current billing period
- Remaining credits until next billing date
- Usage progress visualization

**Additional Information:**
- Next billing date
- Current subscription tier
- Scheduled plan changes (if any)
- Billing status indicator

### Real-Time Updates

Click the **Refresh** button to synchronize your usage data with the latest information. The system automatically tracks credit consumption as AI agents perform operations, but manual refresh ensures you see the most current data.

## Checking Subscription Status

Your dashboard displays subscription status with color-coded indicators:

**Active Subscription (Green)**
- Your plan is working normally
- All features are available
- Credits are being allocated correctly

**Cancelling at Period End (Red)**
- You've cancelled your subscription
- Current plan remains active until billing cycle ends
- Will downgrade to Free plan after the end date

**Plan Change Scheduled (Blue)**
- You've scheduled an upgrade or downgrade
- Current plan continues until next billing date
- New credit allocation takes effect on the specified date

**Credits Exceeded (Red)**
- You've used all available credits for this month
- AI operations are restricted until credits reset
- Consider upgrading to a higher tier for immediate access

## Managing Your Subscription

### Upgrading from Free to Pro

To access more credits and premium features:

1. Click **Upgrade to Paid** on your Cost Analysis page
2. Select your desired monthly credit tier:
   - 100 credits: $25/month
   - 200 credits: $50/month
   - 400 credits: $100/month
   - 1,000 credits: $250/month
   - 2,000 credits: $500/month
   - 3,000 credits: $750/month
   - 5,000 credits: $1,250/month
3. Enter your payment information in the secure checkout
4. Confirm your subscription

Your Pro plan activates immediately and credits are available right away.

### Changing Your Credit Allocation

For existing Pro subscribers:

1. Click **Edit Plan** on the Cost Analysis page
2. Select a different credit tier from the dropdown menu
3. Review the change summary
4. Confirm your new plan

**Upgrade Changes:**
- Take effect immediately
- New credits added to your current allocation
- Billing adjusts for the remainder of your cycle

**Downgrade Changes:**
- Scheduled for the end of your current billing period
- You keep your current credits until then
- New lower allocation starts on your next billing date

### Accessing Billing Management

Click **Manage Billing** to open your secure customer portal where you can:

- Update payment methods
- View complete billing history
- Download invoices for accounting
- Update billing address
- Cancel or modify subscriptions

All payment changes are processed securely through the billing provider.

## Understanding Plan Changes

### Scheduled Upgrades

When you upgrade, you'll see:
- Green notification confirming the upgrade
- New credit allocation amount
- Effective date (usually immediate)
- Updated billing amount

### Scheduled Downgrades

When you downgrade, you'll see:
- Blue notification about the pending change
- Future credit allocation
- Date the downgrade takes effect
- Reminder that current credits remain available

### Cancellation Notices

If you've cancelled:
- Red notification appears at the top
- Shows when you'll revert to the Free plan
- Lists features you'll lose access to
- Displays the final day of Pro benefits

You can modify or cancel any scheduled change before it takes effect by clicking **Edit Plan**.

## Optimizing Your Credit Usage

### Monitor Usage Patterns

Review your Cost Analysis page regularly to:
- Identify which days you use the most credits
- Understand typical consumption for different analysis types
- Determine if your current tier matches your needs
- Plan future analyses based on available credits

### Choose the Right Plan

**Signs you should upgrade:**
- Consistently using all monthly credits
- Frequently running out mid-month
- Waiting for credits to reset to continue work
- Need for more comprehensive analyses

**Signs you can downgrade:**
- Using less than 50% of your allocation
- Credits resetting with large amounts remaining
- Analysis needs have decreased
- Want to optimize costs

### Plan Your Billing Cycle

**Early in the cycle:**
- Run your most important analyses
- Execute complex workflows
- Take advantage of full credit availability

**Late in the cycle:**
- Check remaining credits before starting large operations
- Save simpler tasks for end-of-month
- Consider whether to upgrade if you need more capacity

### Cost-Effective Analysis Tips

1. **Run analyses strategically:** Schedule comprehensive reviews when you have plenty of credits
2. **Start with smaller scopes:** Test on single files before analyzing entire repositories
3. **Monitor after each operation:** Check credit deduction to understand costs
4. **Batch similar tasks:** Group related analyses to optimize agent efficiency
5. **Use targeted workflows:** Focus on specific issues rather than running everything

## Understanding Billing Cycles

### Monthly Allocation

Credits are allocated based on your billing cycle:
- **Free plan:** Resets on the 1st of each month
- **Pro plans:** Resets on your subscription anniversary date

### Billing Date Information

Your dashboard displays:
- Next billing date when credits will reset
- Days remaining in current billing period
- Expected credit renewal amount
- Any scheduled changes taking effect that date

### Automatic Renewals

All billing happens automatically:
- Credits reset at the start of each cycle
- Payment processed on your billing date
- No action required from you
- Email confirmation sent for each transaction

## Preventing Service Interruptions

### For Free Plan Users

When you reach 50 credits:
- AI agent operations pause until the next month
- You retain access to view previous analyses
- Credits automatically reset on the 1st
- Consider upgrading for immediate access

### For Pro Plan Users

When you exhaust your monthly credits:
- AI operations are restricted until next billing date
- Upgrade to a higher tier for instant credit top-up
- Review usage patterns to select appropriate tier
- Credits automatically renew on your next billing date

### Setting Usage Alerts

**Coming soon:** Credit threshold notifications that alert you when you've used:
- 50% of monthly allocation
- 75% of monthly allocation
- 90% of monthly allocation

## Billing Transparency

### Real-Time Credit Tracking

The system provides complete visibility:
- Credits consumed per analysis displayed after each operation
- Running total updated automatically
- Usage history available for review
- Detailed breakdown by workspace and operation type

### Understanding Costs

Every AI agent operation shows:
- Credits consumed for that specific task
- Brief explanation of the cost
- Timestamp of the operation
- User or automation that triggered it

This transparency helps you understand exactly where credits are being used.

### Payment History

In the billing portal, access:
- Complete invoice history
- Payment method on file
- Upcoming charges
- Past transaction details
- Downloadable receipts for expense reporting

## Getting Support

### Free Plan Support

Access self-service resources:
- Documentation and guides
- Community forums
- Email support for billing questions

### Pro Plan Support

Pro subscribers receive:
- 24/7 email support
- Priority response times
- Direct assistance with billing issues
- Usage optimization guidance
- Custom solutions for high-volume needs

Contact support through your dashboard or billing portal for:
- Unexpected credit usage questions
- Billing discrepancies
- Plan selection advice
- Usage pattern analysis
- Technical billing issues

## Ownership and Usage Rights

**All code and documentation generated by OrchestrAI belongs to you:**
- Export using git management tools
- Integrate with GitHub (GitLab and Bitbucket coming soon)
- Collaborate directly in the platform
- Use generated content without restrictions

You maintain full ownership regardless of your plan tier or credit usage.

## Future Billing Features

**Coming Soon:**

**Cost Forecasting**
- Estimate credit cost before running workflows
- Preview operation costs in advance
- Budget credits more effectively

**Usage Analytics**
- Detailed credit consumption reports
- Trend analysis over time
- Cost optimization recommendations
- Comparative analysis across workspaces

**Custom Enterprise Plans**
- Dedicated credit pools
- Volume discounts
- Flexible billing arrangements
- Service level agreements

---

**Quick Reference:**
- **Free Plan:** 50 credits/month, $0
- **Pro Plans:** Starting at 100 credits for $25/month ($0.25 per credit)
- **Pricing Formula:** $0.25 per credit across all Pro tiers
- **Credit Reset:** Automatic at the start of each billing cycle
- **Plan Changes:** Immediate upgrades, end-of-period downgrades