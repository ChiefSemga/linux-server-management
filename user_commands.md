# User Management Commands

## Creating and Deleting Users
- `sudo useradd <username>`                   # Add a new user
- `sudo passwd <username>`                    # Set a password for the user
- `sudo userdel <username>`                   # Delete a user
- `sudo userdel -r <username>`                # Remove a user and their home directory
- `sudo useradd -m -s /bin/bash <username>`   # Create a new user with a specified home directory and shell

---

## Modifying Users
- `sudo usermod -d /home/new_home <username>`  # Modify a user (e.g., change home directory)
- `sudo usermod -aG <group-name> <username>`   # Add a user to a group
- `sudo usermod -L <username>`                # Lock a user account
- `sudo usermod -U <username>`                # Unlock a user account

---

## Viewing User Information
- `cat /etc/passwd`                           # List all users on the system
- `id <username>`                             # Display current user details (UID, GID, groups)
- `groups <username>`                         # Display all groups a user is a member of
- `who`                                       # Show currently logged-in users
- `w`                                         # Display information about currently logged-in users
- `last`                                      # Check last login information of users
- `getent passwd`                             # Display all user accounts
- `lastlog`                                   # Show users' login records

---

## Password Expiry Management
- `sudo chage -E YYYY-MM-DD <username>`       # Change user password expiration date
- `sudo chage -M 30 <username>`               # Set maximum days before password change required
- `sudo chage -M -1 <username>`               # Disable password expiry
- `sudo chage -l <username>`                  # Display password expiration information

