# 🛡️ Wazuh SIEM Lab – Windows & Linux Attack Detection

> SOC-focused SIEM lab demonstrating real-time attack detection across Windows and Linux endpoints using Wazuh.

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

## ⚙️ SIEM Deployment (Wazuh Installation)

### Download Wazuh

```bash
curl -sO https://packages.wazuh.com/4.x/wazuh-install.sh
