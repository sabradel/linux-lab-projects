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

## Step 3: Logging Baseline on Ubuntu Server

### Objective
Establish a logging baseline on the target system so that security-relevant
events can be observed, analyzed, and correlated.

### Why Logging Matters in SOC
Logs are the primary data source for SOC analysts.
Without logs:
- Attacks cannot be detected
- Incidents cannot be reconstructed
- Alerts have no context

### Logging Scope
This lab focuses on core Linux logs commonly monitored by SOC teams:
- Authentication activity
- User privilege changes
- Network service events
- System messages

### Key Log Files
- /var/log/auth.log
  Records:
    - SSH login attempts
      - sudo usage
        - Authentication failures and successes

        - /var/log/syslog
          Records:
            - General system activity
              - Service start/stop events
                - Network-related messages

                ### Baseline Principle
                Before simulating attacks, a baseline of normal system behavior
                must be understood. This allows abnormal activity to stand out.

                ### Immutable Consideration
                Logging configuration is defined once in the system build.
                If logging requirements change, the server is rebuilt rather than modified live.
                


## Step 4: SSH Authentication Visibility and Event Generation

### Objective
Generate controlled SSH authentication events and observe how they
are recorded in system logs. This step teaches how SOC analysts
differentiate between normal administrative access and suspicious activity.

### SOC Relevance
SSH is one of the most targeted services on Linux systems.
SOC analysts routinely monitor SSH logs to detect:
- Brute-force attempts
- Unauthorized access
- Credential abuse
- Lateral movement

### Normal vs Suspicious Behavior

Normal behavior includes:
- Successful SSH logins from known internal IPs
- Occasional failed login followed by success
- Use of non-root administrative accounts

Suspicious behavior includes:
- Repeated failed login attempts
- Login attempts for non-existent users
- Authentication attempts from unexpected IPs
- Root login attempts

### Log Source
All SSH authentication activity is recorded in:
- /var/log/auth.log

### Event Types Observed
- Successful SSH login
- Failed SSH login
- Invalid user attempts
- sudo privilege usage after login

### Detection Mindset
SOC analysts do not stop attacks — they detect and report them.
This lab focuses on visibility, not prevention.

### Immutable Principle
No SSH configuration changes are made during analysis.
If SSH policies require changes, the system is rebuilt from the golden image.


## Step 5: Simulated Brute-Force Behavior and Log Pattern Recognition

### Objective
Simulate controlled brute-force-like SSH behavior and analyze how
repeated authentication failures appear in system logs.
This step builds the foundation for SOC alert detection logic.

### SOC Relevance
Brute-force attacks against SSH are one of the most common
threats observed in SOC environments.

SOC analysts look for:
- High frequency failed login attempts
- Repeated failures from a single source IP
- Attempts against multiple usernames
- Authentication failures without successful login

### Attack Simulation (Controlled)
The activity performed in this lab simulates attacker behavior
without exploiting vulnerabilities or causing harm.
This is strictly for detection and learning purposes.

### Indicators of Brute-Force Activity
Patterns that may indicate brute-force attempts:
- Multiple "Failed password" entries within a short time window
- Repeated attempts for the same or different users
- Consistent source IP address
- No corresponding successful login

### Log Source
Brute-force indicators are recorded in:
- /var/log/auth.log

### SOC Detection Logic
A SOC analyst would typically:
- Count failed authentication attempts
- Correlate failures by source IP
- Apply thresholds (e.g., >10 failures in 1 minute)
- Escalate as a potential brute-force incident

### Analyst Outcome
This activity would be documented as:
- Suspicious authentication behavior
- Potential SSH brute-force attempt
- Medium to high severity depending on frequency

### Immutable Principle
No defensive changes are applied during detection.
Blocking or hardening actions require rebuilding the image.


### Detection Note
Initial searches for exact "Failed password" strings may return no results
due to variations in SSH logging formats on Ubuntu 24.04.

SOC analysis requires flexible pattern matching across:
- "failed"
- "invalid user"
- "authentication failure"
- PAM-related messages

Detection logic should focus on behavior patterns rather than exact strings.

