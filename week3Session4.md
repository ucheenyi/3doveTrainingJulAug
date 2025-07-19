# Week 3 Session 4: Troubleshooting & Recovery
## Student Class Notes

### **Story Theme: "Workshop Emergency Response Team"**

*"Every workshop empire faces crises - systems fail, data corruption occurs, and emergencies strike at the worst possible moments. Today you become the workshop's emergency response specialist, mastering the critical skills of system troubleshooting, disaster recovery, and crisis management."*

---

## **Part 1: Systematic Troubleshooting (The Detective Approach)**

### **The SYSTEM Method - Your Troubleshooting Framework**

When something goes wrong in your workshop, don't panic! Follow this systematic approach:

**S** - **Symptoms**: What exactly is wrong?
**Y** - **Yield Information**: Gather all the clues
**S** - **Systematic Approach**: Follow logical steps
**T** - **Test Theories**: Make educated guesses and test them
**E** - **Execute Solutions**: Apply fixes carefully
**M** - **Monitor Results**: Make sure the fix worked

### **Basic Information Gathering Commands**

```bash
# Step 1: Document the problem
echo "Problem started: $(date)" > /tmp/troubleshoot_log.txt
echo "What user reported: Website is slow" >> /tmp/troubleshoot_log.txt

# Step 2: Gather system information
echo "=== BASIC SYSTEM INFO ===" >> /tmp/troubleshoot_log.txt
whoami >> /tmp/troubleshoot_log.txt        # Who am I?
date >> /tmp/troubleshoot_log.txt          # What time is it?
uptime >> /tmp/troubleshoot_log.txt        # How long has system been running?
```

### **Check System Resources (Like Checking Your Workshop Supplies)**

```bash
# Check memory usage (like checking how much workspace you have)
free -h >> /tmp/troubleshoot_log.txt

# Check disk space (like checking storage room)
df -h >> /tmp/troubleshoot_log.txt

# Check what processes are running (like seeing who's working)
ps aux >> /tmp/troubleshoot_log.txt
```

### **Simple Diagnostic Script**

```bash
#!/bin/bash
# Simple troubleshooting helper

echo "🔍 Starting Simple Diagnostics..."
echo "Time: $(date)"
echo "=================================="

# Check if internet works
if ping -c 3 google.com >/dev/null 2>&1; then
    echo "✅ Internet connection: OK"
else
    echo "❌ Internet connection: PROBLEM"
fi

# Check disk space
disk_usage=$(df / | tail -1 | awk '{print $5}' | sed 's/%//')
if [ $disk_usage -gt 80 ]; then
    echo "⚠️  Disk space: Getting full ($disk_usage%)"
else
    echo "✅ Disk space: OK ($disk_usage%)"
fi

# Check memory
memory_usage=$(free | grep Mem | awk '{printf "%.0f", $3/$2 * 100}')
if [ $memory_usage -gt 80 ]; then
    echo "⚠️  Memory usage: High ($memory_usage%)"
else
    echo "✅ Memory usage: OK ($memory_usage%)"
fi

echo "=================================="
echo "Basic diagnostics complete!"
```

---

## **Part 2: Emergency Response (The First Aid Kit)**

### **Emergency System Stabilization**

When your workshop system is in crisis, you need quick first aid:

```bash
#!/bin/bash
# Emergency first aid for your system

echo "🚨 EMERGENCY RESPONSE ACTIVATED 🚨"

# Function to log what we're doing
log_action() {
    echo "[$(date)] $1" | tee -a /tmp/emergency_log.txt
}

# Clear system memory (like clearing your workspace)
log_action "Clearing system caches..."
sync  # Make sure all data is written to disk
echo 3 > /proc/sys/vm/drop_caches 2>/dev/null

# Check for disk space problems
log_action "Checking disk space..."
df -h | grep -E "9[0-9]%|100%"  # Show any drives over 90% full

# Clean up temporary files (like emptying the trash)
log_action "Cleaning temporary files..."
find /tmp -type f -atime +1 -delete 2>/dev/null

# Check critical services
log_action "Checking critical services..."
systemctl status ssh networking 2>/dev/null
```

### **Simple Service Recovery**

```bash
#!/bin/bash
# Fix broken services

echo "🔧 Checking and fixing services..."

# Check if a service is running
check_service() {
    service_name=$1
    if systemctl is-active $service_name >/dev/null 2>&1; then
        echo "✅ $service_name is running"
    else
        echo "❌ $service_name is stopped - trying to start..."
        systemctl start $service_name
        if systemctl is-active $service_name >/dev/null 2>&1; then
            echo "✅ Successfully started $service_name"
        else
            echo "❌ Failed to start $service_name"
        fi
    fi
}

# Check common services
check_service "ssh"
check_service "networking"
```

---

## **Part 3: Basic Data Recovery (The Backup Rescue)**

### **Finding Lost Files**

```bash
#!/bin/bash
# Help find lost files

echo "🔍 Looking for lost files..."

# Check common backup locations
echo "Checking backup locations..."
find /home -name "*.backup" -o -name "*.bak" -o -name "*~" 2>/dev/null

# Check trash directories
echo "Checking trash directories..."
find /home -name ".Trash*" -o -name "trash*" 2>/dev/null

# Look for recently modified files
echo "Recently modified files:"
find /home -type f -mtime -1 2>/dev/null | head -10
```

