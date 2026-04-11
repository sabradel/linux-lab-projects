# 🛡️ Wazuh SIEM Lab – Windows & Linux Attack Detection

---

## 📌 Overview

This project demonstrates a SOC-style SIEM lab built using Wazuh on a bare-metal Ubuntu server.

The lab monitors both Linux and Windows endpoints and detects security events in real time.

### ✅ What this lab simulates:

- SIEM deployment (Wazuh)
- Windows & Linux log monitoring
- Secure connectivity using Tailscale VPN
- Attack detection (failed login / brute force)
- Real SOC investigation workflow

---

## 🏗️ Lab Environment

| Machine | Hostname | OS | Role |
|--------|----------|----|------|
| SIEM Server | log-server01 | Ubuntu Server | Wazuh Manager |
| Linux Endpoint | file01 | Ubuntu | Wazuh Agent |
| Windows Endpoint | HELPDESK-PC01 | Windows 10 | Wazuh Agent |

---

## 🔧 Technologies Used

- Wazuh SIEM (Manager + Dashboard + Agents)
- Ubuntu Server 22.04
- Windows 10 Pro
- Tailscale VPN
- Bash / PowerShell
- Windows Event Logs

---

## ⚙️ Installation & Setup

### Download Wazuh

![Download Wazuh](screenshots/01-download-wazuh.png)

---

### Start Installation

![Install Start](screenshots/02-install-start.png)

---

### Installation Progress

![Install Progress](screenshots/03-install-progress.png)

---

### Wazuh Login

![Wazuh Login](screenshots/04-wazuh-login.png)

---

### Wazuh Dashboard

![Wazuh Dashboard](screenshots/05-wazuh-dashboard.png)

---

## 🌐 Secure Connectivity (Tailscale)

### Install Tailscale

![Tailscale Install](screenshots/06-tailscale-install.png)

---

### Devices Connected

![Tailscale Devices](screenshots/07-tailscale-devices.png)

---

### Connectivity Test

![Tailscale Connectivity](screenshots/08-tailscale-connectivity.png)

---

## 🎯 Attack Simulation

### Scenario: Failed Login Attack (Brute Force)

A brute-force login attempt was simulated on Windows using:

```powershell
runas /user:administrator cmd
