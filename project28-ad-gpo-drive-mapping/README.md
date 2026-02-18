# Project 28: Helpdesk Active Directory Lab – Drive Mapping with GPO (HR + Sales)

## 📌 Overview
This project simulates a real-world **IT Helpdesk / Desktop Support Active Directory environment**.

In this lab, I built a small enterprise domain where users are organized into departments (**HR** and **Sales**) and shared drives are automatically mapped using **Group Policy Preferences (Drive Maps)**.

The goal is to demonstrate **real workplace skills** such as:
- Active Directory user/group management
- SMB file sharing
- GPO automation
- Access control using security groups
- Troubleshooting Group Policy issues

---

## 🎯 Skills Demonstrated (Recruiter Friendly)
✅ Active Directory User & Group Administration  
✅ Organizational Unit (OU) Structure Design  
✅ SMB Share Configuration (Linux File Server)  
✅ Group Policy Management (GPMC)  
✅ Group Policy Preferences – Drive Mapping  
✅ Security Filtering + Item Level Targeting  
✅ Helpdesk Troubleshooting (`gpupdate`, `gpresult`, `net use`)  
✅ Permissions Debugging (Authenticated Users issue fix)  
✅ Documentation + Evidence Screenshots  

---

## 🏗️ Lab Environment

| System Role | Hostname | OS |
|------------|----------|----|
| Domain Controller | DC01 | Windows Server 2022 |
| File Server | FILE01 | Ubuntu Server |
| Client Workstation | HELPDESK-PC01 | Windows 10 Pro |

### Domain Name
`firstcanadian.local`

---

## 📂 Active Directory Structure

### Organizational Units (OUs)
- **FC-Users**
- **FC-Groups**
- **FC-Computers**
- **FC-Servers**

### Security Groups
- **HR_Users**
- **Sales_Users**

### Users Created
- **maria.hr** → HR Department
- **john.sales** → Sales Department

---

## 📁 File Shares Created (Ubuntu File Server)

The Ubuntu file server was configured with SMB shares for each department.

| Department | Drive Letter | Share Path |
|-----------|--------------|-----------|
| HR | H: | `\\192.168.56.30\hr` |
| Sales | S: | `\\192.168.56.30\Sales` |

---

## 🛠️ Group Policy Objects (GPOs)

Two separate GPOs were created to automate department drive mappings:

| GPO Name | Drive Letter | Share Path | Applied To |
|---------|--------------|-----------|-----------|
| GPO-Map-HR-Drive | H: | `\\192.168.56.30\hr` | HR_Users |
| GPO-Map-Sales-Drive | S: | `\\192.168.56.30\Sales` | Sales_Users |

Drive mapping was configured under:

`User Configuration → Preferences → Windows Settings → Drive Maps`

---

## 🔐 Security Filtering & Targeting

This lab uses real enterprise access control concepts:

### HR Drive (H:)
- Security Filtering: **HR_Users**
- Only HR users receive H: drive mapping

### Sales Drive (S:)
- Security Filtering: **Sales_Users**
- Only Sales users receive S: drive mapping

This prevents unauthorized users from seeing other department shares.

---

## 🐛 Troubleshooting & Fixes Performed

During testing, the HR drive mapping initially failed due to missing permissions.

### Fix Applied
- Added **Authenticated Users** with Read permission to the GPO security settings.

After the fix, Group Policy applied successfully and drive mapping worked.

---

## ✅ Testing & Verification Commands (Windows Client)

These commands were used on Windows 10 to validate drive mapping and GPO processing:

```cmd
gpupdate /force
gpresult /r
net use
wmic logicaldisk get name
echo %logonserver%
