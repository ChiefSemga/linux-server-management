# Group Management Commands

## Create a New Group
- `sudo groupadd <group-name>`         # Create a new group

---

## Delete a Group
- `sudo groupdel <group-name>`         # Delete a group

---

## Modify an Existing Group
- `sudo groupmod -n <new-group-name> <old-group-name>`  # Change group name
- `sudo groupmod -g <new-gid> <group-name>`             # Change the group ID (GID)

---

## User Group Management
- `sudo usermod -aG <group-name> <username>`  # Add a user to a group
- `sudo gpasswd -d <username> <group-name>`   # Remove a user from a group

---

## Viewing Group Information
- `cat /etc/group`                 # List all groups on the system
- `groups <username>`              # Display the groups a user belongs to
- `getent group <group-name>`      # Show the members of a group
- `getent group <group-name>`      # Display the GID of a group
- `id <username>`                  # List all groups a user is part of

