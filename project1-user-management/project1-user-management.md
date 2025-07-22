# Project 1: User Management on Rocky Linux

## Task
- Create a new user `testuser`
- Set a password for the user
- Add user to `wheel` group for sudo privileges
- Verify sudo access by switching user and running `sudo whoami`

## Commands run

```bash
sudo adduser testuser
sudo passwd testuser
sudo usermod -aG wheel testuser
getent passwd testuser
su - testuser
sudo whoami

