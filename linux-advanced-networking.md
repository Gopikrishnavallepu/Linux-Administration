# Advanced Linux Networking Guide

## 1. Network Fundamentals

### OSI Model Layers
1. **Physical Layer**: Physical transmission
2. **Data Link Layer**: MAC addressing
3. **Network Layer**: IP routing
4. **Transport Layer**: TCP/UDP
5. **Session Layer**: Connection management
6. **Presentation Layer**: Data formatting
7. **Application Layer**: User interactions

### TCP/IP Model
- **Link Layer**: Network interface
- **Internet Layer**: IP routing
- **Transport Layer**: TCP/UDP
- **Application Layer**: Protocols

## 2. Network Configuration

### IP Address Management
```bash
# Configure Static IP
sudo nano /etc/netplan/01-netcfg.yaml
network:
  version: 2
  renderer: networkd
  ethernets:
    eth0:
      addresses: [192.168.1.100/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]

# Apply configuration
sudo netplan apply
```

### Subnet Calculation
```bash
# CIDR Notation Breakdown
# 192.168.1.0/24
# Network: 192.168.1.0
# Broadcast: 192.168.1.255
# Usable IPs: 192.168.1.1 - 192.168.1.254
```

## 3. Advanced Networking Commands

### Network Diagnostics
```bash
# Comprehensive Network Info
ip addr show
ip route
ss -tuln  # Socket Statistics
netstat -rn  # Routing Table

# Bandwidth Testing
iperf3 -s  # Server
iperf3 -c server_ip  # Client

# Port Scanning
nmap -p- server_ip
```

### Network Monitoring
```bash
# Real-time Network Monitor
sudo iftop

# Bandwidth Usage
nethogs

# Connection Tracking
conntrack -L
```

## 4. Firewall Configuration

### UFW (Uncomplicated Firewall)
```bash
# Enable Firewall
sudo ufw enable

# Allow Specific Ports
sudo ufw allow 22/tcp
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Block IP
sudo ufw deny from 192.168.1.50

# Logging
sudo ufw logging on
```

### Advanced iptables
```bash
# Block Specific IP Range
iptables -A INPUT -m iprange --src-range 192.168.1.100-192.168.1.200 -j DROP

# Port Forwarding
iptables -t nat -A PREROUTING -p tcp --dport 8080 -j REDIRECT --to-port 80
```

## 5. Advanced Routing

### Policy-Based Routing
```bash
# Create Routing Table
echo "200 myisp" >> /etc/iproute2/rt_tables

# Configure Routing Rules
ip rule add from 192.168.1.0/24 table myisp
ip route add default via 192.168.1.1 dev eth0 table myisp
```

## 6. Network Troubleshooting

### Diagnostic Workflow
1. Check physical connection
2. Verify IP configuration
3. Test DNS resolution
4. Check routing
5. Firewall investigation
6. Application-level diagnostics

### Practical Diagnostic Commands
```bash
# DNS Resolution
dig @8.8.8.8 example.com
nslookup example.com

# Traceroute
traceroute -n example.com

# Packet Capture
tcpdump -i eth0 port 80
```

## 7. Security Best Practices
- Disable unnecessary services
- Use strong firewall rules
- Implement network segmentation
- Regular security audits
- Keep network stack updated

## Practical Exercises
1. Configure static IP
2. Set up complex firewall rules
3. Implement port forwarding
4. Create custom routing tables
5. Perform network diagnostics
