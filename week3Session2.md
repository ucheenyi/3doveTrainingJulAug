# **Week 3 Session 2: Remote Administration**
## **AI-Powered Linux & Git Course** *Duration: 2 Hours*
### Managing Your Workshop Empire 🏭

### 🎯 **Story Setup**
Your workshop has grown! You now have a second location across town. Instead of driving back and forth, you'll learn to manage both workshops remotely using SSH - like having a magic window into your other workshop.

---

## 🔑 **Part 1: Understanding SSH (Your Digital Keys)**

### **The Story**: Your First Remote Connection
SSH (Secure Shell) is like having a secure phone line to your remote workshop. You can see what's happening, give commands, and manage everything from your main location.

### **What is SSH?**
- **SSH**: A secure way to connect to another computer over the internet
- **Server**: The remote computer you want to connect to
- **Client**: Your computer (where you type commands)
- **Encrypted**: All communication is scrambled for security

### **🛠️ Your First SSH Connection**

```bash
# Basic SSH connection
ssh username@server-address

# Example: Connect to your workshop server
ssh workshop@192.168.1.100
```

**What happens:**
1. You type your password
2. SSH creates a secure connection
3. You see the remote computer's command prompt
4. You can now run commands on the remote computer!

### **🔧 Making SSH Easier with SSH Keys**

**The Problem**: Typing passwords every time is annoying and less secure.
**The Solution**: SSH keys - like having a special ID card.

```bash
# Generate your SSH key pair
ssh-keygen -t rsa -b 2048

# This creates two files:
# ~/.ssh/id_rsa     (private key - keep secret!)
# ~/.ssh/id_rsa.pub (public key - safe to share)
```

**Simple explanation:**
- **Private key**: Your secret key (never share this!)
- **Public key**: Like giving someone your business card

### **🛠️ Hands-On Exercise: Set Up Key-Based Login**

**Step 1: Generate your SSH key pair**
```bash
# Generate your key pair (press Enter for default location)
ssh-keygen -t rsa -b 2048

# When prompted:
# - File location: Press Enter (uses default ~/.ssh/id_rsa)
# - Passphrase: Enter a secure passphrase or press Enter for none
```

**Step 2: Test your current password login**
```bash
# Connect to the server with password
ssh champion@79.72.72.205

# Once connected, check your home directory
pwd
ls -la

# Exit back to your local machine
exit
```

**Step 3: Copy your public key to the server**
```bash
# Method 1: Use ssh-copy-id (easiest)
ssh-copy-id champion@79.72.72.205

# Method 2: Manual copy (if ssh-copy-id doesn't work)
cat ~/.ssh/id_rsa.pub | ssh champion@79.72.72.205 'mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys'
```

**Step 4: Set correct permissions on the server**
```bash
# Connect to server and fix permissions
ssh champion@79.72.72.205

# Set correct permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

# Check the permissions
ls -la ~/.ssh/

# Exit back to local machine
exit
```

**Step 5: Test key-based login**
```bash
# Now you should be able to login without password!
ssh champion@79.72.72.205

# If it works, you'll connect without typing a password
# Exit when done testing
exit
```

**Why this is better:**
- No more typing passwords
- More secure than passwords
- Faster connections

### **🔧 Create SSH Config File for Easy Access**

**The Story**: Instead of typing `ssh champion@79.72.72.205` every time, let's create a shortcut called `oracle3dove`!

**Step 1: Create SSH config file**
```bash
# Create the config file
cat > ~/.ssh/config << 'EOF'
# Oracle3dove server configuration
Host oracle3dove
    HostName 79.72.72.205
    User champion
    Port 22
    IdentityFile ~/.ssh/id_rsa
    ServerAliveInterval 60
    ServerAliveCountMax 3
EOF
```

**Step 2: Set proper permissions**
```bash
# Make config file secure
chmod 600 ~/.ssh/config
```

**Step 3: Test your new shortcut**
```bash
# Now you can simply type:
ssh oracle3dove

# Instead of:
ssh champion@79.72.72.205
```

**What each setting means:**
- `Host oracle3dove`: Your friendly nickname for the server
- `HostName 79.72.72.205`: The actual server address
- `User champion`: Your username on the server
- `Port 22`: SSH port (22 is default)
- `IdentityFile ~/.ssh/id_rsa`: Which key to use
- `ServerAliveInterval 60`: Send keepalive every 60 seconds
- `ServerAliveCountMax 3`: Try 3 times before giving up

