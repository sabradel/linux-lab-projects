# OpenVPN Server Configuration

## server.conf
Location: /etc/openvpn/server/server.conf

Configuration highlights:
- Protocol: UDP 1194
- Bind IP: 192.168.56.109 (Host-Only)
- Tunnel Network: 10.8.0.0/24
- Certificates: easy-rsa PKI
- Logging: /var/log/openvpn.log

## Service Management

Enable and start service:
sudo systemctl enable openvpn-server@server
sudo systemctl start openvpn-server@server

Verify status:
sudo systemctl status openvpn-server@server

Expected output:
Active: active (running)
Status: Initialization Sequence Completed
