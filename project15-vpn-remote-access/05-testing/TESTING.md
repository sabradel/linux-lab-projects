# VPN Testing

## Kali Client Connection

- Client successfully connects to VPN server.
- Tunnel interface: tun0
- Assigned IP: 10.8.0.6

## Verification

Ping VPN server inside tunnel:
ping 10.8.0.1

Result:
- 0% packet loss
- Stable latency

Interface check:
ip a | grep tun -A3
