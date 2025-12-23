# Powerlevel10k Theme Reconfiguration Guide

## How to Reconfigure Powerlevel10k

### Method 1: Interactive Wizard (Recommended)
Run the interactive configuration wizard anytime:

```bash
p10k configure
```

This will launch the step-by-step configuration menu with all visual options.

### Method 2: Quick Reset
If you want to start fresh:

```bash
# Backup current configuration
cp ~/.p10k.zsh ~/.p10k.zsh.backup.$(date +%Y%m%d)

# Re-run the wizard
exec zsh
# Then answer "y" when asked to run configuration wizard
# Or manually run: p10k configure
```

## Complete Configuration Options

### Visual Style Choices

#### 1. **Prompt Style** (First Question)
Choose your overall layout:

```
[1] Lean
    → Minimal, single-line prompt
    → Clean, modern look
    → Example: ~/projects ❯

[2] Classic
    → Two-line prompt (most popular)
    → Shows context on first line
    → Example: user@host ~/projects
                 ❯

[3] Rainbow
    → Colorful segments like original screenshot
    → Each segment has different color
    → Most visually striking

[4] Pure
    → Inspired by Pure prompt
    → Minimal with Git integration
    → Shows only when needed

[5] Lean (8 lines)
    → Lean style with detailed status
    → Shows more information
```

**Recommendation**: Choose **3 (Rainbow)** for the most colorful, segmented look.

#### 2. **Character Set** (Second Question)
```
[1] Unicode (recommended)
    → Uses icons and special characters: ❯  ⚡ ✓
    → Requires Nerd Fonts
    → Modern, beautiful appearance

[2] ASCII
    → Uses only basic characters: > | +
    → Compatible with all terminals
    → Less visually appealing
```

#### 3. **Prompt Height**
```
[1] One line
    → Compact, more screen space
    → Shows less information

[2] Two lines
    → More room for information
    → Clear separation of context
```

#### 4. **Prompt Connection**
How segments connect to each other:

```
[1] Angled: 
    → Sharp, modern connections
    → Powerline style
    → Most popular choice

[2] Round: ⮀
    → Smooth, rounded connections
    → Softer appearance

[3] Straight: │
    → Vertical separators
    → Clean, minimal

[4] Disconnected
    → No connections between segments
    → Space separated
```

#### 5. **Prompt Heads**
Left side of prompt segments:

```
[1] Sharp: 
    → Angled left side
    → Consistent with connections

[2] Round: ⮂
    → Rounded left side
    → Softer look

[3] Blurred
    → Faded edges
    → Modern gradient effect
```

#### 6. **Prompt Tails**
Right side of prompt segments:

```
[1] Sharp: 
    → Angled right side
    → Most common choice

[2] Round: ⮀
    → Rounded right side

[3] Blurred
    → Gradient fade out
```

#### 7. **Prompt Flow**
How information flows in prompt:

```
[1] Continuous
    → Segments flow into each other
    → Traditional powerline

[2] Framed
    → Each segment has borders
    → Box-like appearance

[3] Sparse
    → More space between segments
    → Airy, minimal look
```

### Color Scheme Options

#### 8. **Color Scheme**
Choose your overall color palette:

```
[1] Dark
    → Optimized for dark backgrounds
    → High contrast colors

[2] Light
    → Optimized for light backgrounds
    → Softer colors

[3] 256 colors
    → Uses extended terminal colors
    → More color options

[4] Original Powerlevel9k
    → Legacy color scheme
    → Familiar to Powerlevel9k users
```

#### 9. **Contrast**
Adjust brightness contrast:

```
[1] High
    → Bright, vivid colors
    → Best for visibility

[2] Medium
    → Balanced colors
    → Good for most setups

[3] Low
    → Muted, subtle colors
    → Easy on the eyes
```

#### 10. **Color Temperature**
```
[1] Warm
    → Red/orange/yellow tones
    → Cozy feel

[2] Neutral
    → Balanced color temperature
    → Standard choice

[3] Cool
    → Blue/green/purple tones
    → Modern, technical feel
```

### Icon Preferences

#### 11. **Icons**
```
[1] Many icons
    → Shows icons for everything
    → Very visual
    → Example: 📁 🐍 ⚡ 

[2] Few icons
    → Only essential icons
    → Cleaner look
    → Example: ~/project >

[3] No icons
    → Text only
    → Maximum compatibility
```

#### 12. **Icon Style**
```
[1] Filled
    → Solid icons: ● ■ ▲
    → Bold appearance

[2] Outlined
    → Hollow icons: ○ □ △
    → Light, airy feel

[3] Mix
    → Combination of both
    → Visual hierarchy
```

