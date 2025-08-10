# 💻 VS Code/VSCodium Quick Reference Guide

*Master your code editor with powerful shortcuts and features*

---

## ⚡ Essential Shortcuts

### File & Project Management
| Shortcut | Action | Why It's Useful |
|----------|--------|-----------------|
| `Cmd+N` | **New file** | Quick file creation without menus |
| `Cmd+O` | **Open file** | Browse and open any file |
| `Cmd+Shift+N` | **New window** | Work on multiple projects simultaneously |
| `Cmd+W` | **Close file** | Clean up your workspace |
| `Cmd+Shift+W` | **Close window** | Close entire VS Code instance |
| `Cmd+P` | **Quick Open** | Jump to any file by name - fastest navigation method |
| `Cmd+Shift+P` | **Command Palette** | Access any VS Code command by typing |
| `Cmd+,` | **Open Settings** | Customize your editor preferences |

**Pro tip:** `Cmd+P` is your best friend - type partial filenames to jump anywhere instantly!

### Tab Management
| Shortcut | Action | Why It's Useful |
|----------|--------|-----------------|
| `Cmd+T` | **Show all symbols** | Find functions, classes across your workspace |
| `Cmd+1-9` | **Switch to tab** by number | Quick navigation between open files |
| `Cmd+Shift+[/]` | **Navigate between tabs** | Move through open files sequentially |
| `Cmd+Shift+T` | **Reopen closed tab** | Recover accidentally closed files |
| `Cmd+K, Cmd+W` | **Close all tabs** | Clean slate for new work |

---

## 🔍 Search & Navigation

### Finding Things
**What is this?** VS Code's powerful search system helps you find anything in your codebase instantly.

| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Cmd+F` | **Find in file** | Search current file for text, variables, functions |
| `Cmd+Shift+F` | **Find in files** | Search entire project - perfect for tracking down where something is used |
| `Cmd+G` / `Cmd+Shift+G` | **Find next/previous** | Navigate through search results |
| `Cmd+D` | **Select next occurrence** | Multi-cursor editing - select all instances of selected text |
| `Cmd+Shift+L` | **Select all occurrences** | Change all instances at once |

**Example workflow:** Need to rename a variable? Select it, hit `Cmd+Shift+L`, then type the new name to change everywhere at once.

### Go To Commands
**What are these?** Smart navigation that understands your code structure.

| Shortcut | Action | Why It's Powerful |
|----------|--------|-------------------|
| `Cmd+Click` | **Go to definition** | Jump to where functions/variables are defined |
| `F12` | **Go to definition** | Same as Cmd+Click but keyboard-only |
| `Cmd+F12` | **Go to implementation** | See how interfaces/abstract classes are implemented |
| `Shift+F12` | **Find all references** | See everywhere something is used |
| `Cmd+Shift+O` | **Go to symbol** | Jump to functions/classes in current file |
| `Cmd+T` | **Go to symbol in workspace** | Find any function/class across all files |

**Use case:** Debugging a bug? Use "Find all references" to see everywhere a function is called.

---

## ✏️ Editing Superpowers

### Multi-Cursor Magic
**What is this?** Edit multiple locations simultaneously - one of VS Code's most powerful features.

| Shortcut | Action | Perfect For |
|----------|--------|-------------|
| `Alt+Click` | **Add cursor** | Place cursors exactly where you need them |
| `Cmd+Alt+↑/↓` | **Add cursor above/below** | Create vertical columns of cursors |
| `Cmd+D` | **Select next occurrence** | Select matching text incrementally |
| `Cmd+K, Cmd+D` | **Skip next occurrence** | Skip one match when using Cmd+D |
| `Cmd+U` | **Undo last cursor operation** | Step back in multi-cursor selection |

**Example:** Need to add quotes around multiple words? Place cursors at the start of each word, type `"`, then move to the end and type `"` again.

### Line Operations
| Shortcut | Action | Why It's Faster |
|----------|--------|-----------------|
| `Cmd+L` | **Select line** | Select entire line without positioning cursor |
| `Cmd+Shift+K` | **Delete line** | Remove line instantly without selecting |
| `Alt+↑/↓` | **Move line up/down** | Reorder code without cut/paste |
| `Shift+Alt+↑/↓` | **Copy line up/down** | Duplicate lines quickly |
| `Cmd+Enter` | **Insert line below** | Add new line without moving cursor to end |
| `Cmd+Shift+Enter` | **Insert line above** | Add new line above current position |

### Code Manipulation
| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Cmd+/` | **Toggle comment** | Comment/uncomment code blocks |
| `Shift+Alt+A` | **Toggle block comment** | Multi-line comment blocks |
| `Cmd+]` / `Cmd+[` | **Indent/outdent** | Fix indentation quickly |
| `Shift+Alt+F` | **Format document** | Auto-format entire file |
| `Cmd+K, Cmd+F` | **Format selection** | Format just selected code |

