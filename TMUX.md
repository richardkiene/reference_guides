# 🚀 Tmux + iTerm2 Quick Reference Guide

*Your go-to cheat sheet for terminal multiplexing mastery with iTerm2 integration*

---

## 🍎 iTerm2 + Tmux Integration

**Native Integration:** iTerm2 can integrate directly with tmux for a seamless experience!

```bash
# Start tmux with iTerm2 integration
tmux -CC

# Or attach to existing session with integration
tmux -CC attach -t mysession
```

**Benefits:**
- Native macOS scrolling and copy/paste
- iTerm2's split panes work alongside tmux
- Better mouse support and trackpad gestures
- Native notifications and badge support

---

## 🎯 Core Concepts

**Sessions** → Think of these as workspaces for different projects  
**Windows** → Like browser tabs within a session  
**Panes** → Split views within a window  

**Default Prefix Key:** `Ctrl+b` (shown as `C-b` below)

**Key Notation:** 
- `C-b` = `Ctrl+b`
- `C-b d` = Press `Ctrl+b`, release, then press `d`
- `C-b C-←` = Press `Ctrl+b`, release, then `Ctrl+←` (hold Ctrl)

---

## 📋 Session Management

### Starting & Attaching
```bash
tmux                    # Start new session
tmux new -s myproject   # Start named session
tmux ls                 # List all sessions
tmux attach -t 0        # Attach to session 0
tmux attach -t myproject # Attach to named session
```

### Inside Tmux
| Command | Action |
|---------|--------|
| `C-b d` | **Detach** from session |
| `C-b $` | **Rename** current session |
| `C-b s` | **Switch** between sessions |

---

## 🪟 Window Management

| Command | Action |
|---------|--------|
| `C-b c` | **Create** new window |
| `C-b ,` | **Rename** current window |
| `C-b &` | **Kill** current window |
| `C-b p` | **Previous** window |
| `C-b n` | **Next** window |
| `C-b 0-9` | **Switch** to window by number |
| `C-b l` | **Last** used window |
| `C-b w` | **List** all windows |

---

## 📱 Pane Management

### Creating Panes
| Command | Action |
|---------|--------|
| `C-b %` | **Split vertically** (side by side) |
| `C-b "` | **Split horizontally** (top/bottom) |

### Navigating Panes
| Command | Action |
|---------|--------|
| `C-b ←↑↓→` | **Move** between panes |
| `C-b o` | **Cycle** through panes |
| `C-b ;` | **Toggle** between current and last pane |
| `C-b q` | **Show** pane numbers |
| `C-b q 0-9` | **Jump** to pane by number |

### Resizing Panes
| Command | Action |
|---------|--------|
| `C-b C-←↑↓→` | **Resize** pane (hold Ctrl) |
| `C-b Alt-←↑↓→` | **Resize** in larger increments |

### Pane Operations
| Command | Action |
|---------|--------|
| `C-b x` | **Kill** current pane |
| `C-b z` | **Zoom** pane (toggle fullscreen) |
| `C-b !` | **Break** pane into new window |
| `C-b {` | **Move** pane left |
| `C-b }` | **Move** pane right |

---

## 📋 Copy Mode with iTerm2

### Native iTerm2 Method (Recommended)
- **Cmd+C / Cmd+V** work natively with `-CC` integration
- **Three-finger tap** for word selection
- **Trackpad scrolling** works naturally

### Traditional Tmux Copy Mode
| Command | Action |
|---------|--------|
| `C-b [` | **Enter** copy mode |
| `Space` | **Start** selection |
| `Enter` | **Copy** to tmux buffer |
| `C-b ]` | **Paste** from tmux buffer |
| `q` | **Exit** copy mode |

### macOS Clipboard Integration
```bash
# Copy tmux buffer to macOS clipboard
C-b : run "tmux save-buffer - | pbcopy"

# Or add to .tmux.conf for automatic clipboard sync
bind -T copy-mode-vi y send-keys -X copy-pipe-and-cancel 'pbcopy'
```

### Navigation in Copy Mode
| Command | Action |
|---------|--------|
| `↑↓←→` | Move cursor |
| `w` | Next word |
| `b` | Previous word |
| `g` | Go to top |
| `G` | Go to bottom |
| `/` | Search forward |
| `?` | Search backward |

---

## ⚙️ iTerm2-Optimized Configuration

