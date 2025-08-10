# 🖥️ iTerm2 Quick Reference Guide

*Master your macOS terminal with style and efficiency*

---

## ⚡ Essential Shortcuts

### Window & Tab Management
| Shortcut | Action |
|----------|--------|
| `Cmd+T` | **New tab** |
| `Cmd+N` | **New window** |
| `Cmd+W` | **Close current tab** |
| `Cmd+Shift+W` | **Close current window** |
| `Cmd+1-9` | **Switch to tab** by number |
| `Cmd+←/→` | **Navigate between tabs** |
| `Cmd+Shift+←/→` | **Move tab left/right** |
| `Cmd+Alt+←/→` | **Switch between windows** |

### Pane Management
| Shortcut | Action |
|----------|--------|
| `Cmd+D` | **Split pane right** (vertical split) |
| `Cmd+Shift+D` | **Split pane down** (horizontal split) |
| `Cmd+[` / `Cmd+]` | **Navigate between panes** |
| `Cmd+Opt+←/→/↑/↓` | **Navigate panes directionally** |
| `Cmd+Shift+Enter` | **Maximize/restore pane** |
| `Cmd+;` | **Autocomplete from history** |

---

## 🔍 Search & Navigation

### Text Search
| Shortcut | Action |
|----------|--------|
| `Cmd+F` | **Open find** |
| `Cmd+G` | **Find next** |
| `Cmd+Shift+G` | **Find previous** |
| `Cmd+E` | **Use selection for find** |
| `Cmd+Shift+H` | **Find and replace** |

### Buffer Navigation
| Shortcut | Action |
|----------|--------|
| `Cmd+↑/↓` | **Scroll to top/bottom** |
| `Page Up/Down` | **Scroll page** |
| `Cmd+Shift+↑/↓` | **Scroll line by line** |
| `Cmd+Home/End` | **Go to beginning/end** |

---

## 📋 Copy & Paste

### Selection & Clipboard
| Shortcut | Action |
|----------|--------|
| `Cmd+C` | **Copy** |
| `Cmd+V` | **Paste** |
| `Cmd+Shift+V` | **Paste history** |
| **Triple-click** | **Select entire line** |
| **Cmd+click** | **Select URL or path** |
| **Cmd+Shift+A** | **Select all** |

### Smart Selection
**What is this?** iTerm2 can intelligently detect and select different types of content with special click patterns.

| Method | Action | Example Use Case |
|---------|--------|------------------|
| **Double-click** | Select word | Quick selection of filenames, variables |
| **Triple-click** | Select line | Copy entire command or file path |
| **Cmd+Double-click** | Select URL/email/path | Instantly select `https://github.com/user/repo` or `/usr/local/bin` |
| **Shift+click** | Extend selection | Select from cursor to click point |
| **Opt+click** | Move cursor to position | Jump cursor without selecting |

**Why it's useful:** No more careful dragging to select long file paths or URLs - just Cmd+double-click!

---

## 🎨 Appearance & Profiles

### View Controls
| Shortcut | Action |
|----------|--------|
| `Cmd+Plus/Minus` | **Zoom in/out** |
| `Cmd+0` | **Reset zoom** |
| `Cmd+Shift+F` | **Toggle fullscreen** |
| `Cmd+U` | **Toggle transparency** |
| `Cmd+R` | **Clear buffer** |
| `Cmd+K` | **Clear scrollback** |

### Profile Management
```bash
# Switching profiles
Cmd+I                   # Open profiles
Cmd+Opt+B              # Browse arrangements

# Profile features
Dynamic profiles        # JSON-based profile configs
Automatic profile switching # Based on hostname/user
Color schemes          # Built-in and custom themes
```

---

## 🔧 Advanced Features

### Marks & Annotations
**What are marks?** Think of marks as bookmarks in your terminal session. They let you quickly jump back to important points in your terminal output.

**Why use marks?** Perfect for long-running processes, build outputs, or when you need to reference earlier command results without scrolling endlessly.

| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Cmd+M` | **Set mark** | Before running long commands, at error locations |
| `Cmd+Shift+M` | **Jump to last mark** | Return to your last bookmark quickly |
| `Cmd+Shift+↑/↓` | **Jump between marks** | Navigate through multiple bookmarks |
| `Cmd+Shift+A` | **Add annotation** | Label important output with notes |

**Example workflow:** Set a mark before running tests → scroll through results → jump back to mark to see the start

### Command History
**What is this?** iTerm2 tracks your command history and can intelligently suggest completions based on what you've typed before.

| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Cmd+;` | **Autocomplete** | Type partial command, get suggestions from history |
| `Cmd+Shift+;` | **Command history** | Browse all previous commands in a searchable list |
| `Cmd+Opt+B` | **Browse arrangements** | Quickly switch between saved window layouts |
| `Cmd+Shift+O` | **Open quickly** | Fast file/directory opener (like Spotlight for terminal) |

