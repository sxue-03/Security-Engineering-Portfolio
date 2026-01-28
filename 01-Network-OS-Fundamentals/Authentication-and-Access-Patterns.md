# Authentication and Access Patterns

## Normal Authentication Patterns
- Single user → single host
- Business hours logins
- Known source IP ranges
- Consistent device usage

## Suspicious Authentication Patterns
- Login attempts across many hosts
- Sudden privilege elevation
- Service account interactive logins
- Logins from new geographies

## Privilege Escalation Patterns
- Repeated sudo usage
- Admin group membership changes
- Token impersonation
- Pass-the-hash / pass-the-ticket indicators

## Lateral Movement Access Patterns
- One account accessing many systems
- Authentication without prior login
- SMB / WinRM / SSH spread

## How These Appear in Logs
- Windows Security Event IDs
- Linux auth.log / secure
- SIEM correlation logic

## How These Map to ATT&CK
- Credential Access
- Privilege Escalation
- Lateral Movement
