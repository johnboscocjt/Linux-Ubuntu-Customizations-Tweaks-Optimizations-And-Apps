# Essential Linux Tools & Applications Guide

A curated collection of **useful Linux applications** for productivity, media, system management, and development.

**Video Guide:** [Essential Linux Tools](https://youtu.be/f-txoU7tpGU)

---

## 📖 Table of Contents
- [System Management](#system-management)
- [Media & Graphics](#media--graphics)
- [File Management](#file-management)
- [Development & Terminal Tools](#development--terminal-tools)
- [Network & Connectivity](#network--connectivity)
- [Productivity & Utilities](#productivity--utilities)
- [Security & Privacy](#security--privacy)
- [Container & Package Management](#container--package-management)
- [AI & Machine Learning](#ai--machine-learning)

---

## 🖥️ System Management

### 1. Ananicy-cpp
**Purpose:** Process priority management daemon  
**Description:** Monitors running processes and automatically assigns CPU/IO priorities to improve system responsiveness. Games and interactive apps get higher priority while background tasks are throttled.  
**Installation:**
```bash
git clone https://gitlab.com/ananicy-cpp/ananicy-cpp
cd ananicy-cpp && mkdir build && cd build
cmake .. -DCMAKE_BUILD_TYPE=Release -DENABLE_SYSTEMD=ON
make -j$(nproc) && sudo make install
sudo systemctl enable --now ananicy-cpp
```
**Learn more:** [GitLab Repository](https://gitlab.com/ananicy-cpp/ananicy-cpp)

---

### 2. systemd-oomd
**Purpose:** Out-of-Memory killer daemon  
**Description:** Proactively terminates memory-hungry processes before the system becomes unresponsive. Uses Pressure Stall Information (PSI) to monitor system pressure.  
**Installation:**
```bash
sudo apt install systemd-oomd
sudo systemctl enable --now systemd-oomd.service
```
**Learn more:** [systemd Documentation](https://www.freedesktop.org/software/systemd/man/latest/systemd-oomd.service.html)

---

### 3. Timeshift
**Purpose:** System backup and restore  
**Description:** Creates filesystem snapshots using rsync or BTRFS. Perfect for system recovery after updates or configuration changes.  
**Installation:**
```bash
sudo apt install timeshift
```

---

### 4. BleachBit
**Purpose:** System cleaner  
**Description:** Deletes junk files, cleans cache, and frees disk space. Similar to CCleaner but for Linux.  
**Installation:**
```bash
sudo apt install bleachbit
```

---

### 5. NetPeek
**Purpose:** Network scanner  
**Description:** Simple network scanner that discovers active devices on your local network.  
**Installation:**
```bash
# Available on Flathub
flatpak install flathub com.github.netpeek
```

---

### 6. Easy Effects
**Purpose:** Audio effects processor  
**Description:** Advanced audio equalizer and effects for PipeWire. Enhance your audio experience with equalizers, limiters, and compressors.  
**Installation:**
```bash
sudo apt install easyeffects
```

---

### 7. Audio Sharing
**Purpose:** Network audio streaming  
**Description:** Share your current computer audio playback as an RTSP stream that can be played back by other devices (e.g., using VLC).  
**Learn more:** [GitHub Repository](https://github.com/mikebrady/audio-share)

---

### 8. Monitor
**Purpose:** System resource monitoring  
**Description:** Monitor your CPU, Memory, Disk, Network, and GPU usage, accompanied by a per-app and per-process breakdown of these statistics.  
**Installation:**
```bash
# GNOME System Monitor
sudo apt install gnome-system-monitor

# Mission Center (modern alternative)
flatpak install flathub io.missioncenter.MissionCenter
```

---

### 9. Cloudflare Warp
**Purpose:** VPN/Proxy service  
**Description:** Cloudflare's VPN service for secure and private internet browsing.  
**Installation:**
```bash
curl -fsSL https://pkg.cloudflareclient.com/install | sudo bash
sudo systemctl enable --now warp-svc
```

---

## 🎨 Media & Graphics

### 10. MPV Player
**Purpose:** Video player  
**Description:** Lightweight, powerful video player with extensive customization options and keyboard shortcuts.  
**Installation:**
```bash
sudo apt install mpv
```

---

### 11. HandBrake
**Purpose:** Video converter  
**Description:** Convert videos between different formats, resolutions, and codecs. Batch processing and presets available.  
**Installation:**
```bash
sudo apt install handbrake
```

---

### 12. Upscayl
**Purpose:** Image upscaling  
**Description:** AI-powered image upscaler that enhances image resolution while preserving quality.  
**Installation:**
```bash
flatpak install flathub org.upscayl.Upscayl
```

---

### 13. Converseen
**Purpose:** Batch image processor  
**Description:** Convert, resize, rotate, and flip an infinite number of images with a single click.  
**Installation:**
```bash
sudo apt install converseen
```

---

### 14. Switcheroo
**Purpose:** Image conversion  
**Description:** Simple GUI tool to convert images between formats.  
**Installation:**
```bash
sudo apt install switcheroo
```

---

### 15. Spectacle
**Purpose:** Screenshot tool  
**Description:** KDE's powerful screenshot utility with annotation features.  
**Installation:**
```bash
sudo apt install spectacle
```

---

### 16. Peek
**Purpose:** GIF recorder  
**Description:** Create animated GIFs from screen recordings. Perfect for tutorials and demos.  
**Installation:**
```bash
sudo apt install peek
```

---

### 17. Identity
**Purpose:** Image/Video comparison  
**Description:** Compare multiple versions of an image or video side-by-side.  
**Learn more:** [GitHub Repository](https://github.com/orgs/identity-linux)

---

### 18. Constrict
**Purpose:** Video compression  
**Description:** Compress videos to a chosen file size. No more manual trial-and-error with bitrates.  
**Installation:**
```bash
flatpak install flathub com.github.constrict
```

---

### 19. Audacity
**Purpose:** Audio recorder/editor  
**Description:** Free, open-source audio recording and editing software.  
**Installation:**
```bash
sudo apt install audacity
```

---

## 📁 File Management

### 20. Nemo / Dolphin
**Purpose:** File managers  
**Description:** Feature-rich file managers with built-in terminal integration.  
- **Nemo:** Cinnamon's file manager  
- **Dolphin:** KDE's file manager  

**Installation:**
```bash
# Nemo
sudo apt install nemo

# Dolphin
sudo apt install dolphin
```

**Pro Tip:** Use `Alt + Shift + A` to open a terminal in the current directory (Nemo).

---

### 21. Ventoy
**Purpose:** Bootable USB creator  
**Description:** Create bootable USB drives with multiple ISO files. Just copy ISO files to the USB drive.  
**Installation:**
```bash
wget https://github.com/ventoy/Ventoy/releases/download/v1.0.99/ventoy-1.0.99-linux.tar.gz
tar -xzf ventoy-*.tar.gz
cd ventoy-*
sudo ./VentoyGUI.x86_64
```
**Learn more:** [Official Website](https://www.ventoy.net/)

---

### 22. Impression
**Purpose:** ISO burner  
**Description:** Simple application to burn ISO images to USB drives.  
**Installation:**
```bash
flatpak install flathub org.gnome.Impression
```

---

### 23. Czkawka
**Purpose:** Duplicate file finder  
**Description:** Find and remove duplicate files, empty folders, and similar images.  
**Installation:**
```bash
flatpak install flathub com.github.qarmin.czkawka
```

---

## 💻 Development & Terminal Tools

### 24. Micro Editor
**Purpose:** Terminal text editor  
**Description:** Modern, intuitive terminal editor with syntax highlighting, mouse support, and easy keybindings.  
**Installation:**
```bash
sudo apt install micro
```

---

### 25. Kitty Terminal
**Purpose:** Terminal emulator  
**Description:** Fast, feature-rich GPU-accelerated terminal emulator.  
**Installation:**
```bash
sudo apt install kitty
```

---

### 26. Ghostty
**Purpose:** Terminal emulator  
**Description:** Modern terminal emulator focused on performance and customization.  
**Learn more:** [Official Website](https://ghostty.org/)

---

### 27. Gedit
**Purpose:** Text editor  
**Description:** Simple, lightweight GUI text editor for GNOME.  
**Installation:**
```bash
sudo apt install gedit
```

---

### 28. Bat / Batcat
**Purpose:** Syntax-highlighted file viewer  
**Description:** A `cat` clone with syntax highlighting for reading files. **Note:** This is a read-only viewer, not an editor.  
**Installation:**
```bash
sudo apt install bat
# May be installed as 'batcat' on some systems
```
**Usage:**
```bash
bat config.yaml
# or
batcat config.yaml
```

---

### 29. GitHub Desktop
**Purpose:** Git GUI client  
**Description:** Official GitHub GUI client for managing repositories.  
**Installation:**
```bash
flatpak install flathub io.github.shiftey.Desktop
```

---

### 30. Clapgrep
**Purpose:** PDF content search  
**Description:** Search for text across multiple PDF files in a folder. Find what you're looking for without opening each PDF individually.  
**Learn more:** [GitHub Repository](https://github.com/clapgrep)

---

### 31. Text Pieces
**Purpose:** Text transformation  
**Description:** Convert and transform text with various operations (JSON formatting, base64 encode/decode, etc.).  
**Installation:**
```bash
flatpak install flathub com.github.textpieces
```

---

### 32. Vish
**Purpose:** Bash creator  
**Description:** Tool for creating and managing bash scripts.  
**Learn more:** [GitHub Repository](https://github.com/vish)

---

### 33. Dev Tools for Format
**Purpose:** Development utilities  
**Description:** Tools for code formatting, linting, and development workflow optimization.

---

## 🌐 Network & Connectivity

### 34. KDE Connect
**Purpose:** Phone integration  
**Description:** Connect your Android phone to Linux. Share files, receive notifications, control media, and use your phone as a remote.  
**Installation:**
```bash
sudo apt install kdeconnect
```

---

### 35. Ferdium
**Purpose:** Messaging aggregator  
**Description:** Combine multiple messaging apps (WhatsApp, Telegram, Slack, etc.) into one application.  
**Installation:**
```bash
flatpak install flathub org.ferdium.Ferdium
```

---

### 36. Celeste
**Purpose:** Cloud storage client  
**Description:** Connect to Dropbox, Google Drive, and other cloud services from a single interface.  
**Installation:**
```bash
flatpak install flathub com.celeste
```

---

### 37. Onion Share
**Purpose:** Anonymous file sharing  
**Description:** Share files and host websites on the Tor network.  
**Learn more:** [GitHub Repository](https://github.com/onionshare/onionshare)

---

### 38. Pipeline
**Purpose:** Video downloader  
**Description:** Download videos from YouTube and other platforms.  
**Installation:**
```bash
flatpak install flathub com.github.pipeline
```

---

### 39. Actioneer
**Purpose:** GitHub Actions tracker  
**Description:** Track and monitor your GitHub Actions workflows.  
**Learn more:** [GitHub Repository](https://github.com/actioneer)

---

## 📋 Productivity & Utilities

### 40. Bazaar
**Purpose:** Flatpak manager  
**Description:** GUI for managing Flatpak applications.  
**Installation:**
```bash
flatpak install flathub com.github.bazaar
```

---

### 41. Okular
**Purpose:** PDF viewer  
**Description:** Feature-rich PDF and document viewer with annotation capabilities.  
**Installation:**
```bash
sudo apt install okular
```

---

### 42. Ulauncher
**Purpose:** Application launcher  
**Description:** Fast, customizable application launcher with extensions.  
**Installation:**
```bash
sudo apt install ulauncher
```

---

### 43. Gdebi
**Purpose:** DEB package installer  
**Description:** Simple GUI to install .deb packages with dependency resolution.  
**Installation:**
```bash
sudo apt install gdebi
```

---

### 44. Metadata Cleaner
**Purpose:** Metadata removal  
**Description:** Remove metadata from files to protect privacy.  
**Installation:**
```bash
sudo snap install metadata-cleaner
```

---

### 45. Flatseal
**Purpose:** Flatpak permissions manager  
**Description:** Manage permissions for Flatpak applications.  
**Installation:**
```bash
flatpak install flathub com.github.tchx84.Flatseal
```

---

### 46. Warehouse
**Purpose:** Flatpak management  
**Description:** Simple UI to control complex Flatpak options without using the command line.  
**Installation:**
```bash
flatpak install flathub io.github.flattool.Warehouse
```

---

### 47. Gear Lever
**Purpose:** AppImage manager  
**Description:** Organize and manage AppImage files, generate desktop entries, and update apps in-place.  
**Installation:**
```bash
flatpak install flathub it.mijorus.gearlever
```

---

### 48. Stirling PDF
**Purpose:** PDF manipulation  
**Description:** Self-hosted web application for PDF operations (merge, split, compress, convert). Similar to ilovepdf but self-hosted.  
**Installation:**
```bash
docker run -d -p 8080:8080 frooodle/s-pdf:latest
```
**Learn more:** [GitHub Repository](https://github.com/Stirling-Tools/Stirling-PDF)

---

### 49. Reminders
**Purpose:** Task management  
**Description:** Simple reminder application for tracking tasks and events.  
**Installation:**
```bash
flatpak install flathub com.github.reminders
```

---

### 50. Mousam
**Purpose:** Weather app  
**Description:** Current weather conditions and forecasts.  
**Installation:**
```bash
flatpak install flathub com.github.mousam
```

---

### 51. Countdown
**Purpose:** Event tracker  
**Description:** Track events until they happen or since they happened.  
**Installation:**
```bash
flatpak install flathub com.github.countdown
```

---

### 52. Smile
**Purpose:** Emoji picker  
**Description:** Simple emoji picker for Linux with custom tags support.  
**Installation:**
```bash
flatpak install flathub com.github.smile
```

---

### 53. Authenticator
**Purpose:** 2FA code generator  
**Description:** Generate Two-Factor Authentication codes.  
**Installation:**
```bash
flatpak install flathub com.github.authenticator
```

---

### 54. Collector
**Purpose:** Drag-and-drop utility  
**Description:** Drag multiple files into a single window and drop them anywhere. Also downloads images automatically when pasting URLs.  
**Learn more:** [GitHub Repository](https://github.com/collector)

---

## 🛡️ Security & Privacy

### 55. Lenspect
**Purpose:** Antivirus  
**Description:** Lightweight antivirus scanner for Linux.  
**Learn more:** [GitHub Repository](https://github.com/lenspect)

---

## 🐳 Container & Package Management

### 56. Pods
**Purpose:** Container manager  
**Description:** GUI for managing Podman/Docker containers.  
**Installation:**
```bash
flatpak install flathub com.github.pods
```

---

### 57. Distrobox
**Purpose:** Containerized environments  
**Description:** Run any Linux distribution inside a container with GUI support. Perfect for installing packages not available on your distro.  
**Installation:**
```bash
sudo apt install distrobox
```
**GUI Companion:** BoxBuddy for graphical management

---

## 🤖 AI & Machine Learning

### 58. Pinokio
**Purpose:** AI tools installer  
**Description:** Install and manage AI tools and applications on your system.  
**Learn more:** [Official Website](https://pinokio.computer/)

---

### 59. Speech Note
**Purpose:** Offline speech recognition  
**Description:** Speech-to-text, text-to-speech, and machine translation entirely offline. No data sent to the internet.  
**Installation:**
```bash
flatpak install flathub net.mkiol.SpeechNote
```

---

### 60. Buzz
**Purpose:** Audio transcription  
**Description:** Transcribe and translate audio to text offline using OpenAI's Whisper. Supports multiple models and export formats.  
**Installation:**
```bash
flatpak install flathub com.github.buzz
```

---

### 61. Waydroid
**Purpose:** Android apps on Linux  
**Description:** Run Android applications as native Linux apps.  
**Installation:**
```bash
sudo apt install waydroid
```

---

## 📊 Complete Tool List (All 62 Unique Tools)

| # | Tool | Category |
|---|------|----------|
| 1 | Ananicy-cpp | System Management |
| 2 | systemd-oomd | System Management |
| 3 | Timeshift | System Management |
| 4 | BleachBit | System Management |
| 5 | NetPeek | System Management |
| 6 | Easy Effects | System Management |
| 7 | Audio Sharing | System Management |
| 8 | Monitor | System Management |
| 9 | Cloudflare Warp | System Management |
| 10 | MPV Player | Media & Graphics |
| 11 | HandBrake | Media & Graphics |
| 12 | Upscayl | Media & Graphics |
| 13 | Converseen | Media & Graphics |
| 14 | Switcheroo | Media & Graphics |
| 15 | Spectacle | Media & Graphics |
| 16 | Peek | Media & Graphics |
| 17 | Identity | Media & Graphics |
| 18 | Constrict | Media & Graphics |
| 19 | Audacity | Media & Graphics |
| 20 | Nemo/Dolphin | File Management |
| 21 | Ventoy | File Management |
| 22 | Impression | File Management |
| 23 | Czkawka | File Management |
| 24 | Micro Editor | Development & Terminal |
| 25 | Kitty Terminal | Development & Terminal |
| 26 | Ghostty | Development & Terminal |
| 27 | Gedit | Development & Terminal |
| 28 | Bat/Batcat | Development & Terminal |
| 29 | GitHub Desktop | Development & Terminal |
| 30 | Clapgrep | Development & Terminal |
| 31 | Text Pieces | Development & Terminal |
| 32 | Vish | Development & Terminal |
| 33 | Dev Tools for Format | Development & Terminal |
| 34 | KDE Connect | Network & Connectivity |
| 35 | Ferdium | Network & Connectivity |
| 36 | Celeste | Network & Connectivity |
| 37 | Onion Share | Network & Connectivity |
| 38 | Pipeline | Network & Connectivity |
| 39 | Actioneer | Network & Connectivity |
| 40 | Bazaar | Productivity & Utilities |
| 41 | Okular | Productivity & Utilities |
| 42 | Ulauncher | Productivity & Utilities |
| 43 | Gdebi | Productivity & Utilities |
| 44 | Metadata Cleaner | Productivity & Utilities |
| 45 | Flatseal | Productivity & Utilities |
| 46 | Warehouse | Productivity & Utilities |
| 47 | Gear Lever | Productivity & Utilities |
| 48 | Stirling PDF | Productivity & Utilities |
| 49 | Reminders | Productivity & Utilities |
| 50 | Mousam | Productivity & Utilities |
| 51 | Countdown | Productivity & Utilities |
| 52 | Smile | Productivity & Utilities |
| 53 | Authenticator | Productivity & Utilities |
| 54 | Collector | Productivity & Utilities |
| 55 | Lenspect | Security & Privacy |
| 56 | Pods | Container & Package Management |
| 57 | Distrobox | Container & Package Management |
| 58 | Pinokio | AI & Machine Learning |
| 59 | Speech Note | AI & Machine Learning |
| 60 | Buzz | AI & Machine Learning |
| 61 | Waydroid | AI & Machine Learning |

---

## 🎯 Quick Installation Reference

### Most Essential Tools
```bash
# System management
sudo apt install timeshift bleachbit easyeffects

# Media
sudo apt install mpv handbrake spectacle audacity

# File management
sudo apt install nemo dolphin ventoy

# Terminal
sudo apt install micro kitty bat

# Productivity
sudo apt install ulauncher gdebi okular
```

### Flatpak Applications
```bash
# Install Flatpak if not already
sudo apt install flatpak

# Common Flatpak apps
flatpak install flathub org.ferdium.Ferdium
flatpak install flathub com.github.qarmin.czkawka
flatpak install flathub net.mkiol.SpeechNote
flatpak install flathub io.missioncenter.MissionCenter
flatpak install flathub com.github.bazaar
flatpak install flathub com.github.tchx84.Flatseal
flatpak install flathub io.github.flattool.Warehouse
flatpak install flathub it.mijorus.gearlever
```

---

## 📝 Notes

- **Bat/Batcat:** Remember this is a read-only viewer, not an editor. Use `micro`, `nano`, or `vim` for editing.
- **Ventoy:** After installation, you can copy multiple ISO files directly to the USB drive.
- **Distrobox:** Use BoxBuddy as a GUI companion for easier management.
- **Flatpak:** Many applications are available on Flathub, making them distribution-agnostic.
- **Monitor:** For modern resource monitoring, Mission Center offers a beautiful GTK4 interface.
- **Kitty & Ghostty:** Both are modern terminal emulators - Kitty is GPU-accelerated, Ghostty focuses on performance and customization.

---

## 📄 Documentation Maintained By

*Community Contribution*

---

*For issues or questions about specific tools, please refer to their respective GitHub repositories or documentation.*
```

This guide has **61 unique tools**. 
