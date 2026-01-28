# Authentication and Access Patterns

## Purpose
This document describes how authentication and access behavior is analyzed during
security monitoring, alert triage, and incident response. The focus is on identifying
abnormal access patterns that may indicate credential compromise, privilege escalation,
or lateral movement.

These patterns apply across operating systems, cloud environments, and network services.

---

## Normal Authentication Patterns
Normal authentication behavior typically shows consistency over time.

Common characteristics:
- Limited failed login attempts
- Logins during normal business hours
- Access from known IP ranges or devices
- Stable user-to-host relationships

Establishing a baseline of normal behavior is critical for reducing false positives
in SIEM alerting.

---

## Suspicious Authentication Patterns
Authentication activity becomes suspicious when it deviates from established baselines.

Common indicators:
- Repeated failed login attempts from a single source
- One IP attempting multiple usernames
- Authentication attempts outside normal working hours
- Logins from new or unusual geographic locations
- Sudden spikes in authentication volume

These patterns often indicate brute force attacks or credential stuffing.

---

## Privilege Escalation Patterns
Attackers frequently attempt to escalate privileges after gaining initial access.

Indicators include:
- Unusual or repeated sudo usage
- Accounts added to administrative or privileged groups
- Privileged access occurring immediately after authentication
- Service accounts used for interactive logins

Privilege escalation events are high-risk and should be investigated immediately.

---

## Lateral Movement Access Patterns
After obtaining credentials, attackers may move laterally across systems.

Common patterns:
- One account authenticating to multiple hosts in a short time window
- Authentication without prior interactive login
- Use of administrative protocols across systems
- Access attempts to systems unrelated to the user’s role

Lateral movement is often a strong indicator of an active intrusion.

---

## How These Patterns Appear in Logs

### Windows
- Failed and successful logon events
- Privilege assignment and group membership changes
- Process creation following authentication

### Linux
- SSH authentication failures and successes
- Sudo usage and privilege elevation
- PAM authentication events

These logs are typically forwarded to a SIEM for correlation and alerting.

---

## Detection and Correlation
Security teams detect authentication-based attacks by correlating:
- Failed vs successful login ratios
- Source IP behavior over time
- Account activity across multiple systems
- Authentication events followed by privilege usage

Correlation helps distinguish user error from malicious activity.

---

## MITRE ATT&CK Mapping
Authentication and access abuse maps to multiple ATT&CK techniques, including:
- Brute Force
- Credential Access
- Privilege Escalation
- Lateral Movement

Mapping these behaviors helps align detections with standardized threat models.

---

## Portfolio Relevance
This document supports:
- Log Analyzer detection logic for failed authentication
- SIEM alerting rules for access abuse
- Attack scenario walkthroughs involving brute force and lateral movement
- Incident response investigations and reporting