### **Simple Backup Creation**

```bash
#!/bin/bash
# Create simple backups

BACKUP_DIR="/home/$(whoami)/backups"
DATE_STAMP=$(date +%Y%m%d_%H%M%S)

# Create backup directory
mkdir -p $BACKUP_DIR

echo "📦 Creating backup..."

# Backup important user files
tar -czf $BACKUP_DIR/my_files_$DATE_STAMP.tar.gz \
    /home/$(whoami)/Documents \
    /home/$(whoami)/Desktop \
    2>/dev/null

# Backup system configuration (if you have permission)
cp /etc/passwd $BACKUP_DIR/passwd_backup_$DATE_STAMP 2>/dev/null
cp /etc/group $BACKUP_DIR/group_backup_$DATE_STAMP 2>/dev/null

echo "✅ Backup created in $BACKUP_DIR"
ls -la $BACKUP_DIR
```

---

## **Part 4: Creating an Incident Report (The Workshop Logbook)**

### **Simple Incident Documentation**

```bash
#!/bin/bash
# Create incident report

INCIDENT_ID="ISSUE_$(date +%Y%m%d_%H%M%S)"
REPORT_FILE="/tmp/incident_$INCIDENT_ID.txt"

echo "📋 Creating incident report..."

cat > $REPORT_FILE << EOF
===============================================
WORKSHOP INCIDENT REPORT
===============================================

Incident ID: $INCIDENT_ID
Date/Time: $(date)
Reported by: $(whoami)

WHAT HAPPENED:
(Describe the problem here)

WHAT WAS AFFECTED:
(List what stopped working)

WHAT WE DID TO FIX IT:
(Steps taken to resolve)

CURRENT STATUS:
(Is it fixed? Partially fixed? Still broken?)

PREVENTION IDEAS:
(How can we prevent this next time?)

===============================================
Report saved: $REPORT_FILE
===============================================
EOF

echo "✅ Incident report created: $REPORT_FILE"
echo "📝 Edit it with: nano $REPORT_FILE"
```

---

## **Part 5: Prevention Checklist (The Maintenance Schedule)**

### **Daily Health Checks**

```bash
#!/bin/bash
# Daily system health check

echo "🏥 Daily System Health Check"
echo "Date: $(date)"
echo "=========================="

# Check system load
echo "System Load:"
uptime

# Check disk space
echo -e "\nDisk Space:"
df -h | grep -E "/$|/home"

# Check memory
echo -e "\nMemory Usage:"
free -h

# Check running services
echo -e "\nImportant Services:"
systemctl is-active ssh networking 2>/dev/null | \
    while read status; do
        echo "Service status: $status"
    done

# Check for errors in logs
echo -e "\nRecent Errors:"
journalctl --since "1 hour ago" -p err --no-pager | tail -3

echo "=========================="
echo "Health check complete!"
```

### **Weekly Maintenance Tasks**

```bash
#!/bin/bash
# Weekly maintenance routine

echo "🔧 Weekly Workshop Maintenance"
echo "=============================="

# Update package lists
echo "1. Updating package information..."
apt update 2>/dev/null

# Clean up old files
echo "2. Cleaning temporary files..."
find /tmp -type f -atime +7 -delete 2>/dev/null

# Check disk usage
echo "3. Checking disk usage..."
df -h

# Create weekly backup
echo "4. Creating weekly backup..."
tar -czf /tmp/weekly_backup_$(date +%Y%m%d).tar.gz \
    /home/$(whoami)/Documents 2>/dev/null

echo "=============================="
echo "Weekly maintenance complete!"
```

---

## **Key Takeaways for Workshop Emergency Response**

### **The Golden Rules of Troubleshooting:**

1. **Don't Panic**: Stay calm and think systematically
2. **Document Everything**: Write down what you see and do
3. **Change One Thing at a Time**: Don't make multiple changes simultaneously
4. **Test After Each Change**: Verify if your fix worked
5. **Keep Backups**: Always have a way to undo changes

### **Emergency Response Priority:**

1. **Safety First**: Make sure the system is stable
2. **Assess the Damage**: Understand what's broken
3. **Fix Critical Issues**: Get essential services running
4. **Document the Incident**: Record what happened and how you fixed it
5. **Prevent Future Problems**: Learn from the experience

### **Simple Command Summary:**

```bash
# Quick system check
uptime && df -h && free -h

# Check service status
systemctl status servicename

# View recent errors
journalctl -p err --no-pager

# Basic backup
tar -czf backup_$(date +%Y%m%d).tar.gz /path/to/important/files

# Clean temporary files
find /tmp -type f -atime +1 -delete
```

### **When to Ask for Help:**

- **System won't boot**: This needs advanced recovery
- **Data corruption**: Don't try to fix alone, get expert help
- **Security breach**: Stop and call for professional assistance
- **Hardware failure**: Physical problems need hardware expertise

### **Prevention is Better Than Cure:**

- **Regular backups**: Schedule weekly backups of important data
- **System updates**: Keep your system updated but test first
- **Monitor resources**: Check disk space and memory regularly
- **Document changes**: Keep track of what you modify
- **Learn from incidents**: Review what went wrong and why

---

Remember: Every expert was once a beginner. The key to becoming a skilled workshop emergency responder is practice, patience, and learning from each incident. Your workshop empire depends on your ability to stay calm under pressure and solve problems systematically!
