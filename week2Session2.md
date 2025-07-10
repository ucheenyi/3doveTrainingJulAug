# Week 2 Session 6: Package Management
## "Managing the Workshop Supply Chain"

### Learning Objectives
By the end of this session, you will be able to:
- Understand Linux package management systems and their components
- Use APT (Advanced Package Tool) to install, update, and remove software
- Work with different package managers (APT, YUM, Snap, Flatpak)
- Implement security best practices for package management
- Compile software from source code
- Set up development environments with proper dependency management

---

## Part 1: Understanding the Supply Network (40 minutes)

### Story Context
*"Your workshop has grown beyond basic tools. You need specialized equipment, regular supply deliveries, and must keep everything updated and maintained. Today you master the workshop's supply chain management system."*

### Technical Foundation: Package Management Systems

#### What Are Package Managers?
Package managers are software tools that automate the process of installing, updating, configuring, and removing software packages. Think of them as automated supply chain managers for your system.

**Key Components:**
- **Repositories**: Remote servers storing software packages
- **Packages**: Pre-compiled software with metadata and dependencies
- **Dependencies**: Other packages required for software to function
- **Package Database**: Local record of installed software

#### APT (Advanced Package Tool) - Ubuntu/Debian Systems

**Core APT Commands:**
```bash
# Update package information from repositories
apt update                    # Refreshes package lists (always run first)

# Search for packages
apt search "text editor"      # Find packages containing keywords
apt list --installed | grep nano  # Check if specific package is installed

# Get detailed package information
apt show nano                 # Display package details, dependencies, size
apt policy git               # Show available versions and sources
```

**Technical Explanation:**
- `apt update` downloads package lists from repositories but doesn't install anything
- Package names are case-sensitive and often include version numbers
- The package database is stored in `/var/lib/apt/lists/`

### Memory Framework: The SIDU Process
- **S**earch: Find the package you need
- **I**nstall: Add the package to your system
- **D**ependencies: Automatically resolved by package manager
- **U**pdate: Keep packages current with security patches

### Hands-On Practice: Basic Package Operations

```bash
# Professional installation workflow
sudo apt update                    # Always update first
sudo apt install tree            # Install the 'tree' directory viewer
sudo apt install -y curl wget    # Batch install with auto-confirmation

# Package information and verification
dpkg -l | grep tree              # Verify installation
which tree                       # Find executable location
tree --help                      # Test the installed software
```

**Technical Notes:**
- `sudo` is required for system-wide package operations
- The `-y` flag automatically answers "yes" to prompts
- `dpkg` is the low-level package manager that APT uses

---

## Part 2: Advanced Supply Management (50 minutes)

### Multi-Platform Package Management

#### RPM-Based Systems (Red Hat/CentOS/Fedora)
While we're using Ubuntu, understanding different package managers is crucial for system administrators.

**YUM (Yellowdog Updater Modified):**
```bash
# Traditional Red Hat package management
yum search editor                # Search for packages
sudo yum install nano           # Install package
yum list installed              # List installed packages
sudo yum update                 # Update all packages
```

**DNF (Dandified YUM) - Modern Red Hat:**
```bash
# Modern Red Hat package management
dnf search git                  # Search repositories
sudo dnf install git           # Install package
dnf history                     # View transaction history
```

#### Universal Package Systems

**Snap Packages:**
```bash
# Ubuntu's universal package system
snap find "code editor"         # Search snap store
sudo snap install code --classic  # Install with classic confinement
snap list                       # List installed snaps
snap info code                  # Package information
```

**Technical Explanation:**
- Snaps are containerized applications that include all dependencies
- `--classic` removes sandbox restrictions for development tools
- Snaps auto-update by default

**Flatpak:**
```bash
# Alternative universal package system
sudo apt install flatpak        # Install Flatpak system
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
flatpak search gimp            # Search for applications
sudo flatpak install flathub org.gimp.GIMP  # Install from Flathub
```

### Language-Specific Package Managers

**Python (pip):**
```bash
# Python package management
pip3 install --user requests    # Install for current user only
pip3 install --upgrade pip      # Update pip itself
pip3 list                       # List installed packages
pip3 show requests              # Package information
```

**Node.js (npm):**
```bash
# JavaScript package management
npm install -g http-server      # Global installation
npm list -g --depth=0          # List global packages
npm update -g                   # Update all global packages
```

**Technical Security Note:**
- Use `--user` flag with pip to avoid system-wide changes
- Global npm packages (`-g`) require careful consideration
- Language-specific packages don't integrate with system package manager

### Package Security and Verification

