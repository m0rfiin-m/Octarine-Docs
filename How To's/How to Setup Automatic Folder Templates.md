# How to Auto-Apply Templates Based on Folder in Obsidian

## Problem
You want templates to automatically apply when creating notes in specific folders (e.g., Concepts folder always uses Concept template, Projects folder uses Project template).

## Solution
Use the **Templater** community plugin to trigger templates based on folder location.

---

## Option 1: Manual Template Insertion (No Plugin)

### How It Works
1. Create new note in desired folder
2. Press `/` or `Cmd/Ctrl + P`
3. Type "Insert template"
4. Choose template

### Pros & Cons
✅ No plugin needed
✅ Simple and built-in
❌ Manual each time
❌ Easy to forget

**Use this if:** You prefer simplicity and don't mind the extra step.

---

## Option 2: Templater Plugin (Recommended)

### Step 1: Install Templater

1. **Open Settings** (⚙️ icon or `Cmd/Ctrl + ,`)

2. **Turn off Safe Mode:**
   - Go to **"Community plugins"**
   - If you see "Safe mode is currently enabled"
   - Click **"Turn off Safe Mode"**
   - Click **"Browse"** to open community plugins

3. **Install Templater:**
   - Search for **"Templater"**
   - Click **"Install"**
   - Click **"Enable"** after installation

---

### Step 2: Configure Templater

1. **Open Templater Settings:**
   - Settings → **"Templater"** (under Community plugins section)

2. **Set Template Folder:**
   - **Template folder location:** `Templates`
   - This tells Templater where your templates are

3. **Enable Folder Templates:**
   - Scroll down to **"Folder Templates"** section
   - Click **"Add New"** button

4. **Set Up Folder-Template Pairs:**

   **For Concepts folder:**
   - **Folder:** `Concepts`
   - **Template:** `Templates/Concept Note Template.md`
   - Click **"Add"**

   **For Projects folder:**
   - **Folder:** `Projects`
   - **Template:** `Templates/Project Template.md`
   - Click **"Add"**

   **For Learning Notes:**
   - **Folder:** `Learning Notes`
   - **Template:** `Templates/Learning Note Template.md`
   - Click **"Add"**

   **For Thoughts:**
   - **Folder:** `Thoughts`
   - **Template:** `Templates/Thought Note Template.md`
   - Click **"Add"**

5. **Enable Automatic Template:**
   - Toggle ON: **"Trigger Templater on new file creation"**
   - This makes templates auto-apply

---

### Step 3: Test It

1. **Create a new note in Concepts folder:**
   - Right-click **Concepts** folder
   - Click **"New note"**
   - Name your note
   - **Template automatically applies!**

2. **Try other folders:**
   - Create note in Projects → Project template appears
   - Create note in Thoughts → Thought template appears

---

## Option 3: QuickAdd Plugin (Advanced)

### When to Use
- You want capture workflows
- You want button-triggered templates
- You need more complex automation

### Basic Setup

1. **Install QuickAdd:**
   - Settings → Community plugins
   - Browse → Search "QuickAdd"
   - Install and Enable

2. **Create Capture:**
   - Settings → QuickAdd
   - Click "Manage Macros" OR "Add Choice"
   - Choose "Template"
   - Configure folder and template

3. **Assign to Folder:**
   - More complex - see QuickAdd documentation

**Recommendation:** Start with Templater first. QuickAdd is powerful but more complex.

---

## Comparison Table

| Feature | Manual | Templater | QuickAdd |
|---------|--------|-----------|----------|
| **Ease of Setup** | ✅ Instant | ⚡ 5 minutes | ⏰ 15+ minutes |
| **Auto-apply** | ❌ No | ✅ Yes | ✅ Yes |
| **Folder-specific** | ❌ No | ✅ Yes | ✅ Yes |
| **Power features** | ❌ Limited | ⚡ Good | ✅✅ Extensive |
| **Plugin needed** | ❌ No | ✅ Yes | ✅ Yes |
| **Learning curve** | ✅ Easy | ⚡ Medium | ❌ Steep |

---

## Recommended Setup for You

