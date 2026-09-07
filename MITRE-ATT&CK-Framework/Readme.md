MITRE ATT&CK Framework

---
Overview

This lab focused on understanding how Wazuh maps security events to the MITRE ATT&CK framework.
The objective was to identify observed tactics and techniques, understand their purpose, and learn how security analysts use MITRE ATT&CK during threat detection and investigations.

MITRE ATT&CK provides a standardized framework for categorizing adversary behavior based on real-world attack techniques and tactics.

---
Objectives
Explore the MITRE ATT&CK module in Wazuh.
Understand the difference between tactics and techniques.
Review ATT&CK mappings generated from endpoint activity.
Identify the most common tactics detected on the monitored endpoint.
Analyze techniques associated with Registry modifications and system changes.
Understand how MITRE ATT&CK supports SOC investigations.

---
Environment

Platform: Wazuh Cloud

Agent Name: Gab

Agent ID: 001

Operating System: Microsoft Windows 11 Pro

Wazuh Version: 4.14.7

---
Understanding MITRE ATT&CK
Tactics

A tactic represents the attacker's objective.

Examples include:

Persistence
Privilege Escalation
Defense Evasion
Impact
Credential Access
Execution

Tactics answer the question:

"What is the attacker trying to achieve?"

---
Techniques

A technique describes the method used to achieve a tactic.

Examples include:

T1112 - Modify Registry
T1070.004 - File Deletion
T1485 - Data Destruction

Techniques answer the question:

"How is the attacker achieving that objective?"

---
Tactics Identified

The following MITRE ATT&CK tactics were detected during monitoring:

Defense Evasion

1321 events

Defense Evasion was the most common tactic observed.

This tactic includes activities intended to avoid detection or bypass security controls.

Examples observed:

Registry modifications
System configuration changes

---
Impact

573 events


Impact-related activity involved:

File Deletion
Data Destruction
Stored Data Manipulation

These actions are associated with modification or removal of data within a system.

---
Privilege Escalation

15 events

Privilege Escalation events were generated when elevated privileges were assigned during user authentication activities.

Example:
Special privileges assigned to new logon

---
Persistence
1 event

Persistence techniques allow activity or configuration changes to remain active after system restarts or user logoffs.

---
Techniques Identified
T1112 - Modify Registry

Events Detected
1307


Tactic

Defense Evasion

Analysis

Registry modification events were generated during File Integrity Monitoring activities.

Examples included:

Registry Key Added
Registry Value Added
Registry Key Deleted

These changes were mapped to MITRE technique:

T1112 - Modify Registry
2
 
---
T1565.001 - Stored Data Manipulation

Events Detected

380

Analysis

This technique represents modifications to stored data within the system.

Such activity may be observed during legitimate system operations or as part of malicious actions intended to alter information.

---
T1485 - Data Destruction

Events Detected

187

Analysis

Data Destruction is categorized under the Impact tactic and represents attempts to remove, destroy, or corrupt data.

---
T1070.004 - File Deletion

Events Detected

187

Analysis

File Deletion events involve the removal of files from a system.

Attackers often use file deletion techniques to:

Remove evidence
Hide activity
Destroy data
Reduce forensic visibility

---
T1484 - Domain Policy Modification

Events Detected

14

Analysis

Domain Policy Modification techniques involve changes to security or system policies and may affect system behavior or access controls.

---
Security Impact

MITRE ATT&CK provides valuable context for security investigations by:

Standardizing attacker behaviors.
Mapping alerts to known techniques.
Assisting threat hunters during investigations.
Improving incident response workflows.
Supporting SOC alert triage and prioritization.

Instead of reviewing events individually, analysts can quickly understand how observed activity relates to known attacker techniques.

---
Key Findings
Wazuh successfully mapped security events to the MITRE ATT&CK framework.
Defense Evasion was the most frequently observed tactic.
Registry modifications generated the highest number of ATT&CK-mapped events.
Impact-related techniques were also detected through file and data modification activities.
Authentication-related events contributed to Privilege Escalation mappings.
ATT&CK mappings provided additional context for security monitoring.

---
Conclusion

This lab demonstrated how Wazuh integrates the MITRE ATT&CK framework to classify security events and provide contextual intelligence for investigations.
The monitored Windows endpoint generated events associated with Defense Evasion, Impact, Privilege Escalation, and Persistence tactics.
By mapping activity to ATT&CK techniques such as T1112 (Modify Registry) and T1070.004 (File Deletion),
Wazuh helped translate raw events into meaningful attack behaviors that can be used during threat hunting and incident response.

---
Skills Demonstrated
MITRE ATT&CK Framework
Threat Intelligence Mapping
Wazuh Security Monitoring
Security Event Analysis
Threat Hunting
ATT&CK Technique Analysis
SOC Operations
Incident Investigation Support
