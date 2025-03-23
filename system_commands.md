# System Information
- `uname -a`                     # Display all system information (kernel, architecture, etc.)
- `hostname`                     # Show the system's hostname
- `uptime`                       # Show system uptime and load averages
- `top`                          # Real-time system process viewer
- `htop`                         # An enhanced version of top (with a better UI)
- `dmesg`                        # Display kernel-related messages
- `free -h`                      # Display memory usage (human-readable)
- `lsblk`                        # List all block devices (e.g., hard drives, partitions)
- `df -h`                        # Show disk space usage in human-readable format
- `du -sh <directory>`           # Display the disk usage of a specific directory
- `lscpu`                        # Display CPU architecture details
- `lshw`                          # Display detailed hardware information
- `ps aux`                       # Show all running processes
- `vmstat`                       # Display virtual memory statistics
- `w`                            # Show who is logged in and what they are doing
- `who`                          # Show who is currently logged into the system

# System Monitoring
- `netstat -tuln`                 # Show listening ports and active connections
- `ss -tuln`                      # A modern alternative to netstat
- `iostat`                        # Show CPU and device I/O statistics
- `uptime`                       # Display system uptime and load averages
- `journalctl`                   # View systemd logs
- `journalctl -xe`                # View detailed system logs with errors

# Process Management
- `kill <pid>`                    # Kill a process by PID
- `killall <process-name>`         # Kill all processes with the specified name
- `pkill <process-name>`           # Kill processes by name (case-sensitive)
- `nice <command>`                 # Run a command with a modified scheduling priority
- `renice <pid> -n <priority>`     # Change the priority of a running process

# System Performance & Optimization
- `top`                          # Real-time system resource monitor (CPU, memory, etc.)
- `htop`                         # Interactive process viewer with more features than `top`
- `iotop`                        # Monitor I/O usage by processes (requires root)
- `atop`                         # Advanced system and process monitor
- `sar`                          # Collect, report, or save system activity information

# Disk and File Systems
- `mount <device> <mount_point>`    # Mount a filesystem
- `umount <mount_point>`           # Unmount a filesystem
- `lsblk`                         # List block devices
- `fdisk -l`                      # Show partition table of all disks
- `blkid`                         # Display information about block devices
- `fsck <device>`                 # Check and repair a file system
- `tune2fs -l <device>`           # Show filesystem details (ext2/ext3/ext4)

# System Configuration
- `sysctl -a`                     # Display all kernel parameters
- `sysctl <parameter>`             # Show specific kernel parameter
- `sysctl -w <parameter=value>`    # Set kernel parameter value
- `echo <value> > /proc/sys/<parameter>`  # Set a kernel parameter manually

# System Reboot & Shutdown
- `reboot`                        # Reboot the system
- `shutdown -h now`               # Shut down the system immediately
- `halt`                          # Halt the system immediately
- `poweroff`                      # Turn off the system
- `init 0`                        # Shutdown the system (alternative to `shutdown`)
- `init 6`                        # Reboot the system (alternative to `reboot`)

# Time and Date Management
- `date`                          # Display the current date and time
- `timedatectl`                   # View or set the system's time and timezone
- `ntpdate <time-server>`         # Synchronize the system clock with a time server
- `hwclock`                       # Show or set the hardware clock

# Hardware Information
- `lscpu`                         # Display CPU architecture information
- `lsusb`                         # List all connected USB devices
- `lspci`                         # List all PCI devices
- `lsblk`                         # List block devices (e.g., disks, partitions)
- `dmesg`                         # Display boot messages from the kernel
- `smartctl -a /dev/sda`          # Check hard drive's SMART status

