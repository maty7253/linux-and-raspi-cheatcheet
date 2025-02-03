# Linux & Raspberry Pi OS Command Cheatsheet

## Table of Contents
- [Basic Navigation](#basic-navigation)
- [File Operations](#file-operations)
- [System Information](#system-information)
- [Package Management](#package-management)
- [Process Management](#process-management)
- [User Management](#user-management)
- [File Permissions](#file-permissions)
- [Networking](#networking)
- [Text Editing](#text-editing)
- [System Control](#system-control)
- [Raspberry Pi Specific](#raspberry-pi-specific)
- [Power Tips](#power-tips)

## Basic Navigation

### Essential Navigation Commands
```bash
pwd           # Print Working Directory - shows current location
ls            # List files and directories
ls -l         # Detailed list
ls -a         # Show hidden files
ls -la        # Detailed list including hidden files
cd directory  # Change Directory
cd ..         # Go up one directory
cd ~          # Go to home directory
cd /          # Go to root directory
clear         # Clear terminal screen (or Ctrl+L)
```

### Directory Shortcuts
```bash
.             # Current directory
..            # Parent directory
~             # Home directory
/             # Root directory
-             # Previous directory
```

## File Operations

### Basic File Commands
```bash
touch file.txt          # Create empty file
mkdir directory         # Create directory
mkdir -p dir1/dir2     # Create nested directories
rm file.txt            # Remove file
rm -r directory        # Remove directory and contents
rm -rf directory       # Force remove directory (be careful!)
cp file1 file2         # Copy file
cp -r dir1 dir2       # Copy directory
mv file1 file2        # Move/rename file
mv dir1 dir2          # Move/rename directory
```

### File Viewing
```bash
cat file.txt           # Display file contents
less file.txt         # View file with pagination
head file.txt         # Show first 10 lines
tail file.txt         # Show last 10 lines
tail -f file.txt      # Follow file changes in real-time
nano file.txt         # Edit file with nano editor
vim file.txt          # Edit file with vim editor
```

### File Search
```bash
find . -name "*.txt"   # Find files by name
grep "text" file.txt   # Search for text in file
grep -r "text" .       # Search recursively in current directory
locate filename        # Find file in database
which command         # Show path of command
```

## System Information

### System Commands
```bash
uname -a              # All system information
hostname              # System hostname
df -h                # Disk space usage
du -sh directory     # Directory size
free -h              # Memory usage
top                  # Process viewer (interactive)
htop                 # Enhanced process viewer
date                 # Current date/time
uptime               # System uptime
whoami               # Current user
```

## Package Management

### APT (Debian/Ubuntu/Raspberry Pi OS)
```bash
apt update                    # Update package list
apt upgrade                   # Upgrade all packages
apt install package           # Install package
apt remove package            # Remove package
apt autoremove               # Remove unused packages
apt search keyword           # Search for package
apt list --installed         # List installed packages
```

## Process Management

### Process Commands
```bash
ps                    # Show running processes
ps aux               # Show all processes
kill pid             # Kill process by ID
killall process      # Kill process by name
top                  # Process monitor
htop                 # Enhanced process monitor
bg                   # Send process to background
fg                   # Bring process to foreground
Ctrl+C               # Stop current process
Ctrl+Z               # Suspend current process
```

## User Management

### User Commands
```bash
sudo command         # Run command as root
su username          # Switch user
passwd              # Change password
adduser username    # Add new user
deluser username    # Delete user
groups              # Show user groups
usermod             # Modify user
```

## File Permissions

### Permission Commands
```bash
chmod 755 file      # Change file permissions
chmod +x file       # Make file executable
chown user file     # Change file owner
chgrp group file    # Change file group
```

### Permission Numbers
- 4 = read (r)
- 2 = write (w)
- 1 = execute (x)
- 0 = no permission

Common combinations:
- 755 = rwxr-xr-x
- 644 = rw-r--r--
- 777 = rwxrwxrwx (avoid using!)

## Networking

### Network Commands
```bash
ifconfig            # Network interfaces
ip addr             # IP addresses (modern)
ping host          # Test connectivity
netstat -tulpn     # Show active ports
ssh user@host      # SSH connection
scp file user@host:path  # Secure copy
wget url           # Download file
curl url           # Transfer data
```

### WiFi (Raspberry Pi)
```bash
iwconfig           # Wireless info
iwlist scan        # Scan for networks
raspi-config       # Configure WiFi (GUI)
```

## Text Editing

### Nano Editor
```bash
Ctrl+O             # Save file
Ctrl+X             # Exit
Ctrl+K             # Cut line
Ctrl+U             # Paste line
Ctrl+W             # Search
```

### Vim Editor
```bash
i                  # Enter insert mode
Esc                # Exit insert mode
:w                 # Save
:q                # Quit
:wq                # Save and quit
:q!               # Quit without saving
```

## System Control

### System Commands
```bash
shutdown -h now    # Shutdown immediately
shutdown -r now    # Restart immediately
reboot            # Restart
systemctl start service   # Start service
systemctl stop service    # Stop service
systemctl status service  # Check service status
systemctl enable service  # Enable at boot
systemctl disable service # Disable at boot
```

## Raspberry Pi Specific

### Raspberry Pi Commands
```bash
raspi-config       # Raspberry Pi configuration tool
vcgencmd measure_temp     # CPU temperature
vcgencmd get_mem arm     # ARM memory split
vcgencmd get_mem gpu     # GPU memory split
gpio readall      # Read all GPIO pins
pinout            # Show GPIO pinout
```

### GPIO Control
```bash
gpio -g mode pin out     # Set pin as output
gpio -g write pin 1      # Set pin HIGH
gpio -g write pin 0      # Set pin LOW
gpio -g read pin        # Read pin state
```

## Power Tips

### Keyboard Shortcuts
```bash
Ctrl+A            # Move to beginning of line
Ctrl+E            # Move to end of line
Ctrl+U            # Clear line before cursor
Ctrl+K            # Clear line after cursor
Ctrl+R            # Search command history
Tab               # Auto-complete command/path
Ctrl+L            # Clear screen
Ctrl+D            # Exit terminal
```

### Command History
```bash
history          # Show command history
!!               # Repeat last command
!n               # Repeat command number n
!string          # Repeat last command starting with string
```

### Redirections
```bash
command > file   # Output to file (overwrite)
command >> file  # Output to file (append)
command < file   # Input from file
command1 | command2  # Pipe output to another command
command &        # Run in background
command1 && command2 # Run command2 if command1 succeeds
```

### Aliases
Add these to ~/.bashrc:
```bash
alias ll='ls -la'
alias update='sudo apt update && sudo apt upgrade'
alias temp='vcgencmd measure_temp'
alias ports='netstat -tulpn'
```

Remember to source your .bashrc after adding aliases:
```bash
source ~/.bashrc
```

## Tips for Learning
1. Use `man command` or `command --help` to get help
2. Practice in a safe environment
3. Make backups before major changes
4. Use tab completion to avoid typing errors
5. Keep a backup of your important commands
6. Use `history` to recall commands
7. Create aliases for frequently used commands

## Safety Tips
1. Always verify before using `rm -rf`
2. Double-check `sudo` commands
3. Make backups before system changes
4. Be careful with permissions (chmod)
5. Verify network commands
6. Use `sudo` only when necessary
7. Keep system updated regularly
```
