# 🐚 Zsh Quick Reference Guide

*Master the Z shell with powerful features and shortcuts*

---

## ⚡ Essential Shortcuts

### Command Line Navigation
**What is this?** Efficient ways to move around and edit your command line without using arrow keys.

| Shortcut | Action | Why It's Faster |
|----------|--------|-----------------|
| `Ctrl+A` | **Move to beginning** | Jump to start instantly |
| `Ctrl+E` | **Move to end** | Jump to end instantly |
| `Alt+F` | **Forward one word** | Skip words instead of characters |
| `Alt+B` | **Backward one word** | Navigate by word boundaries |
| `Ctrl+U` | **Delete to beginning** | Clear everything before cursor |
| `Ctrl+K` | **Delete to end** | Clear everything after cursor |
| `Alt+D` | **Delete word forward** | Remove next word |
| `Ctrl+W` | **Delete word backward** | Remove previous word |

**Example:** Instead of holding backspace to delete a long path, use `Ctrl+W` to delete word by word.

### Command Editing
| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Ctrl+L` | **Clear screen** | Clean slate, faster than `clear` command |
| `Ctrl+C` | **Cancel command** | Abort current input and start fresh |
| `Ctrl+Z` | **Suspend process** | Pause running command (resume with `fg`) |
| `Ctrl+D` | **Exit/EOF** | Close terminal or end input |
| `Ctrl+R` | **Reverse search** | Find commands from history |
| `!!` | **Repeat last command** | Quick way to run previous command |
| `!$` | **Last argument** | Reuse the last argument from previous command |

---

## 📚 History & Search

### Command History Magic
**What is this?** Zsh remembers thousands of your previous commands and makes them easily searchable and reusable.

| Feature | Usage | Why It's Powerful |
|---------|-------|-------------------|
| `Ctrl+R` | **Interactive search** | Type partial command, see matches instantly |
| `history` | **Show recent commands** | Browse your command history |
| `history \| grep ssh` | **Search history** | Find all commands containing "ssh" |
| `!n` | **Run command number n** | Execute specific history entry |
| `!ssh` | **Run last ssh command** | Execute most recent command starting with "ssh" |

### Advanced History Features
```bash
# History expansion examples
!!              # Last command
!-2             # Command from 2 lines ago
!ssh            # Last command starting with "ssh"
!?config?       # Last command containing "config"
!!:p            # Print last command without executing
^old^new        # Replace "old" with "new" in last command

# Example workflow:
ls /very/long/path/to/file.txt
cd !$           # Changes to /very/long/path/to/ (reuses last argument)
```

### History Configuration
**Add to `~/.zshrc` for better history:**
```bash
# History settings
HISTSIZE=10000              # Commands in memory
SAVEHIST=10000             # Commands saved to file
HISTFILE=~/.zsh_history    # Where to save history

# Useful history options
setopt HIST_IGNORE_DUPS    # Don't save duplicate commands
setopt HIST_IGNORE_SPACE   # Don't save commands starting with space
setopt SHARE_HISTORY       # Share history between terminals
setopt APPEND_HISTORY      # Append to history file
setopt INC_APPEND_HISTORY  # Add commands immediately
```

---

## 🔄 Tab Completion

### Smart Completion System
**What is this?** Zsh's intelligent completion system that understands context and provides relevant suggestions.

**Why it's revolutionary:** Unlike basic tab completion, zsh knows about command options, file types, and even command-specific contexts.

### Basic Completion
| Action | Result | Example |
|--------|--------|---------|
| `Tab` | **Complete or show options** | `cd Doc<Tab>` → `cd Documents/` |
| `Tab Tab` | **Show all possibilities** | `git <Tab><Tab>` → shows all git commands |
| **Partial + Tab** | **Smart matching** | `cd D/P/m<Tab>` → `cd Documents/Projects/myapp/` |

### Advanced Completion Features
```bash
# Context-aware completion examples
git checkout <Tab>          # Shows branches
ssh <Tab>                   # Shows known hosts from ~/.ssh/config
kill <Tab>                  # Shows running processes
docker <Tab>                # Shows docker commands and containers
npm run <Tab>               # Shows scripts from package.json

# Case-insensitive completion
zstyle ':completion:*' matcher-list 'm:{a-z}={A-Z}'

