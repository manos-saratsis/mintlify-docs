# How to Manage Compliance

OrchestrAI helps you continuously monitor and improve your codebase's compliance posture across six critical security dimensions. This guide explains how to assess compliance, interpret results, and implement improvements.

## Overview

The compliance feature analyzes your code across six interconnected dimensions that together determine your overall security and regulatory compliance:

- **Data Privacy** - Protection of personal and sensitive data throughout your codebase
- **Data Protection** - Safeguarding data from unauthorized access and security breaches
- **Access Control** - User permissions, authentication mechanisms, and authorization patterns
- **Audit Trails** - Logging and monitoring of security-relevant events and user actions
- **Encryption** - Data protection through cryptographic methods and secure transmission
- **Compliance** - Adherence to regulatory standards and industry best practices

Each dimension receives an individual score, and your results map to multiple regulatory frameworks including SOC2, ISO 27001, HIPAA, and GDPR.

## Getting Started with Compliance Analysis

### Step 1: Connect Your Repository

Before running compliance checks, you need to connect your code repository:

1. Navigate to the Compliance page
2. If you see "No Enabled Repositories," select **Manage Repositories**
3. Connect your GitHub, GitLab, or Bitbucket account
4. Enable OrchestrAI analysis on the repositories you want to scan

### Step 2: Run Your First Compliance Check

Once you have repositories connected:

1. Go to the Compliance page
2. You'll see a table titled "Recent Compliance Analyses" showing all your enabled repositories
3. Select a repository and initiate an analysis
4. The system will scan your entire codebase across all six compliance dimensions

The analysis runs in the background, so you can continue working while it processes. You'll be notified when results are ready.

### Step 3: View Compliance Results

After your analysis completes:

1. Select **View Results** from the Compliance page
2. You'll see scores for each of the six dimensions
3. Review file-level findings showing exactly where compliance issues exist
4. Access detailed remediation recommendations for each finding

## Understanding Compliance Dimensions

### Data Privacy

This dimension evaluates how your code handles personal and sensitive information. The analysis checks three key areas:

**Data Collection and Minimization**
- Input fields: Verifies only necessary personal data is collected (data minimization principle)
- Tracking scripts: Identifies cookies and scripts collecting personally identifiable information or behavioral data
- Third-party integrations: Detects SDKs and APIs that may collect or process user data without proper consent

**Consent Management**
- Cookie banners and consent modals: Ensures users receive clear, granular choices for non-essential cookies
- Consent storage: Verifies consent is stored with timestamps and version information
- Consent enforcement: Confirms data collection only occurs after valid consent is obtained

**Data Subject Rights**
- Access and deletion endpoints: Checks if users can easily request and receive their data, and if the code supports erasure or rectification requests
- Data portability: Verifies ability to export personal data in portable formats like JSON or CSV

### Data Protection

This dimension focuses on safeguarding data from unauthorized access:

**Data Transfers**
- Reviews APIs and webhooks to ensure personally identifiable information transfers occur only to compliant recipients
- Verifies appropriate safeguards for international data transfers

**Access Control Implementation**
- Checks for role-based access controls throughout the codebase
- Ensures proper authorization checks protect sensitive data

### Access Control

This dimension examines authentication and authorization mechanisms:

**Authentication**
- Password policies: Verifies strong password requirements and multi-factor authentication where applicable
- Protection mechanisms: Ensures secure token generation, storage, and invalidation; checks for rate-limiting and brute-force protection on login endpoints

**Session Management**
- Secure cookies: Confirms use of secure, HTTP-only, same-site cookies for session tokens
- Session expiration: Verifies automatic timeout for inactive sessions and maximum session lifetime limits
- JWT tokens: Validates proper signing, expiration checking, and validation of JSON Web Tokens

### Audit Trails

This dimension evaluates logging and monitoring capabilities:

**Sensitive Data in Logs**
- Scans logs to ensure no sensitive information (passwords, tokens, personal data) is inadvertently recorded

**Traceability**
- Sufficient logging: Confirms logs contain adequate details (user ID, IP address, session ID, actions performed) for forensic investigations
- Data retention and rotation: Verifies log retention policies meet regulatory requirements like GDPR and HIPAA

### Encryption

This dimension assesses cryptographic protection of data:

**Data Protection in Transit and at Rest**
- HTTPS: Verifies all communications use the latest TLS versions
- Data storage: Confirms personal data encryption at rest (database encryption)

**Encryption Security**
- Cipher strength: Identifies deprecated or weak ciphers (DES, RC4, MD5, SHA1)

**Secrets Management**
- Credentials: Ensures API keys, tokens, and credentials are not hardcoded or exposed in repositories; verifies integration with secrets managers

### Compliance Standards

This dimension maps your code against specific regulatory frameworks:

**GDPR (General Data Protection Regulation)**
- European data protection requirements
- Data subject rights implementation
- Cross-border data transfer compliance

**CCPA (California Consumer Privacy Act)**
- California privacy law requirements
- Consumer rights to access and delete data
- Opt-out mechanisms for data sales

**ePR (ePrivacy Directive)**
- Cookie consent requirements
- Electronic communications privacy
- Marketing communication rules

## Interpreting Compliance Scores

### Score Ranges

Each dimension receives a score that indicates compliance strength:

