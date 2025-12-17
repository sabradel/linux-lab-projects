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

