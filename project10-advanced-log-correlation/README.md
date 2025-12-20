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


## Step 5: Incident Summary (SOC Perspective)

### Incident Title
Suspicious Authentication Activity with Privilege Escalation

### Incident Description
The Ubuntu server generated multiple authentication-related security
events, including invalid user login attempts and failed password
entries. Shortly after these failures, a successful sudo privilege
escalation was observed.

### Timeline Summary
- Multiple failed login attempts detected
- Invalid user authentication attempts recorded
- Successful sudo access achieved by a valid user

### Impact Assessment
No confirmed system compromise was detected. However, the activity
pattern suggests potential credential abuse or unauthorized access
attempts.

### Actions Taken
- Authentication logs reviewed
- Event correlation performed
- System integrity verified

### Recommended Next Steps
- Continue monitoring authentication activity
- Enforce stronger authentication controls
- Review user access privileges


## Project Outcome and Skills Demonstrated

This project demonstrates hands-on SOC-style log analysis and incident
handling using native Linux tools.

### Skills Demonstrated
- Authentication log analysis using journalctl and auth logs
- Detection of suspicious login and privilege escalation activity
- Correlation of multiple security events into a single incident
- SOC-style incident documentation and reporting
- Linux security monitoring fundamentals

### SOC Relevance
The activity simulated in this project mirrors real-world Tier 1 SOC
alerts related to brute-force attempts, unauthorized access, and
privilege escalation.

This project demonstrates the ability to move beyond command execution
and into security analysis, investigation, and communication.
