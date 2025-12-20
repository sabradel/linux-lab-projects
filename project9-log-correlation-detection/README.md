# Project 9: Log Correlation & Detection

## Objective
Demonstrate basic log correlation and detection techniques using Linux systems,
simulating real-world authentication events commonly monitored by Security
Operations Centers (SOC).

## Lab Overview
- Ubuntu Server acts as the log-generating target system
- Kali Linux acts as the attacker, tester, and analyst workstation
- Authentication events are deliberately generated
- Logs are collected, correlated, and analyzed for suspicious behavior

## Technology Used
- Ubuntu Server 24.04 LTS
- Kali Linux
- Linux command-line tools:
  - journalctl
  - grep
  - awk
  - wc
- (Optional) Syslog for centralized log forwarding

---

## Step 2: Authentication Event Simulation

### Objective
Generate realistic authentication and privilege escalation events to produce
security logs suitable for SOC-style detection and analysis.

### Events Simulated
The following events were intentionally generated on the Ubuntu server:

- Invalid user login attempts
- Failed password attempts for valid users
- Successful privilege escalation using sudo

### SOC Relevance
These events are routinely monitored in Security Operations Centers to detect:

- Brute-force login attempts
- Unauthorized access attempts
- Privilege escalation activity
- Potential insider threat behavior

### Log Sources
Authentication and authorization events were collected from:

- systemd journal
- SSH authentication logs
- sudo command audit trails

### Detection Insight
Patterns such as repeated failed logins followed by successful privilege
escalation may indicate:

- Credential guessing attacks
- Compromised user accounts
- Preparation for lateral movement

