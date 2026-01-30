# Threat Modeling – Linux Attacker Behaviors

## Threat Focus
This project focuses on common post-compromise attacker behaviors on Linux systems.

### Selected ATT&CK Techniques
- T1110 – Brute Force (SSH)
- T1053 – Scheduled Task / Cron Persistence
- T1068 – Privilege Escalation

## Attacker Objectives
- Gain initial access via SSH
- Enumerate system and users
- Escalate privileges
- Establish persistence

## Defender Goal
Detect attacker behavior early using log correlation and behavioral detections rather than single events.
