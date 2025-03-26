# Linux Interview Preparation Guide

## 1. Introduction to Linux

### What is Linux?
Linux is an open-source, Unix-like operating system kernel first created by Linus Torvalds in 1991. It forms the basis of numerous operating systems known as Linux distributions (or distros), such as Ubuntu, Fedora, CentOS, and Red Hat Enterprise Linux.

### Key Features of Linux
- Open-source and free
- Highly secure and stable
- Customizable and flexible
- Multi-user and multi-tasking
- Supports a wide range of hardware
- Robust networking capabilities
- Powerful command-line interface

### Linux Architecture
Linux architecture consists of several layers:
1. **Hardware Layer**: Physical components like CPU, RAM, and devices
2. **Kernel Layer**: Core of the operating system
   - Manages system resources
   - Provides low-level services to hardware and upper layers
   - Handles process management, memory management, and device drivers
3. **Shell Layer**: Interface between user and kernel
   - Interprets and executes user commands
   - Provides scripting capabilities
4. **User Applications Layer**: Software used by end-users

### Linux File System Hierarchy
Key directories and their purposes:
- `/`: Root directory
- `/home`: User home directories
- `/etc`: System configuration files
- `/var`: Variable data (logs, temporary files)
- `/bin`: Essential user binaries
- `/sbin`: System binaries
- `/dev`: Device files
- `/proc`: Virtual filesystem for process and kernel information
- `/tmp`: Temporary files
- `/usr`: User utilities and applications

## 2. Virtual Machines (VMs)

### VM Structure and Components
- **Hypervisor**: Manages VM creation and resource allocation
- **Virtual CPU**: Emulated processor
- **Virtual RAM**: Allocated memory
- **Virtual Disk**: Emulated storage
- **Network Interfaces**: Virtual network connections

### Creating and Connecting to a VM via SSH
```bash
# Install SSH client
sudo apt-get install openssh-client  # Ubuntu/Debian
sudo yum install openssh-clients     # CentOS/RHEL

# Connect to VM
ssh username@vm_ip_address

# Generate SSH key pair
ssh-keygen -t rsa -b 4096

# Copy public key to remote server
ssh-copy-id username@vm_ip_address
```

### Managing Ports
```bash
# List all listening ports
sudo netstat -tuln

# Check specific port status
sudo netstat -tulnp | grep :port_number

# Open/close ports using UFW (Uncomplicated Firewall)
sudo ufw allow port_number
sudo ufw deny port_number
```

## 3. Essential Linux Commands

### File Management
```bash
# Copy file
cp source_file destination

# Move/rename file
mv source_file destination

# Remove file/directory
rm file_name
rm -r directory_name

# Create directory
mkdir directory_name
```

### Viewing and Editing Files
```bash
# View file contents
cat filename
less filename

# Edit files
nano filename
vim filename
```

### Process Management
```bash
# List running processes
ps aux

# Real-time process monitoring
top

# Kill process by ID
kill process_id

# Force kill unresponsive process
kill -9 process_id
```

### Disk Usage
```bash
# Disk free space
df -h

# Disk usage by directory
du -sh directory_path
```

### Advanced File Searching
```bash
# Find files
find /path -name "filename"

# Search file contents
grep "search_term" filename

# Complex text processing
awk '{print $1}' filename
sed 's/old_text/new_text/g' filename
```

## 4. Package Management

### Using Package Managers
```bash
# Ubuntu/Debian (apt)
sudo apt update
sudo apt upgrade
sudo apt install package_name
sudo apt remove package_name

# CentOS/RHEL (yum)
sudo yum update
sudo yum install package_name
sudo yum remove package_name
```

### Managing Repositories
```bash
# Add custom repository
sudo add-apt-repository ppa:repository_name
sudo apt update
```

## 5. File/Folder Permissions

### Permission Types
- **Read (r)**: View file contents
- **Write (w)**: Modify file
- **Execute (x)**: Run file/access directory

### Managing Permissions
```bash
# Change permissions
chmod 755 filename
# 7 (owner): read, write, execute
# 5 (group): read, execute
# 5 (others): read, execute

# Change owner
chown username:groupname filename

# Special Permissions
chmod u+s filename  # setuid
chmod g+s directory # setgid
chmod +t directory  # sticky bit
```

## 6. User & Group Management
```bash
# Add user
sudo useradd username
sudo adduser username  # More interactive

# Modify user
sudo usermod -aG groupname username

# Delete user
sudo userdel username
sudo userdel -r username  # Remove home directory

# Add group
sudo groupadd groupname

# Delete group
sudo groupdel groupname
```

## 7. Linux Networking

### Network Fundamentals
- **Network Interface**: Connection point between device and network
- **OSI Model**: 7-layer network communication model
- **TCP**: Connection-oriented, reliable protocol
- **UDP**: Connectionless, faster protocol
- **Routing**: Path selection for network traffic

### Networking Commands
```bash
# Network interfaces
ip addr
ifconfig

# Connection status
netstat -tuln

# Ping remote host
ping hostname_or_ip

# Trace route
traceroute hostname

# DNS lookup
nslookup domain
dig domain
```

## 8. Shell Scripting Basics

### Sample Shell Script
```bash
#!/bin/bash
# Basic shell script example

# Variables
name="Linux Learner"
age=25

# User input
read -p "Enter your name: " user_name

# Conditionals
if [ $user_name == $name ]; then
    echo "Welcome, $name!"
else
    echo "Hello, $user_name!"
fi

# Loop example
for i in {1..5}; do
    echo "Iteration $i"
done

# Function
greet() {
    echo "Hello, $1!"
}

greet "World"

# Error handling
set -e  # Exit immediately if a command exits with non-zero status
```

## 9. Troubleshooting Tips
- Check system logs: `/var/log/syslog`
- Monitor system resources: `top`, `htop`
- Verify network connectivity: `ping`, `traceroute`
- Check disk space: `df -h`
- Analyze system performance: `sar`, `vmstat`

## 10. Interview Preparation Strategies
- Practice command-line skills
- Set up a home lab with VirtualBox or VMware
- Understand core Linux concepts
- Read official documentation
- Solve practical problems
- Learn shell scripting
- Stay updated with latest Linux trends

**Pro Tip**: Many interviews include practical exercises. Be prepared to demonstrate:
- File manipulation
- Process management
- Scripting
- Troubleshooting scenarios