### Essential `.tmux.conf` for iTerm2
```bash
# Enable iTerm2 integration features
set-option -g default-terminal "screen-256color"
set-option -sa terminal-overrides ",xterm*:Tc"

# Better mouse support for iTerm2
set -g mouse on

# Enable clipboard integration with macOS
set-option -g default-command "reattach-to-user-namespace -l $SHELL"

# Fix for iTerm2 copy/paste
bind-key -T copy-mode-vi Enter send-keys -X copy-pipe-and-cancel "reattach-to-user-namespace pbcopy"
bind-key -T copy-mode-vi MouseDragEnd1Pane send-keys -X copy-pipe-and-cancel "reattach-to-user-namespace pbcopy"

# Start windows and panes at 1, not 0
set -g base-index 1
setw -g pane-base-index 1

# Reload config file
bind r source-file ~/.tmux.conf \; display-message "Config reloaded!"

# Better pane splitting (more intuitive)
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"

# New windows in current path
bind c new-window -c "#{pane_current_path}"
```

### iTerm2 Profile Settings
**In iTerm2 Preferences:**
- **Terminal → Report Terminal Type:** `xterm-256color`
- **Terminal → Scrollback:** Unlimited (or high number)
- **Keys → Key Mappings:** Add mapping for `Cmd+K` to send `C-l` for clear
- **Advanced → Mouse → Scroll wheel sends arrow keys:** No

---

## ⚙️ Configuration Essentials

### Custom Prefix Key
Add to `~/.tmux.conf`:
```bash
# Change prefix to Ctrl-a
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix
```

### Essential Settings
```bash
# Enable mouse mode
set -g mouse on

# Start windows and panes at 1, not 0
set -g base-index 1
setw -g pane-base-index 1

# Reload config file
bind r source-file ~/.tmux.conf \; display-message "Config reloaded!"

# Better pane splitting
bind | split-window -h
bind - split-window -v
```

---

## 🎨 Status Bar Customization

```bash
# Status bar colors
set -g status-bg colour235
set -g status-fg colour255

# Show session name, window & pane info
set -g status-left '#[fg=green]#S #[default]'
set -g status-right '#[fg=yellow]%Y-%m-%d %H:%M#[default]'
```

---

## 🚨 Emergency Commands

| Command | Action |
|---------|--------|
| `tmux kill-session -t myproject` | Kill specific session |
| `tmux kill-server` | Kill all tmux sessions |
| `C-b :` | Enter command mode |

---

## 💡 Pro Tips for iTerm2 + Tmux

**🔥 Most Used Commands**
- `tmux -CC` → Start with iTerm2 integration
- `C-b c` → New window
- `C-b %` → Split vertically  
- `C-b "` → Split horizontally
- `C-b d` → Detach (keeps session running)
- `C-b z` → Zoom pane

**🎯 Optimal Workflow**
1. `tmux -CC new -s project` → Start integrated session
2. Use native iTerm2 scrolling and copy/paste
3. `C-b c` → Create windows for different tasks
4. `C-b %` or `C-b "` → Split panes as needed
5. `Cmd+D` for quick iTerm2 splits when needed
6. `C-b d` → Detach when done
7. `tmux -CC attach -t project` → Resume with integration

**⚡ iTerm2-Specific Efficiency Boosters**
- Use `-CC` flag for the best experience
- Combine tmux sessions with iTerm2 profiles
- Set up iTerm2 window arrangements for common layouts
- Use native macOS notifications with tmux
- Take advantage of iTerm2's search (Cmd+F) in tmux sessions

**🔗 Hybrid Approach**
- Use tmux for session persistence and window management
- Use iTerm2 splits for temporary pane divisions
- Leverage both tmux copy mode AND native macOS clipboard
- Use iTerm2 tabs for different tmux sessions

**🎨 Visual Enhancements**
- Enable iTerm2's minimal theme for cleaner tmux integration
- Use iTerm2's automatic profile switching with tmux
- Configure different color schemes for different tmux sessions
- Use iTerm2 badges to show tmux session info

---

## 📖 Quick Command Reference

### iTerm2 Integration Commands
```bash
# Start tmux with native iTerm2 integration
tmux -CC

# Create integrated session with multiple windows
tmux -CC new -s dev \; new-window -n editor \; new-window -n server

# Attach to existing session with integration
tmux -CC attach -t mysession || tmux -CC new -s mysession

# List sessions (works great with iTerm2's session restoration)
tmux ls
```

### Traditional Commands
```bash
# Create session with multiple windows  
tmux new -s dev \; new-window -n editor \; new-window -n server

# Attach or create session
tmux attach -t mysession || tmux new -s mysession

# Send commands to specific session
tmux send-keys -t mysession 'ls -la' Enter
```

### Clipboard Integration
```bash
# Install reattach-to-user-namespace for better clipboard support
brew install reattach-to-user-namespace

# Copy current tmux buffer to macOS clipboard
tmux save-buffer - | pbcopy

# Load from macOS clipboard to tmux
pbpaste | tmux load-buffer -
```

---

*Remember: Start with `tmux -CC` for the best iTerm2 experience! The integration provides native scrolling, better mouse support, and seamless copy/paste while maintaining all of tmux's session management power.*
