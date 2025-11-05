# Windows System Management

**Last Updated:** October 24, 2025

---

## Overview

Marco's Windows PC maintenance, troubleshooting patterns, and system configuration knowledge.

---

## System Specifications

### Hardware
- **CPU:** AMD Ryzen 9 7900X
- **Motherboard:** Gigabyte B650M AORUS ELITE AX
- **Cooling:** Thermalright Frost Commander 240mm AIO
- **Case:** Montech Air 100 (161mm CPU cooler clearance)
- **Storage:** Multiple drives (C:\, D:\, E:\)

### Software Environment
- Windows 11
- Docker Desktop
- Various MCP servers

---

## Common Issues & Solutions

### Microsoft Store Popup Loop

#### Problem
- Store popup appears on startup
- Sometimes computer won't fully shutdown (returns to login screen)
- Restart gets stuck in loop
- Started after Windows update

#### Root Causes Identified
1. **Fast Startup Issue**
   - Fast Startup doesn't fully shut down (hibernates kernel instead)
   - Prevents updates and drivers from installing properly
   - **Solution:** Disable via Control Panel → Power Options → "Choose what power button does" → Uncheck "Turn on fast startup"

2. **Startup Folder Shortcuts**
   - Check `%APPDATA%\Microsoft\Windows\Start Menu\Programs\Startup`
   - Check `C:\ProgramData\Microsoft\Windows\Start Menu\Programs\Startup`
   - Remove any Store shortcuts

3. **Registry Entries**
   - Malware/adware can create registry entries
   - **Location:** `HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Run`
   - Search for suspicious entries using Registry Editor (regedit)

4. **Task Scheduler Triggers**
   - Windows creates tasks that open Store at startup
   - **Check:** Task Scheduler → Microsoft → Windows → WindowsUpdate
   - **Disable:** Tasks with "Consumer" or "Store" in name

5. **Command Line Shutdown**
   - Force proper shutdown: `shutdown /s /f /t 0`
   - Force restart: `shutdown /r /f /t 0`

### Malware Removal (blueone.win)

#### Problem
- Browser hijacker redirecting through "me.blueone.win"
- Default protocol handlers hijacked
- Popup persists after removing Windows Store

#### Solution Process
1. **Reset Default App Associations**
   - Settings → Apps → Default apps → Reset

2. **Registry Cleanup**
   - Open regedit
   - Press F3 to search
   - Search for "blueone"
   - Delete all entries found (found 3 instances)
   - Restart required

3. **DNS Flush**
   - `ipconfig /flushdns`
   - Verify DNS servers: `ipconfig /all`

4. **Malware Scanning**
   - Malwarebytes (free version)
   - AdwCleaner
   - Restart between scans

5. **Check Scheduled Tasks**
   - Task Scheduler → Look for suspicious tasks
   - Delete anything unfamiliar or referencing malware domains

6. **Hosts File Check**
   - Location: `C:\Windows\System32\drivers\etc\hosts`
   - Should be mostly empty except localhost entries
   - Delete lines referencing external domains

---

## Virtualization Setup

### Enabling Virtualization

#### Check if Enabled
1. Task Manager (Ctrl + Shift + Esc)
2. Performance tab → CPU
3. Look for "Virtualization: Enabled" at bottom right

#### Enable in BIOS
**For Gigabyte B650M AORUS ELITE AX:**
1. Restart and press Delete key repeatedly
2. Navigate to Advanced or M.I.T. tab
3. Find "SVM Mode" or "AMD-V"
4. Change to Enabled
5. Save (F10) and exit

#### Post-Enable Setup
- Used for Docker
- Required for Hyper-V
- Enables WSL2

---

## Software Management

### Removing Development Tools
- Cleaned Python, Node.js, VS Code, Visual Studio
- Kept Docker for MCP servers
- Removed all LSP servers and global npm packages

### Uninstall Commands
```powershell
# VS Code
winget uninstall Microsoft.VisualStudioCode

# Remove data
Remove-Item -Recurse -Force $env:USERPROFILE\.vscode
Remove-Item -Recurse -Force $env:APPDATA\Code

# Node global packages
npm list -g --depth=0  # List first
npm uninstall -g <package-name>
```

---

## Audio Drivers

### Removed
- **WaveLink Virtual Audio Driver**
  - Location: `/Library/Audio/Plug-Ins/HAL`
  - Command: `sudo rm -rf WaveLinkVirtualAudio.driver`
  - Restart Core Audio: `sudo killall coreaudiod`

- **Black Hole**
  - Manual removal: Delete driver files from system directories
  - Used Audio MIDI Setup to verify removal

### Kept
- MS Teams audio driver
- Parrot audio driver

---

## Fan Control Setup

### Software
- **Fan Control** (open source)
- Alternative: MSI Afterburner, SpeedFan

### Configuration Issues
- Had configuration wrong initially
- **Pump:** Should be 100% flat, always (for AIO cooler)
- **Radiator fans:** Aggressive curve based on CPU temp
- **Sensor:** Use CPU (Tctl/Tdie), not motherboard temp
- **Settings:**
  - Hysteresis: 3°C
  - Response time: 2 seconds

### Temperature Targets
- **Idle:** 40-45°C (was experiencing 55°C)
- **Gaming:** 68-75°C (was experiencing 80°C)
- Ryzen 9 7900X outputs 170W heat

---

## Fresh Windows Install

### Preparation Checklist
- ✅ Back up all important files
- ✅ Note Windows product key
- ✅ Note Wi-Fi password
- ✅ Create bootable USB (Windows Media Creation Tool)
- ✅ Know which drive to wipe
- ✅ Have motherboard/GPU drivers ready

### Installation Process
1. Boot from USB
2. Delete all partitions on target drive
3. Let Windows create new partitions automatically
4. Complete installation (15-30 minutes)
5. Run Windows Update until no updates remain
6. Install chipset drivers first (AMD B650)
7. Install GPU drivers
8. Install other drivers as needed

---

## RAM Issues

### Problem Identification
- System not booting properly
- Need to reseat RAM
- Check RAM placement in correct slots (usually A2/B2)

---

## Keyboard Shortcuts

### PowerShell Management
- Open as Admin: Windows key → type "PowerShell" → right-click → "Run as administrator"
- Required for system-level commands

---

**Related:** [[Technical Setup]], [[System Maintenance]], [[PC Building & Hardware]]
