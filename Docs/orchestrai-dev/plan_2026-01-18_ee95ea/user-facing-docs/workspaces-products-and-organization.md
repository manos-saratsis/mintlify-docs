I'll retrieve the key source files first to understand the organizational structure.# Workspaces, Products, and Organization

## Overview

OrchestrAI uses a hierarchical structure to help you organize your work effectively. At the top level are **workspaces**, which contain **products**, which in turn contain **repositories**. This structure allows you to manage everything from individual projects to complex multi-team organizations with clear boundaries and access controls.

## Workspaces

### What is a Workspace?

A workspace is your main organizational container in OrchestrAI. Think of it as a shared space where you keep all your projects, team members, and settings together. Whether you're working solo or with a team, workspaces help you keep everything organized in one place.

Workspaces are where billing happens, team members are managed, and access permissions are set. Everything you do in OrchestrAI exists within a workspace.

### Personal vs Team Workspaces

**Personal Workspaces**

When you first sign up, OrchestrAI creates a default workspace for you automatically. This is your personal workspace where you can:

- Store your individual projects and repositories
- Experiment and test features
- Work independently without sharing access

**Team Workspaces**

You can create additional workspaces designed for team collaboration. Team workspaces allow you to:

- Share projects with multiple team members
- Control who can access what through member roles
- Collaborate on the same repositories
- Manage team access centrally

### Creating and Managing Workspaces

**Creating a New Workspace**

To create a new workspace:

1. Navigate to the Workspace Management page from your dashboard
2. Click the "New Workspace" button in the top right
3. Enter a name for your workspace
4. Click "Create"

Your new workspace is immediately available and ready to use.

**Renaming a Workspace**

To change a workspace's name:

1. Go to Workspace Management
2. Find the workspace in your list
3. Click the edit icon next to the workspace name
4. Enter the new name
5. Click "Save"

**Switching Between Workspaces**

You can easily switch between your workspaces:

1. Locate the workspace in your workspace list
2. Click the "Switch" button next to it

The workspace you select becomes your active workspace, and you'll see all projects and settings associated with it. OrchestrAI remembers your last selected workspace, so when you return, you'll be right where you left off.

**Deleting a Workspace**

To remove a workspace you no longer need:

1. Go to Workspace Management
2. Find the workspace you want to delete
3. Click the delete icon (trash can)
4. Confirm the deletion

**Important:** You must always have at least one workspace. OrchestrAI won't let you delete your last workspace.

## Products

### What is a Product?

A product is a container within a workspace that groups related repositories together. Products help you organize multiple repositories that belong to the same project, application, or initiative. For example, you might have a product called "E-commerce Platform" that contains repositories for your frontend, backend, mobile app, and documentation.

Products sit between workspaces and repositories in the organizational hierarchy:
- **Workspace** → **Product** → **Repository**

### Creating Products

To create a new product in your workspace:

1. Make sure you're in the correct workspace
2. Navigate to the product management area
3. Click to create a new product
4. Provide a name and description for your product
5. Save the product

Once created, you can add repositories to this product to keep related code organized together.

### Managing Products

**Product Information**

For each product, you can view and manage:
- Product name and description
- Associated repositories
- Team members with access
- Product-specific settings

**Adding Repositories to Products**

When connecting a repository to OrchestrAI, you'll assign it to a product. This helps you:
- Keep related repositories grouped
- Apply settings across multiple repositories
- View aggregated insights for all repositories in a product
- Manage access at the product level

**Organizing Multiple Products**

Within a single workspace, you can create multiple products to separate different areas of work:
- Different applications or services
- Separate client projects
- Frontend and backend systems
- Distinct product lines

### Product Permissions

Products inherit the base permissions from your workspace membership, but can have additional controls:

**Workspace-Level Access**
- Your role in the workspace (Owner, Admin, Member) determines your base level of access to products

**Product-Level Visibility**
- Some products may be visible to all workspace members
- Other products may have restricted access to specific team members

**Managing Product Access**

Workspace owners and admins can control who sees and accesses specific products, allowing for granular control over sensitive or specialized projects.

## Team Collaboration

### Workspace Member Roles

OrchestrAI uses three member roles to control access at the workspace level:

