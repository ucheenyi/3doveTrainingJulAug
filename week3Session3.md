# Week 3 Session 3: System Monitoring & Performance
## Workshop Performance Optimization Lab

### 📖 Story Context
Your workshop empire now serves thousands of customers daily. Performance directly impacts customer satisfaction and revenue. Today you become the performance optimization specialist - learning to monitor every aspect of your workshop operations, identify bottlenecks, and maximize efficiency.

---

## 🎯 Learning Objectives
- Master real-time system performance monitoring
- Understand CPU, memory, disk, and network performance analysis
- Learn automated monitoring and alerting techniques
- Implement performance optimization strategies

---

## 📊 Part 1: Real-Time Performance Monitoring

### System Performance Dashboard
**What it is**: A comprehensive view of your system's current health and performance metrics.

**Key Monitoring Tools**:
```bash
# Interactive system monitor (like Task Manager on Windows)
htop                    # Shows processes, CPU, memory usage in real-time
top -d 1               # Classic process monitor, updates every 1 second
free -h                # Shows memory usage in human-readable format
```

**Technical Explanation**:
- **htop**: Interactive process viewer showing CPU cores, memory usage, and process list
- **top**: Shows running processes sorted by CPU usage
- **free -h**: Displays total, used, and available memory in GB/MB format

### CPU Performance Analysis
**What it monitors**: How hard your processor is working and what's using it.

```bash
# Get CPU information
lscpu                  # Shows CPU architecture, cores, speed
nproc                  # Number of processing units available
uptime                 # Shows system load average
```

**Technical Explanation**:
- **Load Average**: Numbers like "1.5, 2.0, 1.8" represent system load over 1, 5, and 15 minutes
- **High Load**: If load > number of CPU cores, system is overworked
- **CPU Usage**: Percentage of CPU time being used vs. idle time

### Memory Performance Analysis
**What it monitors**: How much RAM is being used and by what processes.

```bash
# Memory monitoring
free -h -s 2           # Update memory status every 2 seconds
vmstat 1 5             # Virtual memory statistics
cat /proc/meminfo      # Detailed memory information
```

**Technical Explanation**:
- **Physical Memory**: Actual RAM installed in your system
- **Virtual Memory**: Memory + swap space (hard disk used as backup RAM)
- **Memory Pressure**: When system runs low on available RAM

---

## 💽 Part 2: Storage & Network Performance

### Disk Performance Monitoring
**What it monitors**: How fast your storage devices are reading/writing data.

```bash
# Disk space monitoring
df -h                 # Shows filesystem disk space usage
du -sh /*             # Shows directory space usage
iostat 1 5            # I/O statistics updated every second
```

**Technical Explanation**:
- **Filesystem**: How data is organized on your disk
- **I/O Operations**: Input/Output - reading from and writing to disk
- **Disk Utilization**: Percentage of time disk is busy processing requests

### Network Performance Monitoring
**What it monitors**: How data flows in and out of your system over the network.

```bash
# Basic network monitoring
ip -s link            # Shows network interface statistics
ss -tuln              # Shows active network connections
ping -c 10 google.com # Tests network connectivity and speed

# Network interface information
ip addr show          # Shows all network interfaces and their IP addresses
ifconfig              # Alternative way to view network interfaces
iwconfig              # Shows wireless network interfaces (WiFi)

# Network connectivity testing
ping -c 5 8.8.8.8     # Test connectivity to Google DNS
traceroute google.com # Shows the path packets take to reach destination
nslookup google.com   # Test DNS resolution
dig google.com        # Another DNS lookup tool

# Network traffic monitoring
netstat -i            # Shows network interface statistics
netstat -tuln         # Shows listening ports and connections
ss -s                 # Shows socket statistics summary
cat /proc/net/dev     # Raw network device statistics

# Speed and performance testing
wget -O /dev/null --progress=dot:giga http://speedtest.tele2.net/10MB.zip
curl -o /dev/null -s -w "Download time: %{time_total}s\n" http://google.com
```

**Technical Explanation**:
- **Network Interface**: Your network card (ethernet, WiFi)
- **Bandwidth**: How much data can flow through your network connection
- **Latency**: Time it takes for data to travel to destination and back
- **DNS Resolution**: Converting website names (google.com) to IP addresses
- **Traceroute**: Shows each router your data passes through to reach destination
- **Listening Ports**: Network services waiting for incoming connections

---

## 🔧 Part 3: Performance Optimization & Alerting

### Performance Optimization Techniques
**What it does**: Makes your system run faster and more efficiently.

```bash
# Simple memory cleanup
sudo apt clean                               # Clear package cache
sudo journalctl --vacuum-time=7d             # Clean old logs

# Process management
kill PID                                     # Stop a specific process
pkill firefox                               # Stop all Firefox processes
```

**Technical Explanation**:
- **Cache Clearing**: Removes temporary files that take up space
- **Log Cleanup**: Removes old system logs to free disk space
- **Process Management**: Stopping unnecessary programs frees up resources

