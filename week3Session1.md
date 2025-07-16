# Week 3 Session 1: Configuration Management
**AI-Powered Linux & Git Course**  
*Duration: 2 Hours*

---

## 📖 Session Overview: "Designing the Perfect Workshop Blueprint"

**Learning Objectives:**
- Master Linux configuration management principles
- Create reproducible system configurations
- Implement automated deployment scripts
- Establish environment standardization practices

**Story Context:** Your successful workshop needs to be replicated worldwide. Today you'll learn to create blueprints and templates that ensure consistency across all locations.

---

## 🏗️ Part 1: Workshop Blueprint Creation (50 minutes)

### A. Configuration as Code Philosophy (25 minutes)

#### **The Blueprint Metaphor**
Think of system configuration like architectural blueprints for a building. Just as architects create detailed plans that any construction team can follow, we create configuration files that any system administrator can use to recreate identical environments.

#### **Technical Foundation: Configuration File Hierarchy**

**System-Wide Configurations (`/etc/`)**
```bash
# Configuration headquarters - affects entire system
ls -la /etc/                    # Main configuration directory
find /etc -name "*.conf" | head -10  # Find configuration files
locate "*.config"              # Search for config files system-wide
```

**Key Configuration Locations:**
- `/etc/ssh/` - Security system configuration (SSH daemon)
- `/etc/apache2/` - Web server configuration
- `/etc/mysql/` - Database configuration
- `~/.bashrc` - Personal shell environment

**Story Explanation:** These directories are like different departments in your workshop. `/etc/ssh/` is your security department's rulebook, `/etc/apache2/` contains your reception desk procedures, and `~/.bashrc` is your personal workspace setup.

#### **Configuration Hierarchy Levels**

1. **System-wide** (`/etc/`) = Workshop-wide policies that affect everyone
2. **User-specific** (`~/.*`) = Personal workspace customizations
3. **Application-specific** = Department-specific rules and procedures
4. **Runtime** (`/var/`, `/tmp/`) = Dynamic workshop state (temporary files, logs)

#### **Version Control for Configurations**

**Technical Implementation:**
```bash
# Initialize version control for system configurations
sudo git init /etc
sudo git add /etc/ssh/sshd_config /etc/apache2/apache2.conf
sudo git commit -m "Initial workshop security and reception configuration"

# Personal configuration version control
cd ~
git init dotfiles
cp .bashrc .vimrc .gitconfig dotfiles/
cd dotfiles && git add . && git commit -m "Personal workshop setup"
```

**Story Explanation:** Version control for configurations is like maintaining detailed change logs for your workshop procedures. Every modification is tracked, allowing you to revert to previous working states if something goes wrong.

### B. Advanced Configuration Techniques (25 minutes)

#### **Environment Configuration**

**Technical Implementation:**
```bash
# Personal environment setup
echo 'export WORKSHOP_STYLE="efficient"' >> ~/.bashrc
echo 'alias ll="ls -la"' >> ~/.bash_aliases
echo 'export PATH="$HOME/bin:$PATH"' >> ~/.profile

# System-wide environment variables
sudo echo 'WORKSHOP_TIMEZONE="UTC"' >> /etc/environment
sudo locale-gen en_US.UTF-8     # Language settings
sudo update-locale LANG=en_US.UTF-8
```

**Story Explanation:** Environment variables are like workshop atmosphere settings. They define the "mood" and basic operating parameters that affect how all tools and processes behave.

#### **Configuration Templates**

**Technical Concept:** Templates are reusable configuration patterns that can be customized for different scenarios.

```bash
# Creating a reusable web server template
mkdir ~/workshop_templates
cat > ~/workshop_templates/nginx_site.conf << 'EOF'
server {
    listen 80;
    server_name DOMAIN_NAME;
    root /var/www/SITE_NAME;
    index index.html;
}
EOF

# Using the template
sed 's/DOMAIN_NAME/mysite.com/g; s/SITE_NAME/mysite/g' \
    ~/workshop_templates/nginx_site.conf > /tmp/mysite.conf
```

**Story Explanation:** Templates are like blueprint stamps. You create one master design and then stamp out customized versions for different clients or projects.

---

## 🤖 Part 2: Automated Configuration Deployment (50 minutes)

### A. Shell Scripting for Configuration (25 minutes)

