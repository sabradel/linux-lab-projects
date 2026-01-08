# SOC Incident Report – Authentication Attack Detection

## Incident Summary
Multiple authentication failures were detected across Linux and Windows endpoints using Wazuh SIEM. The activity was identified as a credential access attempt consistent with password guessing behavior.

## Environment
- SIEM: Wazuh v4.14.1
- Linux Endpoint: Debian 12 (linux01)
- Windows Endpoint: Windows 10 Pro
- Network: VirtualBox Host-Only Lab

## Detection
- Index: wazuh-alerts-*
- Rule Group: authentication_failed
- Severity: Level 5–7
- MITRE ATT&CK: T1110 – Credential Access (Password Guessing)

## Evidence Observed
### Linux
- SSH authentication failures
- Failed `su` attempts
- Logged via systemd journal and detected by Wazuh

### Windows
- Failed logon attempts
- Windows Security Event ID 4625
- Authentication package: NTLM

## Investigation
Alerts were reviewed in Wazuh Discover. Event metadata, decoded fields, and timelines were analyzed to confirm repeated failed authentication attempts without successful compromise.

## Conclusion
The activity was classified as a credential access attempt. No successful login was observed. Monitoring and alerting functioned as expected.

## Analyst
Adel Yahaya
SOC / Blue Team Analyst