# Fuzzy matching - finds files even with typos
zstyle ':completion:*' matcher-list 'r:|[._-]=* r:|=*' 'l:|=* r:|=*'
```

### File and Directory Completion
**Special patterns zsh understands:**
```bash
# Glob patterns
ls *.txt                    # All .txt files
ls **/*.py                  # All .py files recursively
ls **/test*/**/*.js        # Complex nested patterns

# Directory shortcuts
cd /u/l/b                   # Expands to /usr/local/bin
cd ~john                    # John's home directory
cd -                        # Previous directory
```

---

## 🎯 Powerful Features

### Glob Patterns & Wildcards
**What are these?** Advanced pattern matching that goes far beyond basic `*` wildcards.

| Pattern | Matches | Example Use Case |
|---------|---------|------------------|
| `*.txt` | All .txt files | `rm *.txt` - remove all text files |
| `**/*.js` | All .js files recursively | `grep "TODO" **/*.js` - find TODOs in all JS files |
| `file[0-9].txt` | file0.txt through file9.txt | `ls file[0-9].txt` - list numbered files |
| `!(*.txt)` | Everything except .txt files | `ls !(*.txt)` - show non-text files |
| `*.{jpg,png,gif}` | All image files | `cp *.{jpg,png,gif} images/` - copy images |

### Advanced Glob Options
```bash
# Enable extended globbing (add to ~/.zshrc)
setopt EXTENDED_GLOB

# Extended patterns
ls **/*(.)                  # All files (not directories) recursively
ls **/*(.x)                 # All executable files recursively
ls *(m-1)                   # Files modified in last day
ls *(Lk+100)                # Files larger than 100KB
ls -d */                    # Only directories
```

### Parameter Expansion
**What is this?** Powerful string manipulation built into the shell.

```bash
# Variable manipulation
file="document.txt"
echo ${file%.*}             # "document" (remove extension)
echo ${file#*.}             # "txt" (get extension)
echo ${file/doc/FILE}       # "FILEument.txt" (replace text)

# Path manipulation
path="/home/user/documents/file.txt"
echo ${path:h}              # "/home/user/documents" (directory)
echo ${path:t}              # "file.txt" (filename)
echo ${path:r}              # "/home/user/documents/file" (remove extension)
echo ${path:e}              # "txt" (extension only)

# Array operations
files=(*.txt)
echo ${#files}              # Count of .txt files
echo ${files[1]}            # First file
echo ${files[-1]}           # Last file
```

---

## 🔧 Aliases & Functions

### Creating Useful Aliases
**What are aliases?** Shortcuts for commonly used commands that save typing and reduce errors.

```bash
# Add to ~/.zshrc for permanent aliases

# Navigation shortcuts
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias l='ls -la'
alias ll='ls -l'
alias la='ls -A'

# Git shortcuts
alias g='git'
alias gs='git status'
alias ga='git add'
alias gc='git commit'
alias gp='git push'
alias gl='git log --oneline'

# Development shortcuts
alias serve='python -m http.server 8000'
alias py='python3'
alias v='vim'
alias c='code'

# System shortcuts
alias h='history'
alias grep='grep --color=auto'
alias df='df -h'                # Human readable disk usage
alias du='du -h'                # Human readable directory sizes
alias ps='ps aux'               # Better process list
```

### Powerful Functions
**What are functions?** More complex shortcuts that can take arguments and perform multiple commands.

```bash
# Add to ~/.zshrc

# Extract any archive
extract() {
    if [ -f $1 ] ; then
        case $1 in
            *.tar.bz2)   tar xjf $1     ;;
            *.tar.gz)    tar xzf $1     ;;
            *.bz2)       bunzip2 $1     ;;
            *.rar)       unrar e $1     ;;
            *.gz)        gunzip $1      ;;
            *.tar)       tar xf $1      ;;
            *.tbz2)      tar xjf $1     ;;
            *.tgz)       tar xzf $1     ;;
            *.zip)       unzip $1       ;;
            *.Z)         uncompress $1  ;;
            *.7z)        7z x $1        ;;
            *)           echo "'$1' cannot be extracted" ;;
        esac
    else
        echo "'$1' is not a valid file"
    fi
}

# Create directory and cd into it
mkcd() {
    mkdir -p "$1" && cd "$1"
}

