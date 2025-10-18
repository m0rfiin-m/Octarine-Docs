# How to Set Up Automatic Daily Notes Template in Obsidian

## Problem
When creating daily notes, you want the template to automatically appear instead of manually inserting it each time.

## Solution
Configure Obsidian's Daily Notes core plugin to use your template automatically.

---

## Step 1: Enable Daily Notes Plugin

1. **Open Obsidian Settings**
   - Click the gear icon ⚙️ in the bottom left corner
   - OR press `Cmd + ,` (Mac) or `Ctrl + ,` (Windows/Linux)

2. **Go to Core Plugins**
   - In the left sidebar, click **"Core plugins"**

3. **Enable Daily Notes**
   - Scroll down to find **"Daily notes"**
   - Toggle it **ON** (the switch should turn purple/blue)

---

## Step 2: Configure Daily Notes Settings

1. **Open Daily Notes Settings**
   - Still in Settings, click **"Daily notes"** in the left sidebar under "Plugin options"

2. **Set the Date Format**
   - **Date format field:** Enter `YYYY-MM-DD`
   - This makes files named like: `2025-10-07`

3. **Set the New File Location**
   - **New file location field:** Enter `Daily Notes`
   - This saves all daily notes in your Daily Notes folder

4. **Set the Template File**
   - **Template file location field:** Enter `Templates/Daily Note Template`
   - This tells Obsidian which template to use

5. **Template Date Format (Optional)**
   - Leave as default OR customize if needed
   - This controls how dates appear inside the template

---

## Step 3: Fix Your Template File

The template needs to be in the correct location and format:

1. **Ensure Template Exists**
   - Go to your `Templates` folder
   - Make sure `Daily Note Template.md` exists

2. **Template File Name**
   - The file should be named exactly: `Daily Note Template.md`
   - No extra spaces or characters

---

## Step 4: Create Daily Notes

### Method 1: Using the Ribbon Icon
1. **Find the Calendar Icon** 📅 in the left ribbon (sidebar)
2. **Click it** to create today's note with your template automatically

### Method 2: Using Command Palette
1. Press `Cmd + P` (Mac) or `Ctrl + P` (Windows/Linux)
2. Type "Open today's daily note"
3. Press Enter

### Method 3: Using Hotkey
1. **Set up a hotkey:**
   - Settings → Hotkeys
   - Search "Open today's daily note"
   - Click the + icon to add a hotkey
   - Recommended: `Cmd + D` or `Ctrl + D`

2. **Use your hotkey** to instantly create/open today's note

---

## Step 5: Verify It Works

1. **Create a new daily note** using one of the methods above
2. **Check that:**
   - File is created in `Daily Notes` folder
   - File name is the date (e.g., `2025-10-07.md`)
   - Template content automatically appears
   - All sections are populated

---

## Troubleshooting

### Template Doesn't Appear

**Problem:** Daily note creates but template is blank

**Solutions:**
1. **Check template path:**
   - Settings → Daily notes → Template file location
   - Should be: `Templates/Daily Note Template`
   - Try: `Templates/Daily Note Template.md` (with extension)

2. **Check file location:**
   - Open Files panel (left sidebar)
   - Navigate to Templates folder
   - Confirm file exists and name matches exactly

3. **Check for typos:**
   - File name must match exactly
   - Check for extra spaces
   - Case-sensitive on some systems

### "/" Command Not Working

**Problem:** Typing "/" doesn't show template options

**Solutions:**
1. **Enable Templates core plugin:**
   - Settings → Core plugins
   - Enable "Templates"

2. **Set template folder:**
   - Settings → Templates (under Plugin options)
   - Template folder location: `Templates`

3. **Try the command palette instead:**
   - `Cmd/Ctrl + P`
   - Type "Insert template"
   - Select your template

### File Created in Wrong Location

**Problem:** Daily notes aren't going to Daily Notes folder

**Solution:**
- Settings → Daily notes
- New file location: `Daily Notes` (exact spelling, no slash)

### Template Variables Not Working

**Problem:** Date placeholders like `{{date}}` not filling in

**Solution:**
1. **Check Templater plugin** (if installed)
   - May conflict with core Templates
   - Disable Templater OR use Templater syntax

2. **Use core template variables:**
   - `{{date}}` - current date
   - `{{time}}` - current time
   - `{{title}}` - file name

---

## Pro Tips

### Automatic Daily Note on Startup

**Settings → Daily notes:**
- Toggle ON: **"Open daily note on startup"**
- Obsidian will create/open today's note when you launch

### Quick Navigation

**Calendar Plugin (Community):**
1. Settings → Community plugins → Browse
2. Search "Calendar"
3. Install and enable
4. Visual calendar appears in right sidebar
5. Click any date to create/open that daily note

### Multiple Templates

If you want different templates for different purposes:
1. Create multiple template files
2. Use "/" or `Cmd/Ctrl + P` → "Insert template"
3. Choose which template to insert

---

## Summary

**Quick Setup Checklist:**
- [x] Enable Daily Notes core plugin
- [x] Set date format: `YYYY-MM-DD`
- [x] Set location: `Daily Notes`
- [x] Set template: `Templates/Daily Note Template`
- [x] Verify template file exists
- [x] Test by creating today's note

**Result:** Click the calendar icon 📅 and your daily note appears with the full template automatically!

---

## Your Current Setup

Based on your description:
- ✅ Daily Notes folder exists
- ✅ Template file should exist (we created it)
- ⚠️ Need to configure Daily Notes plugin settings

**Next step:** Follow Step 2 above to configure your Daily Notes settings in Obsidian.

---

Last Updated: October 7, 2025