**Step 4: Test all your new powers**
```bash
# Test the shortcut
ssh oracle3dove

# Check you're on the right server
hostname
whoami

# Exit back to your local machine
exit
```

---

## 🌐 **Part 2: Basic Remote Operations**

### **The Story**: Managing Your Remote Workshop
Now you can "visit" your remote workshop anytime. Let's learn the essential tasks you'll do daily.

### **🛠️ Essential Remote Commands**

```bash
# Check what's happening at your remote workshop
ssh oracle3dove 'pwd'           # Where am I?
ssh oracle3dove 'ls -la'        # What files are here?
ssh oracle3dove 'df -h'         # How much space is left?
ssh oracle3dove 'ps aux'        # What's running?
```

**Think of it like:**
- `pwd`: "Where am I in the building?"
- `ls -la`: "What's in this room?"
- `df -h`: "How much storage space do we have?"
- `ps aux`: "What machines are running?"

### **🔧 Checking System Health**

```bash
# Create a simple system check
ssh oracle3dove 'uptime'         # How long has it been running?
ssh oracle3dove 'free -m'        # How much memory is available?
ssh oracle3dove 'date'           # What time is it there?
```

**Real-world example:**
```bash
# Check if your web server is running
ssh oracle3dove 'systemctl status nginx'
```

### **🛠️ Running Multiple Commands**

```bash
# Method 1: Separate commands
ssh oracle3dove 'ls -la'
ssh oracle3dove 'df -h'
ssh oracle3dove 'uptime'

# Method 2: Multiple commands in one go
ssh oracle3dove 'ls -la; df -h; uptime'
```

---

## 📁 **Part 3: Moving Files Between Workshops**

### **The Story**: Sharing Tools and Materials
You need to move files between your workshops - like sending blueprints or sharing tools.

### **🛠️ Basic File Transfer with SCP**

```bash
# Send a file to your remote workshop
scp myfile.txt oracle3dove:/home/champion/

# Get a file from your remote workshop
scp oracle3dove:/home/champion/remotefile.txt ./

# Send a whole folder
scp -r myfolder/ oracle3dove:/home/champion/
```

**Simple explanation:**
- `scp`: Secure copy (like email for files)
- `source`: Where the file is now
- `destination`: Where you want it to go
- `-r`: Include all files in a folder

### **🔧 Practical File Transfer Examples**

```bash
# Send today's work to the remote workshop
scp project.txt oracle3dove:/home/champion/projects/

# Backup important files to your main workshop
scp oracle3dove:/home/champion/important.txt ./backups/

# Share a folder of tools
scp -r tools/ oracle3dove:/home/champion/shared/
```

---

## 🔧 **Part 4: Simple Remote Management**

### **The Story**: Daily Workshop Operations
Every day you need to check on your workshops, start/stop services, and keep things running smoothly.

### **🛠️ Basic Service Management**

```bash
# Check if a service is running
ssh oracle3dove 'systemctl status nginx'

# Start a service
ssh oracle3dove 'sudo systemctl start nginx'

# Stop a service
ssh oracle3dove 'sudo systemctl stop nginx'

# Restart a service
ssh oracle3dove 'sudo systemctl restart nginx'
```

**Think of services like:**
- **nginx**: Your workshop's front desk
- **mysql**: Your workshop's filing system
- **ssh**: Your workshop's phone system

### **🔧 Create Your First Management Script**

```bash
# Create a simple workshop checker
cat > check_workshop.sh << 'EOF'
#!/bin/bash
echo "Checking remote workshop..."
ssh oracle3dove 'echo "Workshop Status Report"'
ssh oracle3dove 'echo "Current time: $(date)"'
ssh oracle3dove 'echo "Uptime: $(uptime -p)"'
ssh oracle3dove 'echo "Disk space: $(df -h / | tail -1)"'
ssh oracle3dove 'echo "Memory usage: $(free -m | grep Mem)"'
EOF

chmod +x check_workshop.sh
```

**Run your script:**
```bash
./check_workshop.sh
```

---

## 🚨 **Part 5: Basic Troubleshooting**

### **The Story**: When Things Go Wrong
Sometimes your remote workshop has problems. Here's how to investigate and fix common issues.