# Find files by name
ff() {
    find . -type f -name "*$1*"
}

# Search for text in files
search() {
    grep -r "$1" . --include="*.$2"
}
# Usage: search "function" "js" (finds "function" in all .js files)

# Git clone and cd
gclone() {
    git clone "$1" && cd "$(basename "$1" .git)"
}
```

---

## 🎨 Customization & Themes

### Oh My Zsh Framework
**What is Oh My Zsh?** A popular framework that adds themes, plugins, and pre-configured features to zsh.

**Why use it?** Instant access to hundreds of plugins, beautiful themes, and sensible defaults without manual configuration.

```bash
# Install Oh My Zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Or with wget
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```

### Popular Themes
**Set in `~/.zshrc` with `ZSH_THEME="theme-name"`:**

| Theme | Style | Best For |
|-------|-------|----------|
| `"robbyrussell"` | Simple, clean (default) | Beginners, minimal setup |
| `"agnoster"` | Powerline with git info | Git-heavy workflows |
| `"powerlevel10k"` | Highly customizable, fast | Power users who want control |
| `"bira"` | Two-line with git and time | Detailed information display |
| `"avit"` | Clean with git status | Professional, readable |
| `"random"` | Different theme each session | Trying out themes |

**Powerline themes require special fonts:**
```bash
# Install powerline fonts
git clone https://github.com/powerline/fonts.git --depth=1
cd fonts && ./install.sh && cd .. && rm -rf fonts

# Or install specific font
brew tap homebrew/cask-fonts
brew install font-meslo-lg-nerd-font
```

### Essential Oh My Zsh Plugins
**Add to `plugins=()` in `~/.zshrc`:**

**Core Productivity Plugins:**
```bash
plugins=(
    git                     # Git aliases and completion
    sudo                    # ESC ESC to add sudo to previous command
    history-substring-search # Arrow keys search history by what you've typed
    copyfile                # copyfile <file> copies content to clipboard
    copypath                # copypath copies current path to clipboard
    web-search              # google, stackoverflow, github commands
    jsontools               # pp_json, is_json, urlencode_json commands
)
```

**Development Plugins:**
```bash
plugins=(
    # Language/Framework specific
    docker                  # Docker completion and aliases
    docker-compose          # Docker Compose completion
    npm                     # Node.js/npm completion and aliases
    yarn                    # Yarn completion and aliases
    pip                     # Python pip completion
    python                  # Python aliases and completion
    golang                  # Go language aliases
    rust                    # Rust language completion
    
    # Cloud & DevOps
    aws                     # AWS CLI completion
    kubectl                 # Kubernetes completion
    terraform               # Terraform completion
    ansible                 # Ansible completion
)
```

**Navigation & File Management:**
```bash
plugins=(
    z                       # Smart directory jumping
    fzf                     # Fuzzy finder integration
    fd                      # Modern find replacement
    ripgrep                 # Modern grep replacement
    eza                     # Modern ls replacement (if installed)
)
```

### Plugin Explanations & Usage

#### Git Plugin Features
**What it provides:** Tons of git aliases and smart completion.

```bash
# Common git aliases (automatically available)
g='git'
ga='git add'
gaa='git add --all'
gc='git commit -v'
gca='git commit -v -a'
gcm='git commit -m'
gco='git checkout'
gd='git diff'
gp='git push'
gl='git pull'
gs='git status'
gst='git status --short'
glog='git log --oneline --decorate --graph'

# Smart completion
git checkout <Tab>          # Shows branches
git add <Tab>              # Shows modified files
```

#### Sudo Plugin
**What it does:** Double-tap ESC to add `sudo` to your current command.

**Example workflow:**
1. Type: `apt install package`
2. Press Enter → Permission denied
3. Press ESC ESC → Command becomes: `sudo apt install package`

#### Web Search Plugin
**What it provides:** Quick web searches from terminal.

```bash
google "react hooks tutorial"      # Opens Google search
stackoverflow "javascript promises" # Opens Stack Overflow search
github "microsoft/vscode"          # Opens GitHub repository
youtube "zsh tutorial"             # Opens YouTube search
reddit "programming"               # Opens Reddit search