```bash
# Security best practices
apt-key list                    # View trusted repository keys
apt-cache policy               # Check repository priorities
sudo apt update 2>&1 | grep -i warning  # Check for security warnings

# Verify package integrity
apt-cache show package-name | grep -E "(SHA|Size)"  # Check checksums
```

---

## Part 3: Building Custom Tools (40 minutes)

### Compiling from Source Code

#### Understanding the Build Process

**The Three-Step Build Process:**
1. **Configure**: Check system dependencies and create build configuration
2. **Make**: Compile source code into executable binaries
3. **Install**: Copy binaries to system directories

```bash
# Traditional source compilation
wget https://example.com/software-1.0.tar.gz  # Download source
tar -xzf software-1.0.tar.gz                 # Extract archive
cd software-1.0/                             # Enter source directory

# The build process
./configure --prefix=/usr/local              # Configure build
make                                         # Compile source code
sudo make install                           # Install to system
```

**Technical Explanation:**
- `./configure` creates a Makefile based on your system
- `make` reads the Makefile and compiles the code
- `--prefix` specifies installation directory
- Source compilation allows custom optimization flags

#### Build Dependencies
```bash
# Install build tools
sudo apt install build-essential            # GCC compiler, make, etc.
sudo apt install cmake                      # Modern build system
sudo apt install git                        # Version control for source

# Check what's included in build-essential
apt show build-essential
```

### Modern Development Environment Setup

```bash
# Complete development environment
sudo apt install build-essential python3-dev python3-pip python3-venv
sudo apt install nodejs npm default-jdk
sudo apt install git curl wget vim

# Create isolated Python environment
python3 -m venv myproject                   # Create virtual environment
source myproject/bin/activate               # Activate environment
pip install flask requests                  # Install packages in isolation
deactivate                                  # Exit virtual environment
```

**Technical Benefits of Virtual Environments:**
- Isolates project dependencies
- Prevents version conflicts
- Allows different Python versions per project
- Easy to recreate environments

---

## Package Management Best Practices

### Security Guidelines
1. **Always update before installing**: `sudo apt update`
2. **Use official repositories**: Avoid untrusted sources
3. **Verify signatures**: Check package authenticity
4. **Regular updates**: Keep system current with security patches
5. **Minimal installation**: Only install necessary packages

### Maintenance Commands
```bash
# System maintenance
sudo apt update && sudo apt upgrade         # Update system
sudo apt autoremove                        # Remove unused dependencies
sudo apt autoclean                         # Clean package cache
sudo apt list --upgradable                 # Check available updates

# Package information
dpkg -l | wc -l                           # Count installed packages
apt list --installed | grep -c "^ii"      # Alternative count method
du -sh /var/cache/apt/archives/           # Package cache size
```

### Troubleshooting Common Issues

**Broken Dependencies:**
```bash
sudo apt --fix-broken install             # Fix broken dependencies
sudo dpkg --configure -a                  # Configure unconfigured packages
sudo apt clean                            # Clear package cache
```

**Repository Issues:**
```bash
sudo apt update --fix-missing             # Fix missing repository files
sudo apt-key update                       # Update repository keys
```

---

## Lab Challenge: Complete Development Environment

**Scenario**: Set up a full development environment for a new team member.

**Requirements:**
1. Install essential development tools
2. Set up Python, Node.js, and Java environments
3. Install multiple text editors (nano, vim, VS Code)
4. Create a Python virtual environment with data science tools
5. Install one package from source
6. Create an automated setup script

**Solution Template:**
```bash
#!/bin/bash
# Development Environment Setup Script

echo "Updating system..."
sudo apt update

echo "Installing development tools..."
sudo apt install -y build-essential git curl wget vim tree

echo "Installing programming languages..."
sudo apt install -y python3 python3-pip python3-venv nodejs npm default-jdk

echo "Installing editors..."
sudo apt install -y nano vim
sudo snap install code --classic

echo "Setting up Python data science environment..."
python3 -m venv datascience
source datascience/bin/activate
pip install pandas numpy matplotlib jupyter
deactivate

echo "Installation complete!"
```

---

## Key Takeaways

### Technical Concepts Mastered
- Package management systems and their architecture
- Multi-platform package manager differences
- Security practices for software installation
- Source code compilation process
- Virtual environment management

### Practical Skills Developed
- Using APT for package management
- Working with universal package systems
- Setting up development environments
- Troubleshooting package issues
- Creating automated installation scripts

### Professional Best Practices
- Always update repositories before installing
- Use official sources and verify packages
- Maintain regular update schedules
- Document installation procedures
- Use virtual environments for development

**Next Session Preview**: We'll explore system services, networking, and remote management - learning to operate your workshop as a connected, service-oriented environment.