### Time Display

#### 13. **Current Time**
```
[1] 12-hour format
    → Example: 2:30 PM
    → AM/PM notation

[2] 24-hour format
    → Example: 14:30
    → Military/International time

[3] Relative time
    → Example: 5m ago, 2h ago
    → Dynamic time display

[4] No time
    → Don't show time
    → More screen space
```

#### 14. **Time Format**
```
[1] HH:MM
    → Example: 14:30
    → Hours and minutes

[2] HH:MM:SS
    → Example: 14:30:45
    → Includes seconds

[3] Smart
    → Shows seconds only when needed
    → Adaptive display
```

### Git Integration Settings

#### 15. **Git Status Icons**
```
[1] Detailed
    → Shows all Git states
    → Example:  main +2 ~1 -3 ⇡2 ⇣1

[2] Simple
    → Shows only basic status
    → Example:  main *

[3] No status
    → Shows only branch name
    → Minimalist
```

#### 16. **Git Prompt Location**
```
[1] Right prompt
    → Git info on right side
    → Keeps left prompt clean

[2] Left prompt
    → Git info on left side
    → Traditional location

[3] Auto
    → Moves based on content
    → Smart placement
```

### Advanced Visual Options

#### 17. **Transient Prompt**
```
Enable transient prompt? (y/n)
```
- **Yes**: Previous prompt disappears when you start typing
- **No**: All prompts remain visible

#### 18. **Instant Prompt**
```
Enable instant prompt? (y/n)
```
- **Yes**: Shows prompt immediately while loading
- **No**: Waits for full initialization

#### 19. **Show Command Duration**
```
Show command execution time? (y/n)
```
- **Yes**: Shows how long commands took
- **No**: Don't show execution time

#### 20. **Show Exit Code**
```
Show last command exit code? (y/n)
```
- **Yes**: Shows ✓ for success, ✗ for failure
- **No**: Don't show exit status

## Manual Configuration File Editing

If you want to fine-tune beyond the wizard, edit `~/.p10k.zsh`:

```bash
# Open the configuration file
nano ~/.p10k.zsh
```

### Key Sections to Customize:

#### 1. **Prompt Elements Order**
```bash
# Left prompt elements (line 1)
typeset -g POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(
  os_icon                 #   OS logo
  dir                     # 📁 Current directory
  vcs                     #   Git status
  context                 # user@hostname
  # virtualenv            # 🐍 Python environment
  # aws                   #   AWS profile
  # kubecontext           # ☸️  Kubernetes
  newline                 # Line break
  prompt_char             # ❯ Prompt symbol
)

# Right prompt elements
typeset -g POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(
  status                  # ✓/✗ Exit code
  command_execution_time  # 2s Execution time
  background_jobs         # ⏳ Background jobs
  time                    # 🕒 Current time
  # battery               # 🔋 Battery level
  # ram                   # 🐏 RAM usage
)
```

#### 2. **Color Customization**
```bash
# Directory colors
typeset -g POWERLEVEL9K_DIR_FOREGROUND=6     # Cyan text
typeset -g POWERLEVEL9K_DIR_BACKGROUND=4      # Blue background

# Git colors
typeset -g POWERLEVEL9K_VCS_CLEAN_FOREGROUND=2    # Green
typeset -g POWERLEVEL9K_VCS_MODIFIED_FOREGROUND=3 # Yellow
typeset -g POWERLEVEL9K_VCS_UNTRACKED_FOREGROUND=1 # Red

# Time colors
typeset -g POWERLEVEL9K_TIME_FOREGROUND=0     # Black text
typeset -g POWERLEVEL9K_TIME_BACKGROUND=7     # White background
```

#### 3. **Icon Customization**
```bash
# Change icons
typeset -g POWERLEVEL9K_OS_ICON_CONTENT_EXPANSION=''
typeset -g POWERLEVEL9K_DIR_ICON='📁'
typeset -g POWERLEVEL9K_HOME_ICON='🏠'
typeset -g POWERLEVEL9K_HOME_SUB_ICON='📂'
```

#### 4. **Segment Separators**
```bash
# Connection between segments
typeset -g POWERLEVEL9K_LEFT_SEGMENT_SEPARATOR=''
typeset -g POWERLEVEL9K_RIGHT_SEGMENT_SEPARATOR=''
typeset -g POWERLEVEL9K_LEFT_SUBSEGMENT_SEPARATOR=''
typeset -g POWERLEVEL9K_RIGHT_SUBSEGMENT_SEPARATOR=''
```