# Customize search engines in ~/.zshrc
ZSH_WEB_SEARCH_ENGINES=(
    custom "https://example.com/search?q="
)
```

#### Z Plugin (Directory Jumping)
**What it does:** Learns your directory usage and lets you jump by partial names.

```bash
# After visiting directories, z learns patterns
cd ~/Documents/Projects/myapp
cd ~/Documents/Projects/work/client
cd ~/Downloads

# Later, jump quickly
z myapp                    # Goes to ~/Documents/Projects/myapp
z client                   # Goes to ~/Documents/Projects/work/client
z down                     # Goes to ~/Downloads

# Advanced usage
z -l                       # List all tracked directories
z -r myapp                 # Jump to highest ranked match
z -t client                # Jump to most recently accessed match
```

### Managing Oh My Zsh

#### Updating
```bash
# Update Oh My Zsh framework
omz update

# Update specific plugin
cd $ZSH_CUSTOM/plugins/plugin-name && git pull

# Auto-update settings in ~/.zshrc
zstyle ':omz:update' mode auto      # Auto-update without asking
zstyle ':omz:update' frequency 13   # Update every 13 days
```

#### Installing Custom Plugins
```bash
# Install popular external plugins
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git $ZSH_CUSTOM/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-completions $ZSH_CUSTOM/plugins/zsh-completions

# Add to plugins array in ~/.zshrc
plugins=(
    git
    zsh-syntax-highlighting
    zsh-autosuggestions
    zsh-completions
)
```

#### Custom Themes
```bash
# Install custom themes
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k

# Set in ~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"

# Configure Powerlevel10k
p10k configure              # Run configuration wizard
```

### Custom Prompt Configuration
**Without Oh My Zsh, create custom prompts:**
```bash
# Add to ~/.zshrc

# Simple custom prompt
PROMPT='%F{cyan}%n@%m%f:%F{yellow}%~%f$ '

# Advanced prompt with git info
autoload -Uz vcs_info
precmd() { vcs_info }
zstyle ':vcs_info:git:*' formats ' (%b)'
setopt PROMPT_SUBST
PROMPT='%F{green}%n%f@%F{blue}%m%f:%F{yellow}%~%f%F{red}${vcs_info_msg_0_}%f$ '
```

---

## 🎨 Oh My Zsh Configuration & Customization

### Complete ~/.zshrc Setup for Oh My Zsh Users
```bash
# Oh My Zsh configuration
export ZSH="$HOME/.oh-my-zsh"

# Theme selection
ZSH_THEME="agnoster"              # Or your preferred theme

# Plugin configuration
plugins=(
    git
    sudo
    history-substring-search
    copyfile
    copypath
    web-search
    z
    docker
    npm
    zsh-syntax-highlighting      # Install separately
    zsh-autosuggestions         # Install separately
)

# Oh My Zsh auto-update behavior
zstyle ':omz:update' mode auto
zstyle ':omz:update' frequency 13

# Load Oh My Zsh
source $ZSH/oh-my-zsh.sh

# Custom aliases (add after sourcing Oh My Zsh)
alias zshconfig="code ~/.zshrc"
alias ohmyzsh="code ~/.oh-my-zsh"
alias reload="source ~/.zshrc"

# Plugin-specific settings
# History substring search key bindings
bindkey '^[[A' history-substring-search-up
bindkey '^[[B' history-substring-search-down

# Autosuggestions settings
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#666666"
ZSH_AUTOSUGGEST_STRATEGY=(history completion)
```

### Theme Customization Examples

#### Agnoster Theme Customization
```bash
# Add to ~/.zshrc after theme setting
# Customize prompt segments
AGNOSTER_PROMPT_SEGMENTS=(
    prompt_status
    prompt_virtualenv
    prompt_context
    prompt_dir
    prompt_git
    prompt_end
)

# Hide username@hostname when you're the default user
DEFAULT_USER="yourusername"

# Show current time
AGNOSTER_PATH_STYLE="short"     # Show only current directory name
```

#### Powerlevel10k Advanced Setup
```bash
# Install and configure
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k

# Set theme in ~/.zshrc
ZSH_THEME="powerlevel10k/powerlevel10k"

# Configuration wizard (run after installing)
p10k configure

