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

**Technical Foundation:**
- **Linux**: A free, open-source Unix-like operating system kernel first released in 1991
- **Distribution (Distro)**: A complete operating system built around the Linux kernel, including system software, package managers, and desktop environments
- **Open Source**: Software whose source code is freely available for modification and redistribution under licenses like GPL

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

**Technical Reality:**
- **Linux Market Share**: Powers 96.3% of the world's top 1 million web servers
- **Enterprise Usage**: Dominates cloud computing (AWS, Google Cloud, Azure primarily run Linux)
- **Career Value**: Linux skills are required for most IT infrastructure, DevOps, and cybersecurity roles

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

**Command Explanations:**

**`uname -a`**
- **Purpose**: Display detailed system information
- **Technical Details**: Shows kernel name, hostname, kernel release, kernel version, machine hardware, processor type, hardware platform, and operating system
- **Sample Output**: `Linux ubuntu 5.15.0-72-generic #79-Ubuntu SMP Wed Apr 19 08:22:18 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux`
- **Story Connection**: *"Reading the workshop's technical specifications and blueprints"*

**`whoami`**
- **Purpose**: Display the current logged-in username
- **Technical Details**: Returns the effective username of the current user
- **Sample Output**: `student` or `ubuntu`
- **Story Connection**: *"Confirming your identity as the new workshop owner"*

**`pwd`** (Print Working Directory)
- **Purpose**: Display the absolute path of the current directory
- **Technical Details**: Shows your exact location in the filesystem hierarchy
- **Sample Output**: `/home/student` or `/root`
- **Story Connection**: *"Finding your current location in the workshop"*

**`date`**
- **Purpose**: Display or set the system date and time
- **Technical Details**: Shows current system date/time in default format
- **Sample Output**: `Tue Jul  1 14:30:25 UTC 2025`
- **Story Connection**: *"Checking the workshop's master clock"*

#### **Part 2: Your First Workshop Tools (45 minutes)**

##### **A. The Magic Terminal (20 minutes)**
- **Metaphor**: Terminal as your "workshop intercom system"
- **Story Setup**: *"Every great workshop has a communication system. In your digital workshop, the terminal is how you talk to your tools and machines."*

**Technical Foundation:**
- **Terminal**: A text-based interface for interacting with the operating system
- **Shell**: The command interpreter that processes your commands (commonly bash, zsh, or sh)
- **Command Prompt**: The text that appears before your cursor, showing system information and readiness for input

**Hands-on Discovery**:
```bash
# Workshop Communication Basics
echo "Hello, Workshop!"     # Announcing your presence
cal                        # Checking the workshop calendar
uptime                     # How long has the workshop been running?
```

**Command Explanations:**

**`echo "Hello, Workshop!"`**
- **Purpose**: Display text to the terminal output
- **Technical Details**: Outputs the specified string followed by a newline
- **Syntax**: `echo [options] [string]`
- **Sample Output**: `Hello, Workshop!`
- **Story Connection**: *"Announcing your presence to the workshop systems"*

**`cal`**
- **Purpose**: Display a calendar
- **Technical Details**: Shows calendar for current month by default; can specify month/year
- **Options**: `cal 2025` (full year), `cal 7 2025` (July 2025)
- **Sample Output**: ASCII calendar grid for current month
- **Story Connection**: *"Checking the workshop's scheduling calendar"*

**`uptime`**
- **Purpose**: Show how long the system has been running
- **Technical Details**: Displays current time, system uptime, number of logged-in users, and load averages
- **Sample Output**: `14:30:25 up 2 days, 3:45, 2 users, load average: 0.15, 0.10, 0.05`
- **Load Average**: System performance metrics (1min, 5min, 15min averages)
- **Story Connection**: *"Checking how long the workshop has been operational"*

**Memory Technique**: Create a "first conversation" story
- *Student shares what their terminal "said" back to them*

##### **B. Essential Workshop Vocabulary (25 minutes)**
- **Concept as Language Learning**: 
  - *Commands = Workshop instructions*
  - *Arguments = Specific details for instructions*
  - *Options/Flags = Modifying how tools work*

**Technical Foundations:**
- **Command**: The program or instruction you want to execute
- **Arguments**: Input data or targets for the command (files, directories, text)
- **Options/Flags**: Modifiers that change how a command behaves (start with - or --)
- **Syntax**: `command [options] [arguments]`

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

**Detailed Command Explanations:**

**`ls`** (List)
- **Purpose**: List directory contents
- **Basic Usage**: Shows files and directories in current location
- **Story Connection**: *"Show me what's here in my workshop area"*

**`ls -l`** (Long format)
- **Purpose**: List with detailed information
- **Technical Details**: Shows permissions, links, owner, group, size, modification date
- **Sample Output**: `-rw-r--r-- 1 user user 1024 Jul 01 14:30 file.txt`
- **Story Connection**: *"Show me everything with full specifications and details"*

**`ls -la`** (Long format, All files)
- **Purpose**: List all files including hidden ones with details
- **Technical Details**: Hidden files start with '.' (like .bashrc, .profile)
- **Story Connection**: *"Show me everything, including hidden workshop items"*

**`ls /home`** (List specific directory)
- **Purpose**: List contents of specified directory
- **Technical Details**: `/home` is where user directories are typically stored
- **Absolute Path**: Full path from root directory (/)
- **Story Connection**: *"Show me what's in the workshop's living quarters"*

