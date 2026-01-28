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

These indicators often precede privilege escalation or persistence attempts.

---

## Process Investigation

### Why Process Analysis Matters
After initial access, attackers often execute tools or scripts. Process analysis
helps determine whether malicious code is running and how it was launched.

---

### Common Investigation Commands
- `ps aux` – list running processes
- `top` / `htop` – observe real-time activity
- `systemctl status <service>` – inspect services
- `crontab -l` – check scheduled tasks

Security engineers look for:
- Unknown or unexpected processes
- Processes running as root without justification
- Services created or modified recently
- Persistence mechanisms using cron or systemd

---

## Indicators of Compromise in Processes
Common red flags:
- Processes running from unusual directories (e.g., /tmp, /dev/shm)
- Long-running processes with no clear purpose
- Network-connected processes that do not match expected services
- Executables with suspicious names or permissions

---

## Correlation with Network Activity
Process findings should be correlated with network telemetry:
- Network connections originating from unknown processes
- Outbound connections following authentication events
- Repeated connections to external IPs or uncommon ports

Correlation strengthens confidence in compromise assessment.

---

## Response Considerations
If malicious activity is suspected:
- Preserve logs and process information
- Avoid restarting services prematurely
- Escalate findings according to incident response procedures
- Document observations for follow-up analysis

---

## Portfolio Relevance
This document supports:
- Log Analyzer parsing of Linux authentication logs
- SIEM alert validation for SSH and sudo abuse
- Network troubleshooting during incidents
- Brute force and access-related attack scenarios