# Manual configuration options in ~/.zshrc
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
    context dir vcs
)
POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
    status root_indicator background_jobs time
)
```

### Plugin-Specific Configurations

#### Git Plugin Customization
```bash
# Add custom git aliases (beyond the defaults)
alias gfp='git fetch --prune'
alias grv='git remote -v'
alias gclean='git clean -fd'
alias gundo='git reset --soft HEAD~1'

# Git completion for custom aliases
compdef _git gfp=git-fetch
compdef _git grv=git-remote
```

#### FZF Plugin Enhancement
```bash
# Enhanced FZF settings (add to ~/.zshrc)
export FZF_DEFAULT_OPTS="
    --height 40% 
    --layout=reverse 
    --border 
    --preview 'head -20 {}'
"

# FZF with file preview
export FZF_CTRL_T_OPTS="--preview 'cat {}' --preview-window down:3:hidden:wrap --bind '?:toggle-preview'"

# FZF for git files
alias fzf-git='git ls-files | fzf'
```

### Custom Plugin Development

#### Creating Your Own Plugin
```bash
# Create custom plugin directory
mkdir -p $ZSH_CUSTOM/plugins/my-custom

# Create plugin file
cat > $ZSH_CUSTOM/plugins/my-custom/my-custom.plugin.zsh << 'EOF'
# My Custom Plugin

# Quick project navigation
projects() {
    cd ~/Documents/Projects/$1
}

# Completion for projects
_projects() {
    local projects_dir="$HOME/Documents/Projects"
    if [[ -d "$projects_dir" ]]; then
        _files -W "$projects_dir" -/
    fi
}
compdef _projects projects

# Development server shortcuts
alias serve-python='python -m http.server 8000'
alias serve-node='npx http-server -p 8000'

# Quick git shortcuts
alias gquick='git add . && git commit -m "Quick commit" && git push'

# Docker shortcuts
alias dps='docker ps --format "table {{.Names}}\t{{.Image}}\t{{.Status}}"'
alias dlog='docker logs -f'
EOF

# Add to plugins array in ~/.zshrc
plugins=(
    # ... other plugins
    my-custom
)
```

---

## 🔌 Advanced Oh My Zsh Features

### Zsh Syntax Highlighting
**What is this?** Colors your commands as you type to show valid/invalid syntax.

```bash
# Install via Oh My Zsh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Add to plugins in ~/.zshrc
plugins=(... zsh-syntax-highlighting)

# Or install standalone
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

### Zsh Autosuggestions
**What is this?** Suggests commands based on your history as you type.

```bash
# Install via Oh My Zsh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Add to plugins
plugins=(... zsh-autosuggestions)

# Accept suggestion with right arrow or Ctrl+F
```

### FZF Integration
**What is FZF?** Fuzzy finder that makes searching files, history, and processes interactive.

```bash
# Install FZF
brew install fzf
# Or
git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
~/.fzf/install

# Usage examples
Ctrl+R                      # Fuzzy search command history
Ctrl+T                      # Fuzzy search files
Alt+C                       # Fuzzy search directories (cd)
kill <Tab>                  # Fuzzy search processes to kill

# Custom FZF commands
fzf --preview 'cat {}'      # Preview file contents
git log --oneline | fzf     # Interactive git log
```

---

## 📁 Directory Navigation

### Smart Directory Features
**What makes zsh navigation special?** Advanced directory handling and shortcuts.

### Directory Stack
```bash
# Directory stack commands
dirs                        # Show directory stack
pushd /path/to/dir         # Push directory and cd to it
popd                       # Pop directory and cd to it
cd +2                      # Go to 2nd directory in stack

# Auto directory (add to ~/.zshrc)
setopt AUTO_CD             # Type directory name to cd into it
# Now you can type: /usr/local/bin (instead of cd /usr/local/bin)
```

### Named Directories
```bash
# Create shortcuts for frequently used directories
hash -d projects=~/Documents/Projects
hash -d config=~/.config
hash -d logs=/var/log

# Usage
cd ~projects               # Goes to ~/Documents/Projects
ls ~config                 # Lists ~/.config
tail ~logs/system.log      # Views /var/log/system.log
```

### Z Plugin (Smart Jumping)
**What is Z?** Learns your directory usage patterns and lets you jump to directories by partial names.

