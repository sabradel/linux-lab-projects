# Project 4: Firewall Hardening with UFW

## Objective
Secure the Ubuntu system using UFW by allowing only necessary services and blocking all others.

## Steps Taken

1. Set default policies to deny all incoming and allow outgoing.
2. Allowed SSH access on port 2222 (instead of default 22) for better security.
3. Allowed HTTP (port 80) and HTTPS (port 443) for web services.
4. Enabled UFW logging.
5. Enabled UFW to enforce rules.

## Commands Used

```bash
# Set default policies
sudo ufw default deny incoming
sudo ufw default allow outgoing

# Allow SSH on a custom port
sudo ufw allow 2222/tcp

# Allow web traffic
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Enable logging
sudo ufw logging on

# Enable the firewall
sudo ufw enable

# Check status
sudo ufw status verbose


Result
System is now protected with firewall rules that allow:

SSH (on port 2222)

Web traffic (HTTP/HTTPS)

All other traffic is blocked by default.



Save and exit (`Ctrl+O`, `Enter`, then `Ctrl+X` if using nano).

---

#### 🔹 Step 3: Apply the Firewall Rules on Your Ubuntu VM

Now execute the commands from the file:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 2222/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw logging on
sudo ufw enable
sudo ufw status verbose


---

## 🧠 Skills Demonstrated

- Linux firewall configuration using UFW
- Network traffic filtering and access control
- Attack surface reduction on Linux servers
- Secure service exposure and port management
- Understanding of inbound vs outbound traffic rules
- Practical network security hardening techniques
