I'll read the key source files first to understand the credit-based billing system.Let me explore the repository structure to find the relevant files.# Credits, Billing, and Usage

## Overview

OrchestrAI operates on a credit-based billing system where you pay only for what you use. Every time the platform's AI agents analyze your code, generate documentation, or perform automated tasks, credits are consumed based on the complexity of the work. This flexible approach means your costs scale directly with your actual usage.

## What Are Credits?

Credits are the measurement unit for all AI operations in OrchestrAI. When an AI agent processes your files, writes code suggestions, or analyzes patterns in your repository, it uses credits proportional to the task's complexity.

**How credits are consumed:**
- Simple operations consume less than 1 credit
- Complex multi-file analyses may require several credits
- Each task's cost depends on the specific situation and level of complexity involved

This usage-based model ensures you're never paying for idle capacity—only for the work actually performed.

## Subscription Plans

### Free Plan

**Monthly Cost:** $0

**Credit Allocation:** 50 credits per month

The Free plan gives you:
- 50 credits that reset monthly at the start of each billing cycle
- Enough for approximately 3-4 complete AI workflows per month
- Access to 1 public repository
- Collaboration with up to 5 team members
- All credits refresh automatically when your monthly cycle begins

### Pro Plans

**Starting at:** $25/month

**Flexible Credit Packages:**

Choose the monthly credit allocation that fits your needs:

| Credits | Monthly Cost | Cost Per Credit |
|---------|--------------|-----------------|
| 100     | $25          | $0.25           |
| 200     | $50          | $0.25           |
| 400     | $100         | $0.25           |
| 1,000   | $250         | $0.25           |
| 2,000   | $500         | $0.25           |
| 3,000   | $750         | $0.25           |
| 5,000   | $1,250       | $0.25           |

**Additional Pro benefits:**
- Access to all your repositories (public and private)
- Unlimited team collaborators
- Role-based access controls for team management
- Audit logging for agent operations (coming soon)
- Workflow approval capabilities for controlled automation

## How Billing Works

### Monthly Billing Cycles

Your credits are allocated monthly and automatically reset at the beginning of each billing period. The billing cycle starts on the day you initially subscribe to a paid plan.

**Example:** If you subscribe on January 15th, your billing cycle runs from the 15th of each month. Credits refresh on the 15th, and any unused credits from the previous month expire.

### Tracking Your Usage

Monitor your credit consumption in real-time through the Cost Analysis page:

1. Navigate to the Cost Analysis section for your workspace
2. View your current usage against your monthly allocation
3. See exactly how many credits remain for this billing period
4. Track free credits and paid credits separately

**What you'll see:**
- **Monthly Credit Usage:** Total credits consumed versus your allocation
- **Credits Remaining:** How many credits you have left this month
- **Usage Progress:** Visual progress bar showing your consumption rate
- **Subscription Status:** Color-coded indicator of your plan health

### Credit Categories

**Free Credits:** Available to workspaces on the Free plan (50 credits monthly)

**Paid Credits:** Available to Pro plan subscribers based on their selected tier

The system tracks these separately to help you understand usage patterns and plan accordingly.

## Managing Your Subscription

### Upgrading to Pro

To upgrade from the Free plan:

1. Open the Cost Analysis page for your workspace
2. Locate the Subscription Status section
3. Click "Upgrade to Paid"
4. Select your desired monthly credit allocation
5. Complete the payment information
6. Your Pro plan activates immediately with full access to all features

### Changing Your Credit Tier

If you're already on a Pro plan and need to adjust:

1. Go to the Cost Analysis page
2. Find the Subscription Status section
3. Click "Edit Plan"
4. Choose a different credit tier from the available options
5. Confirm your selection

**Important timing information:**
- Plan changes can be scheduled for the end of your current billing period
- A notification will show when the new plan takes effect
- Your current credits remain available until the cycle ends
- You can modify or cancel scheduled changes anytime before they take effect

### Downgrading or Canceling

