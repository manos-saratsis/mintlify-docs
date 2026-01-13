# How to Monitor Costs and Usage

## Overview

Monitor your credit usage, track billing cycles, and manage your subscription plan to control your OrchestrAI costs effectively. The Cost Analysis page provides a complete view of your workspace's credit consumption and billing status.

## Accessing Cost Monitoring

Navigate to the Cost Analysis page from your workspace navigation menu. This page displays your current subscription status, credit usage, and available plan management options.

## Understanding Your Subscription Status

### Current Plan Display

At the top of the Cost Analysis page, you'll see:

- **Plan Type**: Either "Free Plan" or "Pro Plan"
- **Status Badge**: Shows your billing status with color-coded indicators:
  - Green "active" - Your subscription is active and in good standing
  - Red "exceeded" - You've exceeded your monthly credit limit
  - Red "cancelling at period end" - Your subscription is scheduled to cancel
  - Yellow "New plan scheduled" - A plan change is scheduled for your next billing cycle

### Subscription Actions

Depending on your current plan, you'll see different action buttons:

**On Free Plan:**
- **Upgrade to Paid** - Opens the plan selection modal to choose a paid subscription

**On Pro Plan:**
- **Edit Plan** - Modify your credit allocation or downgrade your subscription
- **Manage Billing** - Opens Stripe's customer portal to update payment methods, view invoices, and manage billing details
- **Refresh** - Updates your billing information with the latest data

## Monitoring Credit Usage

### Monthly Credit Tracking

The Cost Analysis page shows a visual progress bar displaying:
- **Credits Used**: Current month's credit consumption
- **Total Credits**: Your monthly credit allowance
- **Credits Remaining**: Available credits for the rest of the month

**Free Plan**: 50 credits per month
**Pro Plans**: Credit limit based on your selected tier (100 to 5,000+ credits/month)

### Billing Cycle Information

For paid subscriptions, you'll see:
- **Next billing date**: When your next payment is due
- **Credits after next billing**: Your credit allocation for the upcoming cycle
- **Scheduled changes**: Any plan modifications that will take effect at the next billing date

## Managing Your Subscription Plan

### Upgrading from Free to Pro

1. Click the **Upgrade to Paid** button
2. In the modal that opens, select your desired credit allocation:
   - 100 credits/month - $25
   - 200 credits/month - $50
   - 400 credits/month - $100
   - 1,000 credits/month - $250
   - 2,000 credits/month - $500
   - 3,000 credits/month - $750
   - 5,000 credits/month - $1,250
3. Click **Upgrade Now**
4. Complete the payment process in Stripe's secure checkout
5. Your workspace will be upgraded immediately upon successful payment

### Modifying Your Pro Plan

#### Upgrading Your Credit Limit

1. Click **Edit Plan**
2. Select a higher credit tier from the dropdown menu
3. Click **Upgrade Now**
4. The change takes effect immediately
5. You'll be charged a prorated amount for the remainder of your billing cycle

#### Downgrading Your Credit Limit

1. Click **Edit Plan**
2. Select a lower credit tier from the dropdown menu
3. Click **Schedule Downgrade**
4. The change will take effect at the end of your current billing period
5. You'll keep your current credit limit until the next billing date

A notification will appear confirming: "Downgrade will take effect at the end of your current billing period. You'll keep your current credit limit until then."

#### Downgrading to Free

1. Click **Edit Plan**
2. Click **Go to Free** at the bottom of the modal
3. Your subscription will be cancelled
4. At the end of your billing period, your workspace will revert to the Free plan (50 credits/month)
5. All private repositories will have OrchestrAI automatically disabled

## Understanding Scheduled Changes

### Pending Plan Changes

When you have a scheduled subscription change, you'll see a blue notification banner with:
- **Current plan expiration**: When your current subscription ends
- **New plan details**: The credit allocation that will take effect
- **Modification options**: Click "Edit Plan" to change or cancel the scheduled update

### Cancelled Subscriptions

If you've cancelled your subscription, you'll see a red notification banner:
- Your current plan remains active until the billing period ends
- After that date, you'll be downgraded to the Free plan
- You can click "Edit Plan" to schedule a new subscription or reactivate your current plan

### Reactivating a Cancelled Subscription

1. Click **Edit Plan** while your cancellation is pending
2. Select your desired credit tier
3. Click **Schedule New Plan**
4. The new subscription will automatically start after your current period ends
5. No service interruption will occur

## Pro Plan Features

When you upgrade to any Pro plan, you gain access to:
- **Enterprise analysis**: Advanced analysis capabilities
- **Unlimited everything**: No restrictions on analysis types or frequency
- **24/7 support**: Round-the-clock assistance
- **Custom solutions**: Tailored configurations for your needs

## Credit Usage by Analysis Type

Different analysis operations consume credits at varying rates. Monitor your usage patterns to optimize your credit consumption:

- The system tracks credit usage in real-time from all analysis executions
- Usage data syncs automatically to ensure accurate billing
- Credits reset at the beginning of each billing cycle

## Managing Billing Details

### Updating Payment Methods

1. Click **Manage Billing** on the Cost Analysis page
2. You'll be redirected to Stripe's secure customer portal
3. Update your payment method, billing address, or other details
4. Changes take effect immediately

### Viewing Invoices

Access your invoice history through the **Manage Billing** portal:
- View all past invoices
- Download invoices as PDFs
- Track payment history
- See itemized charges

## Best Practices for Cost Control

### Monitoring Usage Regularly

- Check your Cost Analysis page weekly to track credit consumption
- Use the **Refresh** button to ensure you're viewing the latest data
- Set internal reminders before your billing date to review usage patterns

### Optimizing Credit Usage

- Start with a lower credit tier and upgrade as needed
- Monitor which analyses consume the most credits
- Schedule downgrades in advance if you anticipate lower usage periods

### Planning Plan Changes

- **Upgrades**: Take effect immediately to provide instant access to more credits
- **Downgrades**: Scheduled for the next billing cycle to avoid losing prepaid credits
- Review scheduled changes before they take effect to ensure they match your needs

## Troubleshooting

### Usage Not Updating

If your credit usage doesn't reflect recent activity:
1. Click the **Refresh** button at the top of the Subscription Status card
2. Wait a few moments for the system to sync
3. The page will reload with updated information

### Plan Change Not Processing

If a plan modification doesn't complete:
- Check the Manage Billing portal for any payment issues
- Verify that your payment method is valid and has sufficient funds
- Contact support if the issue persists

### Exceeded Credit Limit

When your status shows "exceeded":
- New analyses may be blocked until you upgrade or wait for the next billing cycle
- Click **Edit Plan** to increase your credit allocation immediately
- Free plan users must upgrade to a paid plan to continue

## Understanding Billing Cycles

- **Monthly billing**: Charges occur on the same day each month
- **Credit reset**: Your credit allocation refreshes at the start of each billing cycle
- **Prorated charges**: Upgrades are charged proportionally for the remaining cycle period
- **Scheduled changes**: Downgrades and cancellations take effect at cycle end to preserve your prepaid credits