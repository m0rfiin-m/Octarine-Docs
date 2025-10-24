# System Maintenance

**Last Updated:** October 24, 2025

---

## Overview

Troubleshooting documentation for macOS system maintenance, software removal, driver management, and configuration fixes.

---

## Audio Driver Management

### BlackHole Audio Router Removal

**Date:** October 24, 2025

**Context:**  
BlackHole is a virtual audio driver that creates virtual audio devices for routing audio between applications. Removal requires system-level access since it installs as a kernel extension.

---

### Removal Process

**Installation Type:**  
Package installer (.pkg file) - installs kernel extension, not a standard application

**Why No Uninstaller:**  
Audio drivers install as system extensions in `/Library/Audio/Plug-Ins/HAL/` rather than Applications folder. They don't show up as apps and require manual removal.

---

### Step-by-Step Removal

**Step 1: Locate the Driver**

```bash
cd /Library/Audio/Plug-Ins/HAL/
ls
```

**Expected Files:**
- `BlackHole16ch.driver` (or similar variant)
- Other audio drivers may also be present:
  - `ParrotAudioPlugin.driver`
  - `WaveLinkVirtualAudioDevice.driver`
  - `MSTeamsAudioDevice.driver`

---

**Step 2: Remove the Driver**

```bash
sudo rm -rf BlackHole16ch.driver
```

**Critical Syntax:**  
`sudo rm -rf` (NOT `sudo rm ~rf`)
- `-rf` = hyphen + flags (recursive, force)
- `~rf` = tilde (home directory) + "rf" (incorrect)

**Common Error:**
```
no such user or named directory: rf
```

**Cause:** Using tilde (`~`) instead of hyphen (`-`)  
**Solution:** Correct the command to use proper hyphen

---

**Step 3: Restart Audio System**

```bash
sudo launchctl kickstart -kp system/com.apple.audio.coreaudiod
```

**What This Does:**
- Restarts Core Audio daemon
- Reloads audio drivers
- Applies changes without full system restart

---

**Step 4: Verify Removal**

Check if BlackHole is gone:
```bash
ls /Library/Audio/Plug-Ins/HAL/
```

BlackHole should no longer appear in the list.

---

### Troubleshooting

**Issue:** "Permission denied"  
**Solution:** Ensure you're using `sudo` (requires admin password)

**Issue:** "Command not found"  
**Solution:** Verify you're in correct directory (`/Library/Audio/Plug-Ins/HAL/`)

**Issue:** Audio not working after removal  
**Solution:** Restart computer or run the launchctl command again

**Issue:** Driver reappears  
**Solution:** Check if application is reinstalling it, remove the source application

---

### Related Audio Drivers

**Other Virtual Audio Devices Found:**
- **ParrotAudioPlugin** - Parrot virtual audio device
- **WaveLinkVirtualAudioDevice** - Elgato Wave Link audio routing
- **MSTeamsAudioDevice** - Microsoft Teams audio device

**Removal Process:** Same as BlackHole (substitute driver name in rm command)

---

