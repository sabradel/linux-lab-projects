# Project 16: SOC Investigation – SSH Brute Force Attack

## Objective

Investigate a detected SSH brute-force attack against a Linux server using Wazuh SIEM and document the full incident response process as a SOC analyst.

---

## Lab Environment

- Attacker: Kali Linux (Hydra)
- Victim: Debian / Ubuntu Linux Server
- SIEM: Wazuh
- Attack Type: SSH Brute Force
- MITRE ATT&CK: T1110 – Brute Force

---

## Incident Summary

Wazuh generated multiple alerts indicating repeated failed SSH login attempts from a remote IP address. This activity was consistent with an automated brute-force attack.

The investigation confirms this was a real attack generated using Hydra from Kali Linux.

---

## Evidence

### 1. Brute Force Attack & SSH Logs

![Hydra Attack](screenshots/05-hydra-bruteforce-and-ssh-logs.png)

---

### 2. Wazuh Detection Dashboard

![Wazuh Detection](screenshots/06-wazuh-detection-dashboard.png)

---

## Investigation Steps

1. Identified repeated failed SSH login attempts in `/var/log/auth.log`
2. Observed source IP generating high volume authentication failures
3. Verified attack tool (Hydra) from Kali Linux
4. Confirmed Wazuh correlation and alerting
5. Mapped activity to MITRE ATT&CK T1110 (Brute Force)

---

## Impact Assessment

- No successful login detected
- No account compromise observed
- Attack classified as: **True Positive – External Brute Force Attempt**

---

## Recommendations

- Block attacker IP at firewall
- Enforce fail2ban or rate-limiting
- Disable root SSH login
- Enforce SSH key authentication
- Monitor for repeated attempts

---

## Skills Demonstrated

- SOC alert triage
- Log analysis
- Incident investigation
- SIEM analysis (Wazuh)
- MITRE ATT&CK mapping
- Linux security monitoring
- Attack detection & response

---

## Conclusion

This project demonstrates a full SOC-style workflow: detection, investigation, validation, classification, and response recommendations for a real brute-force attack.
