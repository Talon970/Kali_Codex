# Kali Linux Codex - Your Living Cheatsheet

## 📘📘00_System Management (The Foundation)📘📘

nvim ~/.bashrc

datei so andern wie gewollt und dann:
source ~/.bashrc

docker images

docker image prune


# first go in cd ~/Playground in all 3 terminals and open tehese 3 commands in the terminals just once ina terminal
dev-up

dev-shell

dev-chat

dev-stop

# Allgemeine Tipps:
# Daily Shutdown
sudo crontab -e

# zum nachschauen was dadrin steht
sudo crontab -l

# dann NVIM auswhalen oder einen anderen editor deiner wahl und diese zeile einfugen:
0 16 * * * /sbin/shutdown -h now

mit:
sudo crontab -l
uberpr[fen ob es richtig ist es sollte genau der inhalt ausgegeben werden der eingefugt wurde + das was schon in der datei war, falls darin etwas war.

# abbruch des Shutdowns fu diesen tag:
sudo shutdown -c

http://http.net
um sich mit einem WLAN zu verbinden ist eine haufige URL.

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

# Find Desktop-Name
xrandr --query

# Set brightness (external monitor: 1.0 for full brightness)
xrandr --output HDMI-1 --brightness 0.7

# Set brightness (Main monitore)
xrandr --output eDP-1 --brightness 0.7

# Open the Nano Editor with the Setting to Shut down the Computer automaticly at a given time
crontab -e
0 19 * * 1-5 systemctl poweroff

# install extention Continue in VS Code

# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# tell Ollama to get the ¨LLama Modul¨
ollama pull codellama:7b-instruct

# tell Ollama to get the ¨LLama Modul¨
ollama pull starcoder2:3b

# vs code config
nano ~/.continue/config.json
contents:

{
  "models": [
    {
      "title": "Llama 7B - General",
      "provider": "ollama",
      "model": "llama3.2:7b",
      "apiBase": "http://localhost:11434"
    },
    {
      "title": "StarCoder2 3B - Coding",
      "provider": "ollama",
      "model": "starcoder2:3b", 
      "apiBase": "http://localhost:11434"
    }
  ],
  "tabAutocompleteModel": {
    "title": "StarCoder2 3B - Coding",
    "provider": "ollama",
    "model": "starcoder2:3b",
    "apiBase": "http://localhost:11434"
  }
}


# open server in Terminal(keep this terminal in the background)
ollama serve

# open LLM in Terminal
ollama run llama3.2:7b
or
ollama run starcoder2:3b

# shows open process
ps aux | grep ollama

# web use
http://localhost:11434

# find process
ps aux | grep <prozessname>

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
