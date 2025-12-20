# Project 9: Log Correlation & Detection

### Professional Summary
This project demonstrates foundational SOC skills by simulating authentication events on a Linux server and analyzing them from an attacker/analyst perspective using Kali Linux. 

It highlights:
- Event generation (failed logins, invalid users, privilege escalation)
- Correlation and detection techniques
- SOC-style alert creation and response decision-making
- Log investigation using Linux command-line tools

The project provides hands-on experience relevant to SOC analyst and cybersecurity roles, emphasizing **detection, incident response, and documentation**.


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

---

## Step 4: Detection Logic & Analyst Interpretation

### Objective
Analyze authentication logs using Linux command-line tools to detect
suspicious activity patterns and correlate them to potential security
incidents.

### Detection Techniques
- Count failed logins by user and by source IP
- Identify invalid user login attempts
- Detect privilege escalation events following authentication failures

### Sample Findings
- Multiple failed login attempts from the same IP could indicate a
  brute-force attack
- Invalid user attempts suggest scanning or reconnaissance activity
- Successful `sudo` usage after multiple failures may indicate
  credential compromise

### SOC Analyst Insight
By correlating these events, a SOC analyst can:

- Quickly spot compromised accounts
- Determine attack patterns
- Prioritize incidents for further investigation

---

## Step 5: Simulated SOC Alerting & Response

### Objective
Simulate how a SOC analyst would generate alerts and determine response
actions based on correlated authentication events.

### Alert Conditions
An alert would be triggered when the following conditions are observed:

- Multiple failed authentication attempts
- Invalid user login activity
- Successful privilege escalation after failures

### Alert Severity
**Medium to High**

The presence of repeated failures followed by successful sudo access
suggests potential credential compromise.

### Analyst Response Actions
A SOC analyst would typically:

- Flag the affected user account
- Review source IP reputation
- Recommend password reset or account lockout
- Escalate to Tier 2 for further investigation if needed

### SOC Value
This process demonstrates detection-to-response thinking, a core skill
for Security Operations Center roles.


### Key Skills Demonstrated
- Linux system administration
- Log correlation and event analysis
- SOC alert generation and severity assessment
- Command-line log investigation (`journalctl`, `grep`, `awk`, `wc`)
- Incident response planning and documentation


### Optional: Event Correlation Workflow Diagram

Ubuntu Server → Logs Generated
       |
       v
Event Collection (journalctl / syslog)
       |
       v
Detection & Alert Analysis
       |
       v
SOC Response Recommendation
