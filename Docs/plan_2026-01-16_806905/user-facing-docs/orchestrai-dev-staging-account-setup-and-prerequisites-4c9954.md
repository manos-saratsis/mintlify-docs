# Account Setup and Prerequisites

## System Requirements

### Browser Compatibility
OrchestrAI works best with modern web browsers. For the optimal experience, use:
- Chrome (recommended)
- Firefox
- Safari
- Edge

Ensure your browser has JavaScript enabled and allows cookies for authentication.

### Internet Connection
A stable internet connection is required to access OrchestrAI and connect to your code repositories.

## Creating Your Account

### Sign Up Options

You can create an OrchestrAI account in three ways:

**Email and Password**
1. Visit the OrchestrAI sign-up page
2. Enter your email address
3. Create a secure password
4. Optionally provide your full name
5. Click to create your account

**Google Account**
1. Click the "Sign in with Google" button
2. Select your Google account
3. Authorize OrchestrAI to access your basic profile information

**GitHub Account**
1. Click the "Sign in with GitHub" button
2. Log in to your GitHub account if prompted
3. Authorize OrchestrAI to access your basic profile information

### Email Verification

After signing up with email and password, you'll receive a verification email. Check your inbox and click the verification link to activate your account. The email will be sent from OrchestrAI, so check your spam folder if you don't see it within a few minutes.

### Accepting Team Invitations

If you received an invitation to join someone else's workspace:
1. Click the invitation link in your email
2. If you don't have an account, create one using any of the sign-up methods above
3. Your account will automatically be connected to the workspace after sign-up
4. If you already have an account, sign in and you'll be added to the workspace

## Understanding Workspaces

### What is a Workspace?

A workspace is your collaboration environment in OrchestrAI. Think of it as a team space where you can:
- Connect and manage your code repositories
- Share access with team members
- Track usage and costs
- Manage your subscription plan

### Your First Workspace

When you create an account, OrchestrAI automatically creates your first workspace. This workspace:
- Is set as your default workspace
- Starts on the Free plan with 50 monthly credits
- Can be renamed at any time
- Allows you to get started immediately

### Creating Additional Workspaces

You can create multiple workspaces to organize different projects or teams:
1. Navigate to your Account page
2. View your existing workspaces
3. Create a new workspace by providing a name
4. Switch between workspaces as needed

Each workspace has its own:
- Connected repositories
- Team members
- Usage tracking
- Billing plan

### Switching Between Workspaces

When you have multiple workspaces:
1. Your selected workspace is remembered when you return to OrchestrAI
2. Switch workspaces by selecting a different one from your workspace list
3. All actions and repository connections apply to your currently selected workspace

## Repository Connection Requirements

### Supported Platforms

OrchestrAI currently supports:
- **GitHub** (public and private repositories)
- GitLab (coming soon)
- Bitbucket (coming soon)

### GitHub Account Setup

To connect repositories, you need:
- An active GitHub account
- Access to the repositories you want to connect (as owner or collaborator)
- Authorization to grant OrchestrAI access to your repositories

**Free Plan Repository Limits:**
- 1 public repository
- Up to 5 collaborators

**Pro Plan Repository Access:**
- All your public repositories
- All your private repositories
- Unlimited collaborators

### Preparing Your Repositories

Before connecting repositories to OrchestrAI:
- Ensure you have the necessary permissions to the repository
- Verify the repository is active and accessible
- Understand which repositories you want OrchestrAI to analyze

## Pricing Plans and Credits

### Understanding Credits

Credits are OrchestrAI's usage currency. When OrchestrAI analyzes your code, generates documentation, or performs actions, it consumes credits based on the complexity of the task.

**How Credits Work:**
- Different tasks cost different amounts of credits
- Simple analyses may cost less than 1 credit
- Complex workflows may cost several credits
- You only pay for what you actually use

**Why Variable Pricing:**
OrchestrAI agents perform many different types of work - from analyzing single files to processing entire codebases and generating documentation. Each action's complexity determines its credit cost, ensuring fair pricing for all usage patterns.

### Free Plan

**Cost:** $0 per month

**Includes:**
- 50 credits per month
- Credits reset at the beginning of each month
- No daily restrictions
- Approximately 3-4 complete AI workflows per month
- 1 public repository
- Up to 5 collaborators

