# Project 7: Immutable Infrastructure on Linux

## Objective
Demonstrate an immutable infrastructure model using Linux where servers
are never modified after deployment. All changes are introduced by
rebuilding and redeploying golden images.

## Why Immutable Infrastructure
Traditional Linux administration relies on SSH-based changes, which can
lead to configuration drift, security risks, and slow recovery.

Immutable infrastructure improves:
- Security (no live changes)
- Consistency (no configuration drift)
- Incident response (replace instead of repair)
- Auditability (versioned builds)

## Lab Overview
- Build a single Ubuntu Server golden image
- Apply base configuration and security hardening
- Disable SSH access in production
- Clone immutable servers from the image
- Simulate failure and replace servers instead of fixing them

## Technology Used
- Ubuntu Server 24.04 LTS
- VirtualBox
- Linux system administration tools

## Outcome
This project demonstrates a modern Linux infrastructure mindset aligned
with cloud, DevOps, and SOC operational practices.

---

## Step 1: Golden Image Creation

### Objective
Create a hardened Ubuntu Server that will act as a **golden image**.
This image will never be modified after deployment.

### Principles Applied
- No manual changes after deployment
- All servers are replaceable
- Configuration is reproducible and auditable

### Base System
- OS: Ubuntu Server 24.04 LTS
- Hypervisor: VirtualBox
- Role: Golden Image (immutable)

---

## Step 2: SSH and Network Policy (Immutable Design)

### SSH Policy
- SSH is enabled only for:
  - Initial validation
  - Controlled administrative access
- SSH is **not used for live troubleshooting**
- Root SSH login is disabled
- Administrative access is done via a non-root sudo user

### Network Policy
- Default-deny firewall posture
- Only required ports are allowed
- No ad-hoc port opening
- Firewall rules are defined once in the golden image

### Immutable Rule
If SSH access, firewall rules, or network configuration need changes:
➡️ The server is **rebuilt**, not fixed.

---

## Step 4: User Management and SSH Hardening

### Objective
Define a secure administrative access model for the golden image.
All access is controlled, auditable, and reproducible.

### Administrative Users
- A primary administrative user exists in the image
- Root login is disabled for SSH
- Privileged actions require sudo

### User Creation (Golden Image Phase)

The administrative user was created during image preparation:

```bash
sudo adduser adelyahaya
sudo usermod -aG sudo adelyahaya

---

## Step 5: Firewall and Base Service Hardening

### Objective
Harden the golden image by restricting network access and minimizing exposed services.

### Firewall Configuration
- Default-deny for all incoming connections
- Only required ports are allowed
- Example for enabling SSH temporarily during image preparation:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable



---

## Step 6: Cloning Immutable Servers

### Objective
Deploy multiple servers from the golden image without modifying them manually.

### Cloning Procedure (VirtualBox Example)
1. Shutdown the golden image VM.
2. Clone the VM using VirtualBox GUI or CLI:

```bash
VBoxManage clonevm "Golden-Image" --name "Immutable-Server-1" --register
VBoxManage clonevm "Golden-Image" --name "Immutable-Server-2" --register


---

## Step 7: Simulate Failure and Replace a Server

### Objective
Demonstrate recovery and immutable workflow when a server fails.

### Procedure
1. Simulate a server failure (example: stop the VM):

```bash
VBoxManage controlvm "Immutable-Server-1" poweroff
