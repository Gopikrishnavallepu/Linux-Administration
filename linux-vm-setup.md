# Linux Virtual Machine Setup and Advanced Management

## 1. Virtual Machine Types
1. **Type 1 Hypervisors (Bare Metal)**
   - Direct hardware access
   - Highest performance
   - Examples: 
     - VMware ESXi
     - Proxmox
     - Microsoft Hyper-V Server

2. **Type 2 Hypervisors (Hosted)**
   - Run on top of existing OS
   - Easier to set up
   - Examples:
     - VirtualBox
     - VMware Workstation
     - Parallels Desktop

## 2. Comprehensive VM Creation Process

### Using VirtualBox
```bash
# Install VirtualBox
sudo apt update
sudo apt install virtualbox

# Download Linux ISO (e.g., Ubuntu Server)
wget https://releases.ubuntu.com/22.04/ubuntu-22.04.2-live-server-amd64.iso

# Create VM via CLI
VBoxManage createvm --name "UbuntuServer" --ostype "Ubuntu_64" --register
VBoxManage modifyvm "UbuntuServer" --memory 2048 --cpus 2
VBoxManage createhd --filename "UbuntuServer.vdi" --size 20000
VBoxManage storagectl "UbuntuServer" --name "SATA Controller" --add sata
VBoxManage storageattach "UbuntuServer" --storagectl "SATA Controller" --port 0 --device 0 --type hdd --medium "UbuntuServer.vdi"
```

### Advanced SSH Configuration
```bash
# Generate SSH Key with Strong Encryption
ssh-keygen -t ed25519 -a 100

# SSH Config for Multiple Servers
# ~/.ssh/config
Host homeserver
    HostName 192.168.1.100
    User adminuser
    IdentityFile ~/.ssh/home_server_key
    Port 22

Host workserver
    HostName work.example.com
    User devops
    IdentityFile ~/.ssh/work_server_key

# SSH Tunneling
ssh -L 8080:localhost:80 user@remoteserver
```

## 3. Network Configuration in VMs

### Port Forwarding Examples
```bash
# Forward Web Server Port
VBoxManage modifyvm "UbuntuServer" --natpf1 "web,tcp,,8080,,80"

# Multiple Port Forwarding
VBoxManage modifyvm "UbuntuServer" \
    --natpf1 "ssh,tcp,,2222,,22" \
    --natpf1 "web,tcp,,8080,,80" \
    --natpf1 "db,tcp,,5432,,5432"
```

## 4. VM Backup and Snapshot Strategies
```bash
# Create Snapshot
VBoxManage snapshot "UbuntuServer" take "CleanInstall"

# List Snapshots
VBoxManage snapshot "UbuntuServer" list

# Restore Snapshot
VBoxManage snapshot "UbuntuServer" restore "CleanInstall"

# Clone VM
VBoxManage clonevm "UbuntuServer" --name "DevServer" --register
```

## 5. Performance Optimization
- Allocate appropriate RAM
- Use VirtIO drivers
- Enable hardware virtualization
- Use SSD for VM storage
- Limit unnecessary background processes

## 6. Security Hardening
- Disable unnecessary network interfaces
- Use minimal OS installation
- Regular security updates
- Implement firewall rules
- Use SSH key-based authentication
- Disable root login

## Practical Exercises
1. Create a VM with minimal Ubuntu Server
2. Configure SSH key-based authentication
3. Set up port forwarding for a web service
4. Create and manage VM snapshots
5. Implement basic firewall rules
