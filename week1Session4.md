# Session 4: Text Editors & File Management (2 Hours)
### **Story Theme: "Learning the Digital Workshop Tools"**

#### **Opening Story (10 minutes)**
*"Every craftsperson needs good tools to create quality work. In the digital world, text editors are like your workshop tools - some are simple and easy to learn, others are powerful but take more practice. Today, we'll explore the essential tools that every Linux user should know."*

**What You'll Learn**: Text editors help you create and modify files in Linux. Whether you're writing notes, editing configuration files, or creating scripts, these tools are fundamental to working effectively in Linux.

---

## **Part 1: Learning the Basic Writing Tools (50 minutes)**

### **A. Nano - The Friendly Editor (20 minutes)**

#### **Why Start with Nano?**
*"Nano is like a helpful friend who shows you what to do at every step."*

**What is Nano?**
- A simple, beginner-friendly text editor
- Shows helpful commands at the bottom of the screen
- No complicated modes - you can start typing immediately
- Perfect for quick edits and learning

#### **Your First Nano Experience**

**Let's Create a Simple Document:**
```bash
# Start nano with a new file
nano my_first_file.txt
```

**What you see:**
- A clean writing area
- Helpful commands shown at the bottom
- The cursor ready for you to type

**Type this sample text:**
```
My Linux Learning Journey
========================
Date: [Today's date]

What I've learned so far:
- How to navigate directories
- Basic file operations
- Using the command line

Goals for this session:
- Learn to use text editors
- Practice file management
- Feel more confident with Linux
```

**Essential Nano Commands** (shown at bottom of screen):
- **Ctrl+O** - Save your file (WriteOut)
- **Ctrl+X** - Exit nano
- **Ctrl+K** - Cut (delete) a line
- **Ctrl+U** - Paste the cut line back
- **Ctrl+W** - Search for text

**Practice Exercise:**
1. Try searching for the word "Linux" (Ctrl+W)
2. Delete a line and bring it back (Ctrl+K, then Ctrl+U)
3. Save your file (Ctrl+O)
4. Exit nano (Ctrl+X)

**Memory Trick:**
- **Ctrl+O** = **O**pen your notebook to save
- **Ctrl+X** = e**X**it when you're done
- **Ctrl+W** = **W**here is that word?

---

### **B. Vi - The Traditional Editor (20 minutes)**

#### **Meet Vi - The Classic Tool**
*"Vi is like learning to drive a manual transmission car - it takes practice, but once you know it, it's incredibly powerful and available everywhere."*

**Why Learn Vi?**
- Found on every Linux system
- Very powerful once you learn it
- Uses different "modes" for different tasks
- Preferred by many experienced users

**Understanding Vi's Modes:**
Unlike nano where you can always type, Vi has different modes:
- **Normal Mode** - For moving around and giving commands
- **Insert Mode** - For typing text
- **Command Mode** - For saving and quitting

#### **Your First Vi Session**

**Start Vi:**
```bash
vi practice_file.txt
```

**What you see:**
- A mostly blank screen
- Your cursor at the top
- You're in "Normal Mode" (can't type yet)

**Step-by-Step Practice:**

