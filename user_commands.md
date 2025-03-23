# Add a new user
sudo useradd <username>

# Set a password for the user
sudo passwd <username>

# Delete a user
sudo userdel <username>

# Remove a user and their home directory
sudo userdel -r <username>

# Modify a user (e.g., change home directory)
sudo usermod -d /home/new_home <username>

# Add a user to a group
sudo usermod -aG <group-name> <username>

# Remove a user from a group
sudo gpasswd -d <username> <group-name>

# Lock a user account
sudo usermod -L <username>

# Unlock a user account
sudo usermod -U <username>

# List all users on the system
cat /etc/passwd

# Display current user details (UID, GID, groups)
id <username>

# Display all groups a user is a member of
groups <username>

# Show currently logged-in users
who

# Display information about currently logged-in users
w

# Check last login information of users
last

# Change user password expiration date
sudo chage -E YYYY-MM-DD <username>  # Set account expiration date

# Set password expiry information
sudo chage -M 30 <username>  # Maximum days before password change required

# Disable user password expiry
sudo chage -M -1 <username>  # Disable password expiry

# Display password expiration information
sudo chage -l <username>

# Display all user accounts
getent passwd

# Create a new user with a specified home directory and shell
sudo useradd -m -s /bin/bash <username>

# Show users' login records
lastlog

