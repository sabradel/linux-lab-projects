# Phase 4 – Custom Detection: SSH Login Success

## Objective
Detect successful SSH logins on a Linux endpoint using Wazuh custom rules.
This detection helps identify potential misuse of valid credentials and
establishes visibility into remote access activity.

---

## Environment
- **SIEM:** Wazuh Manager (soc01)
- **Agent:** Debian Linux (adel – 192.168.56.107)
- **Attacker / Source:** Kali Linux (192.168.56.101)
- **Log source:** journald / sshd

---

## Threat Context
Successful SSH authentication can indicate:
- Legitimate administrative access
- Use of stolen or reused credentials
- Initial access using valid accounts

**MITRE ATT&CK**
- T1078 – Valid Accounts

---

## Detection Logic

### Wazuh Rule
**File:** `/var/ossec/etc/rules/local_rules.xml`

```xml
<group name="local,linux,ssh,authentication">
  <rule id="100200" level="5">
    <if_sid>5715</if_sid>
    <description>Successful SSH login detected on Linux endpoint</description>
    <mitre>T1078</mitre>
  </rule>
</group>
