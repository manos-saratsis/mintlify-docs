# How to Run Compliance Analysis

## Overview

Compliance Analysis helps you continuously monitor your codebase for regulatory compliance, data privacy requirements, and industry standards. The AI-powered system analyzes your code across six critical compliance dimensions and provides detailed scores, insights, and actionable recommendations.

## What Gets Analyzed

Your code is evaluated across these six compliance dimensions:

- **Data Privacy** - Protection of personal and sensitive data throughout your codebase
- **Data Protection** - Safeguarding data from unauthorized access and security breaches
- **Access Control** - User permissions, authentication mechanisms, and authorization patterns
- **Audit Trails** - Logging and monitoring of security-relevant events and user actions
- **Encryption** - Data protection through cryptographic methods and secure transmission
- **Compliance Standards** - Adherence to regulatory standards and industry best practices

Each dimension receives a detailed score showing how well your code meets compliance requirements. The analysis maps to major regulatory frameworks including SOC2, ISO 27001, HIPAA, and GDPR.

## Prerequisites

Before running compliance analysis, you need:

1. **Active Workspace** - Select a workspace from the top navigation bar
2. **Connected Repository** - At least one GitHub, GitLab, or Bitbucket repository connected to your workspace
3. **Enabled Repository** - The repository must be enabled for Orchestrai analysis

## Getting Started

### Step 1: Connect Your Repository

If you haven't connected a repository yet:

1. Navigate to the Compliance page
2. Click the **Add Git Connection** button
3. Follow the prompts to connect your GitHub, GitLab, or Bitbucket account
4. Select which repositories to analyze

### Step 2: Enable Orchestrai Analysis

Once connected:

1. Go to your Code Management page
2. Find the repository you want to analyze
3. Enable Orchestrai for that repository
4. The system will begin monitoring the repository for compliance

### Step 3: Access Compliance Analysis

1. Navigate to the **Compliance** page from the main menu
2. You'll see a list of all Orchestrai-enabled repositories
3. Each repository displays its current compliance status

## Running an Analysis

### Automatic Analysis

Compliance analysis runs automatically:

- **On Repository Connection** - Initial analysis begins when you first enable a repository
- **On Code Changes** - Analysis runs whenever new code is pushed to your repository
- **Continuous Monitoring** - The system tracks compliance scores over time as your code evolves

### Manual Refresh

To manually refresh your compliance data:

1. Click the **Refresh** button at the top of the Compliance page
2. The system will reload the latest compliance scores for all enabled repositories
3. Wait for the analysis to complete

## Understanding Your Results

### Viewing Analysis Results

To see detailed compliance results:

1. On the Compliance page, locate your repository in the list
2. Click the **Analysis Results** button in the top navigation
3. Review the detailed breakdown of compliance scores

### Repository Compliance Table

The main compliance view shows:

- **Repository Name** - The name of each analyzed repository
- **Compliance Status** - Overall compliance health indicator
- **Dimension Scores** - Individual scores for each of the six compliance dimensions
- **Last Updated** - When the analysis was last performed

### Compliance Scores

Each dimension receives a score indicating:

- **High Score** - Good compliance practices detected
- **Medium Score** - Some issues identified that need attention
- **Low Score** - Significant compliance gaps requiring immediate action

### File-Level Insights

The detailed results include:

- **Precise File Locations** - Exact files where compliance issues exist
- **Issue Descriptions** - Clear explanations of what needs to be fixed
- **Remediation Steps** - Specific guidance on how to resolve each issue
- **Code Examples** - Sample code showing best practices
- **Priority Rankings** - Which issues to address first

## Regulatory Framework Mapping

Your dimension scores automatically map to these compliance standards:

- **SOC2** - System and Organization Controls 2
- **ISO 27001** - Information Security Management
- **HIPAA** - Health Insurance Portability and Accountability Act
- **GDPR** - General Data Protection Regulation

The system shows how your code performs against each framework's specific requirements.

## Common Use Cases

### Ensuring Regulatory Compliance

Monitor adherence to industry regulations including:
- GDPR requirements for data protection
- HIPAA compliance for healthcare data
- SOC 2 controls for service organizations
- PCI DSS standards for payment processing

### Verifying Data Privacy

Check proper handling of sensitive data:
- Detection of personally identifiable information (PII)
- Verification of data encryption practices
- Review of access controls and permissions
- Validation of audit trail implementations

### Enforcing Organizational Policies

Automatically verify code against internal policies:
- Coding standards compliance
- Software licensing requirements
- Documentation completeness
- Security best practices

## Continuous Monitoring

### Tracking Over Time

The system provides:

- **Historical Trend Analysis** - See how compliance scores change as your code evolves
- **Team-Wide Visibility** - Share compliance status across your organization
- **Progress Tracking** - Monitor improvements after implementing recommendations

### Development Pipeline Integration

Compliance checks can integrate into your workflow:

- **Pre-Deployment Checks** - Catch compliance issues before code goes live
- **Automated Notifications** - Receive alerts when compliance scores change
- **Pull Request Integration** - Review compliance impact of proposed changes

## Troubleshooting

### No Repositories Showing

If you don't see any repositories:

1. Verify you've selected a workspace from the top navigation
2. Check that your GitHub/GitLab/Bitbucket account is connected
3. Ensure at least one repository is enabled for Orchestrai
4. Click the Refresh button to reload repository data

### Analysis Not Running

If compliance analysis isn't updating:

1. Confirm the repository is enabled for Orchestrai
2. Check that recent code changes have been pushed
3. Use the manual refresh option to trigger an update
4. Contact support if issues persist

### Understanding Low Scores

If you receive low compliance scores:

1. Review the detailed file-level insights
2. Prioritize issues based on the provided rankings
3. Follow the specific remediation steps for each issue
4. Implement the suggested code examples and best practices
5. Monitor score improvements after making changes

## Best Practices

- **Regular Reviews** - Check compliance scores weekly to stay ahead of issues
- **Prioritize by Risk** - Address high-priority compliance gaps first
- **Team Communication** - Share compliance results with your development team
- **Incremental Improvements** - Fix issues progressively rather than all at once
- **Document Changes** - Track which remediation steps you've implemented
- **Continuous Learning** - Use compliance insights to improve coding practices over time

## Getting Help

If you need assistance with compliance analysis:

- Review the detailed remediation steps provided in your results
- Check that all prerequisites are met (workspace, connected repository, enabled analysis)
- Use the manual refresh option if data appears outdated
- Ensure you have proper permissions to view compliance data in your workspace