**Pro tip:** `Cmd+;` is incredibly useful - start typing `ssh prod` and it'll suggest your full SSH commands!

---

## 🎯 Productivity Features

### Quick Actions
**What are these?** Advanced iTerm2 features that enhance your terminal workflow with visual feedback and automation.

| Feature | Usage | Why It's Useful |
|---------|-------|-----------------|
| **Instant Replay** | `Cmd+Opt+B` → View session recording | Replay your terminal session to see what happened - great for debugging or sharing workflows |
| **Captured Output** | Automatically save command output | iTerm2 remembers output from commands, letting you search and reference old results |
| **Smart Selection** | Double-click to select paths, URLs, IPs | No more careful dragging - click and get perfect selections |
| **Shell Integration** | Enhanced prompt, command status | See which commands succeeded/failed, get better navigation |

**Example:** Run a complex deployment script, then use Instant Replay to show a colleague exactly what happened step-by-step.

### Triggers
**What are triggers?** Automated actions that iTerm2 performs when it sees specific text patterns in your terminal output.

**Why use them?** Automate responses to common events - get notified when builds finish, highlight errors, or make text clickable.

```bash
# Common trigger examples and why they're useful

Pattern: "password"     → Action: Highlight (yellow background)
# Why: Never miss password prompts in long scripts

Pattern: "ERROR"        → Action: Send notification + Bounce dock
# Why: Get alerted to errors even when iTerm2 isn't focused

Pattern: "localhost:3000" → Action: Make clickable URL  
# Why: Instantly click to open your dev server

Pattern: "Build completed" → Action: Post notification
# Why: Know when long builds finish without watching

Pattern: "\\[FAIL\\]"   → Action: Highlight (red background)
# Why: Spot test failures immediately in test output
```

**Setup:** Preferences → Profiles → Advanced → Triggers

### Status Bar Components
**What is this?** A customizable information bar that shows useful context about your terminal session.

**Why use it?** Get important information at a glance without running commands.

| Component | What It Shows | Why It's Useful |
|-----------|---------------|-----------------|
| **Current directory** | `/Users/you/projects/myapp` | Know where you are without `pwd` |
| **Git branch status** | `main ✓` or `feature-x ●2` | See branch and uncommitted changes instantly |
| **CPU/Memory usage** | `CPU: 45% RAM: 8.2GB` | Monitor system performance |
| **Clock/Date** | `14:30 Dec 25` | Always visible time reference |
| **Network activity** | `↑ 1.2MB ↓ 500KB` | See network usage in real-time |

**Setup:** Preferences → Profiles → Session → Configure Status Bar

---

## ⚙️ Essential Preferences

### General Settings
**Preferences → General:**
```
✓ Confirm closing multiple sessions
✓ Confirm "Quit iTerm2" command  
✓ Restore windows when iTerm2 is restarted
Startup: Use System Window Restoration Setting
```

### Appearance Optimizations
**Preferences → Appearance:**
```
Theme: Minimal (or Dark/Auto)
Tab bar location: Top
Status bar location: Bottom
✓ Hide tab bar when there is only one tab
✓ Show border around window
Dimming: 40% (for inactive split panes)
```

### Profile Configuration
**Preferences → Profiles → [Your Profile]:**

#### Colors
```bash
# Popular color schemes
Solarized Dark/Light     # Classic developer theme
Dracula                  # Popular dark theme  
Nord                     # Cool blue theme
Gruvbox                  # Retro warm theme
One Dark                 # Atom editor inspired
```

#### Text Settings
```bash
Font: SF Mono (14pt)     # Or Fira Code, JetBrains Mono
✓ Use ligatures          # For coding fonts
Cursor: Underline        # Or Box/Vertical bar
✓ Blinking cursor
```

#### Window Settings
```bash
Transparency: 10-20%     # Subtle transparency
Blur: Yes               # Background blur effect
Columns: 120            # Width
Rows: 30               # Height
```

---

## 🔗 Shell Integration Setup

