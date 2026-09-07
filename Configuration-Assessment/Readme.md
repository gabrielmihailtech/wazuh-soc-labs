  Configuration Assessment
  
Overview

This lab focused on reviewing the security posture of a Windows 11 endpoint using Wazuh Configuration Assessment.
The assessment was performed against the CIS Microsoft Windows 11 Enterprise Benchmark v3.0.0 to identify security configuration weaknesses and evaluate compliance
with industry-recommended hardening standards.

---
Objectives
Review CIS benchmark results.
Identify passed and failed security controls.
Understand configuration hardening principles.
Analyze risks associated with failed controls.
Evaluate the overall security posture of the monitored endpoint.

---
Environment

Platform: Wazuh Cloud

Agent Name: Gab

Agent ID: 001

Operating System: Microsoft Windows 11 Pro

Policy:

CIS Microsoft Windows 11 Enterprise Benchmark v3.0.0

---
Assessment Results
Overall Score
27%

Results Summary
Passed: 129
Failed: 344
Not Applicable: 9
Total Checks: 482

Interpretation

The endpoint does not fully comply with the CIS Windows 11 benchmark recommendations.

This does not indicate compromise or malware infection. Instead, it shows that multiple hardening recommendations have not been implemented.

---
Passed Controls
Control ID 26000
Ensure 'Enforce password history' is set to '24 or more password(s)'.


Result

Passed


Security Benefit

Prevents users from repeatedly reusing old passwords.

---
Control ID 26001
Ensure 'Maximum password age' is set to '365 or fewer days, but not 0'.


Result

Passed


Security Benefit

Reduces long-term exposure to compromised credentials.

---
Control ID 26010
Ensure 'Accounts: Limit local account use of blank passwords to console logon only'.


Result

Passed


Security Benefit

Restricts the use of blank passwords and reduces unauthorized access risks.

---
Failed Controls
Control ID 26003
Ensure 'Minimum password length' is set to '14 or more character(s)'.


Result

Failed


Risk

Shorter passwords are generally easier to guess or crack using brute-force attacks.

---
Control ID 26004
Ensure 'Relax minimum password length limits' is set to 'Enabled'.


Result

Failed


Risk

Modern password requirements may not be fully supported or enforced.

---
Control ID 26011
Configure 'Accounts: Rename administrator account'.


Result

Failed


Risk

Attackers commonly target the default Administrator account because its name is predictable.

---
Control ID 26012
Configure 'Accounts: Rename guest account'.


Result

Failed


Risk

Predictable account names simplify reconnaissance and account enumeration activities.

---
Control ID 26013
Ensure 'Audit: Force audit policy subcategory settings'.


Result

Failed


Risk

Incomplete audit configuration may reduce log visibility during security investigations.

---
Control ID 26015
Ensure 'Devices: Prevent users from installing printer drivers' is set to 'Enabled'.


Result

Failed


Risk

Improper driver installation controls may increase the attack surface of the system.

---
Security Impact

Configuration Assessment provides visibility into security weaknesses that may not generate alerts during normal monitoring activities.

Poor security configuration can lead to:

Weak authentication controls
Reduced audit visibility
Increased attack surface
Easier privilege escalation
Greater exposure to credential attacks

---
Key Findings
The endpoint achieved a CIS compliance score of 27%.
Password history and password aging policies were properly configured.
Password complexity and hardening settings require improvement.
Default account hardening recommendations were not fully implemented.
Several audit and configuration controls failed CIS recommendations.

---
Conclusion

Wazuh Configuration Assessment successfully evaluated the Windows 11 endpoint against the CIS Microsoft Windows 11 Enterprise Benchmark.
The assessment identified multiple hardening opportunities, particularly in password policy configuration, account management, auditing settings, and device control policies.
While the system passed several important controls, the overall compliance score indicates significant room for improvement in security hardening.

---
Skills Demonstrated
Wazuh Configuration Assessment
CIS Benchmark Analysis
Security Hardening Review
Windows Security Configuration
Security Compliance Assessment
Risk Analysis
Security Monitoring
Endpoint Security Evaluation

