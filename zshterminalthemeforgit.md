# Zsh Terminal Customization Tutorial (Powerlevel10k)

## Overview
This guide will transform your terminal into a professional, information-rich environment with powerline-style segments, icons, and Git integration—matching the aesthetic of modern development workflows.

![Powerlevel10k Terminal Example](https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/prompt-styles-high-contrast.png)

## Prerequisites

### System Requirements
- **Zsh** installed (`zsh --version` should return 5.8 or higher)
- **Git** installed (`git --version`)
- **Curl** or **Wget** for downloading scripts

### Terminal Requirements
Choose one of these modern terminal emulators:

| Platform | Recommended Terminal | Alternative |
|----------|---------------------|-------------|
| **macOS** | [iTerm2](https://iterm2.com/) | Terminal.app |
| **Linux** | [GNOME Terminal](https://wiki.gnome.org/Apps/Terminal) | [Konsole](https://konsole.kde.org/) |
| **Windows** | [Windows Terminal](https://aka.ms/terminal) | [Alacritty](https://alacritty.org/) |

**Verify installation:**
```bash
# Check Zsh
zsh --version  # Should be 5.8+

# Check Git
git --version  # Should be 2.20+

# Check Curl
curl --version  # Optional but recommended
```

## Installation Guide

### Step 1: Install Oh My Zsh (If Not Already Installed)

Oh My Zsh is a community-driven framework for managing Zsh configuration.

```bash
# Install using curl (recommended)
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

# Or using wget (alternative)
sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

**During installation:**
- Press **Enter** to continue
- Type **Y** when asked to change your default shell to Zsh
- Type **Y** if asked to backup existing `.zshrc` file

**Verify installation:**
```bash
echo $ZSH  # Should show: /home/yourusername/.oh-my-zsh
```

### Step 2: Install Powerlevel10k Theme

Powerlevel10k is a fast, highly customizable theme with built-in configuration wizard.

```bash
# Clone the repository (--depth=1 for faster download)
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git \
  ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

**Alternative installation methods:**

```bash
# Method 2: Manual download
git clone https://github.com/romkatv/powerlevel10k.git \
  ~/.oh-my-zsh/custom/themes/powerlevel10k

# Method 3: Using antigen (if you use antigen)
antigen theme romkatv/powerlevel10k
```

### Step 3: Configure the Theme

Edit your Zsh configuration file:

```bash
# Using nano (beginner-friendly)
nano ~/.zshrc

# Using vim
vim ~/.zshrc

# Using code (if VS Code is installed)
code ~/.zshrc
```

**Find and modify the theme line:**
```bash
# Look for this line (around line 11)
ZSH_THEME="robbyrussell"

# Change it to:
ZSH_THEME="powerlevel10k/powerlevel10k"
```

**Example of correct placement:**
```bash
# Lines to keep in your .zshrc
export ZSH="$HOME/.oh-my-zsh"
ZSH_THEME="powerlevel10k/powerlevel10k"
plugins=(git)
source $ZSH/oh-my-zsh.sh
```

**Save and exit:**
- **nano**: `Ctrl+X`, then `Y`, then `Enter`
- **vim**: `:wq` then `Enter`
- **VS Code**: `Ctrl+S` then close window

### Step 4: Install Compatible Fonts

Powerlevel10k requires Nerd Fonts to display icons properly.

#### A. Install MesloLGS Nerd Font (Recommended)

**Linux (Ubuntu/Debian):**
```bash
# Download and install the font
mkdir -p ~/.local/share/fonts
cd ~/.local/share/fonts

# Download all MesloLGS variants
curl -L -o "MesloLGS NF Regular.ttf" \
  "https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Regular.ttf"

curl -L -o "MesloLGS NF Bold.ttf" \
  "https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold.ttf"

curl -L -o "MesloLGS NF Italic.ttf" \
  "https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Italic.ttf"

curl -L -o "MesloLGS NF Bold Italic.ttf" \
  "https://github.com/romkatv/powerlevel10k-media/raw/master/MesloLGS%20NF%20Bold%20Italic.ttf"

# Update font cache
fc-cache -f -v
```

**macOS:**
```bash
# Download and install via Homebrew
brew tap homebrew/cask-fonts
brew install --cask font-meslo-lg-nerd-font

# Or manually download from:
# https://github.com/romkatv/powerlevel10k#manual-font-installation
```

**Windows (WSL2):**
1. Download fonts from: https://github.com/ryanoasis/nerd-fonts/releases
2. Install "MesloLGM NF" by right-clicking each `.ttf` file → "Install"
3. Configure Windows Terminal to use the font (see below)

#### B. Configure Terminal to Use the Font

**GNOME Terminal (Ubuntu):**
1. Open Terminal
2. Edit → Preferences
3. Select your profile
4. Click on "Text" tab
5. Uncheck "Custom font"
6. Type "MesloLGS NF" in font box
7. Set size to 12-14

**iTerm2 (macOS):**
1. iTerm2 → Preferences (⌘+,)
2. Profiles → Text
3. Font → Change Font
4. Select "MesloLGS NF Regular"
5. Size: 12-14

**Windows Terminal:**
1. Open Settings (Ctrl+,)
2. Select your profile (e.g., Ubuntu)
3. Appearance → Text → Font face
4. Choose "MesloLGS NF"
5. Font size: 11-13

#### C. Verify Font Installation
```bash
# List available fonts (Linux)
fc-list | grep -i "meslo"

# Expected output (Linux):
# /home/user/.local/share/fonts/MesloLGS NF Bold Italic.ttf: MesloLGS NF:style=Bold Italic
```

### Step 5: Run the Configuration Wizard

Apply the configuration and start the interactive setup:

```bash
# Reload Zsh configuration
source ~/.zshrc

# Or open a new terminal window/tab
```

**The Powerlevel10k Configuration Wizard will automatically start:**

![Powerlevel10k Wizard](https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/prompt-choices.png)

#### Wizard Options Explained

You'll be prompted with several questions:

1. **"Does this look like a diamond (rotated square)?"**
   - **Yes (y)**: Fonts are working correctly
   - **No (n)**: Fonts need fixing (go back to Step 4)

2. **"Does this look like a lock?"**
   - **Yes (y)**: Icons are displaying properly
   - **No (n)**: Check font installation

3. **"Prompt Style"** (Choose based on preference):
   - **1**: Lean - Minimal, single line
   - **2**: Classic - Two lines, detailed
   - **3**: Rainbow - Colorful segments
   - **4**: Pure - Inspired by Pure prompt

4. **"Character Set"**:
   - **1**: Unicode - Modern icons
   - **2**: ASCII - Compatibility mode

5. **"Show current time?"**:
   - **1**: 12-hour format
   - **2**: 24-hour format
   - **3**: No time display

6. **"Prompt Separators"**:
   - **1**: Angled (>)
   - **2**: Vertical (│)
   - **3**: Round (⮀)

**Pro Tip:** Press `Ctrl+C` at any time to accept defaults.

### Step 6: Customize Further (Optional)

After the wizard completes, your configuration is saved to `~/.p10k.zsh`. You can customize it further:

```bash
# Edit Powerlevel10k configuration
nano ~/.p10k.zsh

# Or reconfigure anytime
p10k configure
```

#### Popular Customizations:

**Change prompt elements order:**
```bash
# In ~/.p10k.zsh, search for "typeset"
# Change the order of POWERLEVEL9K_LEFT_PROMPT_ELEMENTS
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
  os_icon                 # OS icon
  dir                     # Current directory
  vcs                     # Git status
  virtualenv              # Python virtual environment
  context                 # User@hostname
  newline                 # New line
  prompt_char             # Prompt symbol
)
```

**Enable/disable right prompt elements:**
```bash
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
  status                  # Exit code of last command
  command_execution_time  # Duration of last command
  background_jobs         # Background jobs indicator
  time                    # Current time
  # battery              # Battery level (laptops)
  # ram                  # RAM usage
  # load                 # CPU load
)
```

**Change colors:**
```bash
# Change directory color
typeset -g POWERLEVEL9K_DIR_FOREGROUND=6  # Cyan

# Change Git clean color
typeset -g POWERLEVEL9K_VCS_CLEAN_FOREGROUND=2  # Green

# Change Git dirty color
typeset -g POWERLEVEL9K_VCS_MODIFIED_FOREGROUND=3  # Yellow
```

## Features Showcase

### Visual Elements

| Element | Icon | Description |
|---------|------|-------------|
| **Directory** | 📁 | Current folder with truncation |
| **Git Branch** |  | Current branch name |
| **Git Status** | ✔/✘ | Clean/Dirty repository |
| **Python** | 🐍 | Virtual environment |
| **Node.js** | ⬢ | Node version |
| **Time** | 🕒 | Current time |
| **Status** | ✓/✗ | Last command exit code |

### Keyboard Shortcuts

| Shortcut | Action |
|----------|---------|
| `Ctrl+Shift+Space` | Accept autosuggestion |
| `Ctrl+X Ctrl+E` | Edit command in editor |
| `Ctrl+R` | Search command history |
| `Ctrl+T` | Transpose characters |
| `Alt+.` | Insert last argument |
| `Ctrl+U` | Clear line before cursor |

### Git Integration Features

```bash
# Shows in prompt:
#  main ±2  3
# Meaning: Branch "main", 2 modified files, 3 commits ahead

# Common Git operations become visual:
cd project/          # Shows Git status automatically
git add file.txt     # Status updates in real-time
git commit -m "msg"  # Shows commit progress
```

## Troubleshooting

### Common Issues & Solutions

#### 1. Fonts Not Displaying Properly
**Symptoms:** Boxes instead of icons
```bash
# Check font installation
echo "\ue0b0 \u00b1 \ue0a0 \u27a6 \u2718 \u26a1"

# Expected:  ±  ➦ ✘ ⚡
# If boxes appear, reinstall fonts
```

**Fix:**
```bash
# Reinstall fonts
rm -rf ~/.local/share/fonts/Meslo*
# Repeat Step 4
```

#### 2. Wizard Doesn't Start
```bash
# Manually trigger configuration
p10k configure

# Or check theme is set correctly
grep "ZSH_THEME" ~/.zshrc
# Should return: ZSH_THEME="powerlevel10k/powerlevel10k"
```

#### 3. Slow Prompt
```bash
# Check performance
time (p10k reload)

# Disable slow segments in ~/.p10k.zsh
# Comment out: nvm, node_version, etc.
```

#### 4. Reset to Defaults
```bash
# Backup current config
cp ~/.p10k.zsh ~/.p10k.zsh.backup

# Re-run wizard
p10k configure
```

### Performance Optimization

```bash
# Disable unnecessary features
# Add to ~/.zshrc BEFORE sourcing oh-my-zsh.sh
DISABLE_UNTRACKED_FILES_DIRTY="true"  # Faster Git status
DISABLE_MAGIC_FUNCTIONS="true"        # Disable URL paste magic
```

## Advanced Customization

### Add Custom Segments

Create custom prompt elements in `~/.zshrc`:

```bash
# Custom weather segment (requires curl)
function prompt_weather() {
  local temp=$(curl -s "wttr.in/?format=%t")
  p10k segment -f blue -t "${temp}"
}

# Add to left prompt
POWERLEVEL9K_LEFT_PROMPT_ELEMENTS+=(weather)
```

### Theme Switching

```bash
# Switch between Powerlevel10k styles
alias prompt-lean='POWERLEVEL9K_MODE="lean" && p10k reload'
alias prompt-rainbow='POWERLEVEL9K_MODE="rainbow" && p10k reload'
alias prompt-classic='POWERLEVEL9K_MODE="classic" && p10k reload'
```

### Plugin Integration

```bash
# Install useful plugins
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

# Update ~/.zshrc plugins line
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

## Maintenance

### Update Components

```bash
# Update Oh My Zsh
omz update

# Update Powerlevel10k
git -C ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k pull

# Update plugins
for plugin in ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/*; do
  git -C $plugin pull 2>/dev/null
done
```

### Backup Configuration

```bash
# Create backup
backup_dir=~/zsh-backup-$(date +%Y%m%d)
mkdir -p $backup_dir
cp ~/.zshrc ~/.p10k.zsh $backup_dir/

# List backup files
ls -la $backup_dir/
```

## Uninstallation

To revert changes:

```bash
# Remove Powerlevel10k
rm -rf ~/.oh-my-zsh/custom/themes/powerlevel10k
rm ~/.p10k.zsh

# Change theme back to default
sed -i 's/ZSH_THEME="powerlevel10k.*"/ZSH_THEME="robbyrussell"/' ~/.zshrc

# Reload configuration
source ~/.zshrc
```

## Resources & References

- **Powerlevel10k GitHub**: https://github.com/romkatv/powerlevel10k
- **Nerd Fonts**: https://www.nerdfonts.com
- **Oh My Zsh Plugins**: https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins
- **Zsh Documentation**: http://zsh.sourceforge.net/Doc/

---

**Version**: 2025.1  
**Compatible With**: Ubuntu 20.04+, macOS 10.15+, WSL2  
**Last Updated**: January 2025  

*Enjoy your beautiful, productive terminal! ✨*
