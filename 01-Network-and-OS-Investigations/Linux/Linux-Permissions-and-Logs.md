# Linux Permissions and Logs for Security Investigations

## Purpose
This document explains how Linux file permissions and system logs are used during
security monitoring, alert triage, and incident response. The focus is on identifying
misconfigurations, privilege abuse, and persistence mechanisms.

Understanding permissions and logs is critical for validating alerts and assessing
post-compromise impact on Linux systems.

---

## Linux File Permission Model

Linux permissions determine who can read, write, or execute files.

Permission types:
- Read (r)
- Write (w)
- Execute (x)

Permission scopes:
- Owner
- Group
- Others

Security relevance:
- Overly permissive files increase attack surface
- Writable or executable files in sensitive locations may indicate compromise
- Misconfigured permissions can enable privilege escalation

---

## High-Risk Permission Patterns

Security engineers look for:
- World-writable files or directories
- Executables writable by non-privileged users
- Configuration files with excessive permissions
- Scripts or binaries running with elevated privileges

Common risky locations:
- /etc
- /usr/bin
- /usr/local/bin
- /tmp
- /var/tmp
- /dev/shm

Permissions in temporary or shared directories are frequently abused by attackers.

---

## Sudo and Privilege Abuse

### Why Sudo Matters
Sudo allows controlled privilege escalation. Abuse or misconfiguration can grant
attackers full system access.

Indicators of concern:
- Frequent sudo usage by non-admin users
- Sudo commands executed immediately after login
- Commands executed via sudo that modify users, services, or permissions

Relevant logs typically appear in authentication logs.

---

## Key Linux Log Files

### Authentication Logs
- /var/log/auth.log (Debian/Ubuntu)
- /var/log/secure (RHEL/CentOS)

These logs record:
- SSH login attempts
- Sudo command execution
- PAM authentication activity

They are primary data sources for detecting brute force and privilege escalation.

---

### System Logs
- /var/log/syslog
- /var/log/messages

System logs provide:
- Service start and stop events
- System errors
- Context around changes following authentication events

---

## Common Log Indicators

Security-relevant log patterns include:
- Repeated failed authentication attempts
- Successful logins following multiple failures
- Sudo activity shortly after login
- Authentication activity outside expected hours

Log timing and sequence are often more important than individual entries.

---

## Investigation Commands

Common commands used during investigations:
- `ls -l` – review file permissions
- `find / -perm -o+w` – locate world-writable files
- `sudo -l` – list allowed sudo commands
- `last` – review login history
- `journalctl` – query systemd logs

These commands help validate alerts and identify misconfigurations or abuse.

---

## Correlation with Other Telemetry
Linux permission and log findings should be correlated with:
- Network connections from the host
- Process execution and service creation
- SIEM alerts related to authentication or access

Correlation increases confidence in incident assessment.

---

## Response Considerations
When suspicious permission or log activity is identified:
- Preserve relevant logs
- Avoid modifying files before evidence collection
- Escalate according to incident response procedures
- Document findings and remediation steps

---

## Portfolio Relevance
This document supports:
- Log Analyzer parsing of Linux authentication logs
- SIEM alert investigation and validation
- Linux host triage during incidents
- Attack scenarios involving brute force and privilege escalation
