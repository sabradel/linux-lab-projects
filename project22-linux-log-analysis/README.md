# Project 22: Linux Log Analysis & Suspicious Command Detection

## Objective
Demonstrate SOC-style analysis of suspicious Linux command activity using Wazuh logs.

## Lab Environment
- Wazuh Manager: soc01
- Linux Endpoint: linux01

## Threat Activity
The Linux endpoint executed commands commonly associated with post-compromise activity.

## Detection & Analysis
Wazuh collected and analyzed system logs, identifying suspicious command execution.

## Evidence

1. **Agent Connected**
   - `screenshots/01-agent-connected.png`

2. **Suspicious Activity Detected**
   - `screenshots/02-priv-esc-detected.png`

3. **Root Shell Observed**
   - `screenshots/03-root-shell.png`

## Outcome
- Detected suspicious Linux behavior
- Correlated activity to privilege escalation techniques

## Skills Demonstrated
- Linux log analysis
- Wazuh alert review
- SOC-style investigation
