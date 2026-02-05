# Project 24 – Bare Metal Ubuntu Log Server Setup (WiFi + Static IP + SSH Headless)

## Project Overview
This project documents how I converted an old laptop into a **real bare-metal Ubuntu Server** (not a VM) and configured it as a headless server accessible over WiFi using SSH.

This setup is intended to be used as the foundation for future SOC projects including:
- Centralized Linux log collection
- rsyslog forwarding
- SIEM log ingestion (Wazuh / Splunk / Graylog)
- Threat detection and incident response labs

---

## Lab Environment (Bare Metal Hardware)

**Host Machine (Server):**
- Device Type: Laptop (Bare Metal)
- OS: Ubuntu Server 22.04 LTS
- Hostname: `log-server01`
- Network: WiFi (Broadcom BCM4381)
- Role: Log Server / SOC Utility Server

**Client Machines Used to Manage Server:**
- MacBook Pro 2020 (SSH client)
- Workstation Linux machine (SSH client)

---

## Proof This Is Bare Metal (Not Virtual Machine)

### Check system hardware vendor
```bash
sudo dmidecode -s system-manufacturer
sudo dmidecode -s system-product-name
