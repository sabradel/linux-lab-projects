# Phase 1 - Infrastructure Build

## Machines (Current)

- fedora-wrk01 (Fedora Workstation) - Admin / Management
- web01 (Ubuntu Server) - Web / App Server
- backup01 (Ubuntu Server) - Backup Server
- log01 (Ubuntu Server) - Log Server
- monitor01 (Ubuntu Server) - Monitoring Server
- kali-attack (Kali Linux) - Attack / Security Testing

## Network

- Hyper-V Virtual Network: Default Switch
- All machines are in the same subnet and can:
  - Ping each other
  - Be accessed via SSH from Fedora

## Proof Commands Used

On servers:
- `ip a`

From Fedora:
- `ping <server-ip>`
- `ssh <user>@<server-ip>`

## Current Status

✅ SSH working to:
- web01  
- backup01  
- log01  
- monitor01  

✅ Kali Linux deployed for attack simulation
'
