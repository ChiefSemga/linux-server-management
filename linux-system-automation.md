# Cron Jobs

## Managing Cron Jobs
- `crontab -l`                              # View current user's cron jobs
- `crontab -e`                              # Edit current user's cron jobs
- `echo "30 3 * * * /path/to/command" | crontab -`  # Add a cron job (run every day at 3:30 AM)
- `crontab -r`                              # Remove all cron jobs
- `cat /etc/crontab`                        # List system-wide cron jobs
- `sudo run-parts /etc/cron.daily`          # Run a cron job manually

---

# Systemd Services (Service Management)

## Managing Services
- `sudo systemctl start <service-name>`     # Start a service
- `sudo systemctl stop <service-name>`      # Stop a service
- `sudo systemctl restart <service-name>`   # Restart a service
- `sudo systemctl enable <service-name>`    # Enable a service to start on boot
- `sudo systemctl disable <service-name>`   # Disable a service from starting on boot
- `sudo systemctl status <service-name>`    # Check the status of a service
- `sudo journalctl -u <service-name>`       # View logs for a service
- `sudo systemctl list-units --type=service` # List all active services
- `sudo systemctl daemon-reload`            # Reload systemd manager configuration

---

# At Jobs (One-Time Task Scheduling)

## Managing One-Time Jobs
- `echo "/path/to/command" | at now + 5 minutes`   # Schedule a one-time job (run after 5 minutes)
- `atq`                                          # List all scheduled jobs
- `atrm 1`                                        # Remove a specific scheduled job (Job ID 1)
- `echo "/path/to/command" | at now`               # Run a job immediately

---

# Monitoring and Automation Tools

## Monitoring System Resources
- `df -h | mail -s "Disk Usage Alert" your-email@example.com`    # Monitor disk usage (e.g., with cron)
- `top -n 1 > top_output.txt`                             # Monitor system resources with `top` and save the output

---

# Backup Automation

## Automating Backup with Cron
- `echo "0 0 * * * rsync -av /source/dir /backup/dir" | crontab -` # Automate backup using rsync (daily at midnight)
- `echo "0 2 * * * rsync -av /home/user /backup/location" | crontab -` # Automated daily backup with cron
- `echo "0 3 * * * rsync -a --delete / /backup/system/" | crontab -` # Automated system backup (using rsync with cron)

## Creating Backups
- `tar -czf /path/to/backup.tar.gz /path/to/directory`           # Create a compressed backup of a directory
- `backup_dir="/path/to/backup/$(date +\%Y\%m\%d\%H\%M).tar.gz"`  # Backup with timestamped filename
- `tar -czf $backup_dir /path/to/directory`                      # Create a backup with a timestamped filename