```bash
# After visiting directories, z learns your patterns
cd ~/Documents/Projects/myapp
cd ~/Documents/Projects/work/client-site
cd ~/Downloads

# Later, use z to jump quickly
z myapp                    # Jumps to ~/Documents/Projects/myapp
z client                   # Jumps to ~/Documents/Projects/work/client-site
z dow                      # Jumps to ~/Downloads

# Z ranks directories by "frecency" (frequency + recency)
z -l                       # List all z entries with scores
```

---

## ⚙️ Configuration & Setup

### Essential ~/.zshrc Configuration
```bash
# History configuration
HISTSIZE=10000
SAVEHIST=10000
HISTFILE=~/.zsh_history
setopt HIST_IGNORE_DUPS
setopt HIST_IGNORE_SPACE
setopt SHARE_HISTORY
setopt APPEND_HISTORY

# Directory options
setopt AUTO_CD             # Type directory name to cd
setopt AUTO_PUSHD          # Make cd push directories to stack
setopt PUSHD_IGNORE_DUPS   # Don't push duplicates
setopt PUSHD_SILENT        # Don't print stack after pushd/popd

# Completion options
setopt COMPLETE_ALIASES    # Complete aliases
setopt COMPLETE_IN_WORD    # Complete from middle of word
setopt ALWAYS_TO_END       # Move cursor to end after completion

# Globbing options
setopt EXTENDED_GLOB       # Enable extended globbing
setopt NO_CASE_GLOB        # Case insensitive globbing
setopt NUMERIC_GLOB_SORT   # Sort numerically when possible

# Job control
setopt NO_HUP              # Don't kill jobs on shell exit
setopt NO_CHECK_JOBS       # Don't warn about running jobs on exit
```

### Environment Variables
```bash
# Add to ~/.zshrc

# Default editor
export EDITOR='vim'        # or 'code', 'nano', etc.
export VISUAL='vim'

# PATH additions
export PATH="$HOME/bin:$PATH"
export PATH="/usr/local/bin:$PATH"
export PATH="$HOME/.local/bin:$PATH"

# Development environments
export NODE_ENV='development'
export JAVA_HOME='/usr/libexec/java_home'

# Colors for ls
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced
```

---

## 🚀 Advanced Features

### Command Substitution & Pipes
```bash
# Command substitution
files=$(ls *.txt)          # Store command output in variable
echo "Found: $(wc -l < file.txt) lines"

# Process substitution
diff <(sort file1) <(sort file2)    # Compare sorted files
grep pattern <(cat file1 file2)     # Search in combined output

# Advanced piping
ps aux | grep ssh | awk '{print $2}' | xargs kill    # Kill SSH processes
find . -name "*.js" | xargs grep "TODO"              # Find TODOs in JS files
```

### Conditional Execution
```bash
# Logical operators
command1 && command2       # Run command2 only if command1 succeeds
command1 || command2       # Run command2 only if command1 fails
command1; command2         # Run both regardless

# Examples
make && ./program          # Compile then run if successful
git pull || echo "Pull failed"    # Show message if pull fails
cd project && npm install && npm start    # Chain of commands
```

### Background Jobs & Process Management
```bash
# Job control
command &                  # Run in background
jobs                       # List running jobs
fg                         # Bring job to foreground
bg                         # Resume job in background
kill %1                    # Kill job number 1
disown %1                  # Remove job from shell's job table

# Process monitoring
ps aux | grep process_name
pgrep process_name         # Find process IDs
pkill process_name         # Kill processes by name
nohup command &            # Run command immune to hangups
```

---

## 🎯 Productivity Tips

### Oh My Zsh Daily Workflows

#### Development Workflow Example
```bash
# ~/.zshrc setup for development
ZSH_THEME="agnoster"
plugins=(
    git
    docker
    npm
    z
    sudo
    copyfile
    web-search
    zsh-syntax-highlighting
    zsh-autosuggestions
)

# Custom aliases for development
alias dev='cd ~/projects && code .'
alias serve='npm start'
alias build='npm run build'
alias test='npm test'
alias gquick='git add . && git commit -m "WIP" && git push'

# Project-specific shortcuts
projects() { cd ~/Documents/Projects/$1 }
_projects() { _files -W ~/Documents/Projects -/ }
compdef _projects projects
```

