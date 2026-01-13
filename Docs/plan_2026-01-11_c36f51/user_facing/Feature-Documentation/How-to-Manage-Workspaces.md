# How to Manage Workspaces

## Overview

Workspaces help you organize your projects, teams, and resources. Each workspace has its own members, code repositories, and workflow configurations. You can create multiple workspaces to separate different teams or projects.

## Accessing Workspace Management

To manage your workspaces:

1. Navigate to the Dashboard page
2. Click on **Workspace Management** in the sidebar

The Workspace Management page displays an overview of your current workspace, including team members, connected code repositories, and workflow configurations.

## Creating a New Workspace

To create a new workspace:

1. Go to the Dashboard page
2. Open the workspace selector (typically in the navigation area)
3. Click **Create Workspace** or the plus icon
4. Enter a name for your workspace
5. Click **Create**

You will automatically become the owner of the new workspace, and it will be set as your current workspace.

## Switching Between Workspaces

To switch to a different workspace:

1. Click on the workspace selector in the navigation area
2. Select the workspace you want to switch to from the list

Your selected workspace will be remembered for your next visit.

## Managing Team Members

### Viewing Team Members

On the Workspace Management page, you'll see a **Members** section that displays:
- Total number of members
- Each member's name and email
- Their role (Owner, Admin, or Member)
- Their status (Active or Deactivated)

### Inviting New Members

To invite people to your workspace:

1. Go to the Workspace Management page
2. In the Members section, click the **+ Members** button
3. Enter one or more email addresses (separated by commas)
4. Click **Send Invitations**

Invited users will receive an email with instructions to join your workspace. Once they accept, they'll appear in your members list with the "Member" role.

### Managing Member Roles

There are three role types:

- **Owner**: Full control over the workspace, including deleting it and managing all members
- **Admin**: Can manage members and workspace settings, but cannot delete the workspace
- **Member**: Can access workspace resources but cannot manage settings or other members

To change a member's role:

1. Go to the Workspace Management page
2. Find the member in the Members section
3. Click on their current role
4. Select the new role from the dropdown menu

### Managing Member Status

Members can have different statuses:

- **Active**: Full access to the workspace
- **Deactivated**: Temporarily removed from workspace access

To deactivate a member:

1. Go to the Workspace Management page
2. Find the member in the Members section
3. Click the options menu next to their name
4. Select **Deactivate**

Deactivated members can be reactivated by changing their status back to Active.

### Viewing Permissions

To see detailed permission settings:

1. Go to the Workspace Management page
2. Click the **Permissions** button in the Members section

This shows you what each role can do within your workspace.

## Managing Code Repositories

The Code section on the Workspace Management page shows:

- Number of connected Git accounts
- Total repositories available
- Number of enabled repositories

To manage your code repositories:

1. Click on the Code card or click **Go to Code Management**
2. This takes you to the Code Management page where you can:
   - Connect GitHub, GitLab, or other Git providers
   - Enable or disable specific repositories
   - Configure repository settings

## Managing Workflows

The Workflow section displays:

- Enabled workflow modules
- Status of each module (Active, Configured, etc.)

To configure workflows:

1. Click on the Workflow card or click **Go to Workflow Configuration**
2. This takes you to the Workflow page where you can:
   - Enable or disable workflow modules
   - Configure automation settings
   - Set up workflow rules

## Updating Workspace Settings

To update your workspace name or settings:

1. Navigate to the workspace selector
2. Look for workspace settings or edit options
3. Update the workspace name
4. Save your changes

## Leaving a Workspace

To leave a workspace (if you're not the owner):

1. Go to the Workspace Management page
2. Find the options menu
3. Select **Leave Workspace**
4. Confirm your decision

After leaving, you'll be switched to another workspace if you're a member of multiple workspaces.

## Deleting a Workspace

To delete a workspace (owners only):

1. Access the workspace settings
2. Find the delete option
3. Click **Delete Workspace**
4. Confirm the deletion

**Important**: You cannot delete your last remaining workspace. You must have at least one workspace at all times.

## Understanding Workspace Roles and Permissions

### Owner Permissions
- Create and delete the workspace
- Invite and remove members
- Change any member's role
- Access all workspace features
- Manage billing and plans

### Admin Permissions
- Invite and remove members
- Change member roles (except owners)
- Access all workspace features
- Configure workspace settings

### Member Permissions
- Access workspace resources
- View other members
- Participate in workflows
- View code repositories (based on repository permissions)

## Tips for Effective Workspace Management

**Organize by team or project**: Create separate workspaces for different teams or major projects to keep resources organized.

**Assign appropriate roles**: Give Admin roles to team leads who need to manage members, but keep Owner status for yourself or trusted administrators.

**Review members regularly**: Periodically review your members list and deactivate accounts for people who have left your team.

**Use invitations**: Always invite members through the invitation system rather than sharing credentials.

**Monitor workspace activity**: Check the Code and Workflow sections regularly to ensure your workspace is properly configured.

## Troubleshooting

**Cannot see workspace management options**: Ensure you have Admin or Owner role in the workspace. Members cannot manage workspace settings.

**Invitation not received**: Check that the email address is correct and ask the recipient to check their spam folder.

**Cannot delete workspace**: You must have at least one workspace. Create a new workspace before deleting your last one.

**Member changes not visible**: Refresh the page to see the latest updates to the members list.

**Cannot switch workspaces**: If you only see one workspace, you may only be a member of that workspace. Contact your team lead if you need access to others.