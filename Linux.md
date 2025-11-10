
# 🐧 Linux Commands and Real-World Scenarios for DevOps

> **Author:** Ali Masiu Zama
> **Purpose:** Daily practice reference for DevOps learners — includes essential Linux commands and real-world use cases.

---

## 📁 1. File & Directory Management

```bash
ls -l                 # List files in long format
ls -a                 # List all files including hidden
cd /path              # Change directory
pwd                   # Show current directory
mkdir dir_name        # Create directory
rmdir dir_name        # Remove empty directory
rm -rf dir_name       # Remove directory with files
cp file1 file2        # Copy files
mv file1 file2        # Move/Rename file
touch file.txt        # Create empty file
cat file.txt          # View file content
head -n 10 file.txt   # Show first 10 lines
tail -n 10 file.txt   # Show last 10 lines
less file.txt         # View file with scroll
find /path -name "file.txt"   # Search file by name
```

---

## 🧑‍💻 2. File Permissions & Ownership

```bash
chmod 755 file.txt         # Change permission (rwxr-xr-x)
chown user:group file.txt  # Change file owner
ls -l                      # Check permissions
```

---

## ⚙️ 3. System Information

```bash
uname -a             # Show system info
hostname              # Display hostname
df -h                 # Disk space in human readable format
du -sh *              # Show folder sizes
top                   # Show running processes
htop                  # Better process viewer (install if needed)
free -m               # Show memory usage
uptime                # Show system uptime
whoami                # Current user
id                    # Display user ID and groups
ps aux                # Show all running processes
```

---

## 🌐 4. Networking

```bash
ping google.com             # Test connectivity
curl ifconfig.me             # Show public IP
ip a                         # Show IP configuration
netstat -tuln                # Show listening ports
ss -tuln                     # Alternative to netstat
scp file.txt user@ip:/path   # Secure copy to remote
rsync -avz file user@ip:/dir # Sync files
wget URL                     # Download file
curl -O URL                  # Download file
```

---

## 🧱 5. Package Management (Ubuntu/Debian)

```bash
sudo apt update          # Update package list
sudo apt upgrade -y      # Upgrade all packages
sudo apt install nginx   # Install package
sudo apt remove nginx    # Remove package
dpkg -l                  # List installed packages
```

---

## 🐚 6. Shell & Scripting Basics

```bash
echo "Hello Ali"         # Print message
history                  # Show command history
alias ll='ls -la'        # Create alias
export VAR=value         # Create environment variable
env                      # Show environment variables
which command            # Show command path
type command             # Show command type
man command              # Manual page of command
```

---

## 🧩 7. Archive & Compression

```bash
tar -cvf files.tar files/     # Create tar archive
tar -xvf files.tar            # Extract tar file
gzip file.txt                 # Compress file
gunzip file.txt.gz            # Decompress file
```

---

## 🧰 8. User Management

```bash
sudo adduser username         # Add new user
sudo passwd username          # Change password
sudo deluser username         # Delete user
sudo usermod -aG sudo username # Add user to sudo group
who                           # Show logged-in users
```

---

## 🔐 9. Process Management

```bash
ps -ef | grep nginx     # Find process by name
kill PID                # Kill process by PID
killall nginx           # Kill all processes by name
systemctl status nginx  # Check service status
systemctl restart nginx # Restart service
systemctl stop nginx    # Stop service
```

---

## 📜 10. Log Monitoring

```bash
tail -f /var/log/syslog          # Monitor live logs
journalctl -u nginx              # Logs of a specific service
dmesg | tail                    # Kernel messages
```

---

## 🧮 11. Disk & Storage

```bash
lsblk                  # List block devices
mount /dev/sdb1 /mnt   # Mount drive
umount /mnt            # Unmount drive
blkid                  # Display UUID of drives
```

---

## 💡 12. Useful Shortcuts

```bash
!!                     # Repeat last command
!n                     # Run nth command from history
Ctrl + r               # Search previous commands
Tab-Tab                # Auto-complete
Ctrl + c               # Stop process
Ctrl + d               # Logout terminal
```

---

# 🧩 Real-World Scenarios for DevOps Practice

Each scenario combines multiple commands to simulate real tasks you’ll do as a DevOps engineer.

---

## ⚙️ 1️⃣ User and Permission Management

```bash
sudo adduser devuser
sudo usermod -aG sudo devuser
su - devuser
whoami
sudo ls /root
```

**Goal:** Create a new user, give sudo access, and verify permissions.
**Learn:** User creation · Group management · Permission control

---

## 🌐 2️⃣ Service Monitoring (NGINX Example)

```bash
sudo apt install nginx -y
systemctl start nginx
systemctl enable nginx
systemctl status nginx
curl localhost
tail -f /var/log/nginx/access.log
```

**Goal:** Install and monitor NGINX web server.
**Learn:** Service control · Log monitoring · Network testing

---

## 🧠 3️⃣ Process & Resource Monitoring

```bash
top
ps -ef | grep python
kill <PID>
free -m
df -h
```

**Goal:** Identify and stop a high CPU process.
**Learn:** Process handling · Memory and disk monitoring

---

## 🧰 4️⃣ File Backup & Compression

```bash
mkdir /backup
cp /var/log/syslog /backup/
tar -czvf backup_logs.tar.gz /backup/
ls -lh
```

**Goal:** Backup logs and compress them.
**Learn:** File management · Archiving and compression

---

## ⚙️ 5️⃣ Automation with Shell Script

```bash
nano backup.sh
```

Paste inside the file:

```bash
#!/bin/bash
tar -czvf /backup/$(date +%F)_logs.tar.gz /var/log
```

Then run:

```bash
chmod +x backup.sh
./backup.sh
```

**Goal:** Automate log backup.
**Learn:** Bash scripting · Scheduling automation

---

## 🌍 6️⃣ Networking Troubleshooting

```bash
ping 8.8.8.8
curl google.com
ip a
netstat -tuln
```

**Goal:** Check network connectivity and open ports.
**Learn:** Network diagnosis · Port & service visibility

---

## 💾 7️⃣ Disk & Storage Management

```bash
lsblk
sudo mount /dev/xvdb1 /mnt
df -h
sudo umount /mnt
```

**Goal:** Mount an extra disk and verify space.
**Learn:** Disk operations · Mounting/unmounting

---

## 🔍 8️⃣ Log Analysis Challenge

```bash
grep "sshd" /var/log/auth.log | grep "$(date +%b' '%d)" | wc -l
```

**Goal:** Find how many times SSH was used today.
**Learn:** Log parsing · Command chaining

---
