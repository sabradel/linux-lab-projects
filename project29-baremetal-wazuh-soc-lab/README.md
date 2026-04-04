# 🛡️ Wazuh SIEM Lab – Windows & Linux Attack Detection

## 📌 Overview
This project demonstrates a SOC-style SIEM lab built using Wazuh on a bare-metal Ubuntu server. The lab monitors both Linux and Windows endpoints and detects security events in real time.

A failed login attack was simulated on a Windows machine and successfully detected using Wazuh by analyzing Windows Event ID 4625.

---

## 🏗️ Lab Architecture

- **SIEM Server:** Ubuntu (Bare Metal) – Wazuh Manager
- **Linux Endpoint:** file01 (Ubuntu agent)
- **Windows Endpoint:** helpdesk-pc01 (Windows 10 agent)
- **Network:** Tailscale VPN (secure remote connectivity)

---

## 🔧 Technologies Used

- Wazuh SIEM (Manager, Dashboard, Agents)
- Ubuntu Server 22.04
- Windows 10 Pro
- Tailscale (VPN)
- PowerShell / Bash
- Windows Event Logs

---

## 🔍 Attack Simulation

### 🎯 Scenario: Failed Login Attack (Brute Force Simulation)

A brute-force style login attempt was simulated on the Windows endpoint using incorrect credentials.

Command used:

```cmd
runas /user:administrator cmd

Multiple failed login attempts were generated intentionally.

---

## 🚨 Detection

The attack was successfully detected in Wazuh using:

- **Event ID:** 4625 (Failed Login)
- **Source:** Windows Security Event Logs
- **Agent:** HELPDESK-PC01

---

## 📸 Key Evidence

### 🖥️ Wazuh Dashboard (Agents Connected)
![Agents Connected](screenshots/screenshots-24-windows-agent-connected.png)

### 🚨 Failed Login Detection (Event ID 4625)
![Failed Login Detection](screenshots/screenshots-26-wazuh-failed-login-detected.png)

---

## 🧠 Skills Demonstrated

- SIEM deployment and configuration (Wazuh)
- Endpoint monitoring (Linux + Windows)
- Log analysis (Windows Event Logs, Linux logs)
- Attack simulation (failed login / brute force)
- Agent deployment and troubleshooting
- Secure networking using Tailscale VPN

---

## 🎯 Outcome

Successfully built a functional SOC lab capable of:

- Monitoring multiple endpoints  
- Detecting security events in real time  
- Investigating failed authentication attempts  

This project simulates real-world SOC Analyst responsibilities.

---

## 🚀 Future Improvements

- SSH brute-force detection (Linux)
- Alert severity tuning
- Integration with threat intelligence (MISP)
- Automated alerting and response

---

## 👤 Author

Adel Yahaya  
GitHub: https://github.com/sabradel
