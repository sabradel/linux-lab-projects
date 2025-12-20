# Project 10: Advanced Log Correlation & Detection

## Objective
Show how a SOC analyst detects suspicious activity by correlating Linux authentication logs.

## Lab Setup
- Ubuntu Server: Log source
- Kali Linux: Attacker / testing machine
- Both machines are on the same internal network

## Tools Used
- Ubuntu Server 24.04
- Kali Linux
- journalctl
- grep
- awk
- wc

## What This Project Demonstrates
- Failed login detection
- Invalid user detection
- Privilege escalation tracking
- Basic log correlation (SOC Tier 1 skill)

## Lab Status
This project documents simulated attacks and log analysis performed in a controlled lab environment.


## Step 3: Log Extraction and Correlation

### Objective
Extract and correlate authentication-related logs to identify suspicious
activity patterns from a SOC analyst perspective.

### Log Evidence Collected
The following security-relevant events were identified on the Ubuntu server:

- Invalid user login attempts
- Failed authentication attempts
- Successful privilege escalation via sudo

### Detection Commands Used
```bash
journalctl | grep -i "failed password"
journalctl | grep -i "invalid user"
journalctl | grep -i "sudo"