#### System Administration Workflow
```bash
# Plugins for sysadmin work
plugins=(
    git
    docker
    kubectl
    aws
    terraform
    ansible
    sudo
    systemd
    z
)

# Useful aliases
alias ll='ls -la'
alias ports='netstat -tuln'
alias processes='ps aux | grep'
alias disk='df -h'
alias memory='free -h'
alias logs='journalctl -f'
```

#### The Ultimate Oh My Zsh Setup
**Complete ~/.zshrc for power users:**
```bash
# Path to oh-my-zsh installation
export ZSH="$HOME/.oh-my-zsh"

# Theme
ZSH_THEME="powerlevel10k/powerlevel10k"

# Plugins
plugins=(
    git                         # Essential git integration
    sudo                       # ESC ESC for sudo
    history-substring-search   # Better history navigation
    copyfile                   # Copy file contents
    copypath                   # Copy current path
    web-search                 # Web searches from terminal
    z                          # Smart directory jumping
    
    # Development
    docker                     # Docker completion
    docker-compose            # Docker Compose completion
    npm                        # Node.js development
    yarn                       # Alternative to npm
    pip                        # Python package management
    python                     # Python development
    golang                     # Go development
    rust                       # Rust development
    
    # Cloud & DevOps
    aws                        # AWS CLI completion
    kubectl                    # Kubernetes management
    terraform                  # Infrastructure as code
    
    # Enhanced tools (install separately)
    zsh-syntax-highlighting    # Syntax highlighting
    zsh-autosuggestions       # Command suggestions
    zsh-completions           # Additional completions
    fzf                       # Fuzzy finder
)

# Update settings
zstyle ':omz:update' mode auto
zstyle ':omz:update' frequency 7

# Load Oh My Zsh
source $ZSH/oh-my-zsh.sh

# Custom configuration
DEFAULT_USER="yourusername"

# Environment variables
export EDITOR='code'
export BROWSER='open'

# Custom aliases
alias zshconfig="code ~/.zshrc"
alias reload="source ~/.zshrc"
alias update="omz update && brew update && brew upgrade"

# Development shortcuts
alias dev='cd ~/projects'
alias serve='python -m http.server 8000'
alias weather='curl wttr.in'
alias myip='curl ifconfig.me'

# Git shortcuts (beyond Oh My Zsh defaults)
alias gundo='git reset --soft HEAD~1'
alias gclean='git clean -fd'
alias gfp='git fetch --prune'

# FZF configuration
export FZF_DEFAULT_OPTS="--height 40% --layout=reverse --border"

# Plugin-specific settings
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE="fg=#666666"
bindkey '^[[A' history-substring-search-up
bindkey '^[[B' history-substring-search-down
```

### Efficient Workflows
```bash
# Development workflow
alias dev='cd ~/projects && code . && npm start'

# Git workflow
alias gst='git status --short'
alias gcm='git commit -m'
alias gpo='git push origin'

# File management
alias la='ls -la'
alias lt='ls -lt'           # Sort by time
alias lsize='ls -lS'        # Sort by size

# Quick editing
alias zshconfig='code ~/.zshrc'
alias reload='source ~/.zshrc'
```

### Context-Aware Aliases
```bash
# Different behavior based on context
alias ls='ls --color=auto'  # Linux
alias ls='ls -G'            # macOS

# Conditional aliases based on available commands
if command -v exa >/dev/null 2>&1; then
    alias ls='exa'
    alias ll='exa -l'
    alias la='exa -la'
    alias tree='exa --tree'
fi
```

---

## 🚨 Troubleshooting & Performance

### Oh My Zsh Troubleshooting

#### Common Oh My Zsh Issues
| Problem | Cause | Solution |
|---------|-------|----------|
| **Slow startup** | Too many plugins | Remove unused plugins, use lazy loading |
| **Theme not working** | Missing fonts or dependencies | Install powerline fonts, check theme requirements |
| **Plugin conflicts** | Multiple plugins affecting same features | Disable conflicting plugins one by one |
| **Git aliases not working** | Oh My Zsh not loaded properly | Check `source $ZSH/oh-my-zsh.sh` in ~/.zshrc |

#### Performance Optimization for Oh My Zsh
```bash
# Lazy load heavy plugins
lazy_load_nvm() {
    unset -f nvm node npm npx
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
    [ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
}
for cmd in nvm node npm npx; do
    alias $cmd=lazy_load_nvm
done

# Disable unused Oh My Zsh features
DISABLE_AUTO_UPDATE="true"         # If you update manually
DISABLE_UPDATE_PROMPT="true"       # No update prompts
DISABLE_MAGIC_FUNCTIONS="true"     # If experiencing performance issues
```

