# Linux Processes and Services for Security Investigations

## Purpose
This document explains how Linux processes and services are analyzed during
security monitoring and incident response. The focus is on identifying malicious
execution, persistence mechanisms, and post-compromise activity.

Process and service analysis is critical after initial access has been detected.

---

## Why Process and Service Analysis Matters
After authentication or exploitation, attackers must execute code to:
- Maintain access
- Escalate privileges
- Communicate externally
- Persist across reboots

These actions almost always appear as processes or services.

---

## Process Investigation Overview

### What Security Engineers Look For
- Unexpected running processes
- Processes running as root or privileged users
- Processes launched from unusual directories
- Network-enabled processes without clear purpose
- Recently started or long-running suspicious processes

Process context is often more important than process names.

---

## Common Investigation Commands

- `ps aux`  
  List all running processes with ownership and resource usage

- `top` / `htop`  
  Observe real-time CPU and memory usage

- `pstree`  
  Visualize parent-child process relationships

- `lsof -i`  
  Identify processes with active network connections

These commands help identify malicious execution and relationships between processes.

---

## Suspicious Process Indicators
Common red flags include:
- Processes running from `/tmp`, `/var/tmp`, or `/dev/shm`
- Random or misleading process names
- Processes without associated packages or services
- Network connections initiated by unknown binaries
- Processes running under unexpected users

Attackers often attempt to blend in by mimicking legitimate names.

---

## Linux Services and Persistence

### Why Services Matter
Services allow attackers to:
- Maintain persistence
- Execute code on startup
- Hide malicious activity as legitimate system behavior

---

### Common Service Investigation Commands

- `systemctl list-units --type=service`  
  List active services

- `systemctl status <service>`  
  Inspect service configuration and behavior

- `systemctl list-unit-files`  
  Identify enabled services at boot

- `crontab -l` / `/etc/cron*`  
  Check scheduled persistence mechanisms

---

## Service-Based Persistence Indicators
Indicators of concern include:
- Newly created or modified services
- Services running executables from non-standard paths
- Services with vague or misleading names
- Services created shortly after suspicious authentication events

Persistence often appears shortly after initial access.

---

## Correlation with Logs and Network Activity
Process and service findings should be correlated with:
- Authentication logs (SSH, sudo)
- Network connections and traffic patterns
- File permission changes
- SIEM alerts and timelines

Correlation provides stronger confidence than isolated findings.

---

## Response Considerations
When suspicious processes or services are identified:
- Capture process details and command-line arguments
- Preserve service configuration files
- Avoid immediate system restarts
- Escalate findings according to incident response procedures
- Document all observations and actions

Preservation of evidence is critical for accurate incident handling.

---

## Portfolio Relevance
This document supports:
- Linux host investigation during incidents
- Correlation with network and authentication alerts
- Brute force and post-compromise attack scenarios
- Incident response documentation and reporting
