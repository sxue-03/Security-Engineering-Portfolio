# Windows Event IDs — Investigation Reference

## Purpose
This document is a concise reference of high-signal Windows Event IDs used during
security alert triage and incident investigations. It is designed for quick lookup
and correlation, not deep explanation.

Use this alongside:
- Windows-Authentication-and-Privilege-Events.md
- SIEM alerts and dashboards
- Incident response workflows

---

## Authentication Events

| Event ID | Meaning | Investigation Notes |
|--------:|---------|---------------------|
| 4624 | Successful logon | Validate logon type, source, timing |
| 4625 | Failed logon | Look for spikes, repetition, automation |
| 4648 | Explicit credentials used | Often appears with lateral movement |
| 4672 | Special privileges assigned | High-risk; correlate with 4624 |

---

## Account and Group Management

| Event ID | Meaning | Investigation Notes |
|--------:|---------|---------------------|
| 4720 | User account created | Check creator and timing |
| 4722 | User account enabled | Often paired with persistence |
| 4723 | Password change attempt | Verify requester |
| 4724 | Password reset | High-risk if unexpected |
| 4728 | Added to privileged group | Immediate escalation |
| 4732 | Added to local group | Check host and scope |

---

## Process and Execution

| Event ID | Meaning | Investigation Notes |
|--------:|---------|---------------------|
| 4688 | Process created | Review parent-child relationship |
| 4689 | Process exited | Useful for timeline reconstruction |
| 4697 | Service installed | Common persistence method |

---

## Log and Policy Changes

| Event ID | Meaning | Investigation Notes |
|--------:|---------|---------------------|
| 4719 | Audit policy changed | Potential defense evasion |
| 1102 | Audit log cleared | High-confidence malicious activity |

---

## Common Investigation Sequences

- Multiple 4625 → 4624  
  Possible brute force success

- 4624 → 4672  
  Privileged access obtained

- 4624 → 4688 (suspicious binary)  
  Post-authentication execution

- 4720 / 4728 → 4624  
  Persistence via new or elevated account

Event sequencing provides stronger signals than single events.

---

## Correlation Tips
- Always correlate with source IP and host
- Compare timing against business hours
- Validate user role and expected behavior
- Cross-check with network and endpoint telemetry

---

## Portfolio Relevance
This reference supports:
- SIEM rule tuning and alert validation
- Windows authentication investigations
- Attack scenario walkthroughs
- Incident reporting and documentation
