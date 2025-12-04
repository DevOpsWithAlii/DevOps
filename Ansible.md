# 🚀 Ansible Zero to Hero

![Ansible Logo](https://github.com/ansible/logos/blob/main/community-usage/correct-use-white.png)  
*A comprehensive guide to mastering Ansible for DevOps Engineers*

---

# 🧩 Ansible Master–Node Setup (Ubuntu)

### 1️⃣ Update & Install Ansible

```bash
sudo apt-get update -y
sudo apt install ansible -y
```

---

### 2️⃣ SSH Key Setup (if not already done)

```bash
cd ~/.ssh
vim ansible_key          # paste your private key if you created it earlier
chmod 700 ~/.ssh
chmod 600 ~/.ssh/ansible_key
```

---

### 3️⃣ Verify Key & Connect to Node

```bash
ssh -i ~/.ssh/ansible_key ubuntu@3.145.29.59
```

---
### 3️.1 Fix errore if not connect servers

```bash
export ANSIBLE_HOST_KEY_CHECKING=False
```

---

### 4️⃣ Check Ansible Inventory File

```bash
cat /etc/ansible/hosts
```

---

### 5️⃣ Create Custom Inventory Directory

```bash
mkdir ~/ansible
cd ~/ansible
vim hosts
```

**Example `hosts` file:**

```
[servers]
server1 ansible_host=3.145.29.59
server2 ansible_host=3.150.114.25

[all:vars]
ansible_python_interpreter=/usr/bin/python3
```

---

### 6️⃣ Verify Inventory

```bash
ansible-inventory --list -y -i /home/ubuntu/ansible/hosts
```

---

### 7️⃣ Test Ansible Connection

```bash
ansible all -m ping -i /home/ubuntu/ansible/hosts --private-key=~/.ssh/ansible_key
```

---

### 8️⃣ Run Test Command on All Nodes

```bash
ansible all -a "free -h" 
```

### 📦 **Install Nginx (Ubuntu/Debian)**

```bash
ansible all -m apt -b -a "name=nginx state=present update_cache=yes" 
```
---

### 🛑 **Stop and Disable Nginx**

```bash
# Stop the nginx service
ansible all -m ansible.builtin.service -a "name=nginx state=stopped" -b 

# Disable nginx from starting on boot
ansible all -a "systemctl disable nginx" -b 
```

---

### ❌ **Remove Nginx**

```bash
# Uninstall nginx (keeps config files)
ansible all -m apt -a "name=nginx state=absent" -b 

# OR uninstall and remove config files
ansible all -m apt -a "name=nginx state=absent purge=yes" -b 
```

---

### 📊 **System Monitoring Commands**

```bash
# Memory usage
ansible all -a "free -h" 

# Disk usage
ansible all -a "df -h" 

# CPU and uptime
ansible all -a "uptime" 

# Hostname
ansible all -a "hostname" 

# OS info
ansible all -a "cat /etc/os-release" 
```

---

### 🔧 **Package Management Examples**

```bash
# Install multiple packages
ansible all -m apt -a "name=curl,git,state=present update_cache=yes" -b 

# Upgrade all packages
ansible all -m apt -a "upgrade=dist" -b 
```

---

### 🛠️ **Service Management Examples**

```bash
# Start nginx
ansible all -m ansible.builtin.service -a "name=nginx state=started" -b 

# Restart nginx
ansible all -m ansible.builtin.service -a "name=nginx state=restarted" -b 

# Check if nginx is active
ansible all -a "systemctl is-active nginx" -b 
```

---

### 📁 **Useful File/Log Commands**

```bash
# View disk usage by user
ansible all -a "du -sh /home/*" -b 

# Show last 50 lines of syslog
ansible all -a "tail -n 50 /var/log/syslog" -b 
```

---

## ✅ Notes

* All commands assume you have passwordless SSH set up using `ansible_key`.
* `-b` is used to escalate privilege (like `sudo`) where required.
* Replace `all` with group names if your inventory defines them (e.g., `webservers`).

---