#### **Workshop Setup Automation**

**Technical Implementation:**
```bash
# Complete workshop setup script
cat > setup_new_workshop.sh << 'EOF'
#!/bin/bash
# New Workshop Configuration Script

echo "Setting up new workshop environment..."

# Update workshop supplies (system packages)
sudo apt update && sudo apt upgrade -y

# Install essential workshop tools
sudo apt install -y git vim curl wget tree htop

# Configure workshop environment
echo 'alias ll="ls -la"' >> ~/.bashrc
echo 'export EDITOR=vim' >> ~/.bashrc

# Create workshop structure
mkdir -p ~/workshop/{projects,tools,docs,backup}

# Interactive git configuration
read -p "Enter your name: " name
read -p "Enter your email: " email
git config --global user.name "$name"
git config --global user.email "$email"

echo "Workshop setup complete!"
EOF

chmod +x setup_new_workshop.sh
```

**Story Explanation:** This script is like a master checklist that automatically sets up a new workshop location. It handles everything from ordering supplies (installing packages) to arranging furniture (creating directory structure).

#### **Configuration Validation Scripts**

**Technical Implementation:**
```bash
# System health monitoring script
cat > workshop_health_check.sh << 'EOF'
#!/bin/bash
echo "=== Workshop Health Check ==="

echo "Storage Status:"
df -h | grep -v tmpfs

echo -e "\nMemory Status:"  
free -h

echo -e "\nCritical Services:"
systemctl is-active ssh networking

echo -e "\nRecent Errors:"
journalctl -p err --since "1 hour ago" --lines=5

echo "Health check complete!"
EOF
```

**Story Explanation:** This health check script is like a daily inspection routine. It quickly assesses storage space (like checking inventory), memory usage (like monitoring workflow efficiency), and service status (ensuring all departments are operational).

### B. Configuration Management Tools (25 minutes)

#### **Introduction to Professional Tools**

**Ansible Concepts (Demonstration):**
```bash
# Inventory file - list of workshop locations
echo "[workshops]" > inventory
echo "workshop1.example.com" >> inventory
echo "workshop2.example.com" >> inventory

# Playbook concept - automation instructions
cat > workshop_playbook.yml << 'EOF'
---
- hosts: workshops
  tasks:
    - name: Update workshop supplies
      apt: update_cache=yes upgrade=yes
    - name: Install essential tools
      apt: name={{item}} state=present
      with_items:
        - git
        - vim 
        - htop
        - tree
EOF
```

**Story Explanation:** Ansible is like having a master coordinator who can simultaneously give instructions to multiple workshop locations. Instead of manually visiting each site, you send standardized instructions that are executed everywhere at once.

#### **Docker Configuration Concepts**

**Technical Demonstration:**
```bash
# Containerized workshop blueprint
cat > Dockerfile << 'EOF'
FROM ubuntu:20.04
RUN apt update && apt install -y git vim curl
COPY workshop_config/ /etc/workshop_config/
CMD ["/bin/bash"]
EOF
```

**Story Explanation:** Docker is like creating a complete workshop in a shipping container. Everything needed is pre-installed and configured, so you can deploy identical workshops anywhere that can run containers.

---

## 📋 Part 3: Environment Standardization (40 minutes)

### A. Dotfiles Management (20 minutes)

#### **Personal Configuration Repository**

**Technical Implementation:**
```bash
# Create comprehensive dotfiles system
mkdir ~/dotfiles
cd ~/dotfiles

# Backup existing configurations
cp ~/.bashrc bashrc
cp ~/.vimrc vimrc 2>/dev/null || echo "# Vim configuration" > vimrc
cp ~/.gitconfig gitconfig 2>/dev/null || touch gitconfig

# Create installation script
cat > install.sh << 'EOF'
#!/bin/bash
# Dotfiles installation script

# Backup existing files
for file in bashrc vimrc gitconfig; do
    if [ -f ~/.$file ]; then
        cp ~/.$file ~/.$file.backup
    fi
done

# Create symbolic links
ln -sf ~/dotfiles/bashrc ~/.bashrc
ln -sf ~/dotfiles/vimrc ~/.vimrc
ln -sf ~/dotfiles/gitconfig ~/.gitconfig

echo "Dotfiles installed successfully!"
source ~/.bashrc
EOF

chmod +x install.sh
```

