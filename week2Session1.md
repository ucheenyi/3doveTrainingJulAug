# Week 2 Session 5: Users & Permissions - Student Notes
*Building Your Workshop Team*

## Opening Story & Context
**Story Theme**: "Your digital workshop has become so successful that you need to hire assistants and specialists. Today you become not just a workshop owner, but a workshop manager leading a diverse team."

**Technical Context**: Linux is a multi-user system where multiple people can use the computer at the same time. You need to understand how to manage users and control who can access what files.

---

## Part 1: Understanding Your Workshop Team (Users)

### The Workshop Hierarchy - Who's Who in Linux

**Story**: Linux users are like different roles in a workshop
**Technical Reality**: Linux has different types of users with different levels of access

#### Basic User Commands
```bash
# Find out who you are
whoami          # Shows your username
id              # Shows your user number and groups
groups          # Shows what teams you belong to
```

**What This Means**: 
- Every user has a unique number (User ID)
- Users belong to groups (like teams)
- This helps organize permissions

#### Types of Users

**1. Root User (The Boss)**
- **Story**: The Master Craftsman who owns everything
- **Technical**: Can do anything on the system
- **Important**: Never use root for everyday tasks - too dangerous!

**2. Regular Users**
- **Story**: Skilled workers with their own workspace
- **Technical**: Normal people who use the computer
- **Home**: Each user gets their own folder in `/home/username`

**3. System Users**
- **Story**: Invisible helpers that run background services
- **Technical**: Special accounts that run programs, not for humans to log into

#### Getting Root Powers When Needed
```bash
su -            # Become root (need root password)
sudo whoami     # Run one command as root
exit            # Go back to normal user
```

**Key Point**: Use `sudo` for single commands rather than becoming root completely.

### Creating New Users

#### Adding People to Your Workshop
```bash
# Create a new user
sudo useradd -m alice          # -m creates their home folder
sudo passwd alice              # Set their password

# Add user to a group
sudo usermod -aG developers alice  # Add Alice to developers group
```

**What Happens**:
- User gets added to the system
- They get a home directory (`/home/alice`)
- They can now log in with their password

#### Checking User Information
```bash
# See user information
cat /etc/passwd | tail -5      # See recent users
cat /etc/group | grep developers   # Check who's in a group
```

**File Breakdown**:
- `/etc/passwd`: List of all users
- `/etc/group`: List of all groups and their members

---

## Part 2: Workshop Security System (File Permissions)

### Understanding File Permissions - The Lock System

**Story**: File permissions are like locks on doors and filing cabinets
**Technical Reality**: Every file has permissions that control who can read, write, or execute it

#### Reading Permission Information
```bash
ls -la workshop_files/
# Example output: -rwxr-x--- 1 alice developers 1024 Jan 1 12:00 file.txt
```

**Breaking Down the Permissions**:
```
-rwxr-x---
 |||||||^^^ Others (everyone else)
 ||||^^^     Group (team members)
 ^^^         Owner (file creator)
```

**What Each Letter Means**:
- **r** = read (can view the file)
- **w** = write (can change the file)
- **x** = execute (can run the file as a program)
- **-** = no permission

#### Common Permission Patterns
```bash
# Setting permissions with numbers
chmod 755 public_tools/        # Owner: full access, Others: read+run
chmod 700 private_office/      # Owner only
chmod 644 document.txt         # Owner: read+write, Others: read only
chmod 600 secret.txt           # Owner: read+write, Nobody else
```

**Number System**:
- **4** = read
- **2** = write  
- **1** = execute
- Add them up: 7 = read+write+execute, 6 = read+write, 5 = read+execute

#### Changing Permissions
```bash
# Using letters (alternative method)
chmod u+w file.txt             # Give owner write permission
chmod g-x file.txt             # Remove execute from group
chmod o+r file.txt             # Give others read permission
chmod a+x script.sh            # Give everyone execute permission
```

**Letters Explained**:
- **u** = user (owner)
- **g** = group
- **o** = others
- **a** = all (everyone)
- **+** = add permission
- **-** = remove permission

### Changing File Ownership
```bash
# Change who owns a file
sudo chown alice file.txt      # Make alice the owner
sudo chgrp developers file.txt # Change group to developers
sudo chown alice:developers file.txt  # Change both at once
```

---

## Part 3: Workshop Communication & Teamwork

### Working with Groups
```bash
# Create a new group
sudo groupadd developers       # Create developers group
sudo groupadd testers         # Create testers group

# Add users to groups
sudo usermod -aG developers alice  # Add alice to developers
sudo usermod -aG testers bob      # Add bob to testers
```

### Setting Up Shared Workspaces
```bash
# Create a shared folder
sudo mkdir /shared/team_project
sudo chgrp developers /shared/team_project  # Give it to developers group
sudo chmod 775 /shared/team_project         # Group can read/write
```

**What This Does**:
- Creates a folder that the whole team can use
- Everyone in the "developers" group can read and write files
- Other people can only read

### Checking User Activity
```bash
# See who's logged in
who                    # Current users
last                   # Recent login history
```

---

## Simple Lab Challenge: Set Up a Team

### Your Mission
Create a simple team setup with users and shared folders.

#### Step 1: Create Users
```bash
# Create three users
sudo useradd -m alice
sudo useradd -m bob
sudo useradd -m charlie

# Set their passwords
sudo passwd alice
sudo passwd bob
sudo passwd charlie
```

#### Step 2: Create a Group
```bash
# Create a team group
sudo groupadd team

# Add everyone to the team
sudo usermod -aG team alice
sudo usermod -aG team bob
sudo usermod -aG team charlie
```

#### Step 3: Create Shared Folder
```bash
# Create shared workspace
sudo mkdir /shared/teamwork
sudo chgrp team /shared/teamwork
sudo chmod 775 /shared/teamwork
```

#### Step 4: Test It
```bash
# Check your work
groups alice           # Should show "alice team"
ls -la /shared/        # Should show teamwork folder with team group
```

---

## Key Points to Remember

### Security Basics
1. **Don't use root** for everyday tasks - use `sudo` instead
2. **Be careful with permissions** - don't give everyone access to everything
3. **Use groups** to manage team access easily
4. **Check permissions** before sharing sensitive files

### Essential Commands
```bash
# User management
whoami, id, groups
sudo useradd -m username
sudo passwd username
sudo usermod -aG group username

# File permissions
ls -la
chmod 755 file
chmod u+w file
chown user:group file

# Groups
sudo groupadd groupname
groups username
```

### Permission Numbers to Remember
- **755** = Owner: full access, Others: read+execute (good for programs)
- **644** = Owner: read+write, Others: read only (good for documents)
- **700** = Owner only (good for private folders)
- **600** = Owner read+write only (good for private files)

### Common Mistakes to Avoid
- Using chmod 777 (gives everyone full access - dangerous!)
- Forgetting to create home directories with -m
- Not adding users to the right groups
- Working as root when you don't need to