### Automatic Installation
```bash
# Run in iTerm2
iTerm2 > Install Shell Integration

# Or manually download
curl -L https://iterm2.com/shell_integration/install_shell_integration_and_utilities.sh | bash
```

### Features Enabled
- **Enhanced prompts** with return codes
- **Command timeline** in session info
- **Download triggers** for file transfers
- **Remote host detection**
- **Badge integration**

---

## 🎪 Advanced Workflows

### Window Arrangements
**What are these?** Saved layouts of windows, tabs, and panes that you can instantly restore.

**Why use them?** Perfect for setting up complex development environments with one click.

```bash
# Example: "Development Setup" arrangement might include:
# Tab 1: Editor pane + server logs pane
# Tab 2: Database console  
# Tab 3: Git status + file watcher
# Tab 4: SSH to staging server

# Save current layout
Window → Save Window Arrangement → "Development Setup"

# Restore layout (recreates everything exactly)
Window → Restore Window Arrangement → "Development Setup"

# Automate with scripts (advanced)
iTerm2 → Scripts → Manage → New Python Script
```

**Use cases:** Different arrangements for different projects, client work setups, or debugging sessions.

### Python API Integration
```python
#!/usr/bin/env python3
import iterm2

async def main(connection):
    # Create new window with specific profile
    app = await iterm2.async_get_app(connection)
    window = await iterm2.Window.async_create(connection)
    
    # Split and run commands
    session = window.current_tab.current_session
    await session.async_split_pane(vertical=True)
    await session.async_send_text('npm run dev\n')

iterm2.run_until_complete(main)
```

### Semantic History
**What is this?** Makes file paths and URLs in your terminal output clickable and interactive.

**Why use it?** Skip the copy-paste dance - just click to open files, URLs, or directories.

**Preferences → Profiles → Advanced → Semantic History:**
```bash
# Setup to open files in your preferred editor
Action: Open with editor...
Editor: /usr/local/bin/code (or /usr/bin/vim, etc.)

# What becomes clickable:
filename:line           # myfile.js:45 → Opens file at specific line
./relative/path         # Click to open in editor  
/absolute/path          # Click to open in editor
github.com/user/repo    # Click to open in browser
http://localhost:3000   # Click to open in browser
```

**Example workflow:** Your test fails at `src/components/Button.js:23` → click to open that exact line in your editor!

---

## 🚨 Troubleshooting & Tips

### Performance Optimization
```bash
# In Preferences → Advanced
Disable unnecessary visual effects
Reduce scrollback buffer size if needed
Turn off "Save copy/paste history to disk"
Disable unused triggers
```

### Common Issues
| Problem | Solution |
|---------|----------|
| **Slow startup** | Check shell integration, reduce plugins |
| **Font rendering** | Try different renderer in Advanced settings |
| **Color issues** | Check terminal type settings |
| **Copy/paste problems** | Verify clipboard access permissions |

### Pro Tips
- **Cmd+click URLs** to open in browser
- **Cmd+click file paths** to open in editor  
- **Right-click selection** for context actions
- **Drag files** into terminal for instant paths
- **Use badges** to show current directory/git branch
- **Set up triggers** for common patterns in logs
- **Create hotkey windows** for quick terminal access

---

## 🎯 Essential Key Combinations

### Must-Know Shortcuts
| Shortcut | Action | Usage |
|----------|--------|-------|
| `Cmd+T` | New tab | Start fresh workspace |
| `Cmd+D` | Split right | Side-by-side work |
| `Cmd+Shift+D` | Split down | Top/bottom layout |
| `Cmd+F` | Find | Search output |
| `Cmd+K` | Clear | Clean slate |
| `Cmd+;` | Autocomplete | Command completion |
| `Cmd+Shift+H` | Paste history | Access clipboard history |

---

## 📱 Customization Examples

### Custom Key Bindings
**Preferences → Keys → Key Bindings:**
```bash
Cmd+Shift+Left  → Send Hex: 0x01    # Go to line start
Cmd+Shift+Right → Send Hex: 0x05    # Go to line end  
Cmd+Backspace   → Send Hex: 0x15    # Delete line
Option+Delete   → Send Hex: 0x17    # Delete word
```

### Touch Bar Configuration
```bash
# Add to Touch Bar
New Tab, Split Pane, Clear, Man Page for Selection
Customize in System Preferences → Extensions
```

---

*Remember: iTerm2's power comes from customization. Start with the basics, then gradually add features like shell integration, custom profiles, and automation to build your perfect terminal environment!*
