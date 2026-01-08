# Project 15: OpenVPN Remote Access Lab

## 🎯 Objective

Deploy a secure OpenVPN server on a Linux system and connect a Kali Linux client using certificate-based authentication. This simulates real-world secure remote access into an internal network, similar to enterprise and SOC environments.

---

## 🧪 Lab Environment

- **OpenVPN Server:** Ubuntu / Debian (soc01)
- **Client:** Kali Linux
- **Virtualization:** VirtualBox
- **Networking:** Host-Only + NAT
- **VPN Network:** 10.8.0.0/24

---

## 🛠️ What Was Implemented

- Installed and configured OpenVPN server
- Built PKI and generated certificates
- Created client configuration file (`.ovpn`)
- Connected Kali Linux to the VPN
- Verified tunnel interface (`tun0`)
- Verified secure connectivity to VPN gateway (`10.8.0.1`)
- Confirmed encrypted tunnel is operational

---

## 📸 Evidence

### 1️⃣ OpenVPN Server Running

![OpenVPN Server Running](screenshots/01-openvpn-server-running.png)

---

### 2️⃣ Kali Connected (tun0 Interface)

![Kali tun0](screenshots/02-kali-connected-tun0.png)

---

### 3️⃣ Kali Can Ping VPN Gateway

![Ping VPN](screenshots/03-kali-ping-vpn.png)

---

### 4️⃣ OpenVPN Connection Log

![OpenVPN Log](screenshots/04-openvpn-connection-log.png)

---

## 🧠 Skills Demonstrated

- VPN deployment & administration
- Linux networking
- Secure remote access architecture
- PKI & certificate management
- Tunnel interfaces (`tun`)
- Infrastructure security concepts
- SOC / SysAdmin real-world practices

---

## 🏢 Why This Matters

VPN infrastructure is critical in:

- SOC environments
- Secure remote administration
- Internal enterprise networks
- Cloud and hybrid infrastructure
- Incident response access

This project demonstrates real-world secure remote access implementation used in production environments.

