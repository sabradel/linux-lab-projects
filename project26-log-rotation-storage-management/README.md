# Project 26 – Log Rotation & Storage Management (Log Server Hardening)

Goal: Prevent disk exhaustion by rotating and compressing centralized logs stored under `/var/log/remote/`.

## Lab
- Log Server: log-server01 (Ubuntu Server) – 192.168.1.200
- Client: Pop!_OS workstation – 192.168.1.115

## Proof Screenshots
1. Remote log folder size before rotation
2. logrotate version
3. logrotate config file
4. Dry-run test output
5. Force-run output
6. Rotated/compressed logs proof
7. Disk usage after

## Proof Screenshots

| Step | Screenshot |
|------|------------|
| Remote log folder size before rotation | ![](screenshots/01-remote-log-size-before.png) |
| Logrotate version | ![](screenshots/02-logrotate-version.png) |
| Logrotate config file | ![](screenshots/03-logrotate-config-file.png) |
| Dry run test | ![](screenshots/04-logrotate-dry-run.png) |
| Force run execution | ![](screenshots/05-logrotate-force-run.png) |
| Rotated/compressed logs proof | ![](screenshots/06-rotated-logs-proof.png) |
| Disk usage after | ![](screenshots/07-disk-usage-after.png) |
