# Linux Server Best Practices

## **1. System Updates & Package Management**
- `sudo apt update && sudo apt upgrade -y`          # Regularly update system packages (Ubuntu/Debian)
- `sudo yum update -y`                              # Update system packages (CentOS/RHEL 7)
- `sudo dnf update -y`                              # Update system packages (Fedora/RHEL 8+)
- `sudo zypper update -y`                           # Update system packages (openSUSE)
- `sudo apt autoremove`                             # Remove unnecessary dependencies
- `sudo apt clean`                                  # Clean up package cache

---

## **2. User & Group Management**
- `sudo adduser <username>`                         # Create a new user
- `sudo userdel -r <username>`                      # Remove a user and their home directory
- `sudo usermod -aG <group-name> <username>`        # Add user to a group
- `sudo gpasswd -d <username> <group-name>`         # Remove user from a group
- `sudo passwd -l <username>`                       # Lock user account
- `sudo passwd -u <username>`                       # Unlock user account
- `sudo chage -E YYYY-MM-DD <username>`             # Set user account expiration date

---

## **3. File Permissions & Security**
- `chmod 700 <file>`                                # Set file permissions to owner-only access
- `chown <user>:<group> <file>`                     # Change file owner and group
- `umask 027`                                       # Set default file permissions
- `sudo visudo`                                     # Edit sudoers file securely
- `sudo nano /etc/ssh/sshd_config`                  # Secure SSH configuration (Disable root login, set key authentication)
- `sudo systemctl restart sshd`                     # Apply SSH changes

---

## **4. Firewall & Network Security**
- `sudo ufw enable`                                 # Enable firewall (Ubuntu/Debian)
- `sudo ufw allow <port>`                           # Allow specific port in firewall
- `sudo ufw deny <port>`                            # Block specific port
- `sudo firewall-cmd --add-port=<port>/tcp --permanent && sudo firewall-cmd --reload` # Open a port in Firewalld (CentOS/RHEL)
- `sudo iptables -A INPUT -p tcp --dport <port> -j ACCEPT` # Allow port in iptables
- `netstat -tulnp`                                  # Check open network ports
- `sudo tcpdump -i eth0`                            # Monitor network traffic

---

## **5. SSH & Remote Access Best Practices**
- `sudo nano /etc/ssh/sshd_config`
  - **Disable root login:** `PermitRootLogin no`
  - **Change SSH port:** `Port 2222`
  - **Enable key-based authentication:** `PasswordAuthentication no`
- `sudo systemctl restart sshd`                     # Restart SSH service
- `ssh-keygen -t rsa -b 4096`                       # Generate SSH key pair
- `ssh-copy-id user@server`                         # Copy public key to remote server

---

## **6. Process & Service Management**
- `top` or `htop`                                   # Monitor system processes
- `ps aux | grep <service-name>`                    # Find running processes
- `sudo systemctl status <service-name>`            # Check service status
- `sudo systemctl enable <service-name>`            # Enable service on boot
- `sudo systemctl restart <service-name>`           # Restart a service
- `sudo systemctl disable <service-name>`           # Disable a service from startup

---

## **7. Disk & Storage Management**
- `df -h`                                          # Check disk usage
- `du -sh <directory>`                              # Check size of a directory
- `lsblk`                                          # List available disks and partitions
- `sudo fdisk -l`                                   # Display partition information
- `sudo mount /dev/sdX /mnt`                        # Mount a filesystem
- `sudo umount /mnt`                                # Unmount a filesystem
- `sudo fsck -y /dev/sdX`                           # Check and repair a filesystem

---

## **8. Logs & Monitoring**
- `sudo journalctl -xe`                             # View system logs
- `sudo tail -f /var/log/syslog`                    # Monitor system logs in real-time
- `sudo tail -f /var/log/auth.log`                  # Monitor authentication logs
- `sudo du -sh /var/log/`                           # Check log size
- `uptime`                                          # Check system uptime
- `vmstat 1`                                        # Monitor CPU and memory usage
- `iostat -c 1`                                     # Monitor CPU load

---

## **9. Scheduled Jobs & Automation**
- `crontab -e`                                      # Edit user’s cron jobs
- `crontab -l`                                      # List user’s cron jobs
- `echo "0 3 * * * /path/to/script.sh" | crontab -` # Schedule a script to run daily at 3 AM
- `at now + 5 minutes`                              # Schedule a one-time job
- `sudo systemctl restart cron`                     # Restart cron service

---

## **10. Backup & Recovery**
- `tar -czvf backup.tar.gz /path/to/directory`      # Create a compressed backup
- `rsync -av /source/dir /backup/dir`               # Sync files for backup
- `dd if=/dev/sda of=/backup.img bs=4M`             # Create a full disk backup
- `ls /snapshots`                                   # Check backup snapshots (if using BTRFS)
- `sudo cp /etc/fstab /etc/fstab.bak`               # Backup fstab before making changes
- `test -f /backup.tar.gz && echo "Backup exists"`  # Verify backup file

---

## **11. Intrusion Detection & Hardening**
- `sudo apt install fail2ban`                       # Install Fail2Ban to block brute-force attacks
- `sudo fail2ban-client status`                     # Check Fail2Ban status
- `sudo find / -type f -perm -4000`                 # Find all SUID binaries
- `grep "password" /etc/shadow`                     # Check for weak passwords
- `sudo ausearch -m avc`                            # Check SELinux denials
- `sudo auditctl -w /etc/passwd -p wa -k passwd_changes` # Monitor password file changes

---

## **12. Performance Tuning**
- `sudo sysctl -w vm.swappiness=10`                 # Reduce swap usage
- `sudo sysctl -w net.ipv4.tcp_fin_timeout=30`      # Reduce TCP FIN timeout
- `echo noop > /sys/block/sda/queue/scheduler`      # Set disk scheduler to NOOP for SSDs
- `ulimit -n 100000`                                # Increase file descriptor limit
- `sudo systemctl disable NetworkManager-wait-online.service` # Improve boot time

