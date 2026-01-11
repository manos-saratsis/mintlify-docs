# Understanding User Roles and Permissions

This application includes a comprehensive user management system with role-based access control to ensure secure and organized operations. Understanding how user roles and permissions work will help you know what you can do and who can help you with different tasks.

## User Types and Roles

The application supports two types of user accounts:

### Regular Users

Regular users have access to their own personal workspace where they can:

- View and manage their own content and items
- Update their profile information (name and email address)
- Change their password
- Delete their own account (with some restrictions)
- Access standard features available to all authenticated users

Regular users can only see and modify their own data. They cannot view other users' information or manage system-wide settings.

### Administrators (Superusers)

Administrators have elevated privileges that allow them to manage the entire system. They can:

- View a complete list of all users in the system
- Create new user accounts for others
- Update any user's information, including email, name, and role
- Change users' active status (enable or disable accounts)
- Promote regular users to administrator status
- Delete other users' accounts from the system
- Access all standard features available to regular users

Administrators are marked with a "Superuser" designation in the system, making it easy to identify who has elevated privileges.

## Permission Levels and Access Control

The application uses a clear permission structure to determine what each user can do:

### Account Status

Every user account has an active status that controls whether they can use the system:

- **Active Users**: Can sign in and use all features available to their role
- **Inactive Users**: Cannot sign in until an administrator reactivates their account

Administrators can change a user's active status to temporarily restrict access without deleting the account.

### Self-Service Permissions

All authenticated users can manage their own account settings:

- **View Your Profile**: See your current email address, name, and account status
- **Update Your Information**: Change your display name or email address
- **Change Your Password**: Update your password by providing your current password for verification
- **Delete Your Account**: Remove your account from the system (administrators cannot delete their own accounts for safety reasons)

### Administrative Permissions

Only administrators can perform system-wide management tasks:

- **User Directory**: View the complete list of all users with their roles and status
- **Create Accounts**: Add new users to the system
- **Modify Users**: Update other users' information, roles, and active status
- **Remove Users**: Delete other users from the system (except their own account)

When administrators try to view another user's profile or modify their account, the system checks their administrator status before allowing the action.

## How Access Control Works

### Signing In

When you sign in to the application:

1. You provide your email address and password
2. The system verifies your credentials securely
3. You receive an access token that identifies you and your permissions
4. This token is used for all subsequent requests to verify your identity

### Permission Checking

Every time you try to access a feature or view information:

1. The system checks who you are based on your access token
2. It verifies whether you have the necessary permissions for that action
3. Regular actions (viewing your own data) proceed automatically
4. Administrative actions require verification that you have administrator privileges
5. If you lack the required permissions, you'll see an error message

### Protected Actions

Some actions have special protection rules:

- **Viewing Users**: Only administrators can see the list of all users in the system
- **Creating Users**: Only administrators can create new user accounts
- **Modifying Users**: You can update your own information, but only administrators can modify other users
- **Deleting Accounts**: You can delete your own account, but administrators cannot delete their own accounts to prevent accidentally losing administrative access

## Admin Capabilities for User Management

Administrators have access to a dedicated User Management interface where they can:

### View All Users

The User Management page displays a comprehensive table showing:

- Each user's full name (or "N/A" if not provided)
- Email address
- Role (Superuser or User)
- Account status (Active or Inactive)
- Available actions for each user

The list is paginated for easy browsing when there are many users, with clear navigation between pages.

### Create New Users

Administrators can add users to the system by:

1. Clicking the option to add a new user
2. Providing the required information (email, password, name)
3. Setting whether the account should have administrator privileges

When a new user is created, they can immediately sign in with the provided credentials.

### Modify Existing Users

For any user in the system, administrators can:

