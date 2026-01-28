# Attack Scenario 01: Authentication Brute Force Detection and Response

## Scenario Overview
This scenario simulates a brute-force authentication attack targeting a Linux host.
The objective is to demonstrate how raw logs are transformed into alerts, how those
alerts are investigated, and how the incident is resolved and documented.

---

## Initial Access
An external IP address repeatedly attempts to authenticate using invalid credentials.
The attack targets the SSH service exposed to the internet.

MITRE ATT&CK:
- T1110 – Brute Force

---

## Detection

### Log Source
- Linux authentication logs (`/var/log/auth.log`)

### Detection Method
- Failed login attempts parsed using the Log-Analyzer project
- Threshold-based alert triggered after repeated failures from the same IP

Artifacts:
- `02-Log-Analyzer/analyzer.py`
- `02-Log-Analyzer/alerts.csv`

---

## SIEM Correlation

The alert is forwarded into the SIEM for correlation.

### SIEM Logic
- Rule triggers when failed login attempts exceed a defined threshold within a time window
- Source IP and username patterns are correlated

Artifacts:
- `03-SIEM-Alerting-Lab` detection rules

---

## Investigation

### Analyst Actions
- Validate source IP reputation
- Confirm affected host
- Check for successful logins or lateral movement
- Review authentication logs for persistence attempts

---

## Incident Response

### Response Actions
- Block offending IP address
- Rotate affected credentials
- Increase logging verbosity
- Notify stakeholders

### Documentation
- Incident report generated using:
  - `06-Incident-Report-Generator`

---

## Lessons Learned

### Detection Improvements
- Lower detection threshold for high-risk services
- Add geographic anomaly detection

### Preventative Controls
- Enforce multi-factor authentication
- Implement rate limiting
- Restrict SSH exposure

### Policy Mapping
- Logging and Monitoring Policy
- Access Control Policy

Artifacts:
- `07-Policy-Pack`

---

## Outcome
The attack was detected early, contained quickly, and no unauthorized access occurred.
Improvements were identified to reduce future risk.