**Story Explanation:** Dotfiles are like your personal toolkit preferences. By creating a portable dotfiles repository, you can instantly recreate your familiar working environment on any new system.

#### **Enhanced Bash Configuration**

**Technical Implementation:**
```bash
# Advanced .bashrc configuration
cat >> bashrc << 'EOF'
# Workshop-specific configuration
export WORKSHOP_ROOT="$HOME/workshop"
export EDITOR="vim"

# Productive aliases
alias ll='ls -la'
alias la='ls -A'
alias l='ls -CF'
alias ..='cd ..'
alias ...='cd ../..'
alias grep='grep --color=auto'

# Utility functions
mkcd() { mkdir -p "$1" && cd "$1"; }
backup() { cp "$1" "$1.backup.$(date +%Y%m%d)"; }

# Git shortcuts
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git log --oneline'

# System information
alias sysinfo='echo "=== System Info ==="; uname -a; echo; free -h; echo; df -h'
EOF
```

**Story Explanation:** These aliases and functions are like creating shortcuts for common workshop tasks. Instead of typing long commands repeatedly, you create abbreviated versions that save time and reduce errors.

### B. System Configuration Standards (20 minutes)

#### **Enterprise-Level Configuration**

**Technical Implementation:**
```bash
# System-wide standardization script
cat > configure_workshop_system.sh << 'EOF'
#!/bin/bash
# System-wide workshop configuration

echo "Configuring system-wide workshop standards..."

# Time synchronization
sudo timedatectl set-timezone UTC
sudo timedatectl set-ntp true

# Language and locale
sudo locale-gen en_US.UTF-8
sudo update-locale LANG=en_US.UTF-8

# Security configurations
echo "Applying security configurations..."
sudo sed -i 's/#PermitRootLogin yes/PermitRootLogin no/' /etc/ssh/sshd_config
sudo sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# System resource limits
echo "* soft nofile 65536" | sudo tee -a /etc/security/limits.conf
echo "* hard nofile 65536" | sudo tee -a /etc/security/limits.conf

# Apply changes
sudo systemctl restart ssh

echo "System configuration complete!"
EOF

chmod +x configure_workshop_system.sh
```

**Story Explanation:** This script establishes enterprise-grade standards across all workshop locations. It ensures consistent time zones, security policies, and resource limits - like creating a corporate policy manual that all locations must follow.

---

## 🎯 Lab Challenge: Configuration Master (20 minutes)

### Mission: "Standardize 50 Workshop Environments"

**Scenario:** A client wants to replicate your workshop setup across 50 locations worldwide. Create a comprehensive configuration management system.

**Objectives:**
1. **Dotfiles Repository** - Create portable personal configurations
2. **System Configuration** - Develop system-wide standardization script
3. **Application Templates** - Build reusable service configurations
4. **Validation System** - Create compliance checking scripts
5. **Documentation** - Write clear installation and usage guides

---

## 🔑 Key Takeaways

### Technical Concepts Mastered:
- **Configuration Hierarchy**: Understanding system-wide vs. user-specific settings
- **Version Control**: Tracking configuration changes with Git
- **Automation Scripts**: Creating reproducible setup procedures
- **Template Systems**: Building reusable configuration patterns
- **Environment Standardization**: Ensuring consistency across systems

### Story Connections:
- Configuration files are like department rulebooks
- Templates are blueprint stamps for customization
- Automation scripts are master checklists
- Version control provides change history and rollback capability
- Standardization ensures quality and consistency

### Best Practices:
1. Always version control your configurations
2. Use templates for repeated patterns
3. Automate repetitive setup tasks
4. Document your configuration decisions
5. Test configurations before deployment
6. Create validation scripts for compliance checking

---

## 📚 Additional Resources

- **Man Pages**: `man bash`, `man ssh_config`, `man systemd`
- **Configuration Files**: `/etc/` directory exploration
- **Version Control**: Git for configuration management
- **Automation Tools**: Introduction to Ansible and Docker concepts

---

## 🏠 Homework Assignment

Create a complete configuration management system for your personal development environment that includes:
1. Dotfiles repository with installation script
2. System configuration script
3. Application configuration templates
4. Health check validation script
5. Documentation explaining your choices

**Due:** Next session - be prepared to demonstrate your configuration system!
