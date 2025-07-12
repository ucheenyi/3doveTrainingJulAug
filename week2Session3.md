# Week 2 Session 7: System Services & Networking
## Class Notes - "Workshop Operations & External Connections"

---

## 🎯 What You'll Learn Today
By the end of this session, you will be able to:
- Start, stop, and check Linux services
- View basic network information
- Set up simple firewall rules
- Connect to other computers using SSH
- Fix common network problems

---

## 📚 Part 1: Managing Workshop Services (40 minutes)

### What Are System Services?

#### Simple Story
Think of system services as different workers in your workshop who do jobs automatically:
- **SSH worker** = Security guard (lets people in remotely)
- **Web server worker** = Receptionist (serves web pages)
- **Database worker** = File clerk (manages data)
- **Cron worker** = Scheduler (runs tasks at set times)

These workers start automatically when you turn on your computer and keep working in the background.

### Basic Service Commands

#### Checking What's Running
```bash
# See what services are running
systemctl status

# Check one specific service
systemctl status ssh

# Quick check - is it running?
systemctl is-active ssh
```

**What this tells you:**
- Green "active (running)" = service is working
- Red "inactive (dead)" = service is stopped
- You'll also see when it started and recent messages

#### Starting and Stopping Services
```bash
# Start a service
sudo systemctl start apache2

# Stop a service
sudo systemctl stop apache2

# Restart a service (stop then start)
sudo systemctl restart apache2

# Make service start automatically when computer boots
sudo systemctl enable apache2

# Stop service from starting automatically
sudo systemctl disable apache2
```

**Remember:** 
- `start/stop` = right now only
- `enable/disable` = what happens when computer starts up

#### Looking at Service Messages
```bash
# See recent messages from a service
journalctl -u ssh

# Follow messages in real-time (like tail -f)
journalctl -u ssh -f

# See messages from the last hour
journalctl -u ssh --since "1 hour ago"
```

### 🔧 Practice Exercise 1: Service Explorer
**Goal**: Learn about your system's services
```bash
# 1. What services are running?
systemctl --type=service --state=running

# 2. Check SSH service
systemctl status ssh

# 3. Look at SSH messages
journalctl -u ssh --since "today"

# 4. What starts automatically?
systemctl list-unit-files --type=service --state=enabled
```

---

## 🌐 Part 2: Basic Networking (40 minutes)

### Understanding Your Network

#### Simple Story
Your computer's network is like a mail system:
- **IP address** = Your postal address
- **Ports** = Different mailboxes at your address
- **Router** = Post office that delivers messages
- **Firewall** = Security guard checking mail

### Finding Network Information

#### Your Computer's Address
```bash
# See your IP address (modern way)
ip addr show

# See your IP address (older way)
ifconfig

# See how messages get delivered
ip route show
```

**What to look for:**
- `eth0` or `enp0s3` = wired network connection
- `wlan0` = wireless connection
- `lo` = loopback (computer talking to itself)
- Numbers like `192.168.1.100` = your IP address

#### Testing Network Connections
```bash
# Test if you can reach Google
ping google.com

# Test 4 times then stop
ping -c 4 google.com

# See the path to Google
traceroute google.com

# Check if Google's name resolves to an IP
nslookup google.com
```

#### What Ports Are Open?
```bash
# See what services are listening for connections
ss -tuln

# Older way to see the same thing
netstat -tuln
```

**Understanding the output:**
- `0.0.0.0:22` = SSH listening on all network interfaces
- `127.0.0.1:3306` = MySQL only listening locally
- `*:80` = Web server listening on all interfaces

### Simple Firewall Setup

#### Think of Firewall as a Bouncer
The firewall decides who can enter your computer and through which doors (ports).

#### Basic Firewall Commands
```bash
# Check firewall status
sudo ufw status

# Turn on firewall
sudo ufw enable

# Allow SSH connections
sudo ufw allow ssh

# Allow web traffic
sudo ufw allow 80

# Allow secure web traffic
sudo ufw allow 443

# Block a specific port
sudo ufw deny 23

# See all rules
sudo ufw status numbered
```

**Simple Rules:**
- Allow = let traffic through
- Deny = block traffic
- SSH = port 22 (remote access)
- HTTP = port 80 (websites)
- HTTPS = port 443 (secure websites)

### 🔧 Practice Exercise 2: Network Detective
**Goal**: Explore your network setup
```bash
# 1. What's your IP address?
ip addr show
# Look for numbers like 192.168.x.x or 10.x.x.x

# 2. Can you reach the internet?
ping -c 3 google.com

# 3. What services are listening?
ss -tuln
# Look for :22 (SSH), :80 (web), :443 (secure web)

# 4. Check your firewall
sudo ufw status
```

---

## 🔐 Part 3: Connecting to Other Computers (30 minutes)

### SSH - Secure Remote Access

#### Simple Story
SSH is like a secure phone line between computers. You can control another computer as if you were sitting in front of it, but all communication is encrypted so nobody can spy on you.

### Basic SSH Setup

#### Starting SSH Service
```bash
# Install SSH server (if needed)
sudo apt install openssh-server

# Start SSH service
sudo systemctl start ssh

# Make SSH start automatically
sudo systemctl enable ssh

# Check it's running
systemctl status ssh
```