---

## 🔧 Code Intelligence

### IntelliSense & Suggestions
**What is this?** VS Code's smart code completion that understands your project and suggests relevant code.

| Trigger | Action | Why It's Smart |
|---------|--------|----------------|
| `Ctrl+Space` | **Trigger suggestions** | Get code completions even when auto-complete doesn't appear |
| `Cmd+.` | **Quick fix** | Auto-fix errors, add imports, refactor code |
| `F2` | **Rename symbol** | Safely rename variables/functions across entire project |
| `Cmd+Shift+R` | **Refactor** | Access advanced refactoring options |

**Example:** Type `console.l` and IntelliSense suggests `console.log()` with parameter hints.

### Error Navigation
| Shortcut | Action | Perfect For |
|----------|--------|-------------|
| `F8` | **Next error/warning** | Jump through problems in your code |
| `Shift+F8` | **Previous error/warning** | Navigate backwards through issues |
| `Cmd+Shift+M` | **Show problems panel** | See all errors/warnings in one place |

---

## 🎯 Workspace Features

### Side Panel Management
**What are these?** The various panels that provide different views of your project.

| Shortcut | Panel | What It Shows | When to Use |
|----------|-------|---------------|-------------|
| `Cmd+Shift+E` | **Explorer** | File tree, folder structure | Navigate project files |
| `Cmd+Shift+G` | **Source Control** | Git changes, staging area | Manage version control |
| `Cmd+Shift+D` | **Debug** | Debug console, variables | Debug your applications |
| `Cmd+Shift+X` | **Extensions** | Installed and available extensions | Customize VS Code |
| `Cmd+Shift+F` | **Search** | Global search results | Find text across project |

### Terminal Integration
**What is this?** Built-in terminal that shares your project context.

| Shortcut | Action | Why It's Better Than External Terminal |
|----------|--------|---------------------------------------|
| `Ctrl+`` | **Toggle terminal** | Quick access without leaving editor |
| `Cmd+Shift+`` | **New terminal** | Multiple terminals for different tasks |
| `Cmd+1-9` | **Switch terminal** | Navigate between multiple terminals |
| `Cmd+K` | **Clear terminal** | Clean slate (in terminal) |

**Use case:** Run your dev server in one terminal, run tests in another, all without leaving VS Code.

---

## 🔄 Git Integration

### Source Control Magic
**What is this?** VS Code's built-in Git interface that makes version control visual and intuitive.

| Shortcut | Action | Why It's Useful |
|----------|--------|-----------------|
| `Cmd+Shift+G` | **Open source control** | See all changed files at a glance |
| `Cmd+K, Cmd+C` | **Commit all** | Quick commit workflow |
| `Cmd+K, Cmd+S` | **Stage all changes** | Prepare files for commit |
| `Cmd+K, Cmd+U` | **Unstage all changes** | Remove files from staging |

### Diff Viewing
**What is this?** Side-by-side comparison of file changes.

**Features:**
- **Inline changes** highlighted in editor
- **Gutter indicators** show added/modified/deleted lines  
- **Side-by-side diff** for comparing versions
- **Blame annotations** show who changed what when

**Why it's powerful:** See exactly what changed without command-line git tools.

---

## 🎨 Interface Customization

