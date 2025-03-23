# Troubleshooting & Incident Response Commands

## **System Monitoring**

### **CPU & Memory Usage**
- `top`                           # Display real-time system resource usage
- `htop`                          # Interactive process viewer (if installed)
- `free -h`                       # Display memory usage in human-readable format
- `vmstat 1`                      # Show CPU, memory, and I/O statistics every second
- `mpstat -P ALL 1`               # Show per-CPU usage (requires `sysstat` package)
- `cat /proc/meminfo`             # Display detailed memory usage
- `cat /proc/cpuinfo`             # Display CPU information

### **Process Management**
- `ps aux --sort=-%cpu | head`     # List top processes by CPU usage
- `ps aux --sort=-%mem | head`     # List top processes by memory usage
- `kill -9 <PID>`                  # Forcefully terminate a process
- `pkill <process-name>`           # Kill a process by name
- `pgrep <process-name>`           # Get PID(s) of a process

---

## **Disk & Filesystem Issues**

### **Disk Usage**
- `df -h`                         # Show disk space usage (human-readable)
- `du -sh <directory>`             # Show size of a specific directory
- `ncdu`                          # Interactive disk usage analyzer (if installed)

### **Filesystem Errors**
- `lsblk`                         # List all block devices
- `mount`                         # Show mounted filesystems
- `umount <mount-point>`           # Unmount a filesystem
- `fsck -y <device>`               # Check and repair filesystem errors

---

## **Network Troubleshooting**

### **Network Status**
- `ip a`                          # Show all network interfaces and IP addresses
- `ifconfig`                      # (Deprecated) Show network interfaces
- `nmcli device status`           # Show network interface status
- `ethtool <interface>`           # Show network interface details
- `ss -tulnp`                     # Show active listening ports
- `netstat -tulnp`                # (Deprecated) Show open ports

### **Connectivity Issues**
- `ping <host>`                    # Check network connectivity
- `traceroute <host>`              # Trace packet route to destination
- `mtr <host>`                     # Real-time traceroute analysis
- `nslookup <domain>`              # Query DNS information
- `dig <domain>`                   # Get detailed DNS resolution info
- `host <domain>`                  # Resolve domain to IP

### **Firewall & Security**
- `iptables -L -v`                 # List firewall rules (iptables)
- `firewalld --list-all`           # Show active firewalld rules
- `ufw status verbose`             # Show UFW firewall status
- `sudo netstat -tulpn | grep LISTEN` # Check open network ports
- `tcpdump -i eth0 port 80`        # Capture network packets on port 80

---

## **User & Access Issues**

### **User Management**
- `who`                           # Show logged-in users
- `w`                             # Show active user sessions
- `id <username>`                 # Show user UID, GID, and groups
- `groups <username>`             # List groups for a user
- `passwd <username>`             # Reset a user's password
- `chage -l <username>`           # View password expiry details

### **Access & Permission Issues**
- `ls -lah <file>`                # View file permissions and owner
- `chmod 755 <file>`              # Change file permissions
- `chown user:group <file>`       # Change file ownership
- `sudo visudo`                   # Edit sudoers file safely
- `cat /etc/sudoers`              # Check sudo privileges

---

## **Log Analysis & Incident Investigation**

### **System Logs**
- `journalctl -xe`                # View systemd logs for errors
- `journalctl -u <service-name>`   # View logs for a specific service
- `dmesg | tail`                   # View recent kernel messages
- `cat /var/log/syslog`            # View system logs (Debian/Ubuntu)
- `cat /var/log/messages`          # View system logs (RHEL/CentOS)

### **Authentication & Security Logs**
- `cat /var/log/auth.log`          # View authentication logs (Debian/Ubuntu)
- `cat /var/log/secure`            # View authentication logs (RHEL/CentOS)
- `last`                           # Show login history
- `lastb`                          # Show failed login attempts
- `who /var/log/wtmp`              # Show login history
- `cat /var/log/faillog`           # View failed login attempts

### **Service Logs**
- `systemctl status <service>`      # Check status of a service
- `systemctl restart <service>`     # Restart a service
- `cat /var/log/nginx/access.log`   # View Nginx access logs
- `cat /var/log/nginx/error.log`    # View Nginx error logs
- `cat /var/log/httpd/access_log`   # View Apache access logs
- `cat /var/log/httpd/error_log`    # View Apache error logs

---

## **Performance Bottleneck Analysis**

### **I/O Performance**
- `iostat -xz 1`                   # Monitor I/O usage per disk (requires `sysstat`)
- `iotop`                          # Display top I/O-consuming processes (if installed)
- `vmstat 1`                       # Show system performance metrics

### **CPU Performance**
- `uptime`                         # Show system load average
- `sar -u 1 5`                     # CPU usage every second for 5 iterations
- `mpstat 1`                       # Show CPU usage per core

### **Memory Usage**
- `free -m`                        # Display memory usage in MB
- `vmstat -s`                      # Show memory statistics

---

## **Hardware Issues & System Information**

### **Hardware & System Info**
- `uname -a`                       # Display Linux kernel version
- `cat /etc/os-release`            # Show OS version details
- `lsb_release -a`                 # Get detailed OS info (if installed)
- `uptime`                         # Show system uptime
- `dmidecode -t system`            # View system hardware info (requires root)
- `lsusb`                          # List USB devices
- `lscpu`                          # Display CPU details
- `lspci`                          # Show PCI devices

---

## **Automated Recovery & Fixes**

### **Fix Broken Packages**
- `sudo apt --fix-broken install`  # Fix broken package dependencies (Debian/Ubuntu)
- `sudo yum-complete-transaction`  # Resolve unfinished transactions (CentOS/RHEL)
- `sudo dnf check`                 # Check for broken dependencies (Fedora)
- `sudo zypper verify`             # Verify installed packages (openSUSE)

### **Recovering a Crashed System**
- `mount -o remount,rw /`          # Remount root filesystem in read/write mode
- `fsck -y /dev/sda1`              # Repair corrupted filesystem
- `journalctl -xb`                 # View boot logs for troubleshooting
- `rescue mode:` `systemctl rescue` # Switch to rescue mode
- `single-user mode:` `init 1`     # Enter single-user mode (older systems)

---

## **Emergency Response & Security Auditing**

### **Detect Suspicious Activity**
- `ps aux | grep suspicious_process`   # Check for unauthorized processes
- `who`                                # See logged-in users
- `netstat -anp | grep LISTEN`         # Look for unexpected open ports
- `ss -tulnp`                          # Check active connections
- `lsof -i :<port>`                     # List processes using a specific port
- `chkrootkit`                          # Scan for rootkits (if installed)

### **Block Suspicious IPs**
- `iptables -A INPUT -s <IP> -j DROP`   # Block an IP address
- `sudo ufw deny from <IP>`             # Block an IP with UFW
- `fail2ban-client status sshd`         # Check failed SSH login attempts (if installed)