Based on your dual-degree workflow:

### Use Templater with These Mappings:

```
Concepts/              → Concept Note Template
Projects/              → Project Template  
Learning Notes/        → Learning Note Template
Thoughts/              → Thought Note Template
Daily Notes/           → (Already configured separately)
Work Search/           → (Manual - varies by document type)
How To's/              → (Manual - use How-To Guide Structure)
Troubleshooting/       → (Manual - varies by problem)
```

### Why This Works:

**Automatic folders (use Templater):**
- Concepts, Projects, Learning Notes, Thoughts
- These have consistent structure
- You create them frequently

**Manual folders (use "/" command):**
- Work Search, How To's, Troubleshooting
- Document types vary
- Created less frequently
- More control needed

---

## Templater Bonus Features

Once you have Templater installed, you can also use:

### Dynamic Date Insertion
```
Created: <% tp.file.creation_date() %>
Modified: <% tp.file.last_modified_date() %>
```

### File Name as Title
```
# <% tp.file.title %>
```

### Prompts for Input
```
Author: <% tp.system.prompt("Who wrote this?") %>
```

### Move File After Creation
```
<% await tp.file.move("/Concepts/" + tp.file.title) %>
```

**These aren't necessary to start**, but they're available when you want more power.

---

## Step-by-Step: Your First Templater Setup

### Complete Walkthrough:

**1. Install (2 minutes):**
- Settings → Community plugins
- Turn off Safe Mode
- Browse → "Templater"
- Install → Enable

**2. Configure (3 minutes):**
- Settings → Templater
- Template folder: `Templates`
- Enable "Trigger Templater on new file creation"
- Add folder templates:
  - `Concepts` → `Templates/Concept Note Template.md`
  - `Projects` → `Templates/Project Template.md`
  - `Thoughts` → `Templates/Thought Note Template.md`
  - `Learning Notes` → `Templates/Learning Note Template.md`

**3. Test (1 minute):**
- Right-click Concepts folder → New note
- Name it → Press Enter
- Template appears automatically! ✨

**Total time: ~6 minutes**

---

## Troubleshooting

### Template Doesn't Auto-Apply

**Check these:**
1. **Templater is enabled:**
   - Settings → Community plugins
   - "Templater" should show "Disable" button (meaning it's active)

2. **Trigger setting is ON:**
   - Settings → Templater
   - "Trigger Templater on new file creation" = ON

3. **Folder path is correct:**
   - Settings → Templater → Folder Templates
   - Check spelling matches exactly
   - No leading/trailing slashes

4. **Template path is correct:**
   - Should be: `Templates/Template Name.md`
   - Check file exists in Templates folder

### Template Applies But Looks Wrong

**Issue:** Template variables not rendering

**Solution:**
- Templater uses different syntax than core Templates
- Convert `{{date}}` to `<% tp.date.now() %>`
- Or keep using core Templates plugin for Daily Notes
- Use Templater only for folder-based templates

### Both Plugins Conflict

**If you have both core Templates AND Templater:**
- Use **core Templates** for Daily Notes (simpler)
- Use **Templater** for folder-based templates (more powerful)
- They can coexist peacefully

---

## My Recommendation for You

**Set this up:**

1. **Install Templater** (6 minutes)
2. **Configure these folders:**
   - Concepts → Concept template
   - Projects → Project template
   - Thoughts → Thought template
   - Learning Notes → Learning template

3. **Keep using core Daily Notes plugin** for daily notes (already working)

4. **Manual templates for:**
   - Work Search (varies)
   - How To's (varies)

**Result:** 
- 90% of your notes auto-template
- 10% you manually control
- Best of both worlds!

---

## Alternative: No Plugin Solution

If you want to avoid plugins entirely:

### Create Folder with Template Note

**In each folder, keep a template note:**
```
Concepts/
  ├── _Template.md (keep this)
  ├── Actual Concept 1.md
  └── Actual Concept 2.md
```

**To use:**
1. Duplicate `_Template.md`
2. Rename the copy
3. Fill in your content

**Pros:** No plugin
**Cons:** More manual work

---

Last Updated: October 7, 2025
