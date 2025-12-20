# Project 5: Advanced System Monitoring

## Objective
Learn to monitor system resources on Ubuntu using various tools.

## Tools Installed
- htop
- vmstat
- iotop
- netstat
- dstat
- glances

## Commands and Usage

```bash
sudo apt update
sudo apt install -y htop vmstat iotop net-tools dstat glances

htop    # Interactive process viewer
vmstat 1 5    # System performance statistics every 1 second, 5 times
sudo iotop -o    # Disk IO in real-time (requires sudo)
netstat -tulnp    # List listening ports and associated processes
dstat    # Real-time system stats
glances    # Comprehensive monitoring dashboard



Notes
htop provides a colorful, interactive process viewer.

vmstat reports on system processes, memory, paging, block IO, traps, and CPU activity.

iotop tracks disk I/O usage per process.

netstat shows network connections, routing tables, interface stats, etc.

dstat combines vmstat, iostat, netstat, and ifstat in one tool.

glances offers an all-in-one terminal dashboard for monitoring your system.

Summary
This project introduced several powerful monitoring tools to help track and troubleshoot system performance in real time.





---

### Step 3: Save and exit nano

- Press `Ctrl + O` (to write out/save)
- Press `Enter` (confirm file name)
- Press `Ctrl + X` (to exit nano)

---

### Step 4: Add screenshots to the folder

Make sure your screenshots are copied to:

```bash
~/linux-lab-projects/project5-system-monitoring/screenshots/
