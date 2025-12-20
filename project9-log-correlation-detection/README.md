# Project 9: Log Correlation & Detection

## Objective
Demonstrate basic log correlation and detection techniques using Linux servers and Kali Linux for SOC-style analysis.

## Lab Overview
- Ubuntu Server acts as the log-generating system
- Kali Linux acts as the analyst/attacker/tester machine
- Simulate authentication events, failures, and suspicious activity
- Collect logs, correlate events, and detect anomalies

## Technology Used
- Ubuntu Server 24.04 LTS
- Kali Linux
- Linux command-line tools (`journalctl`, `grep`, `awk`, `wc`)
- Optional: Syslog configuration for log forwarding

## Step 2: Authentication Event Simulation

### Objective
Simulate common authentication events to generate realistic security logs
for SOC-style detection and analysis.

### Events Generated
The following authentication-related events were intentionally created
on the Ubuntu server:

- Invalid user login attempt
- Failed password attempts for a valid user
- Successful privilege escalation using sudo

### Why This Matters (SOC Perspective)
These events are commonly monitored in Security Operations Centers to detect:
- Brute-force attacks
- Unauthorized access attempts
- Privilege escalation activity
- Insider threat behavior

### Log Sources
Authentication events are recorded in:
- systemd journal
- SSH authentication logs
- sudo command audit trails

### Detection Value
Repeated failed logins followed by a successful privilege escalation may
indicate:
- Credential guessing
- Compromised user credentials
- Lateral movement preparation

