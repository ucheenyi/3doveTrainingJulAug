# Linux Session 3: System Information & Processes (2 Hours)
### **Story Theme: "Becoming the Workshop Supervisor"**

---

## **Opening Story (5 minutes)**
*"Congratulations! You've been promoted from workshop apprentice to workshop supervisor. Now you need to understand what's happening in your workshop at all times - which machines are running, who's using what tools, and how everything is performing. Today you'll learn to see the invisible activities in your digital workshop."*

---

## **Part 1: Getting to Know Your Workshop (30 minutes)**

### **Workshop Identity Check (15 minutes)**
**Story**: Every supervisor needs to know their workshop's basic information
**Reality**: Understanding your system's identity and current state

**🔧 Try These Commands:**

```bash
# Who am I in this workshop?
whoami
# Shows your username

# What's my workshop called?
hostname
# Shows your computer's name

# What are my credentials?
id
# Shows your user ID and group memberships

# How long has the workshop been running?
uptime
# Shows system uptime and current load

# What time is it?
date
# Shows current date and time
```

**Expected Output:**
```
$ whoami
student

$ hostname
workshop-computer

$ uptime
14:25:32 up 2 days, 3:42, 2 users, load average: 0.15, 0.10, 0.08
```

**What This Means:**
- **student**: That's your username
- **workshop-computer**: Your system's name
- **up 2 days, 3:42**: System has been running for 2 days, 3 hours, 42 minutes
- **2 users**: Two people are currently logged in
- **load average 0.15**: System is using about 15% of its processing power

### **Who Else Is Here? (15 minutes)**
**Story**: A good supervisor knows who's in the workshop
**Reality**: Monitoring user activity

```bash
# Simple view of who's logged in
who
# Shows logged-in users

# Detailed view of what everyone is doing
w
# Shows users and their current activities
```

**Expected Output:**
```
$ who
student  tty1    2024-01-15 10:30
admin    pts/0   2024-01-15 12:15

$ w
USER     TTY   FROM        LOGIN@   IDLE   WHAT
student  tty1  -           10:30    5m     bash
admin    pts/0 192.168.1.5 12:15    2m     vim report.txt
```

**What This Means:**
- **student**: You're logged in directly at the computer (tty1)
- **admin**: Someone logged in remotely (pts/0) and is editing a file
- **IDLE 5m**: You've been idle for 5 minutes

---

## **Part 2: Workshop Resources Dashboard (35 minutes)**

### **Memory and Processing Power (20 minutes)**
**Story**: Understanding your workshop's capacity
**Reality**: Checking CPU and memory resources

```bash
# Check memory usage (like checking available workspace)
free -h
# Shows memory usage in human-readable format

# Check CPU information (like checking your workshop's engine)
lscpu
# Shows CPU details - just look at the first few lines

# Check storage space (like checking warehouse capacity)
df -h
# Shows disk usage in human-readable format
```

**Expected Output:**
```
$ free -h
               total        used        free      shared  buff/cache   available
Mem:           7.7Gi       2.1Gi       3.2Gi       256Mi       2.4Gi       5.1Gi
Swap:          2.0Gi          0B       2.0Gi

$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        20G  8.5G   11G  45% /
/dev/sda2       100G   45G   51G  47% /home
```

**What This Means:**
- **Mem total 7.7Gi**: You have about 8GB of memory
- **available 5.1Gi**: About 5GB is available for new programs
- **Use% 45%**: Your main disk is 45% full - plenty of space left

### **Quick System Health Check (15 minutes)**
**Story**: Creating a daily health report
**Reality**: Combining commands for system overview

**🔧 Practice: Create Your First Health Check Script**