### **🛠️ Simple Diagnostic Commands**

```bash
# Is the server responding?
ping 79.72.72.205

# Check what's using up space
ssh oracle3dove 'du -sh /home/champion/*'

# Look at recent activity
ssh oracle3dove 'tail -10 /var/log/syslog'

# Check if important services are running
ssh oracle3dove 'systemctl is-active nginx mysql ssh'
```

### **🔧 Common Problems and Solutions**

**Problem 1: Can't connect to server**
```bash
# Check if server is reachable
ping 79.72.72.205

# Try connecting with verbose output
ssh -v oracle3dove
```

**Problem 2: Server is slow**
```bash
# Check system load
ssh oracle3dove 'uptime'

# Check memory usage
ssh oracle3dove 'free -m'

# See what's using CPU
ssh oracle3dove 'top -bn1 | head -10'
```

**Problem 3: Running out of space**
```bash
# Check disk usage
ssh oracle3dove 'df -h'

# Find large files
ssh oracle3dove 'find /home/champion -size +100M -type f'
```

---

## 🎯 **Practice Lab: Your Remote Workshop**

### **Mission**: Connect to a remote system and perform basic management tasks

**Step 1: Test your SSH setup**
```bash
# Test your key-based connection
ssh oracle3dove

# Verify you're on the right server
hostname
whoami
pwd

# Exit back to local machine
exit
```

**Step 2: Explore your remote workshop**
```bash
# Connect and explore
ssh oracle3dove

# Once connected:
pwd                    # Where am I?
ls -la                 # What's here?
df -h                  # How much space?
uptime                 # How long running?
free -m                # Memory usage

# Exit back to local machine
exit
```

**Step 3: Transfer some files**
```bash
# Create a test file locally
echo "Hello from local machine" > test.txt

# Send it to the server
scp test.txt oracle3dove:/home/champion/

# Get the hostname file from server
scp oracle3dove:/etc/hostname ./

# Check what you downloaded
cat hostname
```

**Step 4: Create a simple monitoring script**
```bash
cat > my_monitor.sh << 'EOF'
#!/bin/bash
echo "=== Oracle3dove Workshop Status ==="
ssh oracle3dove 'echo "Server: $(hostname)"'
ssh oracle3dove 'echo "Date: $(date)"'
ssh oracle3dove 'echo "Uptime: $(uptime -p)"'
ssh oracle3dove 'echo "Disk usage: $(df -h / | tail -1)"'
ssh oracle3dove 'echo "Memory: $(free -m | grep Mem)"'
echo "=== Check Complete ==="
EOF

chmod +x my_monitor.sh
./my_monitor.sh
```

---

## 🔑 **Key Takeaways**

### **What You've Learned**:
✅ How to connect to remote computers with SSH  
✅ How to set up SSH keys for easier logins  
✅ How to run commands on remote computers  
✅ How to transfer files between computers  
✅ How to check system health remotely  
✅ How to troubleshoot basic problems  

### **Important Security Notes**:
- Never share your private SSH key
- Use strong passwords for your accounts
- Only connect to servers you trust
- Keep your SSH keys in the ~/.ssh/ folder

### **Daily Tasks You Can Now Do**:
- Check if your remote servers are running
- Transfer files between computers
- Start/stop services remotely
- Monitor system health
- Investigate simple problems

---

## 📝 **Quick Reference - Commands You'll Use Daily**

```bash
# Connection
ssh oracle3dove                  # Connect to your server
ssh champion@79.72.72.205       # Connect using IP directly
exit                            # Disconnect from remote server

# File Transfer
scp file.txt oracle3dove:/home/champion/  # Send file to server
scp oracle3dove:/home/champion/file.txt . # Get file from server
scp -r folder/ oracle3dove:/home/champion/ # Send folder to server

# Remote Commands
ssh oracle3dove 'command'        # Run single command
ssh oracle3dove 'uptime'         # Check how long server is running
ssh oracle3dove 'df -h'          # Check disk space
ssh oracle3dove 'free -m'        # Check memory usage

# System Checks
ping 79.72.72.205               # Check if server is reachable
ssh oracle3dove 'systemctl status nginx' # Check service status
```

**Remember**: Start simple, practice regularly, and gradually build your confidence with remote administration! 🚀

**Next Session Preview**: We'll learn about Git and version control - like having a time machine for your code! 📚