**`ls -la /home | grep user`** (Pipe and filter)
- **Purpose**: List detailed contents and filter for lines containing "user"
- **Technical Details**: 
  - `|` (pipe): Sends output of first command to second command
  - `grep`: Searches for patterns in text
- **Story Connection**: *"Find all user-related items with full details"*

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

**Safety Command Explanations:**

**`cp original backup`** (Copy)
- **Purpose**: Copy files or directories
- **Technical Details**: Creates an exact duplicate with a new name/location
- **Syntax**: `cp [options] source destination`
- **Safety Practice**: Always backup before modifying important files
- **Story Connection**: *"Always have a backup plan in your workshop"*

**Technical Safety Principles:**
- **Privilege Awareness**: Understanding user permissions and sudo usage
- **Path Awareness**: Always verify your current location before executing commands
- **Backup Strategy**: Copy important files before modification
- **Command Verification**: Use `ls` to confirm file operations succeeded

**Memory Device**: "The Four Workshop Questions"
1. *Who am I?* (whoami) - **User identity and permissions**
2. *Where am I?* (pwd) - **Current directory location**
3. *What's around me?* (ls) - **Directory contents and file permissions**
4. *What am I about to do?* (think before acting) - **Command verification**

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

**Project Command Explanations:**

**`mkdir my_workshop`** (Make Directory)
- **Purpose**: Create a new directory
- **Technical Details**: Creates a new folder in the filesystem
- **Permissions**: Inherits permissions from parent directory
- **Story Connection**: *"Building your main workshop structure"*

**`cd my_workshop`** (Change Directory)
- **Purpose**: Navigate to a different directory
- **Technical Details**: Changes your current working directory
- **Navigation**: Can use relative paths (my_workshop) or absolute paths (/home/user/my_workshop)
- **Story Connection**: *"Moving into your newly created workshop space"*

**`mkdir tools projects materials documentation`**
- **Purpose**: Create multiple directories simultaneously
- **Technical Details**: Space-separated arguments create multiple directories
- **Organization**: Establishes logical structure for different types of content
- **Story Connection**: *"Setting up organized sections in your workshop"*

**`touch workshop_log.txt`**
- **Purpose**: Create an empty file or update file timestamp
- **Technical Details**: If file doesn't exist, creates it; if it exists, updates access/modification time
- **File Creation**: Quick way to create placeholder files
- **Story Connection**: *"Starting your workshop logbook"*

**`echo "Day 1: Inherited the workshop!" > workshop_log.txt`**
- **Purpose**: Write text to a file (overwrite existing content)
- **Technical Details**: 
  - `echo`: Outputs the text
  - `>`: Redirects output to file (overwrites existing content)
  - `>>`: Would append instead of overwrite
- **Data Management**: Basic method of creating file content
- **Story Connection**: *"Making your first entry in the workshop log"*

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

**Exploration Command Explanations:**

**`ls /bin`** (Binary directory)
- **Purpose**: List executable programs/commands
- **Technical Details**: `/bin` contains essential system binaries (cp, ls, mkdir, etc.)
- **System Architecture**: Core commands needed for basic system operation
- **Story Connection**: *"Checking the main tool shed where all basic tools are stored"*

**`ls /home`** (Home directories)
- **Purpose**: List user home directories
- **Technical Details**: Each user typically has a subdirectory under `/home`
- **User Management**: Shows all users who have accounts on the system
- **Story Connection**: *"Visiting the living quarters where workshop users reside"*

**`ls /var/log`** (Log directory)
- **Purpose**: List system log files
- **Technical Details**: `/var/log` contains system activity logs, error messages, security logs
- **System Monitoring**: Critical for troubleshooting and security analysis
- **Story Connection**: *"Reading the workshop journals that record all activities"*

**`cat /etc/os-release`** (Display file contents)
- **Purpose**: Show operating system information
- **Technical Details**: 
  - `cat`: Displays entire file content
  - `/etc/os-release`: Contains OS identification data
- **System Information**: Provides distribution name, version, and other details
- **Sample Output**: Shows NAME="Ubuntu", VERSION="22.04.3 LTS", etc.
- **Story Connection**: *"Finding the workshop's official specifications and documentation"*

**Technical Context for Exploration:**
- **Filesystem Hierarchy Standard (FHS)**: Linux follows standardized directory structure
- **Root Directory (/)**: Top-level directory containing all other directories
- **System Directories**: `/bin`, `/etc`, `/var`, `/home` serve specific purposes
- **File Permissions**: Different directories have different access restrictions

**Sharing Circle**: Each student shares one "surprising discovery"

---

## **Technical Summary & Key Takeaways**

### **Commands Mastered:**
1. **System Information**: `uname -a`, `whoami`, `pwd`, `date`, `uptime`
2. **File Operations**: `ls`, `ls -l`, `ls -la`, `cat`, `touch`, `cp`
3. **Directory Operations**: `mkdir`, `cd`
4. **Text Operations**: `echo`, `grep` (with pipes)

### **Concepts Learned:**
- **Linux Filesystem Structure**: Understanding `/bin`, `/home`, `/var`, `/etc`
- **Command Syntax**: command [options] [arguments]
- **File Permissions**: Basic understanding of security
- **Redirection**: Using `>` for output redirection
- **Pipes**: Using `|` for command chaining

### **Safety Practices Established:**
- Always verify location with `pwd`
- Check contents with `ls` before acting
- Create backups with `cp` before modifying
- Understand user context with `whoami`

**Next Session Preview**: "Navigating Your Workshop" - Advanced file system navigation, file manipulation, and text editing tools.
