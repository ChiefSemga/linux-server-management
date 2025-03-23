# Cron Jobs
# View current user's cron jobs
crontab -l

# Edit current user's cron jobs
crontab -e

# Add a cron job (run every day at 3:30 AM)
echo "30 3 * * * /path/to/command" | crontab -

# Remove all cron jobs
crontab -r

# List system-wide cron jobs
cat /etc/crontab

# Run a cron job manually
sudo run-parts /etc/cron.daily

# Systemmd_services (service management)
# Start a service
sudo systemctl start <service-name>

# Stop a service
sudo systemctl stop <service-name>

# Restart a service
sudo systemctl restart <service-name>

# Enable a service to start on boot
sudo systemctl enable <service-name>

# Disable a service from starting on boot
sudo systemctl disable <service-name>

# Check the status of a service
sudo systemctl status <service-name>

# View logs for a service
sudo journalctl -u <service-name>

# List all active services
sudo systemctl list-units --type=service

# Reload systemd manager configuration
sudo systemctl daemon-reload

# At Job (One time Task Scheduling)
# Schedule a one-time job (run after 5 minutes)
echo "/path/to/command" | at now + 5 minutes

# List all scheduled jobs
atq

# Remove a specific scheduled job (Job ID 1)
atrm 1

# Run a job immediately
echo "/path/to/command" | at now

# Monitoring and Automation Tools
# Monitor disk usage (e.g., with cron)
df -h | mail -s "Disk Usage Alert" your-email@example.com

# Monitor system resources with `top` and save the output
top -n 1 > top_output.txt

# Automate backup using rsync (daily backup at midnight)
echo "0 0 * * * rsync -av /source/dir /backup/dir" | crontab -

# Set up an alert for high CPU usage (using `ps` and `mail`)
ps aux --sort=-%cpu | head -n 5 | mail -s "High CPU Usage Alert" your-email@example.com

# Back-up Automation 
# Automated daily backup with cron
echo "0 2 * * * rsync -av /home/user /backup/location" | crontab -

# Create a compressed backup of a directory
tar -czf /path/to/backup.tar.gz /path/to/directory

# Automated system backup (using rsync with cron)
echo "0 3 * * * rsync -a --delete / /backup/system/" | crontab -

# Backup with timestamped filename
backup_dir="/path/to/backup/$(date +\%Y\%m\%d\%H\%M).tar.gz"
tar -czf $backup_dir /path/to/directory