- **Critical Issues**: Severe compliance gaps requiring immediate attention
- **Warnings**: Areas needing improvement but not immediately critical
- **Passing**: Meets compliance requirements for that dimension

### Overall Compliance Posture

Your overall compliance posture reflects performance across all six dimensions. Strong performance in some areas cannot fully compensate for critical weaknesses in others, as regulatory compliance requires meeting standards across all dimensions.

### Mapping to Regulatory Standards

Your dimension scores map to specific requirements in major compliance frameworks:

**SOC2 (Service Organization Control 2)**
- Maps to security, availability, processing integrity, confidentiality, and privacy principles
- Uses data protection, access control, audit trails, and encryption dimensions

**ISO 27001**
- Maps to information security management system requirements
- Incorporates all six dimensions with emphasis on access control and encryption

**HIPAA (Health Insurance Portability and Accountability Act)**
- Maps to Protected Health Information (PHI) safeguards
- Focuses heavily on data privacy, encryption, and audit trails dimensions

**GDPR (General Data Protection Regulation)**
- Maps to data protection and privacy requirements
- Emphasizes data privacy, data protection, and consent management

## Configuring Compliance Analysis

### Setting Analysis Scope

You can customize which compliance checks run:

1. Navigate to the Compliance page
2. Select a repository to analyze
3. Before running the analysis, expand the configuration options
4. Choose which dimensions and subcategories to include

### Severity Levels

Configure which severity levels require remediation:

- **None**: Run analysis for visibility only, no remediation recommendations
- **Critical only**: Focus on severe compliance gaps
- **Critical and Warnings**: Address both critical issues and improvement opportunities

### Custom Instructions

Add organization-specific requirements:

1. In the configuration section, locate "Additional Instructions"
2. Enter any custom compliance requirements specific to your organization
3. These instructions guide the analysis to check for your unique policies

## Working with Compliance Reports

### File-Level Findings

Compliance results show exactly where issues exist:

1. Select **View Results** after an analysis completes
2. Navigate through findings organized by dimension
3. Click on any finding to see the specific file and line numbers
4. Review the explanation of why this represents a compliance issue

### Remediation Recommendations

For each finding, you receive:

- **Issue Description**: Clear explanation of the compliance gap
- **Affected Code**: Specific file paths and line numbers
- **Recommended Fix**: Code examples showing how to resolve the issue
- **Priority Level**: Guidance on urgency (critical vs. warning)
- **Regulatory Context**: Which standards this finding impacts

### Implementing Fixes

Follow this workflow to address compliance findings:

1. Review all critical findings first
2. For each finding, examine the affected code in your repository
3. Implement the recommended fix or an equivalent solution
4. Run another compliance analysis to verify the issue is resolved
5. Track progress through the compliance dashboard

## Continuous Compliance Monitoring

### Tracking Improvements Over Time

The Recent Compliance Analyses table shows your compliance history:

- View all previous analyses for each repository
- Compare scores across different time periods
- Monitor whether your compliance posture is improving

### Integrating into Development Workflow

For continuous compliance monitoring:

1. Run compliance checks regularly (weekly or after major changes)
2. Review findings as part of code review processes
3. Address compliance issues before merging code
4. Use compliance scores as release criteria

### Team Visibility

Ensure your entire team can access compliance information:

- All team members can view compliance results for repositories they have access to
- Share findings with developers who need to implement fixes
- Use compliance reports in security reviews and audits

## Common Compliance Scenarios

### Preparing for SOC2 Audit

1. Run a full compliance analysis across all repositories
2. Focus on data protection, access control, and audit trails dimensions
3. Document all findings and remediation actions
4. Maintain regular scanning to demonstrate continuous monitoring

### GDPR Compliance Check

1. Emphasize data privacy, data protection, and compliance dimensions
2. Pay special attention to consent management findings
3. Verify data subject rights implementation
4. Review cross-border data transfer mechanisms

### HIPAA Compliance for Healthcare Applications

1. Prioritize encryption and audit trails dimensions
2. Ensure all Protected Health Information (PHI) handling is secure
3. Verify access control mechanisms meet HIPAA standards
4. Maintain detailed audit logs as required

### General Security Hardening

1. Run analysis with all dimensions enabled
2. Start with critical findings across all dimensions
3. Address encryption and access control issues first
4. Progressively work through warnings to strengthen overall posture

## Best Practices

**Run Regular Scans**
Schedule compliance analyses at consistent intervals to catch issues early before they reach production.

**Address Critical Findings Immediately**
Critical compliance gaps represent serious risks. Prioritize these over feature development when necessary.

**Document Your Decisions**
When you choose not to implement a recommendation, document why. This helps during audits and prevents repeated flagging.

**Involve Security Team Early**
Share compliance results with your security and legal teams to ensure alignment with organizational policies.

**Test After Remediation**
Always run a follow-up analysis after implementing fixes to confirm issues are fully resolved.

**Maintain Configuration Consistency**
Use the same configuration settings across analyses to ensure comparable results over time.

## Getting Help

If you encounter findings you don't understand or need clarification on remediation approaches:

1. Review the detailed explanation provided with each finding
2. Consult the regulatory context to understand which standards are affected
3. Contact your organization's security or compliance team for guidance
4. For platform-specific questions, reach out to OrchestrAI support

Compliance is an ongoing process, not a one-time check. Regular monitoring and continuous improvement across all six dimensions will strengthen your security posture and help meet regulatory requirements.
