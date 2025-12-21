# Project 12 – Windows Active Directory Attack & Defense

## 🎯 Objective
Simulate a real-world Active Directory attack and perform SOC-style detection,
investigation, and defensive hardening in a controlled lab environment.

This project demonstrates hands-on experience with Windows enterprise security,
Active Directory administration, and blue team incident response.

---

## 🧱 Lab Environment

| Machine | OS | Role |
|------|---|---|
| DC01 | Windows Server 2016 | Domain Controller |
| CLIENT01 | Windows 10 | Domain-joined workstation |
| ATTACK01 | Kali Linux | Attacker machine |

**Network Configuration**
- Host-Only Adapter
- Isolated internal lab network

---

## 🛠️ Active Directory Setup (Defender View)

- Installed Active Directory Domain Services (AD DS)
- Promoted server to Domain Controller
- Created domain: `corp.local`
- Created domain user accounts
- Joined Windows 10 client to the domain

---

## ⚔️ Attack Simulation (High-Level Overview)

The following attack techniques were simulated for defensive learning:

- Network discovery of Active Directory services
- Domain user enumeration
- Authentication-based attacks against Active Directory
- Password spraying attempts against weak credentials

All actions were performed in a **controlled lab** for learning and defense.

---

## 🔍 Detection & Investigation (SOC View)

- Analyzed Windows Security Event Logs
- Identified authentication failures
- Detected abnormal login patterns
- Investigated Kerberos-related security events
- Correlated attacker activity across systems

### Confirmed Detection Evidence

Windows Security Event logs confirmed detection of attacker activity.

Event ID 4625 (Audit Failure) recorded:
- Source Workstation: KALI
- Source IP Address: 192.168.56.104
- Authentication Process: NTLM (NtLmSsp)

This confirms that domain authentication attempts originating
from the attacker machine were successfully logged and
correlated by the Domain Controller.

### Successful Authentication Detection

A controlled password spray attempt was performed using a known domain user.

Attack result:
- Account: jdoe
- Authentication method: SMB
- Outcome: Successful login

Detection evidence on DC01:
- Event ID: 4624 (Successful Logon)
- Logon Type: 3 (Network)
- Source IP: 192.168.56.104 (Kali attacker)
- Domain: HERZINGCOLLEGE

This confirms that Active Directory authentication events
can be correlated back to attacker infrastructure during
credential-based attacks.

---

## 🔐 Defensive Hardening Actions

- Enforced account lockout policies
- Reset compromised credentials
- Applied password complexity requirements
- Reduced attack surface using security policies
- Validated mitigations using log analysis

---

## 🧠 Skills Demonstrated

- Active Directory administration
- Windows Server 2016 security
- Domain authentication analysis
- Kerberos security fundamentals
- Password spraying detection
- Windows Event Log analysis
- SOC-style incident investigation
- Blue team defensive hardening
- Linux and Windows security correlation

---

## 📌 Notes

- Activities performed in an isolated lab environment
- Project focused on defense, detection, and mitigation
- No production systems were impacted

---

## 🚀 Why This Project Matters

Active Directory is used in most enterprise environments.
This project demonstrates practical SOC and blue team skills
used to detect and respond to real-world domain attacks.

---

## 🔗 Repository

Part of the Linux & Security Lab Projects repository:
https://github.com/sabradel/linux-lab-projects


Verified full network connectivity between Kali Linux, Windows 10, and Windows Server 2016 using ICMP after configuring Windows Defender Firewall inbound rules in a controlled lab environment.


### RPC Enumeration Outcome

A null RPC session was attempted from the attacker system.
The Domain Controller immediately reset the connection,
demonstrating proper hardening against anonymous RPC access.

This behavior is expected in secured Active Directory environments
and still produces authentication and network security events
useful for SOC detection and investigation.
