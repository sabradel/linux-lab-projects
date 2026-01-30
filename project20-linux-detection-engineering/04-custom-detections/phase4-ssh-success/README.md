# Phase 4 — SSH Successful Login Detection

## What was done
A custom Wazuh rule was created on the SOC server (Ubuntu – soc01) to detect
successful SSH logins on a Linux endpoint.

## Lab machines
- Kali Linux — used to initiate SSH connection
- Debian 12 (adel) — target system with Wazuh agent
- Ubuntu 22.04 (soc01) — Wazuh manager and SIEM

## How the alert was triggered
From Kali Linux, an SSH login was performed to the Debian machine.

Command used:
```bash
ssh adel@192.168.56.107
