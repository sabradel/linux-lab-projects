# Project 25 – Central Logging with rsyslog (Client → Log Server)

Goal: Configure log-server01 to receive syslog events from Pop!_OS and store them centrally.

## Lab
- Log Server: log-server01 (Ubuntu Server) – 192.168.1.200
- Client: Pop!_OS workstation – 192.168.1.115

## Proof Screenshots
1) Server listening on port 514 (TCP/UDP)
2) Firewall rules (UFW)
3) Client rsyslog forwarding config
4) Test log sent from client
5) Log received on server (file evidence)
