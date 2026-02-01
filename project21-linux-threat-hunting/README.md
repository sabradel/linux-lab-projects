# 🚀 Project 21: Linux Threat Hunting & Detection Validation (Wazuh SIEM)

## 🎯 Objective
Perform targeted threat hunting on Linux endpoints using Wazuh SIEM by validating alerts, reviewing logs, and documenting SOC-style investigative findings.

This project focuses on analyst reasoning and alert validation rather than custom rule creation.

---

## 🧪 Environment
- SIEM: Wazuh Manager (soc01)
- Endpoint: Debian Linux (adel – 192.168.56.107)
- Attacker / Source: Kali Linux (192.168.56.101)
- Log Sources: journald, sshd, sudo

---

## 🔍 Threat Hunting Scope
The following activity was investigated:

- SSH successful authentication
- Sudo privilege enumeration
- Sudo-based root shell escalation

---

## 🧠 Investigation Summary

### SSH Login Activity
Reviewed successful SSH logins to identify access patterns and validate expected behavior.

Related Rule:
- 100200 – Successful SSH login detected

---

### Privilege Escalation Activity
Investigated sudo usage leading to root shell access.

Related Rules:
- 100201 – Privilege enumeration via sudo
- 100202 – Sudo spawned interactive root shell

---

## 📸 Evidence
Screenshots captured from Wazuh alerts and terminal investigations are included in the images directory.

---

## 🧰 Skills Demonstrated
- Linux threat hunting
- SOC alert validation
- Wazuh SIEM investigation
- Log analysis (SSH, sudo)
- Security documentation

---

## ✅ Outcome
This project demonstrates the ability to validate detections, interpret Linux security events, and document findings in a SOC-ready format.
