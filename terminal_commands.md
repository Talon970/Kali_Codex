# Kali Linux Codex - Your Living Cheatsheet

## 📘📘00_System Management (The Foundation)📘📘

### apt (Advanced Package Tool)
# Updates the list of available packages. Do this first, always.
sudo apt update

# Upgrades all installed packages to the newest version.
sudo apt upgrade -y

# Combines update and upgrade into one command. The weekly workhorse.
sudo apt update && sudo apt upgrade -y

# Removes packages that were installed automatically to satisfy dependencies but are no longer needed.
sudo apt autoremove -y

# Cleans the local repository of retrieved package files. Frees up disk space.
sudo apt clean

# Removes orphaned packages and their configuration files.
sudo apt autoremove --purge

### shutdown
# Schedules a system shutdown in 60 minutes.
sudo shutdown -h +60

# Cancels a pending shutdown.
sudo shutdown -c

### systemctl (Service Manager)
# Starts a service (e.g., ssh).
sudo systemctl start <service_name>

# Stops a service.
sudo systemctl stop <service_name>

# Checks the status of a service.
sudo systemctl status <service_name>

# Enables a service to start on boot.
sudo systemctl enable <service_name>

# Change to TTY(Desktop without GUI). (you are getting logged out)
STRG + ALT + F4

# Change back to the GUI Desktop. (you have to loggin again)
sudo systemctl restart lightdm

## 📘📘01_Navigation & File System (The Basics)📘📘

### pwd (Print Working Directory)
# Shows the full path of your current directory.
pwd

### ls (List)
# Lists files and directories in the current location.
ls
# Lists in long format with details (permissions, owner, size).
ls -la

### cd (Change Directory)
# Navigates into a directory.
cd /var/www/html
# Goes back one level.
cd ..
# Goes to your home directory.
cd ~

### find
# Finds files by name within the system. Case-insensitive.
find / -iname "<filename>"

### grep (Global Regular Expression Print)
# Searches for a specific string within a file.
grep "password" /etc/shadow

### cp, mv, rm, mkdir (File Operations)
# Copies a file.
cp source.txt destination.txt
# Moves or renames a file.
mv old_name.txt new_name.txt
# Removes a file. Use with caution.
rm file.txt
# Removes a directory and its contents recursively. VERY DANGEROUS.
rm -r /path/to/directory
# Creates a new directory.
mkdir new_directory

## 📘📘02_Network Analysis (The Recon Phase)📘📘

### ip
# Shows your IP address and network interface information.
ip addr

### ping
# Checks connectivity to a host.
ping 8.8.8.8

### netstat / ss
# Shows active network connections. `ss` is the modern replacement.
sudo netstat -tulpn
sudo ss -tulpn

### nmap (Network Mapper)
# The #1 port scanner. This is a deep tool.
# Scans the top 1000 ports of a target, detects OS and services.
sudo nmap -A <target_ip>

## 📘📘03_User & Permission Management (The Privilege Phase)📘📘

### whoami / id
# Shows the current user / Shows detailed user and group info.
whoami
id

### sudo / su
# Executes a command with superuser privileges.
sudo <command>
# Switches to the root user.
su -

### chmod / chown (Change Mode / Change Owner)
# Changes file permissions. Gives the owner read/write/execute permissions.
chmod 700 script.sh
# Changes the owner of a file.
sudo chown user:group file.txt
