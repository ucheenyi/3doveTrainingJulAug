# Week 1: Linux Fundamentals - Story-Driven Lesson Plans
*Building Your Digital Workshop Foundation*

---

## Session 1: Linux Introduction & Setup (2 Hours)
### **Story Theme: "Inheriting a Digital Workshop"**

#### **Opening Narrative (15 minutes)**
*"You've just inherited a mysterious digital workshop from a brilliant but eccentric inventor. The workshop contains powerful tools, but everything looks different from what you're used to. Your mission: learn to master this workshop and unlock its creative potential."*

#### **Part 1: The Workshop Origins (45 minutes)**

##### **A. The Legend of Linux (15 minutes)**
- **Storytelling Approach**: Linux as the "People's Workshop"
  - *Linus Torvalds as the master craftsman who shared his blueprint*
  - *Open source as the "guild system" - craftspeople sharing techniques*
  - *Distributions as different workshop styles (Ubuntu's beginner-friendly, CentOS's industrial, Arch's custom-built)*

- **Memory Palace Technique**: 
  ```
  🏰 1991 - Castle Finland (Linus's origin)
  🐧 Penguin Tux - Workshop mascot/guardian
  🌍 Worldwide Guild - Open source community
  📜 GPL License - The craftsman's code of ethics
  ```

##### **B. Why This Workshop Matters (15 minutes)**
- **Career Story Connections**:
  - *Cloud Engineer*: "Managing digital cities in the sky"
  - *SysAdmin*: "Keeper of the digital realm"
  - *DevOps*: "Bridge builder between creative and operational teams"
  - *Cybersecurity*: "Digital fortress guardian"

##### **C. Workshop Tour (Virtual Machine Setup) (15 minutes)**
- **Analogy**: Setting up your first workbench
- **Hands-on Setup**:
  ```bash
  # Your first workshop inspection
  uname -a     # Reading the workshop blueprint
  whoami       # Confirming your identity as new owner
  pwd          # Finding your current location
  date         # Checking the workshop clock
  ```

#### **Part 2: Your First Workshop Tools (45 minutes)**

##### **A. The Magic Terminal (20 minutes)**
- **Metaphor**: Terminal as your "workshop intercom system"
- **Story Setup**: *"Every great workshop has a communication system. In your digital workshop, the terminal is how you talk to your tools and machines."*

**Hands-on Discovery**:
```bash
# Workshop Communication Basics
echo "Hello, Workshop!"     # Announcing your presence
cal                        # Checking the workshop calendar
uptime                     # How long has the workshop been running?
```

**Memory Technique**: Create a "first conversation" story
- *Student shares what their terminal "said" back to them*

##### **B. Essential Workshop Vocabulary (25 minutes)**
- **Concept as Language Learning**: 
  - *Commands = Workshop instructions*
  - *Arguments = Specific details for instructions*
  - *Options/Flags = Modifying how tools work*

**Progressive Learning**:
```bash
# Level 1: Simple Instructions
ls                    # "Show me what's here"
pwd                   # "Where am I?"
date                  # "What time is it?"

# Level 2: Instructions with Details
ls -l                 # "Show me everything, with details"
ls -la                # "Show me everything, including hidden items"
ls /home             # "Show me what's in the home area"

# Level 3: Complex Workshop Tasks
ls -la /home | grep user    # "Find all user items with details"
```

**Creative Exercise**: Students create their own "workshop phrase book"

#### **Part 3: Workshop Safety & Orientation (30 minutes)**

##### **A. Workshop Safety Rules (15 minutes)**
- **Story Frame**: Every workshop has safety protocols
- **Key Safety Concepts**:
  ```bash
  # Safety First Commands
  whoami              # Always know who you are
  pwd                 # Always know where you are
  ls -la              # Always check before you act
  cp original backup  # Always have a backup plan
  ```

**Memory Device**: "The Four Workshop Questions"
1. *Who am I?* (whoami)
2. *Where am I?* (pwd)
3. *What's around me?* (ls)
4. *What am I about to do?* (think before acting)

##### **B. Your First Workshop Project (15 minutes)**
**Creative Challenge**: "Design Your Ideal Workshop Layout"
```bash
# Create your workshop blueprint
mkdir my_workshop
cd my_workshop
mkdir tools projects materials documentation
touch workshop_log.txt
echo "Day 1: Inherited the workshop!" > workshop_log.txt
```

**Reflection Activity**: Students draw their mental model of the Linux filesystem

#### **Lab Exercise: Workshop Exploration (15 minutes)**
**Scenario**: *"You have 15 minutes to explore your new workshop before the previous owner's assistant arrives to give you the grand tour. What can you discover?"*

**Guided Discovery**:
```bash
# Exploration Mission
ls /bin          # Check the tool shed
ls /home         # Visit the living quarters  
ls /var/log      # Read the workshop journals
cat /etc/os-release  # Find the workshop specifications
```

**Sharing Circle**: Each student shares one "surprising discovery"

---

## Session 2: Command Line Essentials (2 Hours)
### **Story Theme: "Mastering Your Workshop Tools"**

#### **Opening Scene (10 minutes)**
*"The workshop assistant has arrived! She's impressed that you found the terminal but now wants to teach you the essential tools every workshop master must know. 'These tools,' she says, 'will be your daily companions in every project you undertake.'"*

#### **Part 1: Navigation Tools - Your Workshop Compass (40 minutes)**

##### **A. The Workshop Map (20 minutes)**
- **Master Analogy**: Filesystem as a multi-story workshop building
  - *Root (/) = Foundation/Basement*
  - *Home (/home) = Personal workspaces*
  - *Bin (/bin) = Tool storage*
  - *Etc (/etc) = Instruction manuals*

**Visual Learning**:
```bash
# Building Your Mental Map
pwd           # "You are here" marker
ls            # Room contents
ls -la        # Detailed room inventory
cd /          # Go to foundation
tree -L 2     # Workshop blueprint (if available)
```

**Memory Palace Exercise**: Students sketch their workshop building

##### **B. Navigation Mastery (20 minutes)**
**Progressive Skill Building**:

**Level 1: Basic Movement**
```bash
cd ~          # Return to your personal workspace
cd /          # Go to workshop foundation
cd ..         # Go up one floor
cd -          # Return to previous location
```

**Level 2: Efficient Navigation**
```bash
cd ~/Documents     # Direct path to document storage
cd ../..          # Up two floors quickly
pushd /var/log    # Bookmark and jump
popd              # Return to bookmark
```

**Creative Challenge**: "The Fastest Route Game"
- *Students find the quickest path between different workshop areas*
- *Share navigation "tricks" they discover*

#### **Part 2: Information Gathering Tools (40 minutes)**

##### **A. The Workshop Inspector's Toolkit (20 minutes)**
**Story Setup**: *"Every master craftsperson needs to inspect their materials and understand their tools. Here are your essential inspection instruments."*

```bash
# Essential Inspector Tools
ls -la        # Detailed inventory
file script.sh # What type of material is this?
wc document.txt # How much material do we have?
du -h folder   # How much space does this occupy?
stat file.txt  # Complete material specifications
```

**Hands-on Discovery**:
```bash
# Workshop Investigation Mission
cd /bin
file ls cp mv     # Discover tool types
ls -la | head -10 # First 10 tools in storage
du -sh /bin       # How much space do tools occupy?
```

##### **B. Reading Workshop Documentation (20 minutes)**
**Metaphor**: Every tool comes with a manual

**Progressive Manual Reading**:
```bash
# Level 1: Quick Reference
man ls           # The complete manual
man -k copy      # Find tools related to copying
whatis cp        # Quick tool description

# Level 2: Smart Manual Usage
man ls | grep -A5 "sort"  # Find specific features
ls --help        # Quick reference card
```

**Memory Technique**: "The Manual Detective Method"
1. *What does this tool do?* (whatis)
2. *How do I use it?* (--help)
3. *What are all the options?* (man)
4. *Are there related tools?* (man -k)

#### **Part 3: File and Directory Operations (40 minutes)**

##### **A. Workshop Organization Tools (20 minutes)**
**Story Context**: *"A organized workshop is a productive workshop. Let's learn the essential organization tools."*

**Tool Mastery Progression**:
```bash
# Level 1: Basic Organization
mkdir project1           # Create new workspace
touch plan.txt          # Create new document
cp plan.txt backup.txt  # Make safety copy
mv backup.txt archive/  # Move to storage
```

**Level 2: Advanced Organization**
```bash
# Batch Operations
mkdir -p projects/{web,mobile,api}/docs
cp -r template/ new_project/
mv *.txt documents/
```

**Creative Exercise**: "Design Your Project Structure"
```bash
# Students create their ideal project organization
mkdir -p my_projects/{learning,personal,work}/{docs,code,resources}
touch my_projects/learning/linux_journey.md
```

##### **B. Workshop Cleanup Tools (20 minutes)**
**Safety-First Approach**: Deletion as "workshop recycling"

```bash
# Safe Cleanup Practices
ls -la target_file    # Always inspect first
cp important.txt ~/.backup/  # Create backup
rm unnecessary.txt    # Remove safely
rm -i *.tmp          # Interactive removal
```

**The "Backup First" Philosophy**:
```bash
# Professional Cleanup Workflow
mkdir ~/.daily_backup
cp -r current_project ~/.daily_backup/
# Now safe to clean up current_project
```

#### **Part 4: Getting Help in Your Workshop (20 minutes)**

##### **A. Your Workshop Mentor System (10 minutes)**
**Story**: *"Even master craftspeople need guidance. Your workshop comes with built-in mentors."*

```bash
# Your Digital Mentors
man command      # The wise elder
info command     # The detailed teacher  
command --help   # The quick advisor
which command    # The tool locator
type command     # The tool identifier
```

##### **B. Community Workshop Network (10 minutes)**
**Concept**: Connecting to the global workshop community

```bash
# Community Resources (Demo only - explain concepts)
# Online manual: man7.org
# Community forums: Stack Overflow, Unix & Linux Stack Exchange
# Practice platforms: OverTheWire, HackerRank
```

#### **Lab Challenge: Workshop Mastery Test (20 minutes)**
**Scenario**: *"The workshop assistant is testing your readiness. Complete these challenges to prove you've mastered the basic tools."*

**Progressive Challenges**:
```bash
# Level 1: Basic Navigation
# Navigate to /tmp, create a folder with your name, go inside it

# Level 2: File Operations  
# Create 5 text files, copy them to a backup folder, list everything

# Level 3: Information Gathering
# Find the size of /bin directory, count files in /etc, check file types in your folder

# Level 4: Cleanup
# Safely remove temporary files, keeping backups
```

**Peer Learning**: Students help each other complete challenges

#### **Session Wrap-up: Building Your Daily Toolkit (10 minutes)**
**Reflection Activity**: "My Essential Daily Commands"
- Students create a personal "cheat sheet" of their most-used commands
- Share one "aha moment" from the session
- Preview next session: "Tomorrow we learn to monitor and control the workshop's operations"

---

## Session 3: System Information & Processes (2 Hours)
### **Story Theme: "Becoming the Workshop Supervisor"**

#### **Opening Narrative (10 minutes)**
*"Congratulations! You've been promoted from workshop apprentice to workshop supervisor. Now you need to understand what's happening in your workshop at all times - which machines are running, who's using what tools, and how to manage the workflow efficiently. Today you learn to see the invisible activities in your digital workshop."*

#### **Part 1: Workshop Health Monitoring (45 minutes)**

##### **A. Vital Signs of Your Workshop (25 minutes)**
**Medical Analogy**: System monitoring as workshop health checkup

**Essential Health Monitors**:
```bash
# Workshop Vital Signs
uptime           # How long has the workshop been running?
whoami           # Confirming your supervisor identity
who              # Who else is in the workshop?
w                # What is everyone doing?
id               # Your supervisor credentials
```

**Story Connection**: *"Just like a doctor checks pulse, temperature, and blood pressure, you check system uptime, user activity, and resource usage."*

**Hands-on Health Check**:
```bash
# Daily Workshop Inspection Routine
date             # Current time check
uptime           # System health overview
df -h            # Storage space check (like checking supply levels)
free -h          # Memory usage (workshop mental capacity)
```

**Memory Device**: "The DUFF Morning Routine"
- **D**ate - What time is it?
- **U**ptime - How long running?
- **F**ree - Memory status
- **F**ilespace (df) - Storage status

##### **B. Workshop Resource Dashboard (20 minutes)**
**Metaphor**: System resources as workshop utilities (power, space, supplies)

```bash
# Resource Monitoring
lscpu            # Workshop processing power specs
lsmem            # Memory configuration details
lsblk            # Storage device layout
df -h            # Available workspace
du -sh /home/*   # Space used by each worker
```

**Visual Learning Exercise**: Students create a "workshop dashboard sketch"
- CPU = Workshop engines
- Memory = Active workbench space  
- Storage = Warehouse shelves
- Network = Communication lines

#### **Part 2: Understanding Workshop Activities (Processes) (45 minutes)**

##### **A. The Workshop Activity Monitor (25 minutes)**
**Story Setup**: *"Your workshop runs many activities simultaneously - some visible, some invisible. As supervisor, you need to see everything that's happening."*

**Process Discovery Journey**:
```bash
# Level 1: Basic Activity View
ps               # Current workstation activities
ps aux           # All workshop activities (detailed)
ps aux | head    # Top activities summary
```

**Level 2: Live Activity Dashboard**
```bash
top              # Real-time workshop monitor
htop             # Enhanced activity dashboard (if available)
# Navigate using arrow keys, 'q' to quit
```

**Creative Analogy Building**:
- **PID** = Employee ID number
- **CPU%** = How hard someone is working
- **MEM%** = How much workspace they're using
- **TIME** = How long they've been working
- **COMMAND** = What job they're doing

##### **B. Managing Workshop Activities (20 minutes)**
**Responsible Management Philosophy**: *"With great power comes great responsibility. Learn to manage processes ethically and safely."*

**Safe Process Management**:
```bash
# Gentle Process Management
ps aux | grep firefox     # Find specific activity
kill -15 PID             # Polite request to stop
kill -9 PID              # Emergency stop (last resort)
killall firefox          # Stop all instances of a program
```

**Background Operations**:
```bash
# Running Long Tasks
sleep 100 &              # Start background task
jobs                     # Check background activities
fg %1                    # Bring background task to foreground
nohup long_task.sh &     # Task that survives logout
```

**Ethics Discussion**: "When is it appropriate to terminate processes?"
- Your own processes: Always OK
- System processes: Be very careful
- Other users' processes: Usually not allowed/appropriate

#### **Part 3: Workshop Communication Systems (40 minutes)**

##### **A. Internal Communication Network (20 minutes)**
**Story Context**: *"Your workshop has an internal communication system. Understanding it helps you troubleshoot problems and optimize performance."*

**Network Discovery**:
```bash
# Workshop Communication Status
hostname         # Workshop name/address
hostname -I      # Workshop network address
ip addr show     # Detailed network configuration
netstat -tuln    # Active communication channels
ss -tuln         # Modern communication channel viewer
```

**Creative Visualization**: Students draw their workshop's "communication map"

##### **B. System Service Status (20 minutes)**
**Metaphor**: Services as workshop departments (security, maintenance, communications)

```bash
# Department Status Check
systemctl status ssh     # Security department status
systemctl list-units --type=service  # All department statuses
journalctl -xe          # Department activity logs
```

**Understanding Services as Workshop Departments**:
- **SSH** = Security gate
- **HTTP/Apache** = Customer service desk
- **MySQL** = Records department
- **Cron** = Scheduling department

#### **Part 4: Advanced Workshop Intelligence (30 minutes)**

##### **A. Historical Activity Analysis (15 minutes)**
**Detective Work**: Understanding what happened in your workshop

```bash
# Workshop History Investigation
history          # Your command history
last             # Recent workshop visitors
lastlog          # When each worker last visited
journalctl --since "1 hour ago"  # Recent workshop events
```

**Storytelling Exercise**: Students create a "day in the life" story using command history

##### **B. Performance Optimization Insights (15 minutes)**
**Master Craftsperson Skills**: Making your workshop run better

```bash
# Performance Analysis
iostat           # Workshop input/output efficiency
vmstat           # Virtual memory statistics
sar              # System activity reporter (if available)
```

**Concept Introduction**: *"These are advanced tools. Don't worry about mastering them now - just know they exist for when you become a workshop master."*

#### **Lab Challenge: Workshop Supervisor Simulation (20 minutes)**
**Scenario**: *"You're the weekend supervisor. The workshop owner will call in 20 minutes asking for a complete status report. Gather all the information you need!"*

**Required Information**:
1. Workshop uptime and current time
2. Who is currently working
3. Top 5 most active processes
4. Available storage space
5. Memory usage status
6. Any background tasks running
7. Network connectivity status

**Bonus Challenge**: Create a "supervisor's daily report" script

#### **Session Wrap-up: Your Supervisor Toolkit (10 minutes)**
**Reflection Activity**: "My Workshop Supervisor Checklist"
- Students create a personal monitoring routine
- Share their most useful discovery
- **Preview**: "Next session - Managing workshop documents and tools like a professional"

---

## Session 4: Text Editors & File Management (2 Hours)
### **Story Theme: "Mastering the Workshop Documentation System"**

#### **Opening Story (10 minutes)**
*"Every master craftsperson knows that good documentation separates professionals from amateurs. Your workshop contains powerful writing and document management tools that can handle everything from quick notes to complex technical manuals. Today, you become the workshop's master documentarian."*

#### **Part 1: The Workshop Writing Tools (50 minutes)**

##### **A. Quick Note-Taking Tools (15 minutes)**
**Analogy**: Different writing tools for different jobs (pencil vs. pen vs. marker)

**Nano - The Friendly Notepad**:
```bash
# Your trusty notebook
nano quick_notes.txt
# Inside nano:
# Write notes
# Ctrl+O to save (WriteOut)
# Ctrl+X to exit
```

**Story Connection**: *"Nano is like a friendly assistant who guides you through everything with helpful hints at the bottom."*

**Memory Device**: "Nano Commands as Daily Actions"
- **Ctrl+O** = **O**pen your notebook to save
- **Ctrl+X** = e**X**it when done
- **Ctrl+K** = **K**ut (delete) line
- **Ctrl+U** = **U**ndo delete

##### **B. Vi/Vim - The Master's Tool (25 minutes)**
**Epic Story Setup**: *"Vi is the legendary craftsman's tool - complex but incredibly powerful. It's like learning to use a traditional Japanese sword - difficult at first, but masters become lightning fast."*

**The Vi Philosophy**: Modal editing as different "modes of thinking"
- **Normal Mode** = Observation and command mode
- **Insert Mode** = Creation mode  
- **Command Mode** = Workshop management mode

**Progressive Vi Journey**:
```bash
# Step 1: Entering the dojo
vi practice.txt

# Step 2: Basic survival skills
# Press 'i' to enter insert mode (you'll see -- INSERT --)
# Type some text
# Press Esc to return to normal mode
# Type :wq to save and quit
```

**Vi Survival Guide** (Students create this as practice):
```
Vi Emergency Kit:
- i = Insert mode (start typing)
- Esc = Normal mode (command mode)
- :w = Save (write)
- :q = Quit
- :wq = Save and quit
- :q! = Quit without saving
- x = Delete character
- dd = Delete line
```

**Cultural Story**: *"Vi was created in 1976. It's older than most of your parents, but it's still used by millions of professionals daily. Learning Vi connects you to decades of Unix tradition."*

##### **C. Modern Editors (10 minutes)**
**Contemporary Tools Overview**:
```bash
# Modern alternatives (demonstration)
gedit filename.txt      # Graphical notepad
code filename.txt       # VS Code (if available)
emacs filename.txt      # Another legendary editor
```

**Philosophy Discussion**: "Why learn old tools when new ones exist?"
- Older tools are often faster
- Available on every Linux system
- Lightweight and reliable
- Understanding basics helps with advanced usage

#### **Part 2: Advanced File Management (50 minutes)**

##### **A. File Content Analysis Tools (25 minutes)**
**Story Theme**: *"As workshop documentarian, you need to analyze and understand the content of documents quickly and efficiently."*

**Document Analysis Toolkit**:
```bash
# Quick Document Inspection
head document.txt       # First 10 lines (document opening)
tail document.txt       # Last 10 lines (document ending)
head -n 5 document.txt  # First 5 lines only
tail -n 20 logfile.txt  # Last 20 lines (recent events)
```

**Advanced Content Tools**:
```bash
# Document Intelligence
wc document.txt         # Word count (words, lines, characters)
wc -l *.txt            # Count lines in all text files
sort names.txt         # Alphabetical organization
sort -n numbers.txt    # Numerical organization
uniq sorted_file.txt   # Remove duplicates
```

**Hands-on Workshop Project**: "Document Analysis Mission"
```bash
# Create a sample document
cat > workshop_inventory.txt << EOF
hammer
screwdriver
wrench
hammer
saw
drill
wrench
pliers
EOF

# Analyze the inventory
wc -l workshop_inventory.txt      # How many items?
sort workshop_inventory.txt       # Alphabetical order
sort workshop_inventory.txt | uniq # Remove duplicates
sort workshop_inventory.txt | uniq -c # Count each item
```

##### **B. Powerful Search and Replace (25 minutes)**
**Detective Story**: *"Sometimes you need to find specific information hidden in thousands of documents. Here are your detective tools."*

**The Grep Detective Family**:
```bash
# Basic Search
grep "error" logfile.txt          # Find all error mentions
grep -i "ERROR" logfile.txt       # Case-insensitive search
grep -n "TODO" code.txt           # Show line numbers
grep -r "function" project/       # Search entire directory
```

**Advanced Search Techniques**:
```bash
# Pattern Matching
grep "^The" document.txt          # Lines starting with "The"
grep "end$" document.txt          # Lines ending with "end"
grep "[0-9]" mixed.txt            # Lines containing numbers
find . -name "*.txt" -exec grep "important" {} \;  # Search in all .txt files
```

**The Sed Editor** (Introduction):
```bash
# Text Transformation Magic
sed 's/old/new/g' file.txt        # Replace all "old" with "new"
sed 's/error/ERROR/g' log.txt     # Emphasize errors
sed -n '10,20p' large_file.txt    # Show only lines 10-20
```

**Creative Exercise**: "Document Detective Challenge"
Students create a mystery document and challenge classmates to find specific information using grep and sed.

#### **Part 3: File Organization Mastery (40 minutes)**

##### **A. Advanced File Operations (20 minutes)**
**Professional Workshop Organization**:

```bash
# Batch File Operations
find . -name "*.tmp" -delete      # Clean up temporary files
find . -type f -name "*.log" -exec cp {} backup/ \;  # Backup all logs
rename 's/old/new/' *.txt         # Batch rename files
```

**Archive Management**:
```bash
# Workshop Archive System
tar -czf project_backup.tar.gz project/    # Create compressed archive
tar -xzf backup.tar.gz                     # Extract archive
zip -r project.zip project/                # Create zip archive
unzip project.zip                          # Extract zip
```

**Story Context**: *"Professional workshops maintain organized archives. You never know when you'll need to retrieve an old project or restore from backup."*

##### **B. File Permissions and Ownership (20 minutes)**
**Workshop Security System**: Understanding who can access what

**Permission Visualization**:
```bash
ls -la                    # See detailed permissions
# Example output: -rw-r--r-- 1 user group 1024 date filename
#                  ^^^^^^^^^ 
#                  File permissions
```

**Permission Translation**:
- **Position 1**: File type (- = file, d = directory, l = link)
- **Positions 2-4**: Owner permissions (rwx)
- **Positions 5-7**: Group permissions (rwx)  
- **Positions 8-10**: Everyone else permissions (rwx)

**Permission Management**:
```bash
# Changing Permissions
chmod u+x script.sh      # Give owner execute permission
chmod 755 public_script.sh   # Owner: rwx, Group: r-x, Others: r-x
chmod 644 document.txt    # Owner: rw-, Group: r--, Others: r--
chown user:group file.txt # Change ownership
```

**Real-world Scenarios**:
- **Scripts**: Need execute permission (chmod +x)
- **Private documents**: Only owner access (chmod 600)
- **Shared files**: Group readable (chmod 664)
- **Public scripts**: Everyone can execute (chmod 755)

#### **Lab Challenge: Master Documentarian Project (20 minutes)**
**Scenario**: *"The workshop owner has asked you to organize and document a chaotic project directory left by the previous assistant. Show your mastery of file management and documentation tools."*

**Challenge Setup**:
```bash
# Create messy project directory
mkdir chaos_project
cd chaos_project
touch README.txt main.py backup.py.old data.csv temp.tmp log.txt error.log
echo "This project needs organization!" > README.txt
echo "TODO: Fix the bug in line 42" >> main.py
echo "ERROR: Connection failed" >> error.log
echo "INFO: Process completed" >> log.txt
```

**Tasks**:
1. **Document Analysis**: Count files, find TODO items, locate errors
2. **Organization**: Create proper directory structure, move files appropriately
3. **Cleanup**: Remove temporary files, create archives
4. **Documentation**: Create a proper project README using your editor of choice
5. **Security**: Set appropriate permissions for different file types

**Bonus Challenges**:
- Create a script to automate the organization process
- Find and fix the "bug" mentioned in the TODO
- Create a backup strategy for the organized project

#### **Session Wrap-up: Your Documentation System (10 minutes)**
**Reflection Activity**: "My Personal Documentation Workflow"
- Students document their preferred tools and techniques
- Share one productivity tip they discovered
- Create a personal "file management checklist"
- **Preview**: "Next week - Becoming the workshop administrator with user management and security"

---

## Week 1 Assessment & Reinforcement

### **Spaced Repetition Cards**
Students create flashcards for:
- Essential commands with their "workshop analogies"
- File permission patterns with real-world scenarios
- Vi/Vim survival commands
- Process management safety rules

### **Story Connections**
Each student maintains a "workshop journal" documenting:
- Daily discoveries and "aha moments"
- Personal analogies that help them remember concepts
- Real-world connections to course material
- Questions for future exploration

### **Peer Teaching Preparation**
- Students pair up to explain concepts using their own analogies
- Practice sessions where they teach a concept to someone else
- Collaborative creation of "workshop wisdom" - shared tips and tricks

### **Week 1 Mastery Indicators**
By the end of Week 1, students should be able to:
1. Navigate the Linux filesystem confidently using their "workshop map" mental model
2. Monitor system processes and resources like a "workshop supervisor"
3. Edit files efficiently using both simple (nano) and powerful (vi) tools
4. Organize and analyze files using advanced command-line tools
5. Explain Linux concepts using consistent analogies and stories

This foundation prepares them for Week 2's advanced topics while maintaining the engaging, story-driven approach that enhances both retention and creative problem-solving abilities.