### Automated Monitoring & Alerting
**What it does**: Automatically watches your system and alerts you to problems.

**Simple Monitoring Script Example**:
```bash
#!/bin/bash
# Check if disk space is getting full
DISK_USAGE=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')

if [ "$DISK_USAGE" -gt 80 ]; then
    echo "WARNING: Disk is ${DISK_USAGE}% full!"
    echo "Large files in your system:"
    du -sh /var/log /tmp /home 2>/dev/null
fi
```

**Key Concepts**:
- **Monitoring**: Regularly checking system status
- **Thresholds**: Set limits (e.g., disk usage > 80%)
- **Alerts**: Notifications when something needs attention
- **Scripts**: Small programs that do monitoring tasks automatically

---

## 🎯 Key Performance Metrics to Monitor

### CPU Metrics
- **CPU Usage %**: How much of CPU capacity is being used
- **Load Average**: Average system load over time
- **Process Count**: Number of running processes

### Memory Metrics
- **Memory Usage %**: Percentage of RAM being used
- **Swap Usage**: How much swap space is being used
- **Available Memory**: Amount of free memory available

### Disk Metrics
- **Disk Usage %**: Percentage of disk space used
- **I/O Wait**: Time CPU waits for disk operations
- **Read/Write Speed**: How fast data is transferred to/from disk

### Network Metrics
- **Bandwidth Usage**: How much network capacity is being used
- **Connection Count**: Number of active network connections
- **Latency**: Network response time (ping time)
- **Packet Loss**: Percentage of data packets that don't reach destination
- **DNS Resolution Time**: How long it takes to convert domain names to IP addresses
- **Download/Upload Speed**: How fast data transfers in each direction

---

## 🚨 Common Performance Issues & Solutions

### High CPU Usage
**Symptoms**: System feels slow, applications take long to respond
**Solutions**: 
- Use `htop` to see which programs are using too much CPU
- Close unnecessary programs
- Restart programs that are stuck

### High Memory Usage
**Symptoms**: Applications crash, system becomes unresponsive
**Solutions**:
- Close programs you're not using
- Restart your browser (often uses lots of memory)
- Clear temporary files with `sudo apt clean`

### High Disk Usage
**Symptoms**: System runs slowly, "disk full" errors appear
**Solutions**:
- Delete old files with `rm` command
- Clean up downloads folder
- Empty trash/recycle bin
- Use `du -sh *` to find large directories

### Network Issues
**Symptoms**: Slow internet, timeouts, connection drops
**Solutions**:
- Test basic connectivity with `ping google.com`
- Check DNS resolution with `nslookup google.com`
- View network interfaces with `ip addr show`
- Test different servers with `ping 8.8.8.8` (Google DNS)
- Restart network with `sudo systemctl restart networking`
- Check if other devices have the same problem
- Use `traceroute` to find where connection problems occur

---

## 📝 Practical Commands Summary

### Essential Monitoring Commands
```bash
# Quick system overview
htop                    # Interactive system monitor
free -h                 # Memory usage
df -h                   # Disk usage
uptime                  # System load and uptime

# Process monitoring
ps aux --sort=-%cpu     # Top CPU consumers
ps aux --sort=-%mem     # Top memory consumers
top -p PID              # Monitor specific process

# Network monitoring
ss -tuln                # Active connections
netstat -i              # Network interface statistics
ping google.com         # Network connectivity test
traceroute google.com   # Network path tracing
nslookup google.com     # DNS lookup test
ip addr show            # Show all network interfaces
```

### Performance Optimization Commands
```bash
# Simple cleanup
sudo apt clean             # Clear package cache
sudo apt autoremove        # Remove unused packages
df -h                      # Check disk space

# Process management
kill PID                   # Stop a specific process
pkill program-name         # Stop all instances of a program
```

---

## 🎯 Workshop Challenge: Build Your Performance Dashboard

**Mission**: Create a simple monitoring system for your workshop that:
1. Checks CPU, memory, and disk usage regularly
2. Shows warnings when usage gets too high
3. Helps identify which programs are using the most resources
4. Provides a simple daily performance report

**Success Criteria**:
- Can quickly check system performance with one command
- Knows how to identify performance problems
- Can clean up system resources when needed
- Understands when to ask for help with serious issues

---

## 📚 Key Takeaways

1. **Regular Monitoring**: Check your system performance regularly to catch problems early
2. **Start Simple**: Use basic tools like `htop`, `free -h`, and `df -h` to understand your system
3. **Clean Up Regularly**: Remove old files and unused programs to keep your system running smoothly
4. **Know the Warning Signs**: Slow performance, crashes, and error messages are signs to investigate
5. **Practice Makes Perfect**: The more you use these tools, the better you'll understand your system
6. **Ask for Help**: When you see something unusual, don't hesitate to ask for assistance

---

## 🔗 Next Steps
- Practice using monitoring tools daily
- Set up automated monitoring scripts
- Create performance baselines for your systems
- Learn advanced troubleshooting techniques (Session 12)
