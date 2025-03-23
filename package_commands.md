# apt_commands for Ubuntu/Debian

# Update package list
sudo apt update

# Upgrade all packages
sudo apt upgrade

# Install a package
sudo apt install <package-name>

# Remove a package
sudo apt remove <package-name>

# Remove a package and its dependencies
sudo apt autoremove

# Search for a package
apt search <package-name>

# Show package details
apt show <package-name>

# List installed packages
dpkg -l

# List upgradable packages
apt list --upgradable

# Clean up downloaded package files
sudo apt clean

# Upgrade the system
sudo apt dist-upgrade

# Yum_commands for CentOS/RHEL 7 and earlier
# Update all packages
sudo yum update

# Install a package
sudo yum install <package-name>

# Remove a package
sudo yum remove <package-name>

# Search for a package
yum search <package-name>

# List installed packages
yum list installed

# List available updates
yum check-update

# Show package details
yum info <package-name>

# Clean up cached package data
sudo yum clean all

# Install a specific version of a package
sudo yum install <package-name>-<version>

# dnf_commands for CentOS/RHEL 8 and Fedora
# Update all packages
sudo dnf update

# Install a package
sudo dnf install <package-name>

# Remove a package
sudo dnf remove <package-name>

# Search for a package
dnf search <package-name>

# List installed packages
dnf list installed

# List available updates
dnf check-update

# Show package details
dnf info <package-name>

# Clean up cached package data
sudo dnf clean all

# Install a specific version of a package
sudo dnf install <package-name>-<version>

# List enabled repositories
dnf repolist enabled

# zypper_commands for openSUSE
# Update all packages
sudo zypper update

# Install a package
sudo zypper install <package-name>

# Remove a package
sudo zypper remove <package-name>

# Search for a package
zypper search <package-name>

# List installed packages
zypper search --installed-only

# Show package details
zypper info <package-name>

# Refresh repositories
sudo zypper refresh

# Clean up package cache
sudo zypper clean

# Install a specific version of a package
sudo zypper install <package-name>-<version>

# List all repositories
zypper repos



