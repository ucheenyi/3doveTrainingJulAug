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
