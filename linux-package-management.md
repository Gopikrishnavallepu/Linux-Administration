# Comprehensive Linux Package Management Guide

## 1. Package Management Fundamentals

### Package Types
1. **Binary Packages**: Pre-compiled software
2. **Source Packages**: Compile-from-source code
3. **Metapackages**: Dependency collections

### Major Package Managers
- **Debian/Ubuntu**: APT (Advanced Package Tool)
- **Red Hat/CentOS**: DNF/YUM
- **Arch Linux**: Pacman
- **SUSE**: Zypper

## 2. APT Package Management

### Basic Operations
```bash
# Update Package Lists
sudo apt update

# Upgrade All Packages
sudo apt upgrade

# Install Package
sudo apt install package_name

# Remove Package
sudo apt remove package_name

# Remove with Configuration
sudo apt purge package_name

# Clean Package Cache
sudo apt autoremove
sudo apt clean
```

### Advanced Package Management
```bash
# Search Packages
apt-cache search keyword

# Show Package Information
apt-cache show package_name

# List Installed Packages
dpkg -l

# Check Package Dependencies
apt-cache depends package_name

# Find Which Package Provides a File
dpkg -S /path/to/file
```

## 3. Repository Management

### Adding Repositories
```bash
# Add PPA Repository
sudo add-apt-repository ppa:repository_name

# Add Custom Repository
sudo add-apt-repository "deb [arch=amd64] https://custom.repo.com/ubuntu focal main"

# Import GPG Key
wget -qO- https://repo.example.com/gpg.key | sudo apt-key add -
```

### Repository Configuration
```bash
# Edit Sources List
sudo nano /etc/apt/sources.list

# Disable Repository
# Comment out line with #
# deb https://repo.example.com/ubuntu focal main
```

## 4. Package Compilation

### Compile from Source
```bash
# Download Source
wget https://example.com/software.tar.gz
tar -xzvf software.tar.gz
cd software

# Compile Process
./configure
make
sudo make install

# Alternative: checkinstall
sudo checkinstall
```

## 5. Dependency Management

### Resolving Dependencies
```bash
# Fix Broken Packages
sudo apt-get -f install

# Hold Package Version
sudo apt-mark hold package_name

# Unhold Package
sudo apt-mark unhold package_name
```

## 6. Package Security

### Verification Techniques
```bash
# Check Package Integrity
dpkg -V package_name

# Verify GPG Keys
apt-key list
apt-key finger
```

## 7. Advanced Tools

### Package Management Tools
- **Synaptic**: Graphical package manager
- **aptitude**: Advanced CLI package management
- **deborphan**: Find orphaned packages

## 8. Custom Repository Creation

### Local Repository Setup
```bash
# Install Repository Tools
sudo apt install dpkg-dev

# Create Repository Structure
mkdir -p /var/www/repo/pool/main
mkdir -p /var/www/repo/dists/stable/main/binary-amd64

# Generate Packages File
cd /var/www/repo
dpkg-scanpackages pool/main /dev/null > dists/stable/main/binary-amd64/Packages
gzip -k dists/stable/main/binary-amd64/Packages
```

## Practical Exercises
1. Add and manage custom repositories
2. Compile software from source
3. Resolve complex dependency issues
4. Create a local package repository
5. Perform system-wide package audit