```bash
# Create a simple health check script
nano health_check.sh

# Type this content:
#!/bin/bash
echo "=== WORKSHOP HEALTH CHECK ==="
echo "Date: $(date)"
echo "Workshop: $(hostname)"
echo "Supervisor: $(whoami)"
echo ""
echo "=== SYSTEM STATUS ==="
uptime
echo ""
echo "=== MEMORY ==="
free -h
echo ""
echo "=== DISK SPACE ==="
df -h
echo ""
echo "=== CURRENT USERS ==="
who
echo "=== END REPORT ==="

# Make it executable
chmod +x health_check.sh

# Run it
./health_check.sh
```

---

## **Part 3: Understanding Workshop Activities (40 minutes)**

### **What's Running Right Now? (20 minutes)**
**Story**: Seeing all the activities happening in your workshop
**Reality**: Understanding processes and system monitoring

```bash
# See your current activities
ps
# Shows processes in your current session

# See ALL workshop activities
ps aux
# Shows all processes with details (this will be a long list!)

# See activities in a more organized way
ps aux | head -10
# Shows just the first 10 processes
```

**Expected Output:**
```
$ ps aux | head -5
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.1  77616  8964 ?        Ss   Jan15   0:01 /sbin/init
student   1234  0.5  2.3 145620 45680 pts/0    Sl   14:20   0:05 firefox
student   1456  0.0  0.1  21520  2964 pts/0    R+   14:25   0:00 ps aux
```

**What This Means:**
- **PID 1234**: Process ID number (like an employee badge number)
- **%CPU 0.5**: Using half a percent of the CPU
- **%MEM 2.3**: Using 2.3% of memory
- **firefox**: The Firefox browser is running

### **Real-Time Activity Monitor (20 minutes)**
**Story**: Watching your workshop activities live
**Reality**: Using top for real-time monitoring

```bash
# Live activity dashboard
top
# Shows real-time process information
# Press 'q' to quit when you're done looking

# Try these while top is running:
# Press 'P' to sort by CPU usage
# Press 'M' to sort by memory usage
# Press 'q' to quit
```

**Understanding Top Display:**
- **Load average**: How busy your system is (like workshop activity level)
- **Tasks**: Total number of activities running
- **%Cpu(s)**: How much of your processing power is being used
- **Memory**: How much memory is being used

**🔧 Practice: Find and Understand a Process**

```bash
# Start a simple background task
sleep 100 &
# This starts a 100-second timer in the background

# Find your process
ps aux | grep sleep
# Look for your sleep process

# Check it in top
top
# Look for your sleep process, then press 'q' to quit

# Stop your process (replace XXXX with the actual PID)
kill XXXX
```

---

## **Part 4: Basic Process Management (25 minutes)**

### **Starting and Stopping Activities (15 minutes)**
**Story**: Managing workshop tasks responsibly
**Reality**: Basic process control

```bash
# Start a background task
sleep 200 &
# Starts a 200-second timer in background

# List background jobs
jobs
# Shows your background tasks

# Start another task and pause it
sleep 300
# While it's running, press Ctrl+Z to pause it

# Check your jobs again
jobs
# You should see both tasks now

# Resume the paused job in background
bg %2
# Resumes job #2 in background

# Stop all sleep processes
killall sleep
# Stops all sleep processes
```

### **Process Safety (10 minutes)**
**Story**: Being a responsible supervisor
**Reality**: Safe process management practices

**Important Process Management Rules:**
1. **Always check what you're stopping**: Use `ps aux | grep processname` first
2. **Use gentle termination**: Try `kill PID` before `kill -9 PID`
3. **Only stop your own processes**: Don't interfere with system processes
4. **Ask for help**: If unsure about a process, ask an experienced user

**🔧 Safe Practice Exercise:**
```bash
# Safe process checking routine
echo "=== SAFE PROCESS CHECK ==="

# 1. Start a test process
sleep 500 &
TEST_PID=$!
echo "Started test process with PID: $TEST_PID"

# 2. Verify it's running
ps aux | grep sleep | grep -v grep
echo "Confirmed process is running"

# 3. Stop it safely
kill $TEST_PID
echo "Sent termination signal"

# 4. Verify it stopped
sleep 2
ps aux | grep sleep | grep -v grep
echo "Process check complete"
```

