# TCP/IP and Ports for Security Engineering

## Purpose
This document provides a practical overview of TCP/IP behavior and commonly abused
ports from a security engineering perspective. It focuses on how transport protocols
and port usage appear during attacks and investigations.

This file serves as a technical reference that supports network-based detection,
alert triage, and incident response.

---

## TCP/IP in Security Context

### TCP (Transmission Control Protocol)
TCP is connection-oriented and stateful, making it a frequent target for attacks
against authenticated or session-based services.

Security relevance:
- TCP handshakes create observable patterns in logs and network telemetry
- Failed and successful connection attempts can be correlated with authentication events
- Repeated TCP retries often indicate brute force or scanning activity

Common TCP attack use cases:
- SSH brute force
- RDP credential abuse
- Web exploitation attempts

---

### UDP (User Datagram Protocol)
UDP is connectionless and does not guarantee delivery, which makes it useful for
scanning, amplification, and stealthy communication.

Security relevance:
- High-volume UDP traffic may indicate reconnaissance or abuse
- UDP-based services are commonly leveraged for reflection or amplification
- Lack of session state complicates attribution

Common UDP-related concerns:
- DNS misuse
- NTP amplification
- Scanning activity

---

## Common Ports and Their Security Significance

| Port | Service | Security Considerations |
|-----:|--------|--------------------------|
| 22 | SSH | Brute force, credential abuse |
| 80 | HTTP | Web exploitation, scanning |
| 443 | HTTPS | Exploitation, command-and-control |
| 3389 | RDP | Credential attacks, lateral movement |
| 53 | DNS | Beaconing, exfiltration |
| 445 | SMB | Lateral movement, ransomware |
| 25 | SMTP | Spam, phishing infrastructure |
| 123 | NTP | Amplification attacks |

Unexpected exposure or traffic on these ports is frequently suspicious.

---

## Port Exposure and Attack Surface
Open ports define the external attack surface of a system.

Security engineers assess:
- Which ports are exposed to untrusted networks
- Whether exposed services are necessary
- Whether access is restricted by network controls

Minimizing exposed ports reduces risk and alert volume.

---

## Port-Based Detection Logic
Many detections rely on port context.

Examples:
- Repeated connections to port 22 from a single IP
- Authentication failures on port 3389
- Outbound connections to uncommon external ports
- DNS traffic patterns inconsistent with normal usage

Port awareness improves SIEM rule accuracy.

---

## Correlation with Logs and Processes
Port and protocol activity should be correlated with:
- Authentication logs
- Process execution events
- Service start and stop activity

Examples:
- SSH traffic followed by sudo usage
- Outbound connections from newly spawned processes
- SMB connections following authentication events

Correlation provides stronger indicators than network data alone.

---

## Portfolio Relevance
This document supports:
- Network-based SIEM detections
- Brute force and access-related attack scenarios
- Log Analyzer correlation logic
- Incident response investigations
