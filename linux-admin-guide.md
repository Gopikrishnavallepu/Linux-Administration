# Comprehensive Linux Administration Guide

## 1. Introduction to Linux

### What is Linux?
Linux is an open-source, Unix-like operating system kernel first created by Linus Torvalds in 1991. It is the foundation of numerous operating systems (distributions) used across servers, desktops, embedded systems, and more.

### Key Features
- Open-source and free
- Highly secure and stable
- Customizable and flexible
- Supports multiple users and multitasking
- Robust networking capabilities
- Wide hardware support

### Linux Architecture
Linux architecture consists of four primary layers:
1. **Hardware Layer**: Physical components like CPU, RAM, and devices
2. **Kernel Layer**: Core of the operating system managing hardware resources
3. **Shell Layer**: Interface between user and kernel (command-line or GUI)
4. **Application Layer**: User applications and utilities

### Linux File System Hierarchy
Key directories in the Linux file system:
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
- Hypervisor (Type 1 or Type 2)
- Virtual hardware configuration
- Network adapters
- Storage volumes
- Memory allocation

### Creating a VM with VirtualBox
```bash
# Install VirtualBox
sudo apt-get update
sudo apt-get install virtualbox

# Create a new VM
# 1. Open VirtualBox
# 2. Click "New"
# 3. Configure VM settings (name, memory, disk)
# 4. Install OS (e.g., Ubuntu Server)
```

### Connecting via SSH
```bash
# Generate SSH key
ssh-keygen -t rsa -b 4096

# Connect to VM
ssh username@vm_ip_address

# Copy SSH key to VM
ssh-copy-id username@vm_ip_address
```

### Managing VM Ports
```bash
# Forward port in VirtualBox
# Network > Advanced > Port Forwarding
# Add rules like:
# Host Port 8080 -> Guest Port 80
```

## 3. Essential Linux Commands

### File Management
```bash
# Copy file
cp source_file destination

# Move/Rename file
mv old_name new_name

# Remove file
rm filename

# Remove directory
rm -r directory
```

### File Viewing and Editing
```bash
# View file contents
cat filename

# Paginated view
less filename

# Edit with nano
nano filename

# Edit with vim
vim filename
```

### Process Management
```bash
# List processes
ps aux

# Real-time process monitor
top

# Kill process by ID
kill PID

# Force kill
kill -9 PID
```

### Disk Usage
```bash
# Disk free space
df -h

# Disk usage by directory
du -sh /path/to/directory
```

### Advanced File Searching
```bash
# Find files
find /path -name "filename"

# Search file contents
grep "search_term" filename

# Complex text processing
awk '{print $1}' filename
sed 's/old/new/g' filename
```

## 4. Package Management

### Using apt (Debian/Ubuntu)
```bash
# Update package list
sudo apt update

# Upgrade installed packages
sudo apt upgrade

# Install package
sudo apt install package_name

# Remove package
sudo apt remove package_name

# Search for package
apt search keyword
```

### Managing Repositories
```bash
# Add repository
sudo add-apt-repository ppa:repository_name

# List repositories
sudo apt-cache policy

# Update repository list
sudo apt update
```

## 5. File/Folder Permissions

### Permission Basics
- Read (r): 4
- Write (w): 2
- Execute (x): 1

### Changing Permissions
```bash
# Change mode (permissions)
chmod 755 filename    # rwxr-xr-x
chmod u+x filename    # Add execute for user
chmod g-w filename    # Remove write for group

# Change owner
chown username:groupname filename

# Recursive permissions
chmod -R 755 directory
```

### Special Permissions
```bash
# Setuid: Run as file owner
chmod u+s executable

# Setgid: Inherit group permissions
chmod g+s directory

# Sticky bit: Prevent file deletion
chmod +t directory
```

## 6. User & Group Management

### Adding Users
```bash
# Create user
sudo adduser username

# Create user with specific home directory
sudo useradd -m -d /home/username username

# Create system user
sudo useradd -r username
```

### Modifying Users
```bash
# Change user password
sudo passwd username

# Modify user properties
sudo usermod -aG groupname username
```

### Deleting Users
```bash
# Remove user
sudo userdel username

# Remove user and home directory
sudo userdel -r username
```

## 7. Linux Networking

### Network Interfaces
```bash
# List network interfaces
ip link show
ifconfig

# Configure network interface
sudo nmtui
```

### Networking Commands
```bash
# Ping host
ping example.com

# Trace route
traceroute example.com

# Network statistics
netstat -tuln

# DNS lookup
nslookup example.com
dig example.com
```

## 8. Linux Troubleshooting

### Common Errors and Solutions
1. **Permission Denied**
   - Check file permissions
   - Use `sudo`
   - Verify user group membership

2. **Disk Space Full**
   - Use `df -h` to check space
   - Remove unnecessary files
   - Use `du -sh *` to find large directories

3. **Network Connectivity**
   - Check `ifconfig`/`ip` configuration
   - Verify DNS settings
   - Test with `ping`

### Logging and Monitoring
```bash
# System logs
journalctl -xe

# Real-time log monitoring
tail -f /var/log/syslog

# Performance monitoring
top
htop
```

## Practice Exercises
1. Set up a virtual machine
2. Create users with different permissions
3. Install and configure web server
4. Perform network troubleshooting
5. Write bash scripts for automation

## Recommended Learning Resources
- Linux Documentation Project
- Red Hat Linux Documentation
- Linux Academy
- Udemy Linux Courses
