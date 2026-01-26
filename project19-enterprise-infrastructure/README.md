# Project 19: Enterprise Linux Infrastructure Security Lab

## Overview

This project demonstrates the design, deployment, attack simulation, monitoring, and defense of a small enterprise-style Linux infrastructure using multiple servers and security controls.

A real attacker (Kali Linux) performs SSH brute-force attacks against production servers. Centralized logging, investigation, and automated blocking (Fail2ban + nftables firewall) are used to detect and stop the attack.

This lab simulates how a real SOC / Linux infrastructure team protects servers in production.

---

## Lab Architecture

Enterprise lab running on Hyper-V:

- Fedora Workstation (Admin / Analyst)
- Kali Linux (Attacker)
- monitor01 (Security + Fail2ban)
- log01 (Central log server)
- web01 (Production web server)
- backup01 (Backup server)

---

## What Was Built

- Multi-VM enterprise network in Hyper-V
- Centralized SSH log collection
- Hardened SSH configuration
- Attack simulation from Kali Linux
- Log investigation and correlation
- Automated banning using Fail2ban
- Firewall enforcement using nftables
- Validation that attacker is permanently blocked

---

## Attack Simulation

- Kali Linux performs SSH brute-force attempts against servers
- Failed logins appear in:
  - monitor01
  - log01
- Evidence is captured in Phase 7 and Phase 8 screenshots

---

## Detection & Investigation

- Used grep and journalctl to:
  - Identify attacker IP
  - Count failures
  - Verify which servers were targeted
- Confirmed attack patterns and timeline

---

## Defense Implementation

- Fail2ban enabled on monitor01
- SSH jail configured
- After repeated failures:
  - Attacker IP is banned automatically
  - nftables firewall blocks port 22 at kernel level

---

## Final Result

- Attacker is permanently blocked
- SSH is protected automatically
- Firewall enforcement is active
- Enterprise environment continues running normally

Proof:
- Phase 9: nftables firewall rules
- Phase 10: All VMs running in Hyper-V

---

## Skills Demonstrated

- Linux system administration
- Enterprise infrastructure design
- SSH hardening
- Centralized logging
- Incident investigation
- Blue team response workflow
- Fail2ban automation
- Firewall enforcement (nftables)
- Real-world SOC-style thinking

---

## Screenshots

See `screenshots/` folder for:

- Phase 7: Attack evidence & investigation
- Phase 8: Baseline before blocking
- Phase 9: Automatic firewall blocking
- Phase 10: Enterprise environment proof

---

## Why This Matters

This project shows real-world skills:

- How attacks are detected
- How defenders investigate them
- How defenses are automated
- How enterprise Linux servers are protected at scale
