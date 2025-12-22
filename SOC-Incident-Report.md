# SOC Incident Report – Active Directory Account Lockout

## Incident Summary
On December 21, 2025, a domain user account (jdoe) within the HERZINGCOLLEGE.local Active Directory environment was locked out due to multiple failed authentication attempts. The activity originated from an internal attacker host (Kali Linux) attempting unauthorized access to the Domain Controller using SMB/NTLM authentication.

---

## Environment
- Domain: HERZINGCOLLEGE.local
- Domain Controller: Windows Server 2016 (DC01)
- Client Machine: Windows 10 (CLIENT01)
- Attacker Machine: Kali Linux
- Network Type: Host-only (No Internet)

---

## Timeline of Events
| Time | Event ID | Description |
|-----|--------|------------|
| 10:01 AM | 4625 | Multiple failed logon attempts detected from attacker IP |
| 10:02 AM | 4740 | Domain account jdoe was locked out |
| 10:03 AM | 4768 | Kerberos authentication attempts observed |

---

## Evidence Collected
### Event ID 4625 – Failed Logon
- Source IP: 192.168.56.104 (Kali Linux)
- Logon Process: NtLmSsp
- Authentication Package: NTLM
- Result: Audit Failure

### Event ID 4740 – Account Lockout
- Affected Account: jdoe
- Domain: HERZINGCOLLEGE.local
- Lockout triggered by Domain Controller
- Caller Computer Name: Not populated (Expected behavior)

---

## Attack Technique
- Technique: Credential brute-force / password spraying
- Protocol: SMB (TCP 445)
- Authentication: NTLM
- Validation Tool: CrackMapExec (SMB authentication confirmed)

---

## Mitigation and Response
- Account lockout policy enforced
- Password policy reviewed and strengthened
- Administrative monitoring enabled for authentication failures
- Event correlation between 4625 and 4740 implemented

---

## Lessons Learned
- Account lockout events may not contain source host information
- Correlation of multiple event IDs is required for accurate attribution
- Strong password and lockout policies significantly reduce attack success

---

## Analyst Notes
This incident demonstrates effective detection and response to Active Directory authentication attacks using native Windows logging and SOC correlation techniques.

