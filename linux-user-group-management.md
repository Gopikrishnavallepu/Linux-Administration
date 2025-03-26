# Advanced Linux User and Group Management

## 1. User Account Types

### User Categories
1. **Root User (UID 0)**
   - Complete system control
   - Unrestricted access
   - Use with extreme caution

2. **System Users (UID 1-999)**
   - Service and daemon accounts
   - Limited system access
   - No login shell typically

3. **Regular Users (UID 1000+)**
   - Standard user accounts
   - Limited system permissions
   - Normal login capabilities

## 2. User Management Commands

### Creating Users
```bash
# Basic User Creation
sudo adduser username

# Advanced User Creation
sudo useradd -m -s /bin/bash -g users -G sudo,developers username

# Create System User
sudo useradd -r -s /bin/false systemuser

# Options Explained:
# -m: Create home directory
# -s: Set login shell
# -g: Primary group
# -G: Supplementary groups
# -r: System account
```

### User Modification
```bash
# Change User Password
sudo passwd username

# Modify User Properties
sudo usermod -aG additional_group username

# Lock/Unlock User Account
sudo passwd -l username  # Lock
sudo passwd -u username  # Unlock

# Change User Home Directory
sudo usermod -d /new/home/directory username
```

### User Deletion
```bash
# Remove User
sudo userdel username

# Remove User with Home Directory
sudo userdel -r username
```

## 3. Group Management

### Group Creation and Management
```bash
# Create Group
sudo groupadd groupname

# Create Group with Specific GID
sudo groupadd -g 1500 custom_group

# Modify Group
sudo groupmod -n new_groupname old_groupname

# Delete Group
sudo groupdel groupname
```

### Group Membership
```bash
# Add User to Group
sudo usermod -aG groupname username

# Remove User from Group
sudo gpasswd -d username groupname

# List Group Members
getent group groupname
```

## 4. Advanced User Management

### Password Management
```bash
# Set Password Expiration
sudo chage -M 90 username  # Max 90 days
sudo chage -m 7 username   # Min 7 days before change
sudo chage -E 2024-12-31 username  # Account expiry

# Force Password Change on Next Login
sudo passwd -e username
```

### Sudo Access
```bash
# Edit Sudo Configuration
sudo visudo

# Example Sudo Configurations
# Allow user to run specific commands
username ALL=(ALL) /path/to/specific/command

# Grant full sudo access
username ALL=(ALL:ALL) ALL

# Limit sudo to specific groups
%admin ALL=(ALL) ALL
```

## 5. Authentication Methods

### SSH Key Authentication
```bash
# Generate SSH Key
ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519

# Copy Public Key to Server
ssh-copy-id username@server

# Configure SSH Key Permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_ed25519
chmod 644 ~/.ssh/id_ed25519.pub
```

### Password Policies
```bash
# Install Password Strength Checker
sudo apt install libpam-pwquality

# Configure /etc/security/pwquality.conf
minlen = 12        # Minimum password length
dcredit = -1       # Require at least 1 digit
ucredit = -1       # Require at least 1 uppercase
lcredit = -1       # Require at least 1 lowercase
ocredit = -1       # Require at least 1 special character
```

## 6. Security Best Practices
- Limit root account usage
- Use strong password policies
- Implement multi-factor authentication
- Regularly audit user accounts
- Use principle of least privilege
- Monitor user activities

## 7. User Management Scripts

### Example User Creation Script
```bash
#!/bin/bash
# Bulk User Creation Script

# Input file with username,group,shell
while IFS=',' read -r username group shell
do
    # Create user with specified parameters
    sudo useradd -m -g "$group" -s "$shell" "$username"
    echo "Created user: $username"
done < users.csv
```

## Practical Exercises
1. Create users with different permission levels
2. Set up group-based access control
3. Implement password policies
4. Create a bulk user management script
5. Configure SSH key-based authentication

## Recommended Tools
- `adduser`: Interactive user creation
- `useradd`: Scriptable user creation
- `usermod`: User modification
- `chage`: Password aging
- `sudo`: Privilege escalation
