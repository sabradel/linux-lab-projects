# Project 8: SOC Fundamentals Lab (Linux + Kali)

## Objective
Build a beginner-friendly SOC-style lab to practice detection,
logging, and basic incident investigation using Linux systems.

## Lab Scope
This project simulates a small environment where:
- Kali Linux acts as an attacker
- Ubuntu Server acts as a monitored target
- Activity is logged and analyzed instead of manually fixing issues

## Threat Model
The lab focuses on detecting:
- Network reconnaissance (ping, scanning)
- Unauthorized login attempts
- Suspicious process and network activity

## SOC Mindset Applied
- Observe before acting
- Logs over assumptions
- Detect, document, respond
- No “quick fixes” without evidence

## Technology Used
- Kali Linux
- Ubuntu Server
- Linux command-line tools
- VirtualBox internal networking

## Expected Outcome
By the end of this project, the system will:
- Log suspicious activity
- Allow basic investigation using logs
- Demonstrate SOC analyst thinking on Linux systems


## Step 2: Network Architecture & Visibility

### Network Design
This lab uses a simple flat internal network to allow full visibility
between systems while preventing exposure to the host or internet.

### Network Layout
- Network Type: VirtualBox Internal Network
- Subnet: 192.168.56.0/24
- Gateway: None (isolated lab)
- DNS: Not required

### System Roles and IP Addresses
- Kali Linux (Attacker / Tester): 192.168.56.104
- Ubuntu Server (Target / Monitored): 192.168.56.103

### Communication Rules
- Kali Linux can initiate traffic to Ubuntu Server
- Ubuntu Server can respond to traffic
- No external internet access is required for detection activities

### SOC Visibility Principle
Flat networks increase visibility and simplify log correlation.
This allows analysts to focus on detection rather than routing issues.

### Verification
Bi-directional ICMP (ping) communication confirms:
- Network connectivity
- Correct IP addressing
- Proper lab isolation