#### Connecting to Other Computers
```bash
# Connect to another computer
ssh username@192.168.1.100

# Connect to another computer by name
ssh username@other-computer

# Run a single command on remote computer
ssh username@other-computer 'ls -la'
```

### Making SSH More Secure

#### Basic Security Settings
```bash
# Edit SSH configuration
sudo nano /etc/ssh/sshd_config

# Find and change these lines:
# PermitRootLogin no          # Don't allow root login
# Port 2222                   # Change from default port 22
# MaxAuthTries 3              # Only 3 password attempts

# Restart SSH after changes
sudo systemctl restart ssh
```

#### SSH Keys (Optional - Advanced)
SSH keys are like a special lock and key system that's more secure than passwords.

```bash
# Create SSH key pair
ssh-keygen -t rsa

# Copy your key to another computer
ssh-copy-id username@other-computer

# Now you can connect without password
ssh username@other-computer
```

### Transferring Files
```bash
# Copy file to remote computer
scp myfile.txt username@other-computer:/home/username/

# Copy file from remote computer
scp username@other-computer:/home/username/remotefile.txt .

# Copy entire folder
scp -r myfolder/ username@other-computer:/home/username/
```

### 🔧 Practice Exercise 3: SSH Basics
**Goal**: Set up secure remote access
```bash
# 1. Make sure SSH is running
systemctl status ssh

# 2. Allow SSH through firewall
sudo ufw allow ssh

# 3. Test SSH to yourself
ssh localhost
# (Type 'exit' to disconnect)

# 4. Check who's connected
who
```

---

## 🛠️ Simple Lab Challenge: Basic Network Setup

### Your Mission
Set up a basic secure network configuration for your workshop computer.

### What You Need to Do
1. **Check Services**: Make sure SSH is running and will start automatically
2. **Configure Firewall**: Allow SSH and web traffic, block everything else
3. **Test Network**: Make sure you can reach the internet
4. **Secure SSH**: Change SSH to use a different port

### Step-by-Step Guide

#### Step 1: Service Check
```bash
# Check and start SSH
systemctl status ssh
sudo systemctl enable ssh
sudo systemctl start ssh
```

#### Step 2: Basic Firewall
```bash
# Enable firewall
sudo ufw enable

# Allow necessary services
sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443

# Check rules
sudo ufw status
```

#### Step 3: Test Network
```bash
# Test internet connection
ping -c 3 google.com

# Check what ports are open
ss -tuln | grep :22
ss -tuln | grep :80
```

#### Step 4: SSH Security (Optional)
```bash
# Change SSH port
sudo nano /etc/ssh/sshd_config
# Change: Port 2222

# Restart SSH
sudo systemctl restart ssh

# Update firewall
sudo ufw allow 2222
sudo ufw delete allow 22
```

#### Step 5: Create a Simple Monitor
```bash
# Create a simple status check script
cat > ~/check_system.sh << 'EOF'
#!/bin/bash
echo "=== System Status Check ==="
echo "Date: $(date)"
echo ""

# Check SSH
if systemctl is-active ssh > /dev/null; then
    echo "SSH: Running ✓"
else
    echo "SSH: Not running ✗"
fi

# Check firewall
if sudo ufw status | grep -q "Status: active"; then
    echo "Firewall: Active ✓"
else
    echo "Firewall: Inactive ✗"
fi

# Check internet
if ping -c 1 google.com > /dev/null 2>&1; then
    echo "Internet: Connected ✓"
else
    echo "Internet: Not connected ✗"
fi
EOF

chmod +x ~/check_system.sh
echo "Status checker created! Run with: ~/check_system.sh"
```

---

## 📝 Key Things to Remember

### Services
- **systemctl** is your main tool for managing services
- **status** shows if service is running
- **start/stop** controls service right now
- **enable/disable** controls what happens at startup
- **journalctl** shows service messages

### Networking
- **ip addr show** shows your IP address
- **ping** tests if you can reach other computers
- **ss -tuln** shows what ports are listening
- **UFW** is the simple firewall tool

### SSH
- **SSH** lets you control other computers securely
- **Port 22** is the default SSH port
- **Always change default settings** for security
- **SCP** copies files between computers

### Security Basics
- **Enable firewall** and only allow needed services
- **Change default ports** when possible
- **Use strong passwords** or SSH keys
- **Check logs** regularly for problems

---

## 🎓 What's Next?

Once you're comfortable with these basics, you can learn:
- Advanced firewall rules
- SSH key authentication
- Network monitoring tools
- Automated security scripts
- VPN setup

---

## 🆘 Quick Reference

### Most Used Commands
```bash
# Service management
systemctl status servicename
sudo systemctl start servicename
sudo systemctl enable servicename

# Network info
ip addr show
ping google.com
ss -tuln

# Firewall
sudo ufw status
sudo ufw allow ssh
sudo ufw enable

# SSH
ssh username@hostname
scp file.txt username@hostname:/path/
```

### Common Problems and Solutions
- **Service won't start**: Check `journalctl -u servicename`
- **Can't connect to internet**: Check `ping google.com`
- **SSH connection refused**: Check firewall with `sudo ufw status`
- **Forgot to enable firewall**: Run `sudo ufw enable`

Remember: When in doubt, check the status first!
