# Windows Authentication and Privilege Events

## Purpose
This document explains how Windows authentication and privilege-related events are
analyzed during security monitoring and incident response. The focus is on detecting
credential abuse, privilege escalation, and lateral movement using Windows telemetry.

Windows authentication logs are a primary data source in enterprise environments and
are commonly forwarded to a SIEM for correlation.

---

## Core Authentication Events

### Failed Authentication
- Event ID 4625 – Failed logon attempt

Security relevance:
- Repeated failures may indicate brute force or credential stuffing
- Failures across multiple accounts from one source are high risk
- Time-based spikes often indicate automation

---

### Successful Authentication
- Event ID 4624 – Successful logon

Security relevance:
- Successful logins following repeated failures are critical to investigate
- Logon type helps determine access method (interactive, network, remote)
- New source systems or locations may indicate compromise

---

## Privilege-Related Events

### Privileged Logons
- Event ID 4672 – Special privileges assigned to a new logon

This event indicates:
- Administrative or high-privilege access
- Elevated tokens assigned at logon
- Potential post-compromise activity

Privileged logons should be correlated with prior authentication behavior.

---

### Account and Group Changes
- Event ID 4720 – User account created
- Event ID 4728 – User added to a privileged group
- Event ID 4732 – User added to a local group

Security relevance:
- Unexpected account creation may indicate persistence
- Group membership changes can signal privilege escalation
- Timing relative to logons is critical

---

## Process Creation and Post-Authentication Activity
- Event ID 4688 – Process creation

Security relevance:
- Process execution immediately after logon may indicate attacker activity
- Unusual parent-child process relationships are suspicious
- Administrative tools launched by non-admin users require investigation

Process events help identify actions taken after access is gained.

---

## Common Investigation Patterns

Security engineers analyze sequences, not isolated events.

Examples:
- Multiple 4625 events followed by a 4624
- 4624 followed immediately by 4672
- 4624 followed by 4688 with suspicious executables
- Account creation followed by logon activity

Event sequencing provides strong evidence of malicious behavior.

---

## Correlation with Network Activity
Windows authentication events should be correlated with:
- Source IP addresses
- Network connection logs
- Lateral movement protocols (SMB, WinRM, RDP)

Correlation helps distinguish legitimate admin activity from attacker behavior.

---

## Response Considerations
When suspicious authentication or privilege activity is confirmed:
- Identify affected accounts and systems
- Review recent logons and group changes
- Reset or disable compromised accounts
- Escalate according to incident response procedures

Actions should be documented clearly for audit and follow-up.

---

## MITRE ATT&CK Mapping
Windows authentication and privilege abuse commonly map to:
- Credential Access
- Privilege Escalation
- Lateral Movement
- Persistence

Mapping supports standardized detection and reporting.

---

## Portfolio Relevance
This document supports:
- SIEM alerting rules using Windows Event IDs
- Brute force and credential abuse attack scenarios
- Incident response investigations and reporting
- Policy Pack controls for access and privilege management