You have full control over your subscription:

1. Navigate to the Cost Analysis page
2. Click "Manage Billing" to open the customer portal
3. Select cancel subscription or modify your plan

**What happens after cancellation:**
- Your current plan continues through the end of the paid billing period
- All Pro features remain accessible until that date
- After the period ends, your workspace automatically reverts to the Free plan
- Future credit allocations become 50 credits per month
- Clear notifications display the scheduled change date and what changes to expect

### Scheduled Changes

When you have an upcoming plan modification:
- Your current plan continues without interruption
- The new credit allocation begins on your next billing date
- You can modify or cancel the scheduled change by clicking "Edit Plan"
- A notification banner displays details about what will change and when

## Subscription Status Indicators

Your Cost Analysis page uses color-coded badges to show your subscription health:

- **Active** (green badge): Your plan is working normally
- **Cancelling at period end** (red badge): Your subscription will end after this billing cycle
- **New plan scheduled** (blue badge): A plan change is queued for your next billing date
- **Exceeded** (red badge): You've consumed all available credits for this period

## Usage Restrictions and Limits

### Free Plan Restrictions
- 50 credits per month with no rollover
- No daily usage caps—use credits as needed throughout the month
- Access limited to 1 public repository
- Team size capped at 5 collaborators

### Pro Plan Limits
- Monthly credit allocation based on your selected package
- No daily restrictions on credit usage
- Access to all repositories (both public and private)
- No limit on team size or collaborators

### Exceeding Your Credit Limit

If you use all your monthly credits before the billing cycle ends:
- AI agent operations become restricted until credits reset
- You can immediately get more credits by upgrading to a higher tier
- Your billing status will show as "exceeded"
- Credits automatically replenish when your next billing period starts

**No surprise charges:** The system never charges you for overages. Once you reach your limit, operations pause until you upgrade or your credits reset.

## Billing Transparency

### Real-Time Updates

Your credit usage synchronizes automatically:
- Credit consumption updates as AI agents work
- Changes reflect immediately in your Cost Analysis dashboard
- Manual refresh option available via the "Refresh" button for instant updates

### Viewing Your Billing Information

The Cost Analysis page provides complete visibility:
- Current plan name (Free or Pro tier)
- Subscription status with visual indicators
- Monthly credit usage displayed as consumed/total
- Credits remaining for the current period
- Next billing date
- Any scheduled plan changes

### Payment Management

Pro subscribers can access the customer portal for:
- Updating payment methods
- Viewing complete billing history
- Downloading invoices for accounting
- Managing subscription preferences

Access these features by clicking "Manage Billing" from the Cost Analysis page.

## Ownership Rights

**All code, documentation, and other content generated by OrchestrAI belongs entirely to you.** You have complete freedom to:
- Collaborate directly within the platform
- Export all changes using standard git management tools
- Integrate with GitHub (GitLab and Bitbucket support coming soon)
- Use, modify, or redistribute generated content without restriction

OrchestrAI claims no ownership over anything created using the platform.

## Cost Forecasting

**Feature Coming Soon:** You'll be able to preview the approximate credit cost of a workflow or analysis before running it. This forecasting capability will help you budget your credits more effectively and make informed decisions about which operations to run.

## Tips for Managing Your Credits

**Monitor regularly:** Check your Cost Analysis page frequently to understand your consumption patterns and avoid running out of credits unexpectedly.

**Start small:** Begin with the Free plan or the smallest Pro tier to establish your typical usage before committing to larger allocations.

**Scale strategically:** When you consistently approach your credit limit, that's the right time to upgrade to the next tier.

**Use scheduled changes:** Plan subscription modifications to take effect at the end of billing periods, maximizing the value of your current credits.

**Design efficiently:** Consider credit costs when creating complex multi-step workflows. Sometimes breaking a large analysis into smaller focused tasks can be more credit-efficient.

**Track by workspace:** If you manage multiple workspaces, monitor each one's usage separately to identify which projects consume the most resources.