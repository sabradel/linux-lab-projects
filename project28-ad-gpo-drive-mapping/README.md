# Project 28: Helpdesk Active Directory Lab – Users, Groups, Shared Drives & GPO Automation

## 📌 Overview
This lab demonstrates a real-world **Helpdesk / Desktop Support Active Directory environment** where users and departments are managed using **Active Directory**, and shared network drives are mapped automatically using **Group Policy Objects (GPOs)**.

The lab includes two departments (**HR** and **Sales**) with different access rights, using **Security Groups + Security Filtering** to ensure correct access control.

---

## 🎯 Lab Objectives
- Create Organizational Units (OUs) for users, computers, and groups
- Create HR and Sales security groups
- Create HR and Sales user accounts
- Create shared folders for each department
- Configure SMB shared folders
- Create and configure Group Policy Objects (GPOs) to map drives automatically
- Apply security filtering so only the correct department users receive the correct drive mapping
- Verify results using `gpupdate`, `gpresult`, and File Explorer

---

## 🏗️ Lab Environment

| Component | Hostname | OS |
|----------|----------|----|
| Domain Controller | DC01 | Windows Server 2022 |
| Client Workstation | HELPDESK-PC01 | Windows 10 Pro |
| Domain Name | firstcanadian.local | Active Directory Domain |

---

## 📂 Active Directory Structure

### Organizational Units (OUs)
- FC-Users
- FC-Groups
- FC-Computers
- FC-Servers

### Security Groups Created
- HR_Users
- Sales_Users

### User Accounts Created
- maria.hr (HR Department)
- john.sales (Sales Department)

---

## 📁 Shared Folders and Network Paths

Shared folders were created and shared across the network:

| Department | Drive Letter | Share Path |
|-----------|--------------|-----------|
| HR | H: | `\\192.168.56.30\hr` |
| Sales | S: | `\\192.168.56.30\Sales` |

---

## 🛠️ Group Policy Objects (GPOs)

Two GPOs were created to map drives automatically:

| GPO Name | Drive Letter | Share Path | Security Filtering |
|---------|--------------|-----------|-------------------|
| GPO-Map-HR-Drive | H: | `\\192.168.56.30\hr` | HR_Users |
| GPO-Map-Sales-Drive | S: | `\\192.168.56.30\Sales` | Sales_Users |

---

## ⚙️ GPO Configuration (Drive Maps)

Drive mapping was configured under:

`User Configuration > Preferences > Windows Settings > Drive Maps`

### HR Drive Settings
- Action: Create
- Drive Letter: H:
- Path: `\\192.168.56.30\hr`
- Label: HR Drive

### Sales Drive Settings
- Action: Create
- Drive Letter: S:
- Path: `\\192.168.56.30\Sales`
- Label: Sales Drive

---

## 🔐 Security Filtering (Important Part)

Security filtering ensures that:
- HR drive policy applies only to HR users
- Sales drive policy applies only to Sales users

This prevents users from accessing drives outside their department.

---

## ✅ Testing and Verification

### Commands Used on Client PC
```cmd
gpupdate /force
gpresult /r
net use
wmic logicaldisk get name

---
