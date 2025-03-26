# Advanced Linux File Permissions and Access Control

## 1. Permission Fundamentals

### Permission Types
1. **Read (r)**
   - Files: View file contents
   - Directories: List directory contents

2. **Write (w)**
   - Files: Modify or delete file
   - Directories: Create or delete files

3. **Execute (x)**
   - Files: Run as a program
   - Directories: Access directory contents

### Permission Representation
```
-rwxr-xr-x  1 owner group  4096 Mar 26 10:30 filename
│ │ │ │ │     │     │      │      │      └── Filename
│ │ │ │ │     │     │      │      └── Last modified date
│ │ │ │ │     │     │      └── File size
│ │ │ │ │     │     └── Group permissions
│ │ │ │ │     └── Owner permissions
│ │ │ │ └── Others permissions
│ │ │ └── Execute
│ │ └── Write
│ └── Read
└── File type (- for regular file, d for directory)
```

## 2. Permission Modification

### Numeric (Octal) Method
```bash
# Numeric Permission Assignment
chmod 755 filename
# 7 (owner): read + write + execute
# 5 (group): read + execute
# 5 (others): read + execute

# Common Permissions
chmod 644 filename  # Default file permissions
chmod 755 directory # Default directory permissions
chmod 600 sensitive_file  # Restrict to owner only
```

### Symbolic Method
```bash
# Symbolic Permission Modification
chmod u+x filename   # Add execute for user
chmod g-w filename   # Remove write for group
chmod o=r filename   # Set read-only for others

# Complex Modifications
chmod u=rwx,g=rx,o=r filename
```

## 3. Advanced Permissions

### Special Permissions
1. **Setuid (4)**
   ```bash
   # Run file with owner's permissions
   chmod u+s executable
   # Numeric: chmod 4755
   ```

2. **Setgid (2)**
   ```bash
   # Inherit group permissions
   chmod g+s directory
   # Numeric: chmod 2755
   ```

3. **Sticky Bit (1)**
   ```bash
   # Prevent file deletion in directory
   chmod +t directory
   # Numeric: chmod 1755
   ```

## 4. Ownership Management

### Changing Ownership
```bash
# Change File Owner
chown username filename
chown username:groupname filename

# Recursive Ownership Change
chown -R username:groupname directory
```

## 5. Advanced Access Control

### Access Control Lists (ACL)
```bash
# Install ACL Tools
sudo apt install acl

# Set Additional Permissions
setfacl -m u:username:rwx filename
setfacl -m g:groupname:r-x filename

# View ACL
getfacl filename

# Remove ACL
setfacl -x u:username filename
```

### Attribute Management
```bash
# Immutable Files
chattr +i filename  # Make immutable
chattr -i filename  # Remove immutability

# Append-only Files
chattr +a logfile
```

## 6. Security Considerations

### Permission Best Practices
- Minimize permissions
- Use groups for access control
- Avoid setuid when possible
- Regularly audit file permissions
- Use ACLs for granular control
- Implement principle of least privilege

## 7. Permission Analysis Tools
```bash
# Find Files with Specific Permissions
find / -perm 777 2>/dev/null

# Check File Permissions
stat filename

# List Permissions Recursively
ls -lR directory
```

## 8. Practical Permission Scenarios

### Web Server Configuration
```bash
# Typical Web Server Permissions
chmod 750 /var/www/html
chown www-data:www-data /var/www/html
```

### Secure Configuration Script
```bash
#!/bin/bash
# Secure Permission Setup

# Secure Important System Directories
chmod 700 /root
chmod 750 /etc/sudoers.d
chmod 600 /etc/shadow
chmod 644 /etc/passwd

# Secure User Home Directories
chmod 700 /home/*
```

## Practical Exercises
1. Configure complex file permissions
2. Use ACLs for granular access
3. Create a permission audit script
4. Implement secure default permissions
5. Manage special permissions safely

## Recommended Tools
- `chmod`: Permission modification
- `chown`: Ownership change
- `setfacl`: Advanced permissions
- `getfacl`: Permission inspection