## Theme Presets

### Popular Theme Combinations

#### 1. **Rainbow Powerline** (Most Popular)
```bash
# Run wizard and choose:
# Style: 3 (Rainbow)
# Character Set: 1 (Unicode)
# Height: 2 (Two lines)
# Connection: 1 (Angled)
# Colors: 1 (Dark)
# Icons: 1 (Many icons)
```

#### 2. **Minimal Dark**
```bash
# Wizard choices:
# Style: 1 (Lean)
# Character Set: 1 (Unicode)
# Height: 1 (One line)
# Connection: 4 (Disconnected)
# Colors: 1 (Dark)
# Icons: 3 (No icons)
```

#### 3. **Retro Console**
```bash
# Wizard choices:
# Style: 2 (Classic)
# Character Set: 2 (ASCII)
# Height: 2 (Two lines)
# Connection: 3 (Straight)
# Colors: 4 (Original)
# Icons: 3 (No icons)
```

#### 4. **Modern Developer**
```bash
# Wizard choices:
# Style: 3 (Rainbow)
# Character Set: 1 (Unicode)
# Height: 1 (One line)
# Connection: 1 (Angled)
# Colors: 1 (Dark)
# Icons: 1 (Many icons)
# Time: 4 (No time)
# Git: 1 (Detailed)
```

## Live Preview

Test your changes without saving:

```bash
# Reload configuration to see changes
source ~/.p10k.zsh

# Or reload Powerlevel10k specifically
p10k reload
```

## Quick Configuration Scripts

Create shortcuts for different themes:

### Create Theme Switch Commands
```bash
# Add to ~/.zshrc
alias theme-rainbow='sed -i "s/POWERLEVEL9K_MODE=.*/POWERLEVEL9K_MODE=\"rainbow\"/" ~/.p10k.zsh && p10k reload'
alias theme-lean='sed -i "s/POWERLEVEL9K_MODE=.*/POWERLEVEL9K_MODE=\"lean\"/" ~/.p10k.zsh && p10k reload'
alias theme-console='sed -i "s/POWERLEVEL9K_MODE=.*/POWERLEVEL9K_MODE=\"compatible\"/" ~/.p10k.zsh && p10k reload'

# Switch color schemes
alias colors-dark='sed -i "s/typeset -g POWERLEVEL9K_BACKGROUND=.*/typeset -g POWERLEVEL9K_BACKGROUND=0/" ~/.p10k.zsh && p10k reload'
alias colors-light='sed -i "s/typeset -g POWERLEVEL9K_BACKGROUND=.*/typeset -g POWERLEVEL9K_BACKGROUND=15/" ~/.p10k.zsh && p10k reload'
```

## Troubleshooting Visual Issues

### Colors Not Working
```bash
# Check terminal color support
echo $TERM  # Should be xterm-256color or similar

# Set if needed
export TERM=xterm-256color

# Test colors
for i in {0..255}; do printf "\x1b[38;5;${i}mcolor${i}\x1b[0m "; done
```

### Icons Missing
```bash
# Test icon display
echo "Icons:  ⚡ ✓ ✗  🐍 ⬢ ☸️ "

# If boxes appear, fix fonts:
# 1. Install MesloLGS NF font
# 2. Set terminal to use it
# 3. Restart terminal
```

### Prompt Too Slow
```bash
# Disable slow features
# In ~/.p10k.zsh, comment out:
#   - nvm
#   - node_version  
#   - go_version
#   - rust_version
#   - java_version

# Enable instant prompt (already in config)
# This shows prompt immediately while loading
```

## Save and Share Your Theme

Export your configuration:
```bash
# Backup your theme
cp ~/.p10k.zsh ~/my-theme.zsh

# Share with others
cat ~/.p10k.zsh | grep -A5 -B5 "POWERLEVEL9K_"

# Reset to factory defaults
rm ~/.p10k.zsh
exec zsh  # Will recreate with wizard
```

## Final Tips

1. **Take Screenshots** of different configurations to compare
2. **Test in different lighting** conditions (day/night)
3. **Consider accessibility** - ensure good contrast for readability
4. **Keep it functional** - don't sacrifice usability for aesthetics
5. **Regularly update** - Powerlevel10k gets frequent improvements

---

**Need Help?**
- Run `p10k help` for command reference
- Visit: https://github.com/romkatv/powerlevel10k
- Ask in: https://github.com/romkatv/powerlevel10k/discussions

*Enjoy customizing your perfect terminal! 🎨*
