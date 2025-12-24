# Zed Editor CLI Configuration Guide

This guide ensures the Zed editor is properly linked to your system's PATH, allowing you to locate it using `which zed` and launch it from any directory.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation Methods](#installation-methods)
- [Path Configuration](#path-configuration)
- [Verification](#verification)
- [Advanced Configuration](#advanced-configuration)
- [Troubleshooting](#troubleshooting)
- [Uninstallation](#uninstallation)

## Prerequisites

Before proceeding, ensure you have:
- ✅ Ubuntu 20.04 LTS or later (tested on 22.04, 24.04)
- ✅ Zsh installed (`zsh --version`)
- ✅ Zed editor downloaded from [zed.dev](https://zed.dev)
- ✅ Basic terminal knowledge

## Installation Methods

### Method 1: Official Installation Script (Recommended)

```bash
# Download and run the official installation script
curl -fsSL https://zed.dev/install.sh | sh
```

**Script Features:**
- Automatically detects your OS
- Downloads the latest Zed release
- Installs to `~/.local/zed.app/`
- Can add to PATH automatically (with your permission)

### Method 2: Manual Installation

```bash
# Download the latest .deb package
cd ~/Downloads
wget https://zed.dev/api/releases/stable/latest/linux/x86_64/zed.deb

# Install the package
sudo dpkg -i zed.deb

# Fix any missing dependencies
sudo apt install -f
```

### Method 3: AppImage (Universal)

```bash
# Download the AppImage
wget https://zed.dev/api/releases/stable/latest/linux/x86_64/Zed.AppImage

# Make it executable
chmod +x Zed.AppImage

# Move to bin directory
mkdir -p ~/.local/bin
mv Zed.AppImage ~/.local/bin/zed
```

## Path Configuration

### Step 1: Locate the Zed Binary

After installation, find where Zed is located:

```bash
# Search for Zed in common locations
find ~ -name "zed" -type f 2>/dev/null | grep -E "(bin/zed|Zed.AppImage)"

# Common locations:
# - /home/YOUR_USERNAME/.local/zed.app/bin/zed
# - /usr/local/bin/zed
# - /usr/bin/zed
# - ~/.local/bin/zed
```

**Typical Paths:**
| Installation Method | Default Location |
|---------------------|------------------|
| Official Script | `~/.local/zed.app/bin/zed` |
| .deb Package | `/usr/bin/zed` |
| Manual Download | `~/Downloads/zed` |

### Step 2: Create Symbolic Link (If Needed)

If Zed isn't in your PATH, create a symlink:

```bash
# Create local bin directory if it doesn't exist
mkdir -p ~/.local/bin

# Create symbolic link (replace path with your actual location)
ln -sf /home/$(whoami)/.local/zed.app/bin/zed ~/.local/bin/zed

# Alternative: Link to system bin (requires sudo)
sudo ln -sf /home/$(whoami)/.local/zed.app/bin/zed /usr/local/bin/zed
```

### Step 3: Update Shell Configuration

#### For Zsh Users (Recommended):

```bash
# Open Zsh configuration
nano ~/.zshrc

# Add this line at the bottom
export PATH="$HOME/.local/bin:$PATH"

# Save and exit (Ctrl+X, Y, Enter)
```

#### For Bash Users:

```bash
# Open Bash configuration
nano ~/.bashrc

# Add this line at the bottom
export PATH="$HOME/.local/bin:$PATH"
```

#### For Fish Shell Users:

```bash
# Add to Fish configuration
nano ~/.config/fish/config.fish

# Add this line
set -gx PATH "$HOME/.local/bin" $PATH
```

### Step 4: Apply Changes

```bash
# Reload your shell configuration
source ~/.zshrc  # For Zsh
# OR
source ~/.bashrc # For Bash

# Alternative: Open a new terminal window
```

## Verification

Test that Zed is properly configured:

```bash
# 1. Check if Zed is in PATH
which zed
# Expected: /home/yourusername/.local/bin/zed or similar

# 2. Check Zed version
zed --version
# Expected: zed version 1.0.0 or similar

# 3. Test opening current directory
zed .

# 4. Test opening specific file
zed README.md

# 5. List all available commands
zed --help
```

**Expected Output Examples:**
```bash
$ which zed
/home/john/.local/bin/zed

$ zed --version
zed 1.0.0 (abc123)

$ zed --help
Usage: zed [OPTIONS] [PATH]...

Arguments:
  [PATH]...  Paths to files or directories to open

Options:
  -h, --help     Print help
  -V, --version  Print version
```

## Advanced Configuration

### Alias Configuration

Create shortcuts for common tasks:

```bash
# Add to ~/.zshrc or ~/.bashrc

# Open Zed with specific projects
alias zprojects='zed ~/projects'

# Open Zed with current Git repository
alias zgit='zed $(git rev-parse --show-toplevel 2>/dev/null || echo ".")'

# Open Zed with configuration files
alias zconfig='zed ~/.config'

# Quick edit of Zsh configuration
alias zedzsh='zed ~/.zshrc'

# Quick edit of Zed configuration
alias zedconfig='zed ~/.config/zed'
```

### Integration with Git

Configure Zed as your default Git editor:

```bash
# Set Zed as default editor for Git
git config --global core.editor "zed --wait"

# Verify the setting
git config --global core.editor
# Should return: zed --wait
```

**Usage:**
```bash
# Now Git will open Zed for commit messages
git commit
```

### Desktop Integration

Create desktop shortcut:

```bash
# Create desktop entry
cat > ~/.local/share/applications/zed.desktop << EOF
[Desktop Entry]
Name=Zed Editor
Comment=High-performance, multiplayer code editor
Exec=/home/$(whoami)/.local/bin/zed %F
Icon=/home/$(whoami)/.local/zed.app/icon.png
Terminal=false
Type=Application
Categories=Development;IDE;TextEditor;
Keywords=editor;code;ide;development;
StartupNotify=true
MimeType=text/plain;inode/directory;
EOF

# Update desktop database
update-desktop-database ~/.local/share/applications/
```

### Shell Completions

Enable tab completion for Zed commands:

```bash
# For Zsh (if supported)
zed --generate-completion zsh > ~/.zsh/completions/_zed

# Add to ~/.zshrc
fpath=(~/.zsh/completions $fpath)
autoload -U compinit
compinit

# For Bash
zed --generate-completion bash | sudo tee /etc/bash_completion.d/zed
```

## Troubleshooting

### Common Issues & Solutions

#### Issue 1: "zed: command not found"
```bash
# Check if binary exists
ls -la ~/.local/zed.app/bin/zed

# Check PATH variable
echo $PATH | tr ':' '\n' | grep local

# Solution: Ensure PATH includes ~/.local/bin
export PATH="$HOME/.local/bin:$PATH"
source ~/.zshrc
```

#### Issue 2: Permission Denied
```bash
# Check permissions
ls -la ~/.local/bin/zed

# Make executable
chmod +x ~/.local/zed.app/bin/zed
chmod +x ~/.local/bin/zed
```

#### Issue 3: Symbolic Link Broken
```bash
# Check link target
ls -la ~/.local/bin/zed

# Recreate link
rm ~/.local/bin/zed
ln -sf /home/$(whoami)/.local/zed.app/bin/zed ~/.local/bin/zed
```

#### Issue 4: Multiple Zed Installations
```bash
# Find all Zed installations
which -a zed

# Remove duplicates
sudo rm /usr/bin/zed 2>/dev/null
sudo rm /usr/local/bin/zed 2>/dev/null

# Keep only the one in ~/.local/bin
```

### Debugging Commands

```bash
# 1. Full PATH inspection
echo "Current PATH:"
echo $PATH | tr ':' '\n' | nl

# 2. Check all possible zed locations
echo "Searching for zed:"
find /home/$(whoami) /usr/local /usr -name "zed" -type f 2>/dev/null

# 3. Check shell configuration
echo "Shell config files:"
ls -la ~/.*rc ~/.zshrc ~/.bashrc 2>/dev/null

# 4. Test direct execution
echo "Testing direct execution:"
/home/$(whoami)/.local/zed.app/bin/zed --version
```

### Log File Location

Zed stores logs that can help with debugging:

```bash
# View Zed logs
cat ~/.local/share/zed/logs/*.log

# Clear old logs
rm ~/.local/share/zed/logs/*.log 2>/dev/null
```

## Uninstallation

### Remove Zed Completely

```bash
# 1. Remove the application
rm -rf ~/.local/zed.app

# 2. Remove symbolic links
rm ~/.local/bin/zed
sudo rm /usr/local/bin/zed 2>/dev/null

# 3. Remove configuration files
rm -rf ~/.config/zed
rm -rf ~/.local/share/zed

# 4. Remove desktop entry
rm ~/.local/share/applications/zed.desktop 2>/dev/null

# 5. Remove from PATH (edit shell config)
# Remove the line: export PATH="$HOME/.local/bin:$PATH"
# from ~/.zshrc or ~/.bashrc
```

### Verify Complete Removal

```bash
# Check if Zed is still accessible
which zed  # Should return nothing

# Check if files still exist
ls -la ~/.local/zed.app 2>/dev/null || echo "Zed removed successfully"

# Check running processes
ps aux | grep zed
```

## Performance Tips

### Optimize Startup Time

```bash
# Add to ~/.zshrc or ~/.bashrc
alias zed='zed --disable-gpu-sandbox'  # May improve startup on some systems

# Use async loading for shell integration
if command -v zed >/dev/null; then
    # Preload in background
    (zed --version &>/dev/null &)
fi
```

### Memory Optimization

```bash
# Monitor Zed memory usage
alias zedmem='ps aux | grep zed | grep -v grep'

# Limit cache size (add to Zed settings)
# In Zed: Open Settings (Ctrl+,) and add:
# {
#   "cache_size_limit": 1073741824  # 1GB in bytes
# }
```

## Integration Examples

### With VS Code Tasks

Create `.vscode/tasks.json`:
```json
{
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Open in Zed",
            "type": "shell",
            "command": "zed ${fileDirname}",
            "problemMatcher": []
        }
    ]
}
```

### With Makefile

```makefile
# Makefile example
.PHONY: edit
edit:
    zed .

.PHONY: edit-config
edit-config:
    zed Makefile
```

### With Python Scripts

```python
# python_zed_launcher.py
import subprocess
import os

def open_in_zed(path):
    """Open a path in Zed editor"""
    try:
        subprocess.run(['zed', path], check=True)
        return True
    except FileNotFoundError:
        print("Zed not found. Please install from https://zed.dev")
        return False

# Usage
if __name__ == "__main__":
    open_in_zed(os.getcwd())
```

## Community Resources

- **Official Documentation**: [zed.dev/docs](https://zed.dev/docs)
- **GitHub Repository**: [github.com/zed-industries/zed](https://github.com/zed-industries/zed)
- **Community Forum**: [community.zed.dev](https://community.zed.dev)
- **GitHub Issues**: [Report Bugs](https://github.com/zed-industries/zed/issues)

## Contributing

Found an issue or have an improvement?

1. Check existing issues on GitHub
2. Fork the repository
3. Create a feature branch
4. Submit a pull request

---

## Quick Reference Card

```bash
# Installation
curl -fsSL https://zed.dev/install.sh | sh

# Configuration
ln -sf ~/.local/zed.app/bin/zed ~/.local/bin/zed
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# Verification
which zed          # Should show path
zed --version      # Should show version
zed .              # Should open current directory

# Troubleshooting
find ~ -name "zed" -type f 2>/dev/null  # Find installation
echo $PATH | tr ':' '\n'                # Check PATH
```

---

**Last Updated**: January 2025  
**Tested On**: Ubuntu 22.04 LTS, Ubuntu 24.04 LTS, WSL2  
**Zed Version**: 1.0.0+  

*Happy coding with Zed! If you encounter any issues, please check the troubleshooting section or visit the community forum.*
