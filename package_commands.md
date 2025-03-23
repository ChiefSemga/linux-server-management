# Package Management Commands

## **apt_commands** for Ubuntu/Debian

### Managing Packages
- `sudo apt update`                          # Update package list
- `sudo apt upgrade`                         # Upgrade all packages
- `sudo apt install <package-name>`          # Install a package
- `sudo apt remove <package-name>`           # Remove a package
- `sudo apt autoremove`                      # Remove unused packages and dependencies
- `apt search <package-name>`                # Search for a package
- `apt show <package-name>`                  # Show package details
- `dpkg -l`                                  # List installed packages
- `apt list --upgradable`                    # List upgradable packages
- `sudo apt clean`                           # Clean up downloaded package files
- `sudo apt dist-upgrade`                    # Upgrade the system

---

## **yum_commands** for CentOS/RHEL 7 and earlier

### Managing Packages
- `sudo yum update`                         # Update all packages
- `sudo yum install <package-name>`         # Install a package
- `sudo yum remove <package-name>`          # Remove a package
- `yum search <package-name>`               # Search for a package
- `yum list installed`                      # List installed packages
- `yum check-update`                        # List available updates
- `yum info <package-name>`                 # Show package details
- `sudo yum clean all`                      # Clean up cached package data
- `sudo yum install <package-name>-<version>` # Install a specific version of a package

---

## **dnf_commands** for CentOS/RHEL 8 and Fedora

### Managing Packages
- `sudo dnf update`                         # Update all packages
- `sudo dnf install <package-name>`         # Install a package
- `sudo dnf remove <package-name>`          # Remove a package
- `dnf search <package-name>`               # Search for a package
- `dnf list installed`                      # List installed packages
- `dnf check-update`                        # List available updates
- `dnf info <package-name>`                 # Show package details
- `sudo dnf clean all`                      # Clean up cached package data
- `sudo dnf install <package-name>-<version>` # Install a specific version of a package
- `dnf repolist enabled`                    # List enabled repositories

---

## **zypper_commands** for openSUSE

### Managing Packages
- `sudo zypper update`                      # Update all packages
- `sudo zypper install <package-name>`      # Install a package
- `sudo zypper remove <package-name>`       # Remove a package
- `zypper search <package-name>`            # Search for a package
- `zypper search --installed-only`          # List installed packages
- `zypper info <package-name>`              # Show package details
- `sudo zypper refresh`                     # Refresh repositories
- `sudo zypper clean`                       # Clean up package cache
- `sudo zypper install <package-name>-<version>` # Install a specific version of a package
- `zypper repos`                             # List all repositories