### Layout Control
| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Cmd+B` | **Toggle sidebar** | Hide file explorer for more code space |
| `Cmd+J` | **Toggle panel** | Hide terminal/problems panel |
| `Cmd+Shift+U` | **Toggle output** | See build output, extension logs |
| `Cmd+K, Z` | **Zen mode** | Distraction-free coding (hides everything) |
| `F11` | **Toggle fullscreen** | Maximum screen real estate |

### View Options
| Shortcut | Action | Perfect For |
|----------|--------|-------------|
| `Cmd+\` | **Split editor** | Work on multiple files side-by-side |
| `Cmd+1-3` | **Focus editor group** | Switch between split panels |
| `Cmd+K, Cmd+←/→` | **Move editor to group** | Reorganize split layout |
| `Cmd+K, F` | **Close folder** | Close entire project folder |

---

## 🔌 Extensions Ecosystem

### Essential Extension Categories
**What are these?** Add-ons that extend VS Code's functionality for specific languages and workflows.

| Category | Examples | Why You Need Them |
|----------|----------|-------------------|
| **Language Support** | Python, Go, Rust, TypeScript | Syntax highlighting, IntelliSense, debugging |
| **Linting** | ESLint, Pylint, golangci-lint | Catch errors before runtime |
| **Formatting** | Prettier, Black, gofmt | Consistent code style |
| **Git Tools** | GitLens, Git History | Enhanced version control features |
| **Themes** | One Dark Pro, Dracula, Nord | Personalize your coding environment |
| **Productivity** | Bracket Pair Colorizer, Auto Rename Tag | Quality of life improvements |

### Managing Extensions
| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `Cmd+Shift+X` | **Extensions panel** | Browse, install, manage extensions |
| `@installed` | **Filter installed** | See what extensions you have |
| `@recommended` | **Show recommendations** | Find extensions for your current project type |

---

## 🐛 Debugging Features

### Debug Controls
**What is this?** Visual debugging that lets you step through code, inspect variables, and find bugs.

| Shortcut | Action | When to Use |
|----------|--------|-------------|
| `F5` | **Start debugging** | Launch your app in debug mode |
| `F9` | **Toggle breakpoint** | Pause execution at specific lines |
| `F10` | **Step over** | Execute next line of code |
| `F11` | **Step into** | Enter function calls to debug deeper |
| `Shift+F11` | **Step out** | Exit current function |
| `F6` | **Pause** | Stop execution to inspect state |

### Debug Features
- **Variable inspection** - See values of all variables in scope
- **Call stack** - Understand how you got to current execution point
- **Watch expressions** - Monitor specific variables or expressions
- **Debug console** - Execute code in debug context

**Example workflow:** Set breakpoint → run with F5 → when it hits, inspect variables → step through code to find the bug.

---

## ⚙️ Settings & Configuration

### Accessing Settings
**What are these?** VS Code's customization options that control everything from appearance to behavior.

| Method | Access | Best For |
|--------|--------|----------|
| `Cmd+,` | **Settings UI** | Easy browsing and searching options |
| `Cmd+Shift+P` → "settings.json" | **Settings file** | Advanced configuration, copying settings |
| **Workspace settings** | Project-specific settings | Different configs per project |

### Essential Settings Categories
```json
// Example useful settings
{
  "editor.fontSize": 14,
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.formatOnSave": true,
  "editor.minimap.enabled": false,
  "workbench.colorTheme": "One Dark Pro",
  "terminal.integrated.fontSize": 12,
  "files.autoSave": "afterDelay"
}
```

### Settings Sync
**What is this?** Sync your settings, extensions, and keybindings across multiple machines.

**Why use it?** Set up VS Code once, have the same environment everywhere.
- Sign in with GitHub/Microsoft account
- All settings automatically sync
- Extensions install automatically on new machines

---

## 🚀 Advanced Workflows

### Workspace Features
**What are workspaces?** Collections of folders that VS Code treats as a single project.

**Multi-root workspaces** let you:
- Work on frontend and backend simultaneously
- Keep related projects together
- Share settings across multiple folders

```json
// example.code-workspace
{
  "folders": [
    { "path": "./frontend" },
    { "path": "./backend" },
    { "path": "./shared-utils" }
  ],
  "settings": {
    "typescript.preferences.includePackageJsonAutoImports": "on"
  }
}
```

### Tasks & Build Systems
**What are tasks?** Automated commands you can run from VS Code.

**Example tasks:**
- Build your project
- Run tests
- Start dev server
- Deploy to staging

```json
// .vscode/tasks.json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "npm: start",
      "type": "shell",
      "command": "npm start",
      "group": "build"
    }
  ]
}
```

**Run with:** `Cmd+Shift+P` → "Tasks: Run Task"

---

## 🎯 Productivity Tips

### Keyboard-First Workflow
**Why go keyboard-first?** Much faster than mouse navigation once you learn the shortcuts.

**Essential daily shortcuts:**
1. `Cmd+P` - Open any file
2. `Cmd+Shift+P` - Run any command
3. `Cmd+D` - Multi-select text
4. `Cmd+F` - Find in file
5. `Cmd+Shift+F` - Find in project
6. `Cmd+.` - Quick fix
7. `F2` - Rename symbol

### Code Navigation Patterns
**Efficient workflows for large codebases:**

1. **Find and explore:** `Cmd+P` → type filename → `Cmd+Click` definition → `Shift+F12` find references
2. **Refactor safely:** Select symbol → `F2` rename → `Cmd+.` for quick fixes
3. **Debug workflow:** `F9` set breakpoint → `F5` start debug → `F10/F11` step through

### Project Setup Best Practices
```bash
# Recommended project structure
.vscode/
  ├── settings.json      # Project-specific settings
  ├── tasks.json         # Build/test tasks
  ├── launch.json        # Debug configurations
  └── extensions.json    # Recommended extensions
