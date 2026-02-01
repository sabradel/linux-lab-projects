# Project 20: Linux Detection Engineering (Wazuh SIEM)

## Overview
This project focuses on detection engineering for Linux environments using Wazuh SIEM.
It demonstrates how to design, validate, and document custom detections aligned to real SOC workflows.

The project emphasizes **signal quality**, **alert context**, and **analyst usability** rather than attack simulation.

---

## Lab Environment

- **SIEM:** Wazuh Manager (soc01)
- **Endpoint:** Debian Linux (agent)
- **Attack Source:** Kali Linux
- **Log Sources:** journald, sshd, sudo

---

## Detection Phases

### Phase 1: Threat Modeling
- Identified high-risk Linux behaviors
- Mapped techniques to MITRE ATT&CK

### Phase 2: Hunt Hypotheses
- Defined analyst-driven hypotheses
- Focused on privilege escalation and credential abuse

### Phase 3: Log Analysis
- Reviewed raw journald and sudo logs
- Validated reliable detection fields

### Phase 4: SSH Login Success Detection
- Detected successful SSH authentication
- Captured source IP, user, and session context

### Phase 5: Privilege Escalation – sudo Root Shell
- Detected interactive root shells spawned via sudo
- Validated escalation behavior with high confidence alerts

---

## Evidence
Screenshots and alert evidence are included in each phase directory to demonstrate detection validation.

---

## Skills Demonstrated
- Detection engineering methodology
- Wazuh custom rule development
- Linux authentication & privilege escalation analysis
- SOC-aligned alert validation
- Documentation for analyst handoff
