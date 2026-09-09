 --- Incident Investigation

Overview

This investigation focused on analyzing a sequence of security events collected by Wazuh from a Windows 11 endpoint. The objective was to reconstruct an authentication timeline, identify associated privilege assignment activity, review system modifications, and correlate events with MITRE ATT&CK techniques.

The investigation combined data from multiple Wazuh modules, including:

Threat Hunting
Authentication Monitoring
File Integrity Monitoring (FIM)
MITRE ATT&CK Framework

---
Objectives
Investigate a failed authentication attempt.
Identify a successful authentication event.
Review privilege assignment activity.
Analyze Registry modification events.
Correlate findings using MITRE ATT&CK mappings.
Build a timeline of security-relevant activity.

---
Environment

Platform: Wazuh Cloud

Agent Name: Gab

Agent ID: 001

Operating System: Microsoft Windows 11 Pro

Hostname: DP-PM4

---
Incident Summary

A controlled authentication test was performed on the monitored endpoint.

The investigation identified:

Failed Login Attempt
Successful Login
Privilege Assignment
Registry Modification Activity

No evidence of malicious activity was identified. All observed events were associated with authorized testing performed on the endpoint.

---
Investigation Timeline
Time	Event14:39:50	Failed Logon
14:39:58	Privileged Logon
Following authentication	Normal user session activity
Registry monitoring	Registry Key Deletion detected

---
Finding 1 - Failed Authentication Attempt
Event Information

Event ID

4625


Rule ID

60122


Rule Level

5


Description

Logon Failure - Unknown user or bad password


Target User

gmihail


Workstation

DP-PM4


Source IP

127.0.0.1


Timestamp

Sep 9, 2026 @ 14:39:50


Status

AUDIT_FAILURE

Analysis

Wazuh detected a failed authentication attempt for user:

gmihail


The source address:

127.0.0.1


indicates that the login attempt originated locally from the endpoint itself.

The failed authentication was generated during a controlled test by intentionally entering an incorrect password.

Assessment
Benign Activity


No indicators of brute-force activity or unauthorized access were identified.

<img width="962" height="894" alt="image" src="https://github.com/user-attachments/assets/78c8174f-4260-4f40-b98c-9fce05678de3" />
<img width="954" height="901" alt="image" src="https://github.com/user-attachments/assets/62a065a5-d971-4c05-90a7-7b817fc24941" />
<img width="950" height="894" alt="image" src="https://github.com/user-attachments/assets/5a882ca5-84ce-4c24-b10d-3875dda09493" />

---
Finding 2 - Successful Authentication
Event Information

Event ID

4624


Rule ID

67022


Rule Level

3


Description

Non network or service local logon


Target User

gmihail


Workstation

DP-PM4


Logon Type

7


Timestamp

Sep 9, 2026 @ 13:51:32


Status

AUDIT_SUCCESS

Analysis

A successful local authentication event was detected for the same user account:

gmihail


The event confirms valid authentication to the Windows endpoint.

This event represents the successful authentication phase following login activity observed during testing.

Assessment
Authorized and Expected Activity


No suspicious indicators were identified.

---
Finding 3 - Privileged Logon
Event Information

Event ID

4672


Rule ID

67028


Rule Level

3


Description

Special privileges assigned to new logon


User

gmihail


Timestamp

Sep 9, 2026 @ 14:39:58


Status

AUDIT_SUCCESS

Assigned Privileges

Examples observed:

SeSecurityPrivilege
SeTakeOwnershipPrivilege
SeLoadDriverPrivilege
SeBackupPrivilege
SeRestorePrivilege
SeDebugPrivilege

Analysis

Wazuh detected the assignment of elevated privileges after successful authentication.

Event ID 4672 is commonly generated when an account receives administrative privileges.

Such events are frequently reviewed during investigations because privileged accounts provide elevated access to system resources.

Assessment
Expected Administrative Activity


The privileges were assigned to the authenticated local user during testing.

---
Finding 4 - Registry Modification Activity
Event Information

Rule ID

597


Rule Level

5


Description

Registry Key Entry Deleted


Event Type

deleted


Timestamp

Sep 9, 2026 @ 06:46:37

Registry Path
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\xmlprov\Parameters\SchemaGroups\User\...

Analysis

Wazuh File Integrity Monitoring detected the deletion of a Registry Key.

Registry modifications are important because attackers frequently modify Registry locations to:

Establish persistence
Modify system behavior
Evade detection
Maintain access

No malicious behavior was identified during this investigation.

---
MITRE ATT&CK Analysis

The investigation generated several ATT&CK mappings.

T1112 - Modify Registry
Modify Registry


Associated with Registry modifications observed by File Integrity Monitoring.

T1070.004
File Deletion


Associated with deletion-related activity detected by Wazuh.

T1485
Data Destruction


Mapped to integrity monitoring events involving object removal.

T1484
Domain Policy Modification


Observed during privilege-assignment-related activity.

---
Overall Assessment

The investigation identified a complete authentication sequence:

Failed Login
        ↓
Successful Login
        ↓
Privileges Assigned
        ↓
System Activity


All activity originated from the monitored endpoint and was generated during controlled security testing.

No evidence of:

Unauthorized access
Persistence mechanisms
Malware activity
Lateral movement
Privilege abuse

was identified.

---
Conclusion

Wazuh successfully captured authentication events, privilege assignment activity, Registry modifications, and MITRE ATT&CK mappings, allowing a complete investigation timeline to be reconstructed. The collected evidence demonstrated how multiple Wazuh modules can be used together to analyze endpoint activity and support security operations investigations.

---
Skills Demonstrated
Wazuh Threat Hunting
Authentication Monitoring
Security Event Analysis
Event Correlation
File Integrity Monitoring
Windows Security Log Analysis
MITRE ATT&CK Analysis
Incident Investigation
Timeline Reconstruction
SOC Operations Monitoring