```

---

## 🎪 Power User Features

### Command Palette Mastery
**What is this?** The `Cmd+Shift+P` command palette is your gateway to everything in VS Code.

**Pro tips:**
- Type `>` for commands
- Type `@` for symbols in current file
- Type `#` for symbols in workspace
- Type `:` followed by number to go to line
- Type `?` to see all available prefixes

### Snippets & Code Generation
**What are snippets?** Pre-written code templates that expand with shortcuts.

**Built-in snippets:**
- `log` → `console.log()`
- `if` → if statement structure
- `for` → for loop structure
- `func` → function template

**Custom snippets:** Create your own commonly-used code patterns.

### Remote Development
**What is this?** Work on code that lives on remote servers or in containers.

**Extensions:**
- **Remote-SSH** - Work on remote servers
- **Remote-Containers** - Develop inside Docker containers
- **WSL** - Work with Linux subsystem on Windows

**Why it's powerful:** Edit remote code as if it's local, with full IntelliSense and debugging.

---

## 🚨 Troubleshooting & Performance

### Common Issues & Solutions
| Problem | Solution | Prevention |
|---------|----------|------------|
| **Slow performance** | Disable unused extensions, check file watcher limits | Keep extensions minimal |
| **IntelliSense not working** | Reload window, check language server | Ensure proper project setup |
| **Git integration broken** | Check git path in settings | Keep Git updated |
| **Extension conflicts** | Disable extensions one by one | Read extension descriptions carefully |

### Performance Optimization
```json
// Settings for better performance
{
  "search.exclude": {
    "**/node_modules": true,
    "**/dist": true,
    "**/.git": true
  },
  "files.watcherExclude": {
    "**/node_modules/**": true
  },
  "typescript.disableAutomaticTypeAcquisition": true
}
```

---

## 🎯 Essential Shortcuts Summary

### Daily Drivers (Master These First)
| Shortcut | Action | Impact |
|----------|--------|--------|
| `Cmd+P` | Quick Open file | 🔥 Game changer for navigation |
| `Cmd+Shift+P` | Command Palette | 🔥 Access to everything |
| `Cmd+D` | Multi-select | 🔥 Transform editing speed |
| `Cmd+F` | Find in file | ⚡ Essential for code reading |
| `Cmd+Shift+F` | Find in project | ⚡ Essential for large codebases |
| `F2` | Rename symbol | ⚡ Safe refactoring |
| `Cmd+.` | Quick fix | ⚡ Auto-fix errors and imports |

### Weekly Workflow Enhancers
| Shortcut | Action | When You'll Love It |
|----------|--------|-------------------|
| `Cmd+Shift+O` | Go to symbol in file | Navigating large files |
| `Cmd+T` | Go to symbol in workspace | Finding functions across project |
| `Alt+Click` | Multi-cursor | Complex text editing |
| `Cmd+K, Z` | Zen mode | Focus time |
| `F12` | Go to definition | Understanding code flow |

---

*Remember: VS Code's power comes from combining features. Master the basics first (file navigation, search, multi-cursor), then gradually add debugging, extensions, and advanced workflows to build your perfect development environment!*
