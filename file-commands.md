## List files in a directory
```bash
ls                          # List files in the current directory
ls -l                       # List files with detailed information
ls -a                       # List all files, including hidden
ls -lh                      # List files with human-readable sizes

---

## Changing Directories
```bash
cd <directory>              # Change to a specified directory
cd ..                       # Move one directory up
cd /                        # Go to the root directory
cd ~                        # Go to the home directory

---

## Creating files and directories 
```bash
touch <file>                # Create an empty file
mkdir <directory>           # Create a new directory

---

## Copying Files 
```bash
cp <source> <destination>   # Copy a file or directory
cp -r <source> <destination> # Copy a directory recursively
cp -i <source> <destination> # Prompt before overwriting files

---

## Moving or Renaming Files
```bash
mv <source> <destination>    # Move or rename a file or directory
mv <source> <destination>    # Move file to a different directory (or rename)

---

## Removing Files and Directories 
```bash
rm <file>                   # Remove a file
rm -r <directory>            # Remove a directory and its contents
rm -f <file>                 # Force remove a file without prompt
rm -rf <directory>           # Force remove a directory and its contents

---

## Viewing File Contents
```bash
cat <file>                  # Display the content of a file
less <file>                 # View the content of a file with pagination
more <file>                 # Similar to less, but with basic functionality
head <file>                 # Display the first 10 lines of a file
tail <file>                 # Display the last 10 lines of a file
tail -f <file>              # Follow the file, useful for log files

---

## File Permissions
```bash
chmod <permissions> <file>  # Change file permissions
chmod 755 <file>            # Set rwx permissions for owner, rx for others
chown <user>:<group> <file> # Change file owner and group
chgrp <group> <file>        # Change file group

---

## File Search
```bash
find <directory> -name <file> # Search for a file by name
find <directory> -type f     # Search for files
find <directory> -type d     # Search for directories

---

## File Compression and Extraction
```bash
tar -cvf <archive-name>.tar <directory>      # Create a tar archive
tar -xvf <archive-name>.tar                  # Extract a tar archive
tar -czvf <archive-name>.tar.gz <directory>  # Create a compressed tar archive (gzip)
tar -xzvf <archive-name>.tar.gz              # Extract a compressed tar archive (gzip)
gzip <file>                                  # Compress a file
gunzip <file>.gz                             # Decompress a gzip file
zip <archive-name>.zip <file>                # Compress a file into a zip archive
unzip <archive-name>.zip                     # Extract a zip archive

---

## Checking Disk Space
```bash
df -h                        # Display disk space usage in human-readable format
du -sh <directory>            # Display disk usage of a directory (human-readable)

---

## File Comparism
```bash
diff <file1> <file2>          # Compare two files
cmp <file1> <file2>           # Compare two files byte by byte

---

## Creating Symbolic and Hard Links
```bash
ln <source> <link>            # Create a hard link
ln -s <source> <link>         # Create a symbolic (soft) link

---

## File Information
```bash
file <file>                  # Determine file type
stat <file>                  # Display detailed information about a file

