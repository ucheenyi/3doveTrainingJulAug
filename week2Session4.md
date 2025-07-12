# Week 2 Session 8: System Maintenance & Security
## Student Class Notes

### 🎯 **Session Theme: "Workshop Guardian & Maintenance Chief"**

---

## 📚 **What You'll Learn Today**
- Check who can access your Linux system
- Keep your system running smoothly
- Make simple backups of important files
- Handle basic problems when they occur

---

## 🔐 **Part 1: Basic Security (40 minutes)**

### **The Story: Protecting Your Workshop**
*Your digital workshop has valuable projects and data. Just like locking your physical workshop at night, you need to secure your Linux system from unauthorized access.*

### **Who Can Access Your System?**
```bash
# See all users on your system
cut -d: -f1 /etc/passwd         # List all usernames
whoami                          # Show your current username
last -5                         # Show last 5 people who logged in
```

**What this means:** These commands show you everyone who has an account on your system, like checking who has keys to your workshop.

### **What Programs Are Running?**
```bash
# Check running programs
ps aux                          # Show all running programs
top                             # Show programs using most resources (press 'q' to quit)
```

**What this means:** This shows what programs are currently active on your system, like checking what machines are running in your workshop.

### **Basic File Protection**
```bash
# Check file permissions
ls -la                          # Show file permissions in current directory
ls -la /etc/passwd              # Check important system file permissions
```

**What this means:** File permissions control who can read, write, or run files - like having different keys for different rooms in your workshop.

### **Simple Firewall Setup**
```bash
# Basic firewall commands
sudo ufw status                 # Check if firewall is on
sudo ufw enable                 # Turn on firewall
sudo ufw allow ssh              # Allow SSH connections
```

**What this means:** The firewall controls what network connections are allowed - like having a security gate at your workshop entrance.

---

## 🔧 **Part 2: System Maintenance (40 minutes)**

### **The Story: Keeping Your Workshop Clean**
*A well-maintained workshop runs efficiently. Your Linux system also needs regular care to stay healthy and fast.*

### **Check System Health**
```bash
# Check available space
df -h                           # Show disk space usage
du -sh /home                    # Show how much space home directory uses

# Check memory
free -h                         # Show memory usage

# Check system status
uptime                          # Show how long system has been running
```

**What this means:** These commands are like checking fuel levels and engine temperature - they tell you if your system is healthy.

### **Keep Software Updated**
```bash
# Update your system
sudo apt update                 # Check for available updates
sudo apt upgrade                # Install updates
sudo apt autoremove             # Remove packages no longer needed
```

**What this means:** Like maintaining tools in your workshop, you need to keep software updated for security and performance.

### **Clean Up Old Files**
```bash
# Remove temporary files
ls /tmp                         # See what's in temp directory
sudo rm -rf /tmp/*              # Clean temporary files (be careful with this!)

# Check log files
ls -la /var/log/                # See system log files
```

**What this means:** Like cleaning sawdust from your workshop, removing old files keeps your system tidy and frees up space.

### **Monitor System Activity**
```bash
# Check system logs
journalctl --since today        # Show today's system messages
journalctl -p err               # Show only error messages
```

**What this means:** System logs are like a workshop journal that records everything that happens - useful for finding problems.

---

## 💾 **Part 3: Basic Backup (30 minutes)**

### **The Story: Protecting Your Work**
*Imagine if your workshop burned down. What would you lose? Smart workshop owners keep copies of important blueprints and customer lists in a safe place.*

### **Simple File Backup**
```bash
# Create backup directory
mkdir ~/my_backups

# Copy important files
cp -r ~/Documents ~/my_backups/
cp -r ~/Pictures ~/my_backups/
cp ~/.bashrc ~/my_backups/
```

**What this means:** This creates copies of your important files, like making photocopies of important documents.

### **Create Archive Backups**
```bash
# Create compressed backup
tar -czf ~/my_backups/documents-backup.tar.gz ~/Documents

# List what's in a backup
tar -tzf ~/my_backups/documents-backup.tar.gz
```

**What this means:** This creates a compressed backup file - like putting all your important papers in a sealed box.

### **Backup System Settings**
```bash
# Copy important system files
sudo cp /etc/fstab ~/my_backups/
crontab -l > ~/my_backups/my-scheduled-tasks.txt
```

**What this means:** This saves your system configuration - like keeping a list of how your workshop is organized.

---

## 🚨 **Handling Basic Problems**

### **When Things Go Wrong**
```bash
# Quick system check
uptime                          # Is system running normally?
df -h                          # Are we running out of space?
free -h                        # Are we running out of memory?
```

### **Common Solutions**

#### **If Disk is Full:**
```bash
# Find large files
du -sh /home/* | sort -hr       # Show largest directories
ls -la /var/log/ | head -10     # Check log file sizes
```

#### **If System is Slow:**
```bash
# See what's using resources
top                             # Show active programs (press 'q' to quit)
ps aux | head -10               # Show running processes
```

#### **If You Need Help:**
```bash
# Get help with commands
man ls                          # Read manual for 'ls' command
ls --help                       # Quick help for 'ls' command
```

---

## 📝 **Key Points to Remember**

### **Security Basics:**
- Check who has access to your system regularly
- Keep your firewall enabled
- Be aware of what programs are running
- Protect important files with proper permissions

### **Maintenance Basics:**
- Check disk space and memory regularly
- Keep your software updated
- Clean up old files occasionally
- Monitor system logs for problems

### **Backup Basics:**
- Copy important files regularly
- Keep backups in a safe location
- Test that you can restore from backups
- Save your system configuration

---

## 🎯 **Essential Commands to Practice**

```bash
# Security
whoami                          # Who am I?
ps aux                          # What's running?
sudo ufw status                 # Is firewall on?

# Maintenance
df -h                          # How much space left?
free -h                        # How much memory left?
sudo apt update                # Check for updates

# Backup
cp -r ~/Documents ~/backups/   # Copy important files
tar -czf backup.tar.gz ~/Documents  # Create compressed backup

# Problem Solving
uptime                         # System status
top                           # Resource usage
journalctl --since today      # Today's system messages
```

---

## 💡 **Daily System Care Routine**

**Every Day:**
- Check disk space with `df -h`
- Look at system status with `uptime`

**Every Week:**
- Update software with `sudo apt update && sudo apt upgrade`
- Backup important files
- Check system logs for errors

**Every Month:**
- Clean up old files
- Review who has access to your system
- Test that your backups work

---

## 🔧 **Remember: The Three Pillars**

1. **Security**: Keep your system safe from unauthorized access
2. **Maintenance**: Keep your system running smoothly
3. **Backup**: Protect your important data

*Taking care of your Linux system is like maintaining a workshop - a little regular attention prevents big problems and keeps everything running smoothly.*
