# Project 11: Linux Incident Response & Threat Investigation

## 🎯 Objective
Simulate and investigate a security incident on a Linux system by analyzing authentication logs, identifying suspicious behavior, and documenting findings using SOC-style methodology.

---

## 🧪 Lab Environment
- Ubuntu Server 24.04 LTS (Target)
- Kali Linux (Analyst / Attacker)
- systemd journal & auth logs

---

## 🔍 Incident Scenario
Multiple failed login attempts were detected on a Linux server followed by successful privilege escalation activity. This project investigates whether the activity represents brute-force attempts or unauthorized access.

---

## 🛠️ Tasks Performed

### 1️⃣ Identify Failed Authentication Attempts
```bash
sudo journalctl -u ssh --since "1 hour ago" | grep "Failed password"
