# Networking for Security Investigations

## Purpose
This document explains how network behavior is analyzed during security alert triage
and incident investigations. The focus is on identifying abnormal patterns that
indicate reconnaissance, authentication abuse, lateral movement, or command-and-control
activity.

This is not a general networking reference. It documents how security engineers
interpret network evidence during incidents.

---

## Why Network Context Matters in Security
Most attacks interact with the network at multiple stages:
- Initial access
- Credential abuse
- Lateral movement
- Data exfiltration
- Command-and-control

Understanding network behavior allows security engineers to quickly assess intent,
scope, and impact.

---

## TCP and UDP in Attacks

### TCP
Commonly targeted for:
- SSH (22)
- RDP (3389)
- Web services (80/443)
- SMB (445)

Security relevance:
- Repeated TCP connection attempts often indicate brute force or scanning
- Failed TCP sessions followed by success are high-risk indicators

---

### UDP
Commonly involved in:
- DNS activity (53)
- Scanning and discovery
- Amplification or reflection attacks

Security relevance:
- High-volume or unusual UDP traffic may indicate reconnaissance or abuse
- DNS patterns are often used to detect beaconing or exfiltration

---

## Commonly Targeted Ports and Services

| Port | Service | Security Relevance |
|-----:|--------|--------------------|
| 22 | SSH | Brute force, credential abuse |
| 80 / 443 | HTTP / HTTPS | Exploitation, C2 traffic |
| 3389 | RDP | Credential attacks, lateral movement |
| 53 | DNS | Beaconing, data exfiltration |
| 445 | SMB | Lateral movement, ransomware |

Unexpected exposure or traffic on these ports often warrants investigation.

---

## IP Address and Source Analysis
During investigations, source IP addresses are evaluated for:
- Internal vs external origin
- Repetition across alerts
- Geographic anomalies
- Known malicious reputation

Source behavior over time is often more meaningful than a single event.

---

## Traffic Pattern Analysis
Attack behavior typically appears as patterns rather than isolated connections.

Common suspicious patterns:
- Repeated connection attempts in short intervals
- One source interacting with many destinations
- Sequential port targeting
- Authentication-related traffic spikes

Pattern analysis reduces false positives and improves detection accuracy.

---

## Correlation with Authentication and Host Logs
Network findings should be correlated with:
- Authentication failures and successes
- Process execution events
- Privilege escalation activity

Examples:
- Network connections followed by login failures
- Successful authentication after repeated connection attempts
- Outbound traffic from newly spawned processes

Correlation strengthens confidence in investigation conclusions.

---

## Network Indicators in SIEM Detection
Security teams use network indicators such as:
- Source IP frequency
- Destination port targeting
- Connection timing and volume
- Protocol usage patterns

These indicators are commonly combined with host-based logs in SIEM rules.

---

## Investigation Outcomes
Network analysis helps determine:
- Whether activity is malicious or benign
- Which systems are affected
- Whether access was successful
- Whether escalation or lateral movement occurred

This information guides response and containment decisions.

---

## Portfolio Relevance
This document supports:
- SIEM alert investigation and tuning
- Log Analyzer detection logic
- Brute force and access-related attack scenarios
- Incident response workflows and reporting
