# Centralized Logging SOC Lab

## Goal
Build a centralized logging server using rsyslog that collects logs from multiple Linux systems.

## Lab Topology

log01      = 10.10.10.30  (Log Server)
monitor01  = 10.10.10.40  (Monitor Server)
backup01   = 10.10.10.20  (Backup Server)
fedora-wrk01 = 10.10.10.10 (Admin PC)
kali01     = 10.10.10.50  (Attacker)

## Phase 1 — Log Server (log01)

- Installed rsyslog
- Verified rsyslog service is running
- Opened port 514 TCP/UDP
- Created folder /var/log/remote
- Configured rsyslog to store logs per host
- Restarted rsyslog
- Tested logging using logger command


# Phase 2 - Client Log Forwarding (monitor01)

Installed rsyslog on monitor01
Configured rsyslog to forward logs to log01 (10.10.10.30)
Restarted rsyslog on monitor01
Sent test log using logger command
Verified logs appeared on log01 under /var/log/remote/monitor01/

### Proof

- Verified monitor01 logs arrived at log01
- Log file path:
/var/log/remote/monitor01/ash.log

- Sample log entry:
2026-01-23T05:03:10+00:00 monitor01 ash: HELLO FROM MONITOR01 SOC LAB


## Phase 3 — Backup Server Logging (backup01)

- Installed rsyslog on backup01
- Configured forwarding to log01
- Restarted rsyslog
- Sent test log using logger
- Verified logs arrived in:

/var/log/remote/backup01/


# Phase 3 — Multi-Client Log Ingestion

- Configured rsyslog on monitor01 to forward logs to log01
- Verified logs arrived under /var/log/remote/monitor01/
- Configured rsyslog on backup01 to forward logs to log01
- Verified logs arrived under /var/log/remote/backup01/
- Used logger command on both systems to generate test logs
- Confirmed centralized collection is working

Proof commands used:

On clients:
logger "HELLO FROM MONITOR01 SOC LAB"
logger "HELLO FROM BACKUP01 SOC LAB"

On log01:
ls /var/log/remote
grep -R "HELLO" /var/log/remote/


# Recovery Event (Hyper-V)

- Hyper-V checkpoint/state corruption occurred
- All VMs failed to boot due to missing .vmgs files
- Recovered all VMs by re-attaching existing VHDX disks
- No data or configuration was lost
- Disabled checkpoints permanently

This simulates a real enterprise virtualization recovery scenario.