- Change their email address (if the new email isn't already in use)
- Update their full name
- Change their password
- Toggle their administrator status (promote to administrator or demote to regular user)
- Change their active status to enable or disable the account

### Delete Users

Administrators can remove user accounts from the system. When a user is deleted:

- Their account is permanently removed
- All content they created is also deleted
- The action cannot be undone

For safety, administrators cannot delete their own account while signed in as an administrator.

## User Self-Service Features

Regular users and administrators alike can manage their own accounts through self-service features:

### Personal Settings

Access your personal settings to:

- View your current profile information
- Update your display name
- Change your email address (if the new email isn't already registered)

The system prevents you from using an email address that's already associated with another account.

### Password Management

To change your password:

1. Navigate to the password change section
2. Enter your current password for verification
3. Provide your new password (must be at least 8 characters long)
4. Confirm the change

The system ensures:
- Your current password is correct before making changes
- Your new password is different from your current one
- Your new password meets security requirements (8-40 characters)

### Account Self-Deletion

If you need to remove your account:

1. Access the account deletion option in your settings
2. Confirm your decision
3. Your account and all associated data will be permanently removed

Note: If you're an administrator, you cannot delete your own account while signed in. This safety measure prevents accidental loss of administrative access. Another administrator would need to remove your account if necessary.

## How Authentication and Authorization Work Together

### Authentication: Proving Who You Are

When you sign in, authentication confirms your identity:

- Your email and password are checked against secure records
- Passwords are never stored in plain text; they're encrypted for security
- Upon successful authentication, you receive a secure token
- This token is used to identify you for all future requests during your session

### Authorization: Determining What You Can Do

After authentication confirms your identity, authorization determines your permissions:

- The system checks your role (regular user or administrator)
- It verifies your account status (active or inactive)
- Based on these factors, it grants or denies access to specific features
- Authorization checks happen continuously as you use the application

### The Security Flow

Here's what happens when you try to access a feature:

1. **Identity Check**: The system confirms who you are using your access token
2. **Status Verification**: It checks that your account is active
3. **Permission Evaluation**: It determines if your role allows the requested action
4. **Access Decision**: You either gain access or receive a permission denied message

This two-layer approach (authentication + authorization) ensures that only the right people can access sensitive features.

## Security Considerations and Best Practices

### Password Security

The application implements several security measures for passwords:

- **Minimum Length**: Passwords must be at least 8 characters long to ensure adequate complexity
- **Secure Storage**: Passwords are never stored as plain text; they're encrypted using industry-standard methods
- **Verification Required**: You must provide your current password to change it, preventing unauthorized changes

**Best Practices for Passwords:**
- Choose passwords that are unique and not used on other services
- Use a mix of letters, numbers, and special characters
- Change your password if you suspect it may have been compromised
- Never share your password with others

### Account Management

**For Regular Users:**
- Keep your email address current so you can recover your account if needed
- Review your profile information periodically to ensure it's accurate
- Consider carefully before deleting your account, as the action cannot be undone

**For Administrators:**
- Only grant administrator privileges to trusted individuals
- Regularly review the list of users and their roles
- Disable accounts rather than delete them if you might need to restore access
- Maintain at least two active administrator accounts to prevent lockout situations

### Session Security

- Your access token remains valid for a specific period
- If you're using a shared computer, always sign out when finished
- The system automatically requires re-authentication after extended periods of inactivity

### Permission Boundaries

The system enforces strict boundaries to prevent privilege escalation:

- Regular users cannot access administrative features, even if they know the direct location
- Users cannot modify other users' data, even if they know their account identifiers
- Administrators cannot delete their own accounts to prevent accidental system lockout
- All permission checks happen on the server, not just in the user interface

### Audit and Accountability

The role-based system creates clear accountability:

- All actions are associated with the user who performed them
- Administrators can see who created or modified user accounts
- The distinction between regular users and administrators is always visible

### Getting Help

If you need assistance with permissions or account access:

- **Regular Users**: Contact an administrator if you need access to features you cannot reach
- **Administrators**: If you're locked out, another administrator must restore your access
- **Account Issues**: Administrators can help reset passwords or reactivate accounts

By understanding these roles and permissions, you can work confidently within the application while knowing that appropriate security measures protect everyone's data.