---

## **Part 5: Network and Services Basics (25 minutes)**

### **Workshop Network Status (15 minutes)**
**Story**: Checking your workshop's communication systems
**Reality**: Basic network information

```bash
# What's my workshop's network address?
hostname -I
# Shows your IP address

# Check network interfaces
ip addr show
# Shows all network connections (look for your main one)

# Test network connectivity
ping -c 4 google.com
# Tests if you can reach the internet (sends 4 test packets)
```

**Expected Output:**
```
$ hostname -I
192.168.1.100

$ ping -c 4 google.com
PING google.com (172.217.164.110) 56(84) bytes of data.
64 bytes from lga25s54-in-f14.1e100.net: icmp_seq=1 ttl=115 time=12.3 ms
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss
```

**What This Means:**
- **192.168.1.100**: Your workshop's address on the local network
- **0% packet loss**: Your network connection is working perfectly
- **time=12.3 ms**: Very fast response time

### **Basic Service Status (10 minutes)**
**Story**: Checking if workshop departments are running
**Reality**: Introduction to system services

```bash
# Check if the security department (SSH) is running
systemctl is-active ssh
# Should show "active" if running

# Check if it starts automatically
systemctl is-enabled ssh
# Should show "enabled" if it starts at boot

# See basic service information
systemctl status ssh
# Shows detailed service status
```

**Expected Output:**
```
$ systemctl is-active ssh
active

$ systemctl status ssh
● ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; enabled)
   Active: active (running) since Mon 2024-01-15 10:30:15 UTC; 4h ago
   Main PID: 1234 (sshd)
```

**What This Means:**
- **active**: The SSH service is running
- **enabled**: It will start automatically when the system boots
- **running since**: It's been running for 4 hours

---

## **Final Challenge: Weekend Supervisor Report (15 minutes)**

### **The Scenario**
*"You're the weekend supervisor. Your manager will call in 15 minutes asking about the workshop status. Create a simple report with the most important information."*

**🎯 Create Your Supervisor Report:**

```bash
# Create your report script
nano weekend_report.sh

# Add this content:
#!/bin/bash
echo "=================================="
echo "WEEKEND SUPERVISOR REPORT"
echo "=================================="
echo "Date: $(date)"
echo "Workshop: $(hostname)"
echo "Supervisor: $(whoami)"
echo ""

echo "--- BASIC STATUS ---"
echo "Workshop has been running for:"
uptime | cut -d',' -f1
echo ""

echo "Current users in workshop:"
who | wc -l
echo ""

echo "Available memory:"
free -h | grep Mem | awk '{print $7}'
echo ""

echo "Disk space remaining:"
df -h / | tail -1 | awk '{print $4}'
echo ""

echo "Network connectivity:"
if ping -c 1 google.com > /dev/null 2>&1; then
    echo "GOOD - Internet connection working"
else
    echo "ISSUE - No internet connection"
fi
echo ""

echo "--- END REPORT ---"

# Make it executable and run
chmod +x weekend_report.sh
./weekend_report.sh
```

### **Key Takeaways from Today**
1. **System Identity**: Know your system's name, uptime, and basic info
2. **Resource Monitoring**: Check memory, CPU, and disk usage
3. **Process Awareness**: Understand what's running and how to manage it safely
4. **Network Basics**: Check connectivity and basic network information
5. **Service Status**: Know how to check if important services are running

### **What's Next?**
In Session 4, we'll learn about file permissions, user management, and more advanced system administration tasks. You'll become a senior workshop supervisor!

---

## **Quick Reference Card**

**Essential Commands:**
- `whoami` - Who am I?
- `hostname` - What's my system name?
- `uptime` - How long has system been running?
- `free -h` - Memory usage
- `df -h` - Disk usage
- `ps aux` - Show all processes
- `top` - Live process monitor
- `kill PID` - Stop a process
- `systemctl status service` - Check service status

**Remember**: Always be careful when managing processes, and when in doubt, ask for help!
