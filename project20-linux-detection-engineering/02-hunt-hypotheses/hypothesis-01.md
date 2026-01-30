# Hunt Hypothesis 01 – Post-Access System Enumeration

## Hypothesis
If an attacker successfully logs in via SSH, they will perform rapid system and user enumeration within minutes.

## Expected Attacker Commands
- whoami
- id
- uname -a
- sudo -l
- cat /etc/passwd

## Detection Goal
Identify multiple reconnaissance commands executed shortly after SSH authentication.
