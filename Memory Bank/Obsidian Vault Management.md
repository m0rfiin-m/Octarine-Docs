# Obsidian Vault Management

**Last Updated:** October 24, 2025

---

## Overview

Marco's Obsidian vault setup, template system, organizational structure, and sync configuration across devices.

---

## Vault Structure

### Current Organization (Simplified)
```
second brain/
├── Daily Notes/
├── Studio/           (consolidated workspace - 14 files)
├── Work Search/      (resume, cover letters)
├── Passwords/        (kept separate)
└── Templates/        (2 templates)
```

### Evolution
- **Original:** 12 folders with complex nested structure
- **Simplified To:** 4 folders
- **Templates Reduced:** From 5+ down to 2
- Key consolidation: All work, learning, projects, thoughts, and how-tos moved into "Studio" folder

### Path Configurations
- **macOS:** `/Users/marcomorfin/Documents/obsidian/second brain`
- **Windows:** `D:\Obsidian`
- **Previous Confusion:** Vault name matched folder name (m0rfiin/m0rfiin) causing navigation issues

---

## Template System

### Active Templates

#### Daily Note Template
**Simplified Version (Final)**
```markdown
# {{date:YYYY-MM-DD}} - {{date:dddd}}

## Morning Thoughts
*{{time}}*


## Throughout the Day
*{{time}}*


## End of Day
*{{time}}*
```

**Design Philosophy:**
- Maximum simplicity for mental health journaling
- Three time-stamped checkpoints throughout day
- No complex sections that create friction
- "Best daily note is one you'll actually open and use"

**Evolution:**
- Originally had complex template with many sections
- Marco found it "too deep into other things"
- Simplified to encourage actual usage
- Focus: "write my thoughts and that's it"

#### Studio Template
- For all work, learning, projects, and thought pieces
- Flexible structure

### Removed Templates
- Concept Note Template
- Project Template
- Thought Note Template
- Learning Note Template
- Weekly/Monthly/Quarterly/Yearly Note Templates

### Template Automation Research
**Question:** Can templates auto-apply based on folder?
**Answer:** Requires Templater plugin (community plugin)

**Setup Process:**
1. Settings → Community plugins → Browse
2. Search "Templater" → Install → Enable
3. Configure folder mappings:
   - Concepts → Concept template
   - Projects → Project template
   - Thoughts → Thought template
4. Enable "Trigger on new file creation"

**Alternative:** Keep template note in folder (`_Template.md`), duplicate and rename when needed

---

## Sync Configuration

### Git Integration
- **Plugin:** Obsidian Git (community plugin)
- **Repository:** git@github.com:m0rfiin-m/Octarine-Docs.git
- **Authentication:** SSH key (passwordless)

### Settings
- **Vault backup interval:** 10-30 minutes (recommended)
- **Auto pull interval:** 10 minutes
- **Auto push:** Enabled
- **Commit message:** "vault backup: {{date}}"
- **Pull updates on startup:** Enabled

### Multi-Device Workflow
- Changes on Mac automatically committed and pushed
- Windows machine pulls latest changes
- SSH key setup eliminates authentication prompts

### Sync Issues Encountered
- **Trailing Spaces:** Folder names with spaces (e.g., "Web-Development /") invalid on Windows
  - **Solution:** Rename on Mac before cloning to Windows
- **Branch Conflicts:** Resolved using Git protocol
- **Wrong Vault Access:** Initially accessing nested vault incorrectly
  - Confusion between `/m0rfiin/m0rfiin/` vs actual vault path

---

## MCP Integration

### Obsidian MCP Server
- Direct integration with Claude for reading/writing notes
- Can list files, search content, and modify vault programmatically
- Separate from filesystem access

### Common Operations
- `obsidian_list_files_in_vault` - See all files
- `obsidian_get_file_contents` - Read specific note
- `obsidian_append_content` - Add to existing note
- `obsidian_delete_file` - Remove note
- `obsidian_search_notes` - Find content across vault

---

## Writing Preferences

### Style Guidelines
- No em dashes (—) - use regular dashes or alternative punctuation
- Direct, conversational tone
- Avoid filler phrases
- Minimize hedging language (might, could, perhaps)

### Organization Principles
- Emojis for visual organization
- Comprehensive table of contents structures
- Step-by-step numbered instructions with troubleshooting
- ASCII diagrams for technical documentation
- Bold emphasis for UI elements
- Horizontal rules between sections

---

## Usage Patterns

### Note Types in Studio Folder
- AI Agent Prompts (Coding, Content Strategist, Finance, Second Brain)
- Thought pieces (Git collaboration discussions)
- How-to guides (9 different guides)
- Technical documentation
- README files

### Daily Notes
- Mental health journaling
- Thought tracking throughout day
- Simple, low-friction capture

### Work Search
- Resume versions
- Cover letters
- Job application tracking

---

## Periodic Notes (Removed)

### Previously Had
- Weekly Notes
- Monthly Notes
- Quarterly Notes
- Yearly Notes

### Reason for Removal
- Unused complexity
- Created friction
- Simplified to only Daily Notes

---

## Future Considerations

- Template automation via Templater plugin
- Possible folder reorganization as needs evolve
- Integration with other knowledge management tools

---

**Related:** [[LazyVim Customization]], [[Git Workflow]], [[Technical Setup]]
