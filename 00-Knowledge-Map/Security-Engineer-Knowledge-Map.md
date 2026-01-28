# Security Engineer Knowledge Map

## 1. Attack Lifecycle
Reconnaissance → Initial Access → Persistence → Privilege Escalation →
Lateral Movement → Command and Control → Exfiltration

Mapped using the MITRE ATT&CK framework.

---

## 2. Detection Strategy
- Network telemetry (IP, ports, protocols)
- Host telemetry (Windows Event Logs, Linux authentication logs)
- Behavioral detection versus static indicators

---

## 3. Logging Sources
- Windows: Security log, Sysmon
- Linux: auth.log, syslog
- Network: firewall, VPN, DNS
- Cloud: IAM and audit logs

---

## 4. Alerting Philosophy
- High-signal alerts over high volume
- Reduction of false positives
- Prevention of alert fatigue

---

## 5. Incident Response Workflow
Triage → Scope → Contain → Eradicate → Recover → Lessons Learned

---

## 6. Prevention and Policy
- Least privilege
- Logging requirements
- Access control
- Cloud guardrails
