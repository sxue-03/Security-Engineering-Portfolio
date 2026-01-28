# Linux Logs and Processes for Security Investigations

## Purpose
This document explains how Linux logs and process activity are analyzed during
security monitoring and incident response. The focus is on identifying evidence
of authentication attacks, privilege escalation, persistence, and post-compromise
activity.

---

## Key Linux Log Files

### Authentication Logs
- /var/log/auth.log (Debian/Ubuntu)
- /var/log/secure (RHEL/CentOS)

These logs record:
- SSH login attempts (success and failure)
- sudo usage
- PAM authentication events

They are primary sources for detecting brute force attacks and credential abuse.

---

### System Logs
- /var/log/syslog
- /var/log/messages

System logs provide context around:
- Service starts and stops
- Errors and crashes
- Unexpected system behavior following access events

---

## Common Authentication Indicators

Indicators of suspicious behavior include:
- Repeated failed SSH logins from the same source IP
- Multiple usernames targeted by a single source
- Successful logins immediately following repeated failures
- sudo usage shortly after authentication

These indicators