#### Backup and Migration
```bash
# Backup your Oh My Zsh configuration
cp ~/.zshrc ~/.zshrc.backup
tar -czf ohmyzsh-backup.tar.gz ~/.oh-my-zsh

# Migrate to new machine
scp ohmyzsh-backup.tar.gz user@newmachine:~/
ssh user@newmachine
tar -xzf ohmyzsh-backup.tar.gz
cp ~/.zshrc.backup ~/.zshrc
```

### Oh My Zsh vs Manual Configuration

#### When to Use Oh My Zsh
**Pros:**
- **Quick setup** - Working shell in minutes
- **Large ecosystem** - 300+ plugins, 100+ themes
- **Community support** - Well-documented, popular
- **Sensible defaults** - Good configuration out of the box

**Cons:**
- **Performance overhead** - More features = slower startup
- **Less control** - Framework abstracts some customization
- **Plugin quality varies** - Some plugins are outdated or buggy

#### When to Go Manual
**Consider manual configuration if:**
- You want maximum performance
- You prefer to understand every part of your config
- You only need specific features
- You're comfortable writing zsh configuration

```bash
# Minimal manual setup example
# Add to ~/.zshrc for fast, minimal zsh

# History
HISTSIZE=10000
SAVEHIST=10000
HISTFILE=~/.zsh_history
setopt SHARE_HISTORY
setopt HIST_IGNORE_DUPS

# Completion
autoload -U compinit && compinit

# Git info in prompt
autoload -Uz vcs_info
precmd() { vcs_info }
zstyle ':vcs_info:git:*' formats ' (%b)'
setopt PROMPT_SUBST
PROMPT='%F{cyan}%n@%m%f:%F{yellow}%~%f%F{red}${vcs_info_msg_0_}%f$ '

# Essential aliases
alias ll='ls -la'
alias la='ls -A'
alias l='ls -CF'
```

### Performance Optimization
```bash
# Profile zsh startup time
zsh -i -c exit           # Time shell startup

# Lazy loading for heavy plugins
lazy_load_nvm() {
    unset -f nvm
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
}
alias nvm=lazy_load_nvm

# Reduce completion rebuilding
autoload -U compinit
if [[ -n ${ZDOTDIR}/.zcompdump(#qN.mh+24) ]]; then
    compinit
else
    compinit -C
fi
```

### Debugging Configuration
```bash
# Debug what's slow in your config
zsh -xvs < ~/.zshrc > debug.log 2>&1

# Test configuration in clean environment
env -i HOME="$HOME" zsh --no-rcs

# Check which functions/aliases are defined
typeset -f | grep "^[a-zA-Z]"    # List functions
alias | grep "^[a-zA-Z]"         # List aliases
```

---

## 🎯 Essential Commands Summary

### Daily Drivers
| Command | Action | Impact |
|---------|--------|---------|
| `Ctrl+R` | History search | 🔥 Find any previous command |
| `Tab` | Smart completion | 🔥 Let zsh do the typing |
| `!!` | Last command | ⚡ Avoid retyping |
| `!$` | Last argument | ⚡ Reuse file paths |
| `cd -` | Previous directory | ⚡ Quick navigation |
| `Ctrl+A/E` | Line start/end | ⚡ Fast cursor movement |
| `Alt+F/B` | Word forward/back | ⚡ Navigate by words |

### Power Features
| Feature | Usage | When You'll Love It |
|---------|--------|-------------------|
| **Glob patterns** | `**/*.js`, `*.{jpg,png}` | Finding files across directories |
| **Parameter expansion** | `${file%.*}`, `${path:h}` | String/path manipulation |
| **Directory stack** | `pushd`, `popd`, `dirs` | Complex navigation workflows |
| **FZF integration** | `Ctrl+T`, `Ctrl+R` | Interactive file/history search |
| **Z plugin** | `z project`, `z -l` | Smart directory jumping |

---

*Remember: Zsh's power comes from customization and learning patterns. Start with basic navigation and history features, then gradually add completion, aliases, and advanced features to build your perfect shell environment!*
