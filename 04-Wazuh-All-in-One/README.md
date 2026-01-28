# SOC Lab — Wazuh All-in-One

## Objective
Build a small Security Operations Center (SOC) to collect logs, detect suspicious behavior, and practice incident response using Wazuh SIEM.

## Tools Used
- Wazuh All-in-One (Docker)
- Sysmon (Windows)
- Windows 10/11 VM
- Kali Linux VM (for attack simulation)
- Ubuntu Server (Wazuh host)
- Python (for log analysis)
- Power BI (for visualization)

## Skills Learned
- SIEM deployment and configuration
- Agent setup on Windows endpoints
- Custom rule creation and alert tuning
- Basic incident response and triage
- Log parsing and enrichment

## Steps Overview
1. Deploy Wazuh All-in-One on Ubuntu using Docker Compose.
2. Install and configure the Wazuh Agent on a Windows VM.
3. Install and configure Sysmon for detailed process logging.
4. Simulate attacks from Kali (failed logins, PowerShell commands, port scans).
5. Create custom Wazuh rules to detect repeated failed logins.
6. Visualize detections in the Wazuh dashboard and document results.

## Results
- Successful collection of Windows Event and Sysmon logs.
- Detection of brute-force and privilege escalation events.
- Custom rule triggered alerts with screenshots documented in the artifacts folder.

## Next Steps
- Integrate Suricata or Zeek for network visibility.
- Automate alert enrichment with Python.
- Build a Power BI dashboard for event visualization.