1. **Enter Insert Mode:**
   - Press `i` (you'll see "INSERT" at the bottom)
   - Now you can type!

2. **Type some text:**
   ```
   Learning Vi step by step
   This is my practice file
   Vi takes patience but it's worth it
   ```

3. **Return to Normal Mode:**
   - Press `Esc` (INSERT disappears)
   - Now you're back in command mode

4. **Move around (in Normal Mode):**
   - `h` - Move left
   - `j` - Move down
   - `k` - Move up
   - `l` - Move right

5. **Save and quit:**
   - Type `:w` and press Enter (saves file)
   - Type `:q` and press Enter (quits vi)
   - Or combine them: `:wq` (save and quit together)

**Vi Emergency Commands** (for when you get stuck):
- `:q!` - Quit without saving (emergency exit!)
- `Esc` - Always gets you back to Normal Mode
- `u` - Undo your last change

**Practice Challenge:**
1. Open vi with a new file
2. Enter insert mode and type a short message
3. Exit insert mode
4. Save and quit
5. If you get stuck, use `:q!` to start over

---

### **C. Choosing Your Editor (10 minutes)**

#### **When to Use Which Editor**

**Use Nano when:**
- You're learning Linux
- Making quick edits
- You want simple and straightforward
- You see the helpful commands at the bottom

**Use Vi when:**
- You're on a system where nano isn't available
- You want to learn a powerful, universal tool
- You're working on remote systems
- You're ready for a challenge

**Other Options:**
```bash
# If available on your system
gedit filename.txt      # Graphical editor (like Notepad)
code filename.txt       # VS Code (if installed)
```

**The Bottom Line:**
- Start with nano for everyday use
- Learn vi basics for when you need it
- Use what feels comfortable for your work

---

## **Part 2: Managing Your Files Better (50 minutes)**

### **A. Understanding File Content (25 minutes)**

#### **Looking Inside Files Without Opening Them**
*"Sometimes you need to peek inside a file quickly, like looking at the first page of a book before reading the whole thing."*

#### **Quick File Viewing Commands**

**See the Beginning or End:**
```bash
# Look at the start of a file
head filename.txt        # First 10 lines
head -n 5 filename.txt   # First 5 lines only

# Look at the end of a file
tail filename.txt        # Last 10 lines
tail -n 3 filename.txt   # Last 3 lines only
```

**Why This is Useful:**
- Check log files for recent activity
- See file headers or summaries
- Preview large files before opening

**Practical Example:**
```bash
# Create a sample file to practice with
cat > sample_log.txt << 'EOF'
Day 1: Started Linux journey
Day 2: Learned basic commands
Day 3: Explored file system
Day 4: Practiced with directories
Day 5: Learned text editors
Day 6: File management skills
Day 7: Feeling more confident
Day 8: Ready for more challenges
EOF

# Now try the commands
head -n 3 sample_log.txt    # See first 3 days
tail -n 2 sample_log.txt    # See last 2 days
```

**Count Things in Files:**
```bash
# Get file statistics
wc filename.txt         # Lines, words, characters
wc -l filename.txt      # Just count lines
wc -w filename.txt      # Just count words
```

**Try it:**
```bash
wc sample_log.txt       # How many lines in your log?
wc -w sample_log.txt    # How many words?
```

#### **Organizing File Contents**

**Sorting Things:**
```bash
# Put lines in order
sort filename.txt       # Alphabetical order
sort -r filename.txt    # Reverse order
sort -n numbers.txt     # Numerical order (for numbers)
```

**Practice with Lists:**
```bash
# Create a simple list
cat > shopping_list.txt << 'EOF'
bananas
apples
milk
bread
eggs
apples
milk
EOF

# Try sorting
sort shopping_list.txt              # Alphabetical
sort shopping_list.txt | uniq       # Remove duplicates
sort shopping_list.txt | uniq -c    # Count how many of each
```

---

### **B. Finding Things in Files (25 minutes)**

#### **Searching for Text**
*"Finding specific information in files is like having a super-powered search function for your documents."*

#### **Basic Text Search with Grep**

**Simple Searches:**
```bash
# Find lines containing specific text
grep "word" filename.txt           # Find "word" in file
grep -i "word" filename.txt        # Find "word" (ignore case)
grep -n "word" filename.txt        # Show line numbers
grep -c "word" filename.txt        # Count how many lines match
```

**What These Options Do:**
- `-i` makes the search case-insensitive (finds "Word", "WORD", "word")
- `-n` shows you which line number the match is on
- `-c` just tells you how many matches, not the actual text

**Practical Search Exercise:**
```bash
# Create a practice file
cat > practice_search.txt << 'EOF'
The quick brown fox jumps over the lazy dog.
The lazy dog was sleeping in the sun.
A fox is a clever animal.
Dogs are loyal companions.
The brown fox likes to hunt at night.
EOF

# Practice searching
grep "fox" practice_search.txt          # Find all mentions of fox
grep -i "the" practice_search.txt       # Find "the" in any case
grep -n "dog" practice_search.txt       # Find dog with line numbers
grep -c "brown" practice_search.txt     # Count how many lines have brown
```

**Advanced Search Patterns:**
```bash
# Find lines that start with specific text
grep "^The" practice_search.txt         # Lines starting with "The"

# Find lines that end with specific text
grep "dog.$" practice_search.txt        # Lines ending with "dog."

# Find lines containing numbers
grep "[0-9]" practice_search.txt        # Lines with any number
```

#### **Simple Text Replacement**

**Using Sed for Basic Changes:**
```bash
# Replace text in a file
sed 's/old/new/' filename.txt          # Replace first occurrence
sed 's/old/new/g' filename.txt         # Replace all occurrences
```

**Practice Example:**
```bash
# Change fox to wolf in our practice file
sed 's/fox/wolf/g' practice_search.txt

# The original file is unchanged - sed just shows you the result
# To save changes to a new file:
sed 's/fox/wolf/g' practice_search.txt > modified_file.txt
```

**Why This is Useful:**
- Update configuration files
- Fix typos in multiple places
- Prepare files for different uses

---

## **Part 3: Organizing Your Files (40 minutes)**

### **A. Finding Files on Your System (20 minutes)**

#### **The Find Command**
*"The find command is like having a personal assistant who can locate any file on your system."*

**Basic File Finding:**
```bash
# Find files by name
find . -name "*.txt"                # Find all .txt files
find . -name "my_file"              # Find exact filename
find . -name "*.py"                 # Find all Python files
```

**What the Parts Mean:**
- `.` means "search starting from here"
- `-name` means "look for this filename pattern"
- `*` means "match anything" (so `*.txt` finds all files ending in .txt)

**Finding by File Type:**
```bash
# Find different types of items
find . -type f -name "*.txt"        # Files only (not directories)
find . -type d -name "backup"       # Directories only
```

**Practical Finding Exercise:**
```bash
# Create some files to practice with
mkdir -p practice_find/documents
mkdir -p practice_find/scripts
touch practice_find/documents/report.txt
touch practice_find/documents/notes.txt
touch practice_find/scripts/backup.sh
touch practice_find/readme.md

# Now practice finding them
find practice_find -name "*.txt"    # Find text files
find practice_find -name "*.sh"     # Find shell scripts
find practice_find -type d          # Find directories
```

**Find Files by Size or Date:**
```bash
# Find large files
find . -size +1M                    # Files larger than 1 megabyte
find . -size -100k                  # Files smaller than 100 kilobytes

# Find recent files
find . -mtime -7                    # Files modified in last 7 days
find . -mtime +30                   # Files older than 30 days
```

---

### **B. Creating Archives (Backups) (20 minutes)**

#### **Making Backups with Tar**
*"Creating archives is like putting all your important papers in a safe folder that you can store away and retrieve later."*

**What is Tar?**
- A tool for combining multiple files into one archive file
- Like creating a digital folder that contains everything you need
- Useful for backups, sharing projects, or organizing files

**Basic Archive Commands:**
```bash
# Create an archive
tar -czf my_backup.tar.gz folder_to_backup/

# Extract an archive
tar -xzf my_backup.tar.gz

# Look inside an archive without extracting
tar -tzf my_backup.tar.gz
```

**What These Options Mean:**
- `-c` = Create a new archive
- `-x` = Extract files from an archive
- `-t` = List what's in an archive
- `-z` = Compress the archive to save space
- `-f` = Use this filename

**Practical Archive Exercise:**
```bash
# Create a project to backup
mkdir my_project
cd my_project
echo "This is my main file" > main.txt
echo "These are my notes" > notes.txt
mkdir docs
echo "Documentation here" > docs/readme.txt
cd ..

# Create a backup archive
tar -czf project_backup.tar.gz my_project/

# Verify what's in the archive
tar -tzf project_backup.tar.gz

# Test extracting (to a different location)
mkdir test_restore
cd test_restore
tar -xzf ../project_backup.tar.gz
ls -la my_project/
```

**When to Use Archives:**
- Before making major changes to important files
- When sharing multiple files with someone
- For long-term storage of completed projects
- When freeing up space but keeping files safe

---

### **C. Understanding File Permissions (Basic Level)**

#### **Who Can Access Your Files?**
*"File permissions are like locks on your doors - they control who can enter, who can make changes, and who can just look around."*

**Understanding the Basics:**
When you see file information with `ls -la`, you see something like:
```
-rw-r--r-- 1 user group 1024 Jan 1 12:00 myfile.txt
```

**Breaking Down the Permission Code:**
```
-rw-r--r--
|||||||||
|||||||++-- Others (everyone else): can read
||||+++---- Group members: can read
|+++------- Owner (you): can read and write
+---------- File type: - means regular file, d means directory
```

**What r, w, x Mean:**
- **r** = Read (can view the file)
- **w** = Write (can modify the file)
- **x** = Execute (can run the file as a program)

**Simple Permission Changes:**
```bash
# Make a file executable (runnable)
chmod +x script.sh

# Make a file read-only
chmod -w important_file.txt

# Make a file private (only you can read/write)
chmod go-rw private_file.txt
```

**Practical Permission Exercise:**
```bash
# Create test files
touch public_file.txt
touch private_file.txt
echo "#!/bin/bash" > my_script.sh
echo "echo 'Hello World'" >> my_script.sh

# Check current permissions
ls -la *.txt *.sh

# Make the script executable
chmod +x my_script.sh
./my_script.sh              # Now you can run it!

# Make private file truly private
chmod go-rw private_file.txt
ls -la private_file.txt     # See the difference
```

**Why This Matters:**
- Protects your important files from accidental changes
- Keeps sensitive information secure
- Allows you to share files safely with others
- Prevents unauthorized access to your scripts and programs

---

## **Wrap-Up: Your New Digital Workshop Skills**

### **What You've Accomplished Today:**

**Text Editing Skills:**
- Learned to use nano for quick, easy editing
- Understand the basics of vi for universal compatibility
- Know when to use each editor

**File Management Skills:**
- Can quickly preview file contents
- Know how to search for text in files
- Can organize and sort file contents

**File Organization Skills:**
- Can find files anywhere on your system
- Know how to create backup archives
- Understand basic file permissions

### **Next Steps:**
- Practice using these tools daily
- Start with nano for most editing tasks
- Try vi when you feel ready for a challenge
- Use find and grep to explore your system
- Create regular backups of important work

### **Quick Reference Card:**
```
Nano Essentials:
- Ctrl+O = Save    Ctrl+X = Exit    Ctrl+W = Search

Vi Essentials:
- i = Insert mode    Esc = Normal mode    :wq = Save and quit
- Emergency exit: :q!

File Commands:
- head filename = See beginning    tail filename = See end
- grep "text" filename = Search for text
- find . -name "*.txt" = Find files
- tar -czf backup.tar.gz folder/ = Create backup

File Permissions:
- chmod +x filename = Make executable
- chmod -w filename = Make read-only
- ls -la = See permissions
```

Remember: These tools become more natural with practice. Start with the basics and gradually explore more advanced features as you become comfortable!
