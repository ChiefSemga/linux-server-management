# Linux Security Commands for Hardening

## **User and Group Management**

### Manage Users
- `sudo useradd <username>`             # Add a new user
- `sudo passwd <username>`              # Set password for a user
- `sudo userdel <username>`             # Delete a user
- `sudo userdel -r <username>`          # Delete user and their home directory
- `sudo usermod -d /home/new_home <username>`  # Change home directory of a user
- `sudo usermod -L <username>`          # Lock a user account
- `sudo usermod -U <username>`          # Unlock a user account
- `sudo chage -M 30 <username>`         # Set password expiry (maximum days)
- `sudo chage -M -1 <username>`         # Disable password expiry
- `sudo chage -l <username>`            # Display password expiration details
- `sudo gpasswd -d <username> <group-name>` # Remove a user from a group

### Manage Groups
- `sudo groupadd <group-name>`          # Create a new group
- `sudo groupdel <group-name>`          # Delete a group
- `sudo groupmod -n <new-group-name> <old-group-name>` # Rename a group
- `sudo groupmod -g <new-gid> <group-name>`  # Change GID of a group
- `getent group <group-name>`           # Show group details

---

## **SSH Security**

### SSH Configuration
- `sudo nano /etc/ssh/sshd_config`      # Edit SSH configuration file
- `PermitRootLogin no`                  # Disable root login via SSH
- `PasswordAuthentication no`           # Disable password authentication, use key-based authentication
- `ChallengeResponseAuthentication no`  # Disable challenge response authentication
- `AllowUsers <user1> <user2>`          # Allow only specific users to log in via SSH
- `sudo systemctl restart sshd`         # Restart SSH service after changes

### Generate SSH Keys
- `ssh-keygen -t rsa -b 4096`           # Generate an RSA SSH key pair (4096 bits)
- `ssh-copy-id <username>@<hostname>`    # Copy the SSH public key to a remote server

---

## **File Permissions and Ownership**

### Change File Permissions
- `chmod 700 <file>`                    # Set read, write, and execute for owner only
- `chmod 755 <file>`                    # Set read, write, and execute for owner; read and execute for others
- `chmod 644 <file>`                    # Set read and write for owner; read-only for others
- `chmod -R 700 <directory>`            # Recursively change permissions for a directory

### Change File Ownership
- `chown <user>:<group> <file>`          # Change file owner and group
- `chown -R <user>:<group> <directory>`  # Recursively change ownership of a directory

---

## **File Integrity Monitoring**

### Install AIDE (Advanced Intrusion Detection Environment)
- `sudo apt install aide`                # Install AIDE (on Ubuntu/Debian)
- `sudo yum install aide`                # Install AIDE (on CentOS/RHEL)
- `sudo dnf install aide`                # Install AIDE (on Fedora)
- `sudo aideinit`                         # Initialize AIDE database
- `sudo aide --check`                    # Run an integrity check

---

## **Firewall and Network Security**

### Configure UFW (Uncomplicated Firewall)
- `sudo ufw enable`                      # Enable UFW firewall
- `sudo ufw disable`                     # Disable UFW firewall
- `sudo ufw allow <port>`                # Allow a specific port (e.g., 22 for SSH)
- `sudo ufw deny <port>`                 # Deny a specific port
- `sudo ufw status`                      # Check firewall status
- `sudo ufw status verbose`              # Display detailed firewall status

### Configure FirewallD (CentOS/RHEL/Fedora)
- `sudo systemctl start firewalld`       # Start firewall service
- `sudo systemctl enable firewalld`      # Enable firewall service at boot
- `sudo firewall-cmd --zone=public --add-port=22/tcp --permanent` # Allow SSH
- `sudo firewall-cmd --reload`           # Reload firewall to apply changes
- `sudo firewall-cmd --list-all`         # List all firewall rules

---

## **System Updates**

### Update System Packages
- `sudo apt update && sudo apt upgrade`        # Update all packages (Ubuntu/Debian)
- `sudo yum update`                            # Update all packages (CentOS/RHEL 7)
- `sudo dnf update`                            # Update all packages (CentOS/RHEL 8/Fedora)
- `sudo zypper update`                         # Update all packages (openSUSE)
- `sudo apt dist-upgrade`                      # Upgrade the system (Ubuntu/Debian)

### Automate Security Updates
- `sudo apt install unattended-upgrades`      # Enable automatic security updates (Ubuntu/Debian)
- `sudo yum install yum-cron`                 # Enable automatic security updates (CentOS/RHEL)
- `sudo systemctl enable yum-cron`            # Enable automatic updates service

---

## **Log Management and Monitoring**

### View System Logs
- `sudo journalctl`                           # View system logs (systemd-based)
- `sudo tail -f /var/log/auth.log`            # Monitor authentication logs in real-time
- `sudo tail -f /var/log/syslog`              # Monitor system logs in real-time
- `sudo cat /var/log/secure`                  # View security logs (CentOS/RHEL)

### Install Fail2Ban
- `sudo apt install fail2ban`                 # Install Fail2Ban (Ubuntu/Debian)
- `sudo yum install fail2ban`                 # Install Fail2Ban (CentOS/RHEL)
- `sudo systemctl enable fail2ban`            # Enable Fail2Ban service
- `sudo systemctl start fail2ban`             # Start Fail2Ban service
- `sudo fail2ban-client status`               # Check Fail2Ban status

---

## **Disk Encryption**

### Enable LUKS (Linux Unified Key Setup)
- `sudo cryptsetup luksFormat <device>`        # Encrypt a device with LUKS
- `sudo cryptsetup luksOpen <device> <name>`   # Open the encrypted device
- `sudo cryptsetup luksClose <name>`           # Close the encrypted device

---

## **Security Auditing**

### Run Lynis Security Audits
- `sudo apt install lynis`                     # Install Lynis (Ubuntu/Debian)
- `sudo yum install lynis`                     # Install Lynis (CentOS/RHEL)
- `sudo dnf install lynis`                     # Install Lynis (Fedora)
- `sudo lynis audit system`                    # Run a security audit on the system

---

## **SELinux Configuration (CentOS/RHEL/Fedora)**

### Configure SELinux
- `sudo getenforce`                            # Check SELinux status
- `sudo setenforce 0`                          # Disable SELinux temporarily
- `sudo setenforce 1`                          # Enable SELinux temporarily
- `sudo vi /etc/selinux/config`                # Edit SELinux configuration file
- `sudo semanage port -a -t http_port_t -p tcp <port>` # Allow a custom port for a service

