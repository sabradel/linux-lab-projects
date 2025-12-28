# Project 13: Suricata IDS – Detection & Alert Validation

## Objective
Set up Suricata IDS in a lab environment and confirm it can detect network activity and generate security alerts.

## Lab Setup
- Kali Linux (Suricata IDS sensor)
- Ubuntu Linux (Traffic generator / victim)
- VirtualBox Host-only networking

## What I Did
- Installed and configured Suricata IDS on Kali Linux
- Enabled custom detection rules using local.rules
- Created a custom rule to detect network activity
- Generated test traffic from an Ubuntu machine
- Verified alerts were generated in Suricata fast.log
- Tuned alerts by identifying and disabling noisy signatures
- Learned that IDS traffic must pass through the monitored interface to be detected

## Evidence
This folder includes screenshots showing:
- Suricata configuration validation
- Custom rule enabled
- ICMP traffic generated from Ubuntu
- Alerts successfully logged in fast.log

## Skills Demonstrated
- Intrusion Detection Systems (IDS)
- SOC alert analysis
- Custom rule creation
- Network traffic monitoring
- Linux log analysis
