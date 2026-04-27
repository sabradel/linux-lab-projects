# Project 30: SOC Attack Investigation Lab

## Overview
This project demonstrates a full SOC (Security Operations Center) workflow by simulating real-world attacks and analyzing them using Wazuh SIEM.

## Lab Environment
- Kali Linux (Attacker)
- file01 Linux Server (Monitored Endpoint)
- Wazuh Server (SIEM)
- Linux Mint MacBook (SOC Workstation)
- Tailscale Private Network

## Objectives
- Simulate brute-force attacks
- Detect failed and successful logins
- Investigate attacker behavior
- Analyze alerts in Wazuh dashboard
- Understand lateral movement and privilege escalation

## Project Structure
- README.md → Project explanation
- notes/ → Investigation notes
- screenshots/ → Evidence and proof

## Setup Evidence

### Project Folder Structure

![Project Structure](screenshots/01-project-folder-structure.png)

## Scenario 1: SSH Brute-Force Attempt Against Wazuh Server

### Goal
Simulate repeated failed SSH login attempts from Kali Linux against the Wazuh server and investigate the activity from the SOC workstation.

### Attacker
- Kali Linux
- Tailscale IP: `100.114.38.83`

### Target
- Wazuh server
- Tailscale IP: `100.100.30.98`

### Expected Detection
- Failed password attempts in `/var/log/auth.log`
- Repeated attempts from the same source IP
- Fail2Ban blocking the attacker after multiple failures
- Wazuh security events showing the activity
### Log Analysis (auth.log)

The failed login attempts were confirmed in the system authentication logs. Multiple invalid usernames were used by the attacker.

#### Key Findings
- Repeated failed login attempts
- Multiple usernames tested (`fakeuser`, `admin`)
- Same attacker IP: `100.114.38.83` (Kali Linux attacker via Tailscale)

#### Evidence

![Auth Log Failed Passwords](screenshots/06-authlog-failed-passwords.png)

### Timeline Analysis

A detailed review of the authentication logs shows the sequence of attacker activity from the same IP address.

#### Observations
- Initial successful login using a valid account (`adel`)
- Followed by multiple failed login attempts
- Attempts using different usernames (`fakeuser`, `admin`)
- Repeated connections and disconnections

#### Evidence

![Attack Timeline](screenshots/07-attack-timeline.png)

### SOC Analyst Conclusion

During this investigation, a brute-force attack was identified targeting the Wazuh server via SSH.

The attacker, originating from IP `100.114.38.83` (Kali Linux over Tailscale), performed multiple failed login attempts using different usernames such as `fakeuser` and `admin`. This behavior is consistent with credential guessing techniques.

The logs show that the attacker also successfully authenticated using a valid account (`adel`) before continuing further attempts. This indicates a potential risk of unauthorized access and lateral movement within the environment.

Fail2Ban responded by temporarily blocking the attacker IP after repeated failures, demonstrating effective automated defense mechanisms.

Based on the observed activity, this event can be classified as a **brute-force and credential abuse attempt**, potentially leading to unauthorized access if not mitigated.

### Recommendations

- Disable password authentication and enforce SSH key-based login
- Implement multi-factor authentication (MFA)
- Monitor repeated login attempts across all systems
- Strengthen password policies
- Regularly review authentication logs and SIEM alerts

#### Evidence

![SOC Conclusion](screenshots/08-soc-analyst-conclusion.png)


## Scenario 2: SSH Attack on Monitored Endpoint (file01)

### Goal
Simulate an SSH attack from Kali Linux against a monitored endpoint (file01) and detect the activity through Wazuh SIEM.

### Attacker
- Kali Linux
- Tailscale IP: `100.114.38.83`

### Target
- file01 Linux server
- Tailscale IP: `100.120.60.48`

### Expected Detection
- Failed SSH login attempts on file01
- Wazuh alerts showing authentication failures
- Identification of attacker IP in SIEM logs
