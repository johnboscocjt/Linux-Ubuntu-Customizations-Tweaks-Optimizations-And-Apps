# Ubuntu Zsh & Git Plugin Setup Guide (2025)

This guide provides a complete walkthrough for setting up Zsh with Git integration, Autosuggestions, and Syntax Highlighting on Ubuntu in 2025.

## Overview

This installation configures:
- **Zsh**: A powerful shell alternative to Bash
- **Oh My Zsh**: A framework for managing Zsh configuration
- **Git Plugin**: Built-in Git aliases and status information
- **Autosuggestions**: Gray suggestions based on your command history
- **Syntax Highlighting**: Color-coded command validation

## Prerequisites

Ensure you have:
- Ubuntu 20.04, 22.04, or 24.04 (also works on WSL2)
- Basic familiarity with terminal commands
- Internet connection

## Installation Steps

### 1. Install Prerequisites

Update your package list and install required tools:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install zsh git curl wget fonts-powerline -y
```

**Note:** `fonts-powerline` ensures proper icon display in prompts.

### 2. Install Oh My Zsh

Install the Oh My Zsh framework:

```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

When prompted to change your default shell to Zsh, type **Y** (yes).

**Alternative method** (if curl fails):
```bash
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 3. Install Community Plugins

#### A. Zsh Autosuggestions
Clone the autosuggestions plugin:

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

#### B. Zsh Syntax Highlighting
Clone the syntax highlighting plugin:

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git \
  ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### 4. Configure `.zshrc`

Edit your Zsh configuration file:

```bash
nano ~/.zshrc
```

#### A. Set ZSH Theme (Optional but Recommended)
Find the `ZSH_THEME` line and set it to:

```bash
ZSH_THEME="agnoster"  # Clean and informative theme
```

**For basic terminals** (without powerline fonts):
```bash
ZSH_THEME="robbyrussell"  # Default theme
```

#### B. Configure Plugins
Find the `plugins=(...)` line and update it:

```bash
# Order matters: syntax-highlighting must be last
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)

# This line must come AFTER the plugins list
source $ZSH/oh-my-zsh.sh
```

**Save and exit:**
- Press `Ctrl+X`
- Press `Y` to confirm
- Press `Enter` to keep the filename

### 5. Apply Changes

Reload your configuration without restarting the terminal:

```bash
source ~/.zshrc
```

Or open a new terminal session for changes to take effect.

## Verification

Check everything is working:

```bash
# Verify Zsh is default shell
echo $SHELL
# Should return: /usr/bin/zsh

# Verify plugins are loaded
zsh --version
```

## How to Use

### Git Plugin Shortcuts

| Alias | Command | Description |
|-------|---------|-------------|
| `gst` | `git status` | Check repository status |
| `gaa` | `git add --all` | Stage all changes |
| `gcmsg "msg"` | `git commit -m "msg"` | Commit with message |
| `gp` | `git push` | Push to remote |
| `gl` | `git pull` | Pull from remote |
| `gco` | `git checkout` | Switch branches |
| `gcm` | `git checkout main` | Switch to main branch |
| `gcb` | `git checkout -b` | Create and switch to new branch |
| `gd` | `git diff` | Show changes |
| `glog` | `git log --oneline` | Compact log view |

### Plugin Features

#### Autosuggestions
- **Gray text** appears as you type, showing command suggestions
- **Accept suggestion**: Press `→` (right arrow) or `End` key
- **Partial accept**: Press `Ctrl+→` to accept word-by-word

#### Syntax Highlighting
- **Green**: Valid command
- **Red**: Invalid command
- **Blue**: Shell built-in or alias

### Additional Tips

1. **Tab Completion**: Type partial command and press `Tab` for suggestions
2. **Theme Customization**: Edit `~/.oh-my-zsh/themes/agnoster.zsh-theme`
3. **Update Oh My Zsh**:
   ```bash
   omz update
   ```

## Troubleshooting

### Common Issues

#### 1. "Plugin not found" error
```bash
# Verify plugin directories exist
ls ~/.oh-my-zsh/custom/plugins/
# Should show: zsh-autosuggestions  zsh-syntax-highlighting

# Check .zshrc plugin order
grep -n "plugins=" ~/.zshrc
```

#### 2. Icons/characters display as boxes
Install powerline fonts:
```bash
# For Ubuntu
sudo apt install fonts-powerline -y

# For other systems, download manually:
# https://github.com/powerline/fonts
```

#### 3. Autosuggestions not showing
Check if plugin is loaded:
```bash
# Add this to ~/.zshrc if missing
source ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions/zsh-autosuggestions.zsh
```

#### 4. Syntax highlighting colors wrong
Ensure proper plugin order in `.zshrc`:
```bash
# CORRECT order (syntax-highlighting LAST)
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)

# WRONG order (won't work properly)
plugins=(zsh-syntax-highlighting git zsh-autosuggestions)
```

#### 5. Slow terminal startup
Disable unused plugins or use lighter theme:
```bash
ZSH_THEME="simple"  # Faster alternative
```

### Reset Configuration

If something breaks:
```bash
# Backup current config
cp ~/.zshrc ~/.zshrc.backup

# Restore default
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc

# Re-apply changes
source ~/.zshrc
```

## Advanced Customization

### Add Custom Aliases
Add to `~/.zshrc`:
```bash
# Custom aliases section
alias update='sudo apt update && sudo apt upgrade -y'
alias ll='ls -la'
alias cls='clear'
alias zshconfig='nano ~/.zshrc'
alias ohmyzsh='nano ~/.oh-my-zsh'
```

### Change Prompt Appearance
Edit `~/.zshrc`:
```bash
# Show username
export DEFAULT_USER="$(whoami)"

# Enable colors
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
```

## Maintenance

### Update All Components
```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Update Oh My Zsh
omz update

# Update plugins
cd ~/.oh-my-zsh/custom/plugins/zsh-autosuggestions && git pull
cd ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting && git pull
```

### Uninstall
```bash
# Remove Oh My Zsh
uninstall_oh_my_zsh

# Switch back to Bash
chsh -s $(which bash)

# Remove Zsh
sudo apt remove --purge zsh -y
```

## Resources

- [Oh My Zsh GitHub](https://github.com/ohmyzsh/ohmyzsh)
- [Zsh Documentation](http://zsh.sourceforge.net/Doc/)
- [Powerline Fonts](https://github.com/powerline/fonts)
- [Zsh Plugin List](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins)

---

**Last Updated**: January 2025  
**Tested On**: Ubuntu 22.04 LTS & 24.04 LTS  
**Author**: Ubuntu Documentation Community  

*Happy coding with your enhanced terminal! 🚀*
