# Network Plan (Host-Only + NAT)

## Server Interfaces (Ubuntu Wazuh Server)
- Host-Only: 192.168.56.109/24 (enp0s3)
- NAT: 10.0.3.15/24 (enp0s8)
- Default route: via 10.0.3.2 (NAT)

## VPN Design
- VPN Software: OpenVPN
- VPN Port: UDP 1194
- VPN Server Bind: 192.168.56.109 (Host-Only interface)
- VPN Tunnel Network: 10.8.0.0/24

## Clients
- Kali Linux: OpenVPN client -> connects to 192.168.56.109:1194
- Windows: OpenVPN client -> connects to 192.168.56.109:1194

## Notes
- NAT stays enabled for package installs/updates.
- Host-Only is used for lab connectivity and VPN access.
- Wazuh monitoring will be added for OpenVPN logs/auth events.
