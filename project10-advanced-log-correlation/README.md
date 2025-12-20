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


## Step 4: Detection Logic and Alert Criteria

### Objective
Define detection logic that converts authentication logs into actionable
security alerts from a SOC Tier 1 perspective.

### Detection Conditions
An alert would be triggered if the following conditions are observed
within a short time window:

- Multiple failed authentication attempts for one or more users
- Login attempts using non-existent user accounts
- A successful sudo privilege escalation following failed logins

### Alert Severity
- Severity Level: Medium
- Escalation Required: Yes (Tier 2 review)

### Alert Rationale
This activity pattern may indicate:
- Brute-force or credential-guessing attempts
- Account compromise
- Unauthorized privilege escalation

### SOC Response Recommendation
- Review source IP addresses
- Validate affected user accounts
- Confirm legitimacy of sudo activity
- Monitor for additional suspicious behavior
