# Centralized Logging SOC Lab

## Goal
Build a centralized logging server using rsyslog that collects logs from multiple Linux systems in an isolated lab network and simulates real SOC log ingestion and incident response scenarios.

## Lab Topology

log01           = 10.10.10.30  (Central Log Server)
monitor01       = 10.10.10.40  (Monitor Server)
backup01        = 10.10.10.20  (Backup Server)
fedora-wrk01    = 10.10.10.10  (Admin Workstation)
kali01          = 10.10.10.50  (Attacker)

All systems are connected to an internal Hyper-V switch (LabSwitch).

---

# Phase 1 – Central Log Server Setup (log01)

- Installed rsyslog
- Enabled TCP and UDP log listeners on port 514
- Created directory:

  /var/log/remote/

- Configured rsyslog to store logs per-host in:

  /var/log/remote/<hostname>/

- Restarted rsyslog service
- Verified service is listening on port 514
- Tested local logging using:

  logger "HELLO FROM LOG01 SOC LAB"

---

# Phase 2 – Client Log Forwarding (monitor01)

- Installed rsyslog on monitor01
- Configured rsyslog to forward logs to:

  10.10.10.30:514

- Restarted rsyslog
- Sent test log using:

  logger "HELLO FROM MONITOR01 SOC LAB"

- Verified logs appeared on log01 under:

  /var/log/remote/monitor01/

- Sample log entry:

  2026-01-23T05:03:10+00:00 monitor01 ash: HELLO FROM MONITOR01 SOC LAB

---

# Phase 3 – Backup Server Logging (backup01)

- Installed rsyslog on backup01
- Configured rsyslog to forward logs to log01
- Restarted rsyslog
- Sent test log using:

  logger "HELLO FROM BACKUP01 SOC LAB"

- Verified on log01 using:

  ls /var/log/remote
  grep -R "HELLO" /var/log/remote/

- Logs confirmed under:

  /var/log/remote/backup01/

---

# Phase 4 – Multi-Client Log Ingestion Verification

- Confirmed monitor01 and backup01 both send logs to log01
- Verified directories:

  /var/log/remote/monitor01/
  /var/log/remote/backup01/

- Used logger on both systems to generate test logs
- Confirmed centralized collection is working correctly

---

# Incident: Hyper-V VM State Corruption & Recovery

## Incident Summary

- Hyper-V checkpoint / state file corruption occurred
- All VMs failed to boot due to missing .vmgs files
- Error example:

  The system cannot find the file specified (.vmgs)

## Recovery Actions

- Identified that VHDX disks were intact
- Removed broken VM objects (without deleting disks)
- Re-created VMs and re-attached existing VHDX disks
- Disabled checkpoints permanently
- Reconfigured VM firmware and boot settings
- Successfully restored all systems:

  log01, monitor01, backup01, web01, fedora-wrk01, kali01

## Result

- Zero data loss
- All SOC lab services restored
- Logging infrastructure remained fully intact

This simulates a real enterprise virtualization disaster recovery scenario.

---

# Phase 5 – Attacker Log Ingestion (kali01)

- Installed rsyslog on kali01
- Configured rsyslog to forward logs to log01 over TCP 514
- Restarted rsyslog
- Sent test log using:

  logger "HELLO FROM KALI01 SOC LAB"

- Verified logs appeared on log01 under:

  /var/log/remote/kali01/

- Confirmed attacker machine activity is now visible in centralized logs

---

# Final Result

This lab demonstrates:

- Centralized Linux logging architecture
- Multi-client log ingestion
- SOC-style log verification
- Incident recovery of a broken virtualization platform
- Attacker activity being logged and centrally collected

This simulates a real enterprise SOC logging and infrastructure recovery environment.


# Phase 10 — Final Validation (SOC Proof)

## Evidence Collected
Screenshots saved in:
- screenshots/phase10/

## Commands Used (Final Proof)

### On log01 (prove attack logs exist)
sudo ls -lah /var/log/remote
sudo grep -R "Failed password" /var/log/remote/ | head -n 20
sudo grep -R "10.10.10.50" /var/log/remote/ | head -n 20

### On monitor01 (prove auto-blocking works)
sudo fail2ban-client status sshd

### On kali01 (prove attacker is blocked)
ssh ash@10.10.10.40

