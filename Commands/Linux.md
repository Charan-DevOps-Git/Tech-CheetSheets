# Linux Commands Cheatsheet for DevOps

## Table of Contents

1. System Basics
2. File Operations
3. Process Management
4. Networking
5. User Management
6. Package Management
7. Disk Management
8. SSH and File Transfer
9. Monitoring and Performance
10. Scripting and Automation

# System Basics

## Display System Information

- uname -a: Show all system information.
- hostname: Display the system's hostname.
- uptime: Show how long the system has been running.
- whoami: Display the current logged-in user.

## Manage System Time
- date: Display the current date and time.
- timedatectl: View and change system date and time.

# File Operations

## Navigation
- ls: List directory contents.
- cd [directory]: Change the current directory.
- pwd: Print the current working directory.

## File and Directory Manipulation
- cp [source] [destination]: Copy files or directories.
- mv [source] [destination]: Move or rename files or directories.
- rm [file]: Remove files.
- rm -r [directory]: Remove directories and their contents.
- mkdir [directory]: Create a new directory.
- touch [file]: Create a new empty file or update the timestamp of an existing file.

## Viewing and Editing Files
- cat [file]: Display the contents of a file.
- less [file]: View the contents of a file one page at a time.
- head [file]: Display the first 10 lines of a file.
- tail [file]: Display the last 10 lines of a file.
- nano [file]: Edit a file using the Nano text editor.
- vim [file]: Edit a file using the Vim text editor.

# Process Management

## Viewing Processes

- ps: Display a snapshot of current processes.
- top: Display live system processes and resource usage.
- htop: Interactive process viewer (requires installation).

## Managing Processes
- kill [PID]: Terminate a process by its PID.
- killall [process_name]: Terminate all processes with the specified name.
- pkill [process_name]: Send a signal to processes with the specified name.

# Networking

## Network Configuration
- ifconfig: Display or configure network interfaces (deprecated, use ip).
- ip a: Display IP addresses and properties.
- ip route: Display and modify the routing table.

## Network Diagnostics
- ping [host]: Test connectivity to a host.
- traceroute [host]: Display the route packets take to a network host.
- netstat: Network statistics (deprecated, use ss).
- ss: Display network socket information.
- curl [url]: Transfer data from or to a server.

# User Management

## User and Group Management
- adduser [username]: Add a new user.
- userdel [username]: Delete a user.
- usermod -aG [group] [username]: Add a user to a group.
- passwd [username]: Change a user's password.

## Permissions
- chmod [permissions] [file]: Change file permissions.
- chown [user]:[group] [file]: Change file owner and group.

# Package Management

## Debian-based Systems (e.g., Ubuntu)
- apt-get update: Update the package list.
- apt-get upgrade: Upgrade all packages.
- apt-get install [package]: Install a package.
- apt-get remove [package]: Remove a package.

## Red Hat-based Systems (e.g., CentOS)
- yum update: Update the package list.
- yum install [package]: Install a package.
- yum remove [package]: Remove a package.

## Universal Package Managers
- snap install [package]: Install a snap package.
- flatpak install [remote] [package]: Install a flatpak package.

# Disk Management

## Disk Usage
- df -h: Display disk space usage in human-readable format.
- du -h [directory]: Display disk usage of a directory.

## Disk Partitioning
- fdisk -l: List disk partitions.
- mkfs.ext4 /dev/[partition]: Format a partition with ext4 filesystem.

# SSH and File Transfer

## SSH
- ssh [user]@[host]: Connect to a host via SSH.
- ssh-keygen: Generate SSH key pairs.
- ssh-copy-id [user]@[host]: Copy SSH key to a host.

## File Transfer
- scp [source] [user]@[host]:[destination]: Securely copy files to a remote host.
- rsync -avz [source] [user]@[host]:[destination]: Sync files/directories to a remote host.

# Monitoring and Performance

## System Monitoring
- vmstat: Report virtual memory statistics.
- iostat: Report CPU and I/O statistics.
- free -h: Display free and used memory.

## Log Management
- tail -f /var/log/[logfile]: Monitor a log file in real-time.
- journalctl: Query and display logs from systemd journal.

# Scripting and Automation

## Shell Scripting
- #!/bin/bash: Shebang for bash scripts.
- $VAR: Access a variable.
- $(command): Command substitution.

## Cron Jobs
- crontab -e: Edit cron jobs.
- crontab -l: List all cron jobs.
- crontab -r: Remove all cron jobs.

## Example Crontab Entry
```
# Minute Hour Day Month DayOfWeek Command
0 2 * * * /path/to/script.sh  # Run script at 2 AM daily
```
