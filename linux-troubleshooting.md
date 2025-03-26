# Comprehensive Linux Troubleshooting Guide

## 1. Systematic Troubleshooting Approach

### Troubleshooting Methodology
1. **Identify the Problem**
   - Gather specific error messages
   - Collect system logs
   - Understand recent changes

2. **Reproduce the Issue**
   - Create controlled environment
   - Isolate potential causes
   - Document steps to reproduce

3. **Analyze Root Cause**
   - Use diagnostic tools
   - Check system logs
   - Examine configuration files

4. **Develop Solution**
   - Implement minimal fixes
   - Test solution thoroughly
   - Document changes

5. **Prevent Recurrence**
   - Update documentation
   - Implement monitoring
   - Create preventive measures

## 2. System Monitoring Tools

### Performance Monitoring
```bash
# Real-time System Monitor
top
htop

# Detailed System Performance
vmstat 1
iostat -x 1
mpstat -P ALL 1

# Memory Usage
free -h
cat /proc/meminfo

# Disk Usage
df -h
du -sh /home/*
```

### Process Analysis
```bash
# List All Processes
ps aux

# Process Tree
pstree

# Kill Problematic Processes
pkill process_name
kill -9 PID

# Zombie Process Detection
ps aux | awk '$8=="Z"'
```

## 3. Log Analysis

### Key Log Locations
```bash
# System Logs
/var/log/syslog
/var/log/messages
/var/log/kern.log

# Authentication Logs
/var/log/auth.log
/var/log/secure

# Application Logs
/var/log/apache2/error.log
/var/log/mysql/error.log
```

### Log Examination Tools
```bash
# Follow Log in Real-time
tail -f /var/log/syslog

# Search Logs
grep "error" /var/log/syslog

# Log Rotation Management
logrotate /etc/logrotate.conf
```

## 4. Network Troubleshooting

### Connectivity Diagnostics
```bash
# Ping Test
ping -c 4 example.com

# Traceroute
traceroute example.com

# DNS Resolution
nslookup example.com
dig example.com

# Port Connectivity
netstat -tuln
ss -tuln

# Bandwidth Test
iperf3 -c server_ip
```

### Firewall Debugging
```bash
# UFW Status
sudo ufw status verbose

# IPTables Rules
sudo iptables -L -n -v

# Packet Capture
sudo tcpdump -i eth0 port 80
```

## 5. Filesystem Troubleshooting

### Filesystem Checks
```bash
# Check Filesystem
sudo fsck /dev/sda1

# Disk Health
sudo smartctl -a /dev/sda

# Inode Usage
df -i

# Identify Large Files
find / -type f -size +100M 2>/dev/null
```

## 6. Performance Optimization

### System Tuning
```bash
# CPU Information
lscpu
cat /proc/cpuinfo

# Memory Optimization
echo 3 > /proc/sys/vm/drop_caches

# Swap Usage
swapon -s
```

## 7. Recovery Techniques

### Boot Recovery
```bash
# Enter Recovery Mode
# GRUB Menu: Advanced Options
# Select recovery mode

# Repair Filesystem
mount -o remount,rw /

# Restore GRUB
update-grub
grub-install /dev/sda
```

## 8. Troubleshooting Scripts

### System Health Check Script
```bash
#!/bin/bash
# Comprehensive System Health Check

# CPU Load
echo "CPU Load:"
uptime

# Memory Usage
echo -e "\nMemory Usage:"
free -h

# Disk Usage
echo -e "\nDisk Usage:"
df -h

# List Failed Services
echo -e "\nFailed Services:"
systemctl --failed

# Check Log for Errors
echo -e "\nRecent Errors:"
journalctl -p err -n 10
```

## 9. Common Troubleshooting Scenarios

### Scenario: Slow System
1. Check CPU usage
2. Analyze memory consumption
3. Review running processes
4. Check disk I/O
5. Examine system logs

### Scenario: Network Issues
1. Verify physical connectivity
2. Check IP configuration
3. Test DNS resolution
4. Examine firewall rules
5. Review network service logs

## Practical Exercises
1. Create a system health monitoring script
2. Perform comprehensive log analysis
3. Diagnose and resolve performance issues
4. Implement proactive monitoring
5. Create emergency recovery procedures

## Recommended Tools
- `htop`: Interactive process viewer
- `iotop`: I/O monitoring
- `strace`: System call tracer
- `tcpdump`: Packet analyzer
- `journalctl`: Systemd journal viewer