**Owner**
- Full control over the workspace
- Can invite and remove members
- Can change workspace settings
- Can manage all products and repositories
- Can delete the workspace
- Created automatically when you create a workspace

**Admin**
- Can manage products and repositories
- Can invite members
- Can update workspace settings
- Cannot delete the workspace

**Member**
- Can access and work on assigned products
- Can view workspace information
- Limited administrative capabilities

### Inviting Team Members

To add someone to your workspace:

1. Go to Workspace Management
2. Find the workspace you want to share
3. Click the "Invite" icon (person with plus sign)
4. Enter their email address
5. Click "Send Invitation"

The person will receive an invitation email. Once they accept, they'll appear in your workspace members list.

### Viewing Your Team

To see who has access to a workspace:

1. Go to Workspace Management
2. Find the workspace in your list
3. View the "Members" column to see the member count
4. Click on the workspace to see detailed member information

For each member, you can see:
- Their email address or identifier
- When they joined the workspace
- Their role (Owner, Admin, or Member)

### Managing Pending Invitations

Invitations that haven't been accepted yet appear in the "Pending Invitations" section. Here you can:
- See who has been invited
- View when the invitation was sent
- Track invitation status

### Leaving a Workspace

If you're a member of a workspace you no longer need access to:

1. Navigate to Workspace Management
2. Find the workspace
3. Select the option to leave the workspace

When you leave, you'll lose access to all products and repositories in that workspace. You cannot leave a workspace if you're the owner and there are other members—you'll need to transfer ownership or remove other members first.

## Repository Organization

### How Repositories Fit In

Repositories are the actual code projects you connect to OrchestrAI. They live within products, which live within workspaces:

**Workspace** → **Product** → **Repository**

This hierarchy means:
- Every repository must belong to a product
- Every product must belong to a workspace
- Access to repositories is controlled by workspace membership and product permissions

### Connecting Repositories

When you connect a GitHub repository to OrchestrAI:

1. You'll select which workspace it belongs to
2. You'll assign it to a product within that workspace
3. The repository inherits access permissions from the workspace and product

### Viewing Connected Repositories

You can see your connected repositories:
- Within the product view, to see all repositories in a specific product
- In the workspace overview, to see the total count of connected repositories
- Through the repository management interface

## Billing and Workspace Management

### Billing at the Workspace Level

Billing in OrchestrAI happens at the workspace level. This means:

- Each workspace has its own credit balance and usage tracking
- Credit consumption from analysis runs is deducted from the workspace's balance
- Workspace owners and admins can view usage and manage billing

### Credit Usage

When you run analyses on repositories within a workspace:
- Credits are consumed from that workspace's balance
- All team members using the workspace share the same credit pool
- Usage is tracked across all products and repositories in the workspace

### Managing Costs Across Projects

To manage costs effectively:
- Monitor usage regularly through the workspace dashboard
- Set up separate workspaces for projects with different billing needs
- Use products to organize and track which repositories consume the most resources

## Organizing Multiple Projects Effectively

### When to Create Multiple Workspaces

Consider creating separate workspaces when you need to:

- Separate personal and professional work
- Isolate different client projects with separate billing
- Create distinct team environments with different members
- Maintain separate credit balances for different departments
- Enforce strict access boundaries between projects

### When to Create Multiple Products

Use multiple products within a single workspace when you want to:

- Group related repositories together
- Organize different applications or services
- Separate frontend and backend projects
- Keep development and production environments distinct
- Maintain organization without separating teams or billing

### Best Practices for Organization

**For Individual Users:**
- Keep your default workspace for personal projects
- Create additional workspaces for different areas of work (freelance, side projects, etc.)
- Use products to separate different applications or initiatives
- Use clear, descriptive names like "Personal Projects" or "Client Work"

**For Small Teams:**
- Start with one workspace for the team
- Create products for each major project or application
- Invite all team members to the workspace
- Use product-level permissions if some projects need restricted access

**For Growing Organizations:**
- Create workspaces by department or major business unit
- Use products to organize projects within each department
- Assign workspace ownership to team leads
- Document workspace and product purposes for team clarity
- Establish naming conventions early and enforce them