**Best For:** Trying out OrchestrAI and small personal projects

### Pro Plan

**Starting at:** $25 per month

**Credit Options:**
- 100 credits: $25/month
- 200 credits: $50/month
- 400 credits: $100/month
- 1,000 credits: $250/month
- 2,000 credits: $500/month
- 3,000 credits: $750/month
- 5,000 credits: $1,250/month

**Includes:**
- Everything in the Free plan
- All your public and private repositories
- Unlimited collaborators
- Role-based access control

**Best For:** Professional developers and teams actively using OrchestrAI

### Selecting Your Plan

**Starting with Free:**
1. Create your account - you automatically start on the Free plan
2. Your workspace begins with 50 monthly credits
3. No credit card required to get started

**Upgrading to Pro:**
1. Navigate to your Account page
2. Click "Edit Plan" on your workspace
3. Select your desired monthly credit amount
4. Complete the payment setup
5. Your plan activates immediately

**Changing Your Pro Credit Allocation:**
1. Go to your Account page
2. Click "Edit Plan" on your workspace
3. Choose a different credit amount from the dropdown
4. Your new allocation takes effect on your next billing cycle

### Monitoring Usage

Track your credit usage to manage costs effectively:

1. **View Current Usage:**
   - Navigate to your Account page
   - Click "Usage" on any workspace
   - See your credit consumption for the current month

2. **Analyze Costs:**
   - Click "Cost Analysis" on any workspace
   - Review detailed breakdowns of credit usage
   - Identify which activities consume the most credits

3. **Monthly Reset:**
   - Credits reset at the beginning of each calendar month
   - Unused credits do not roll over to the next month
   - Usage history is preserved for your records

### Billing Status

Your workspace displays its billing status:
- **Active:** Plan is current and credits are available
- **Reached Limits:** Monthly credit allocation has been consumed
- **Paused:** Billing is temporarily paused
- **Closed:** Workspace billing has been cancelled

## Team Collaboration Setup

### Inviting Team Members

Share your workspace with collaborators:

1. Navigate to your workspace settings
2. Enter the email address of the person you want to invite
3. Send the invitation
4. They'll receive an email with instructions to join

### Role-Based Access (Pro Plan)

Pro plan workspaces include role-based access control, which allows you to:
- Control who can approve workflows for release
- Manage which team members can operate and call AI agents
- Set permissions appropriate to each user's responsibilities

**Future Enhancement:** Audit logs will track when users call agents and perform actions (coming soon).

### Collaboration Limits

**Free Plan:**
- Up to 5 collaborators per workspace

**Pro Plan:**
- Unlimited collaborators

### Managing Team Members

As a workspace owner, you can:
- View all workspace members
- See pending invitations
- Update member roles (Pro plan)
- Remove members when needed
- Transfer ownership if required

### Leaving a Workspace

If you've been invited to a workspace and want to leave:
1. Navigate to the workspace settings
2. Select the option to leave the workspace
3. Confirm your decision
4. You'll be removed from the workspace and lose access to its repositories

## Code and Documentation Ownership

### What You Own

You retain complete ownership of:
- All code generated by OrchestrAI
- All documentation created by OrchestrAI
- All changes and modifications made through OrchestrAI

### Managing Your Changes

Work with your OrchestrAI-generated content using standard Git tools:
- Collaborate directly at the source
- Check out changes using GitHub or other Git management tools
- Review and approve changes before they're committed
- Maintain full version control over your codebase

## Getting Started Checklist

Before you begin using OrchestrAI for repository analysis:

- [ ] Create your OrchestrAI account (email or OAuth)
- [ ] Verify your email (if using email sign-up)
- [ ] Review your automatically created workspace
- [ ] Understand your Free plan allocation (50 monthly credits)
- [ ] Ensure you have a GitHub account with repository access
- [ ] Decide which repositories you want to connect
- [ ] Invite team members if working collaboratively
- [ ] Review the pricing plans to understand upgrade options
- [ ] Check your usage tracking to monitor credit consumption

## Next Steps

With your account fully set up, you're ready to:
1. Connect your first repository to OrchestrAI
2. Explore the Dashboard to understand your project overview
3. Run your first AI analysis workflow
4. Generate documentation for your codebase
5. Monitor your credit usage and adjust your plan as needed

Your workspace is now configured and ready for AI-powered code analysis and documentation generation.