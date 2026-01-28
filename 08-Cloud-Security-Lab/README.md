# Cloud Security Lab (Azure)

## Objective
Learn how to secure, monitor, and analyze activities within an Azure cloud environment using Microsoft Defender for Cloud and Microsoft Sentinel.

## Tools Used
- Azure Portal (Free Tier)
- Azure Active Directory (Entra ID)
- Microsoft Defender for Cloud
- Microsoft Sentinel (SIEM)
- Kusto Query Language (KQL)

## Skills Learned
- Cloud Identity and Access Management (IAM)
- Conditional Access and MFA configuration
- Azure Defender and Security Policy configuration
- KQL queries for log analysis and detection
- SIEM integration and alert creation

## Steps Overview
1. Create a free Azure account and deploy a test Windows VM.
2. Enable Microsoft Defender for Cloud and review security recommendations.
3. Configure IAM roles, MFA, and Conditional Access.
4. Connect Azure logs to Microsoft Sentinel (Log Analytics Workspace).
5. Write KQL queries to detect failed logins and new admin role assignments.
6. Capture alerts and screenshots of dashboards.

## Results
- Configured a secure cloud environment with Defender alerts.
- Collected and analyzed sign-in logs using Sentinel.
- Built custom detections using KQL.

## Next Steps
- Automate reporting with Logic Apps or PowerShell.
- Integrate Azure alerts with Wazuh SIEM.
- Add Suricata or Zeek for hybrid network monitoring.
