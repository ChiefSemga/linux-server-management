# **Networking Commands for Hardening a Linux Server**

## **1. Network Configuration**
- `ip a`                                  # Show network interfaces and IP addresses
- `ip link show`                          # Display active network interfaces
- `ip route show`                         # Show routing table
- `ifconfig -a`                           # Display all network interfaces (deprecated, use `ip a`)
- `netstat -tulnp`                        # Show open ports and associated processes
- `ss -tulnp`                             # Display listening ports with process details (alternative to netstat)
- `hostname -I`                           # Show IP address of the system
- `nmcli connection show`                  # List all network connections
- `ethtool <interface>`                    # Display network interface details

---

## **2. Firewall Management (iptables & firewalld)**
### **Using iptables**
- `sudo iptables -L -v -n`                 # List firewall rules in detail
- `sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT`  # Allow SSH on port 22
- `sudo iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT` # Allow established connections
- `sudo iptables -P INPUT DROP`            # Set default deny rule for incoming traffic
- `sudo iptables-save > /etc/iptables.rules` # Save iptables rules
- `sudo iptables-restore < /etc/iptables.rules` # Restore saved rules

### **Using firewalld (RHEL/CentOS/Fedora)**
- `sudo systemctl status firewalld`        # Check firewall status
- `sudo firewall-cmd --list-all`           # List all firewall rules
- `sudo firewall-cmd --add-port=22/tcp --permanent`  # Allow SSH (port 22)
- `sudo firewall-cmd --reload`             # Reload firewall rules

---

## **3. Securing SSH**
- `sudo nano /etc/ssh/sshd_config`         # Edit SSH configuration
- `PermitRootLogin no`                     # Disable root login
- `PasswordAuthentication no`              # Disable password authentication (use SSH keys)
- `AllowUsers <username>`                  # Restrict SSH access to specific users
- `sudo systemctl restart sshd`            # Restart SSH service

---

## **4. TCP Wrappers (Access Control)**
- `sudo nano /etc/hosts.allow`             # Define allowed services and IPs

