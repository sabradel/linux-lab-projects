# Phase 4 – SSH Success & Privilege Escalation Detection

## Objective
Detect successful SSH authentication followed by privilege escalation via sudo spawning an interactive root shell.

---

## Environment
- Attacker: Kali Linux
- Target: Debian 12 (agent: adel)
- SIEM: Wazuh Manager on Ubuntu (soc01)

---

## Detection Logic

### Rule 100200 – Successful SSH Login
Triggers when:
- SSH authentication succeeds
- Maps to MITRE T1078 (Valid Accounts)

### Rule 100202 – Privilege Escalation
Triggers when:
- A sudo command spawns `/bin/bash`
- Indicates interactive root shell
- Severity: Level 8
- MITRE: T1548.003 (Sudo and Sudo Caching)

---

## Attack Simulation

From Kali:
```bash
ssh adel@192.168.56.107
sudo /bin/bash
exit
exit
