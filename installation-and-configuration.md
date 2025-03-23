# Installation & Initial Configuration Commands for Linux Server

## **System Update & Upgrade**
- `sudo apt update && sudo apt upgrade -y`    # Ubuntu/Debian: Update package list & upgrade all packages
- `sudo yum update -y`                        # CentOS/RHEL 7: Update all packages
- `sudo dnf update -y`                        # CentOS/RHEL 8/Fedora: Update all packages
- `sudo zypper update -y`                     # openSUSE: Update all packages

---

## **User & Group Management**
- `sudo adduser <username>`                   # Create a new user
- `sudo passwd <username>`                    # Set password for the user
- `sudo userdel -r <username>`                # Remove a user and their home directory
- `sudo usermod -aG <group-name> <username>`  # Add a user to a group
- `sudo gpasswd -d <username> <group-name>`   # Remove a user from a group
- `groups <username>`                         # Display groups a user belongs to

---

## **Hostname & Timezone Configuration**
- `hostnamectl set-hostname <new-hostname>`   # Set a new hostname
- `timedatectl set-timezone <timezone>`       # Set timezone (e.g., `timedatectl set-timezone UTC`)
- `timedatectl`                               # Check current date, time, and timezone

---

## **Networking Configuration**
- `ip a`                                      # Display network interfaces and IP addresses
- `nmcli device show`                         # Show network configurations (for NetworkManager)
- `sudo systemctl restart NetworkManager`     # Restart NetworkManager service
- `sudo nano /etc/hosts`                      # Edit the hosts file for local name resolution

---

## **Firewall Configuration**
- `sudo ufw enable`                           # Enable UFW firewall (Ubuntu/Debian)
- `sudo ufw allow <port-number>`              # Allow traffic on a specific port
- `sudo firewall-cmd --add-port=<port>/tcp --permanent`  # Open a port (CentOS/RHEL)
- `sudo firewall-cmd --reload`                # Reload firewall rules

---

## **SSH Configuration**
- `sudo systemctl enable ssh`                 # Enable SSH on system startup
- `sudo systemctl start ssh`                  # Start SSH service
- `sudo nano /etc/ssh/sshd_config`            # Edit SSH configuration
- `sudo systemctl restart sshd`               # Restart SSH service

---

## **Storage & Disk Management**
- `lsblk`                                     # List all available storage devices
- `df -h`                                     # Check disk usage in human-readable format
- `du -sh <directory>`                        # Check space used by a specific directory
- `mount /dev/sdX /mnt`                       # Mount a partition
- `umount /mnt`                               # Unmount a partition
- `mkfs.ext4 /dev/sdX`                        # Format a partition with ext4 filesystem

---

## **Package Management**
### **Ubuntu/Debian**
- `sudo apt install <package-name>`           # Install a package
- `sudo apt remove <package-name>`            # Remove a package

### **CentOS/RHEL**
- `sudo yum install <package-name>`           # Install a package
- `sudo yum remove <package-name>`            # Remove a package

### **Fedora**
- `sudo dnf install <package-name>`           # Install a package
- `sudo dnf remove <package-name>`            # Remove a package

### **openSUSE**
- `sudo zypper install <package-name>`        # Install a package
- `sudo zypper remove <package-name>`         # Remove a package

---

## **Service Management**
- `sudo systemctl start <service-name>`       # Start a service
- `sudo systemctl stop <service-name>`        # Stop a service
- `sudo systemctl restart <service-name>`     # Restart a service
- `sudo systemctl enable <service-name>`      # Enable a service on boot
- `sudo systemctl disable <service-name>`     # Disable a service on boot
- `sudo systemctl status <service-name>`      # Check service status

---

## **Process & Resource Monitoring**
- `top`                                       # Display real-time system resource usage
- `htop`                                      # Enhanced process viewer (install using `sudo apt install htop`)
- `ps aux`                                    #

