# Incident Report – Authentication Failures (Wazuh SOC Lab)

## Summary
Wazuh detected multiple failed authentication attempts across monitored endpoints during a controlled attack simulation.

## Detection Sources
- Linux SSH authentication logs
- Windows Security Event Log (Event ID 4625)
- Wazuh SIEM correlation rules

## Alert Details
- Rule group: authentication_failed
- Severity: Medium
- Affected agents: linux01, windows10
- Authentication methods: SSH, NTLM

## Investigation Steps
1. Opened Wazuh Dashboard → Explore → Discover
2. Selected index pattern wazuh-alerts-*
3. Filtered alerts using:
   - rule.groups : authentication_failed
4. Verified failed login evidence in raw logs
5. Confirmed no successful authentication followed the failures

## MITRE ATT&CK Mapping
- Tactic: Credential Access
- Technique: T1110 – Password Guessing

## Conclusion
The alerts were validated as authentication attack attempts. No endpoint compromise was identified, and the SIEM detection pipeline functioned as expected.