**For Enterprises:**
- Structure workspaces by cost center or billing entity
- Use products to represent applications, services, or initiatives
- Implement clear policies for workspace and product creation
- Regularly audit workspace membership and access
- Consider creating separate workspaces for development, staging, and production

### Naming Conventions

Good naming helps everyone understand the organization at a glance:

**Workspaces:**
- "Engineering Team"
- "Marketing Department"
- "Client ABC - Project X"
- "Personal Development"

**Products:**
- "Mobile App"
- "E-commerce Platform"
- "Internal Tools"
- "Documentation Site"

**Keep It Consistent:**
- Decide on a naming pattern early
- Use similar structures across workspaces
- Make names descriptive but concise
- Avoid technical jargon unless everyone understands it

## Common Scenarios

### Starting Fresh

When you create a new account:
1. OrchestrAI sets up your first workspace automatically
2. Create your first product to organize your repositories
3. Connect your repositories to the product
4. Start running analyses

### Growing Your Team

As your team expands:
1. Invite new members to your workspace
2. Assign appropriate roles based on responsibilities
3. Organize repositories into products based on team focus areas
4. Consider creating additional workspaces if teams need separate billing or strict access separation

### Managing Multiple Clients

For agencies or consultants managing multiple client projects:
1. Create a separate workspace for each client
2. Within each workspace, create products for different projects or services
3. Invite client team members only to their specific workspace
4. This ensures complete separation of billing, access, and data

### Reorganizing Your Work

If you need to restructure your organization:
1. Plan your new workspace and product structure
2. Create new workspaces and products as needed
3. Invite team members to the appropriate workspaces
4. Reconnect repositories to the new structure if needed
5. Archive or delete old workspaces you no longer need

### Scaling Up

When moving from individual use to team collaboration:
1. Start by organizing your existing repositories into logical products
2. Create a team workspace for shared work
3. Invite team members and assign roles
4. Move collaborative projects to the team workspace
5. Keep your personal workspace for individual experiments

## Workspace Settings and Information

### What You Can View

For each workspace, you can see:

- **Workspace Name**: The identifier you chose
- **Creation Date**: When the workspace was created
- **Member Count**: How many people have access
- **Git Connections**: Number of repositories connected
- **Default Status**: Whether this is your default workspace
- **Active Status**: The workspace you're currently using

### Active Workspace Indicator

The workspace you're currently using is marked as "Current" in your workspace list. This helps you stay oriented when managing multiple workspaces.

## Workspace Limitations and Requirements

- You must maintain at least one workspace at all times
- You must be signed in to create or manage workspaces
- Each workspace requires a unique name within your account
- Workspace owners cannot leave until ownership is transferred or the workspace is deleted
- All repositories must belong to a product within a workspace

## Tips for Success

**Keep It Simple**: Don't create too many workspaces or products. More isn't always better—it can make navigation confusing. Start simple and add structure as needed.

**Name Clearly**: Use descriptive names that make it obvious what each workspace and product contains. Avoid abbreviations or internal jargon.

**Review Regularly**: Periodically check your workspace members and remove access for people who no longer need it. Archive products that are no longer active.

**Plan Your Structure**: Before inviting a large team, think through your workspace and product organization. It's easier to set up correctly from the start than to reorganize later.

**Start Small**: Begin with one workspace and a few products. Add more only as your needs grow.

**Communicate**: Let your team know which workspace and product to use for which projects. Document your organizational structure.

**Use Products Wisely**: Products are powerful organizational tools. Use them to group repositories that truly belong together, not just to create more structure.

**Separate Billing Needs**: If different parts of your organization need separate billing, use separate workspaces. If they can share a credit pool, keep them in the same workspace.

## Getting Help

If you encounter issues with workspaces, products, or organization:
- Check that you're signed in to your account
- Verify you have the correct role permissions for what you're trying to do
- Ensure you're viewing the correct workspace
- Confirm the product you're looking for is in your current workspace
- Try refreshing the page if information seems outdated
- Contact support if you need help reorganizing your structure

Understanding workspaces, products, and how to organize them effectively will help you and your team stay productive and maintain clear boundaries between different areas of work. This organizational structure scales from individual developers to large enterprises, providing flexibility as your needs grow.