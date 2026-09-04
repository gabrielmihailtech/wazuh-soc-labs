Wazuh Lab 05 - Authentication Monitoring

---
Overview

This lab focused on monitoring and analyzing user authentication events collected by Wazuh from a Windows 11 endpoint. The objective was to identify successful logins, failed login attempts, privileged logins, and user logoff events, providing visibility into user activity and authentication-related security events.

---
Objectives
Monitor Windows authentication events.
Identify successful logins.
Detect failed login attempts.
Analyze privileged login events.
Review user logoff activity.
Understand how Wazuh processes authentication-related logs.

---
Environment

Platform: Wazuh Cloud

Agent Name: Gab

Agent ID: 001

Operating System: Microsoft Windows 11 Pro

Wazuh Version: 4.14.7

----
Authentication Event Analysis
Event 1 - Successful Logon

Rule ID
67022

Rule Description
Non network or service local logon


Severity Level
3

Analysis

Wazuh detected a successful local authentication on the Windows endpoint.

This event confirms that a user successfully logged into the system through a local interactive session.

---
Event 2 - Privileged Logon

Rule ID
67028

Rule Description
Special privileges assigned to new logon


Severity Level
3

Analysis

Wazuh identified a login session where special privileges were assigned to the authenticated account.

These events are important because administrator accounts and privileged users represent high-value targets during security investigations.

---
Event 3 - User Logoff

Rule ID
67023

Rule Description
Non service account logged off

Severity Level
3

Analysis

This event indicates that a user session was successfully terminated.

Logoff events are useful when establishing user activity timelines and correlating authentication activity during investigations.

---
Event 4 - Failed Logon

Rule ID
60122


Rule Description
Logon Failure - Unknown user or bad password


Severity Level
5

Analysis

The event was generated after intentionally entering an incorrect password during a Windows login attempt.

Wazuh successfully detected and recorded the failed authentication attempt.

Failed login events are commonly monitored by SOC analysts because they may indicate:

Password guessing attempts
Brute-force activity
Invalid credentials
Unauthorized access attempts
Account enumeration attempts

---
Authentication Workflow Observed

During testing, the following authentication sequence was observed:


Failed Login Attempt
↓
Successful Logon
↓
Privileges Assigned
↓
User Logoff

Wazuh successfully captured each stage of the authentication process and generated associated security events.

---
Security Impact

Authentication monitoring is one of the most important functions of a SIEM platform.

Monitoring authentication activity allows security teams to:

Detect unauthorized access attempts
Identify brute-force attacks
Monitor privileged account activity
Investigate suspicious user behavior
Build user activity timelines
Support incident response investigations

---
Key Findings
Wazuh successfully collected Windows authentication logs.
Successful local logins were detected and recorded.
Privileged login sessions were identified.
User logoff events were logged.
Failed login attempts generated alerts with increased severity.
Authentication events provided valuable investigation data for security monitoring.

---
Conclusion

This lab demonstrated Wazuh's ability to monitor and analyze authentication activity on a Windows 11 endpoint.
The platform successfully detected successful logins, failed login attempts, privileged logons, and user logoff events.
Authentication monitoring provides essential visibility for detecting unauthorized access attempts and supports security investigations by establishing a clear timeline of user activity.

---
Skills Demonstrated
Wazuh Authentication Monitoring
Windows Authentication Analysis
Security Event Monitoring
Failed Login Detection
Privileged Account Monitoring
User Activity Analysis
Threat Detection
Security Operations Monitoring