[BlackHole Removal Conversation](https://claude.ai/chat/dbd0af4e-e0b6-4b37-83e9-1b8324914198)

---

## Terminal Command Syntax

### Common Flags and Operators

**rm (Remove) Command:**
- `-r` or `-R` - Recursive (delete directories and contents)
- `-f` - Force (don't prompt for confirmation)
- `-i` - Interactive (ask before each deletion)
- `-v` - Verbose (show what's being deleted)

**Combined Flags:**
- `-rf` - Force recursive deletion (use with extreme caution)
- Always use absolute paths with `rm -rf` to avoid accidents

---

### Symbols That Matter

**Hyphen vs Tilde:**
- `-` (hyphen) - Flag indicator for commands
- `~` (tilde) - Shortcut for home directory (`/Users/username/`)

**Example:**
```bash
# Correct - removes file with force/recursive flags
sudo rm -rf filename

# Incorrect - tries to access home directory of user "rf"
sudo rm ~rf filename
```

---

### Safe Deletion Practices

**Before Using rm -rf:**
1. Double-check the path
2. Verify you're in the correct directory
3. Use `ls` to confirm file exists
4. Consider backing up if uncertain
5. Use `rm -i` for interactive mode if learning

**Dangerous Patterns to Avoid:**
```bash
# DANGEROUS - Could delete everything
sudo rm -rf /

# DANGEROUS - Could delete entire home directory
sudo rm -rf ~

# DANGEROUS - Could delete current directory
sudo rm -rf .
```

---

## System-Level File Locations

### macOS Directory Structure

**System Locations:**
- `/Library/` - System-wide files (requires admin)
- `/System/Library/` - Core macOS files (protected by SIP)
- `/usr/` - Unix system resources
- `/private/` - System configuration and logs

**User Locations:**
- `~/` or `/Users/username/` - User home directory
- `~/Library/` - User-specific application data
- `~/Desktop/` - Desktop files
- `~/.config/` - User configuration files

---

### Audio Plugin Locations

**HAL (Hardware Abstraction Layer) Plugins:**
- `/Library/Audio/Plug-Ins/HAL/` - System-wide audio drivers
- `~/Library/Audio/Plug-Ins/HAL/` - User-specific audio plugins

**Other Audio Locations:**
- `/Library/Audio/Plug-Ins/Components/` - Audio components
- `/Library/Audio/Plug-Ins/VST/` - VST plugins
- `/Library/Audio/Plug-Ins/VST3/` - VST3 plugins

---

## File System Best Practices

### Permission Management

**Understanding sudo:**
- `sudo` - "Superuser do" - run commands as administrator
- Prompts for password
- Required for system-level changes
- Use carefully - mistakes can break system

**File Permissions:**
- Read (r) - View file contents
- Write (w) - Modify file
- Execute (x) - Run file as program

**Checking Permissions:**
```bash
ls -la
```

Shows detailed permissions for all files.

---

### Safe System Modifications

**Before Making Changes:**
1. Research the file/directory purpose
2. Back up if possible
3. Understand what the command does
4. Test in safe environment if available
5. Know how to reverse the change

**After Making Changes:**
1. Verify change worked as expected
2. Test related functionality
3. Document what was changed and why
4. Monitor for unexpected side effects

---

## Common macOS Maintenance Tasks

### Application Removal

**Standard Apps (with installer):**
1. Drag from Applications to Trash
2. Empty Trash
3. Check for leftover files in `~/Library/`

**System Extensions/Drivers:**
1. Locate in system directories
2. Use sudo rm -rf to remove
3. Restart related services or system

**Package Managers (Homebrew):**
```bash
brew uninstall package-name
brew cleanup
```

---

### Cache and Temporary Files

**User Caches:**
```bash
rm -rf ~/Library/Caches/*
```

**System Temporary Files:**
```bash
sudo rm -rf /tmp/*
```

**Note:** System will recreate necessary cache files automatically.

---

### System Restarts and Services

**Restart Specific Service:**
```bash
sudo launchctl kickstart -kp system/[service-name]
```

**Stop Service:**
```bash
sudo launchctl stop [service-name]
```

**Start Service:**
```bash
sudo launchctl start [service-name]
```

**Full System Restart:**
```bash
sudo shutdown -r now
```

---

## Troubleshooting Checklist

### General Debugging Steps

1. **Identify the Problem**
   - What's not working?
   - When did it start?
   - What changed recently?

2. **Check Logs**
   - Console.app for system logs
   - Terminal error messages
   - Application-specific logs

3. **Verify Permissions**
   - Do you have access to required files?
   - Is sudo needed?
   - Are files locked or in use?

4. **Research Solutions**
   - Official documentation
   - Known issues and fixes
   - Community forums and GitHub issues

5. **Apply Fix Carefully**
   - Understand the solution
   - Back up if possible
   - Test incrementally

6. **Verify Resolution**
   - Does the problem persist?
   - Are there side effects?
   - Should the fix be documented?

---

## Related Documents

- [[Technical Setup]] - Development environment configuration
- [[LazyVim Customization]] - Editor troubleshooting

---

**Back to:** [[Index]]
