# Technical Setup

**Last Updated:** October 23, 2025

---

## MCP Server Configuration

### Active Configuration

**Current Setup:**
- **Primary Server:** MCP_DOCKER
- **Command:** `docker mcp gateway run`
- **Status:** ✅ Active and functional

**Configuration File Location:**
```
/Users/marcomorfin/Library/Application Support/Claude/claude_desktop_config.json
```

**Current Configuration:**
```json
{
  "mcpServers": {
    "MCP_DOCKER": {
      "command": "docker",
      "args": ["mcp", "gateway", "run"]
    }
  }
}
```

---

### MCP_DOCKER Capabilities

**Integrated Tools:**
- **Obsidian Integration:** Full vault access, search, file management
- **YouTube Tools:** Transcript extraction, video info, timed transcripts
- **Knowledge Graph:** Create entities, relations, observations
- **Sequential Thinking:** Advanced problem-solving workflows

**Tool Functions:**

**Obsidian:**
- `obsidian_get_file_contents` - Read files
- `obsidian_batch_get_file_contents` - Read multiple files
- `obsidian_append_content` - Add to files
- `obsidian_patch_content` - Insert content at specific locations
- `obsidian_list_files_in_vault` - Browse vault root
- `obsidian_list_files_in_dir` - Browse specific directories
- `obsidian_simple_search` - Text search
- `obsidian_complex_search` - JsonLogic queries
- `obsidian_delete_file` - Remove files
- `obsidian_get_recent_changes` - Track modified files
- `obsidian_get_periodic_note` - Access daily/weekly/monthly notes
- `obsidian_get_recent_periodic_notes` - Multiple periodic notes

**YouTube:**
- `get_transcript` - Extract full video transcript
- `get_timed_transcript` - Transcript with timestamps
- `get_video_info` - Video metadata

**Knowledge Graph:**
- `create_entities` - Add knowledge nodes
- `create_relations` - Link entities
- `add_observations` - Update entity data
- `search_nodes` - Query knowledge
- `open_nodes` - Retrieve specific nodes
- `read_graph` - Full graph view
- `delete_entities` - Remove nodes
- `delete_observations` - Remove data
- `delete_relations` - Remove links

**Sequential Thinking:**
- `sequentialthinking` - Multi-step problem-solving with revision capability

---

### Configuration History

**October 6, 2025: OnlyOffice MCP Removal**

**Reason for Removal:**
- Configuration conflicts with multiple authentication methods
- Error: Multiple authentication types detected (API key + username/password)
- User granted full permission for removal
- Decision: Focus on MCP_DOCKER for core functionality

**Previous Configuration Attempt:**
```json
{
  "mcpServers": {
    "MCP_DOCKER": {
      "command": "docker",
      "args": ["mcp", "gateway", "run"]
    },
    "onlyoffice-docspace": {
      // Removed due to authentication conflicts
    }
  }
}
```

**Resolution:**
- Removed OnlyOffice server completely
- Kept MCP_DOCKER intact
- All Docker-based tools remain functional

[Removal Conversation](https://claude.ai/chat/e43dbc5a-2202-4554-ad36-4e83e71f8f41)

---

### Configuration Management

**How to Update:**
1. Edit: `/Users/marcomorfin/Library/Application Support/Claude/claude_desktop_config.json`
2. Make changes to JSON structure
3. Save file
4. Restart Claude application
5. Verify functionality

**Best Practices:**
- Always backup config before changes
- Test one server at a time when adding new
- Verify authentication requirements before adding servers
- Check for conflicts between server requirements
- Restart Claude after any config changes

---

## Email Management

### Outlook Configuration

**Primary Email:** m.m0rfiin@gmail.com (through Outlook)  
**Previous Email:** marco_morfin@hotmail.com (being phased out)

---

### Automated Email Rules

**Created October 9, 2025**

**Rule 1: Gmail Forwards - Google Play**
- **Rule ID:** AQAACFxVvm8=
- **Trigger:** Emails from `googleplay-noreply@google.com`
- **Action:** Auto-move to "Gmail Forwards" folder
- **Purpose:** Keep inbox clean from Google Play notifications

**Rule 2: Gmail Forwards - Google Accounts**
- **Rule ID:** AQAACFxVvm4=
- **Trigger:** Emails from `no-reply@accounts.google.com`
- **Action:** Auto-move to "Gmail Forwards" folder
- **Purpose:** Organize Google account notifications separately

**Status:** Both rules active and functioning

[Rule Creation Conversation](https://claude.ai/chat/c070e7bd-00e0-43ac-836d-e7f3a704014e)

---

### Email Cleanup History

**October 9, 2025: Junk Email Analysis**

**Period Analyzed:** October 1-9, 2025  
**Total Junk:** 37 emails

**Breakdown:**
- **Job Spam:** 25 emails (68%)
  - Adzuna: 9 emails
  - LinkedIn: 8 emails
  - Hire-Fi.com: Multiple
  - Randstad, ZipRecruiter: Various
  
- **Marketing/Product Updates:** 11 emails (32%)
  - Replit: 3 emails
  - Tella: 2 emails
  - Crayo AI, DocHipo, Canny, Composio, Activepieces: Various

- **Delivery Failures:** 1 email

**Action Taken:**
- Analyzed patterns
- Created filtering strategies
- Set up automated rules for recurring senders

[Cleanup Analysis](https://claude.ai/chat/c070e7bd-00e0-43ac-836d-e7f3a704014e)  
[Outlook Cleanup Process](https://claude.ai/chat/7dfae296-17c8-421a-a879-51660344f76f)

---

### Email Management Workflow

**For Recurring Unwanted Emails:**
1. Identify sender patterns (domains, addresses)
2. Create rule to auto-route or delete
3. Move existing emails to appropriate folders
4. Monitor rule effectiveness
5. Adjust as needed

**Folder Strategy:**
- **Inbox:** Active, actionable emails only
- **Gmail Forwards:** Google service notifications
- **Junk/Spam:** Automated filtering
- **Archive:** Completed/reference emails

---

## YouTube Integration

### Capabilities

**Available Through MCP_DOCKER:**
- Extract full video transcripts
- Get timed transcripts with timestamps
- Retrieve video metadata (title, description, etc.)
- Support for English and other languages
- Pagination for long transcripts

**Storage Location:**
- Transcripts stored in Obsidian vault
- File: `Youtube Videos.md`
- Organized with video title, URL, and key learnings

---

### YouTube Workflow

**Standard Process:**
1. Receive YouTube URL from user
2. Extract transcript using `get_transcript` tool
3. Analyze content for key learnings
4. Store valuable content in Obsidian
5. Organize with headers and structure

**Example Usage:**
```
User provides: https://youtu.be/QBXLNEMv5so

1. get_transcript(url)
2. Analyze for main concepts
3. Extract actionable takeaways
4. Store in Youtube Videos.md
5. Cross-reference to relevant topics
```

---

### Tool Testing History

**October 4, 2025: Initial YouTube Tool Challenges**

**Issue:** Early attempts at YouTube integration had difficulties accessing content  
**Resolution:** Switched to MCP_DOCKER tools  
**Outcome:** ✅ Fully functional transcript extraction

[YouTube Tool Testing](https://claude.ai/chat/cfb18ec8-f5dd-4db1-86d3-f43590a65ffa)  
[YouTube Access Questions](https://claude.ai/chat/dfbe173f-9df5-4635-8cff-7057b76751e1)

---

### Stored YouTube Content

**Current Content:**
- Communication skills video (Vinh Giang)
- Transcript and key learnings stored
- See [[Communication Skills]] for full analysis

**Future Content:**
- Any valuable educational videos
- Industry insights and tutorials
- Skill development resources

---

## Obsidian Vault Structure

**Root Directories:**
```
Root/
├── AAS in AI Software Engineering/
│   └── [Course materials by code]
├── AI Chat/
├── AI-Agents/
│   └── [Agent configurations]
├── Career/
│   └── [Professional documents]
├── Claude Memory Bank/
│   └── [Memory system - this folder]
├── How To's/
│   └── [Practical guides]
├── Projects/
│   └── [Project documentation]
├── Telos/
│   └── [Personal goals/system]
└── Web-Development/
    └── [Dev resources]
```

---

### File Naming Conventions

**Established Patterns:**
- How-To guides: `How to [Action].md`
- Agent configs: `[Agent Name].md`
- Career docs: `[Full Name] [Document Type].md`
- Academic: `[Course Code]/[Topic].md`
- Memory docs: `[Topic].md` (in Claude Memory Bank/)

**Critical Rule:** Always `filename.md` (no space before extension)

---

### Obsidian Integration Features

**Available Operations:**
- Read individual or multiple files
- Search by text or complex queries
- Create and append content
- Delete files with confirmation
- List directories and contents
- Track recent changes
- Access periodic notes (daily, weekly, monthly)
- Insert content at specific locations (headings, blocks, frontmatter)

**Best Practices:**
- Use batch operations for multiple files
- Leverage search before creating duplicates
- Maintain consistent naming conventions
- Cross-link related documents
- Update timestamps on reference materials

---

## Tool Integration Workflow

### When to Use Which Tool

**Obsidian:**
- Storing knowledge and reference materials
- Creating structured documentation
- Building interconnected knowledge base
- Maintaining project documentation
- Tracking decisions and processes

**YouTube:**
- Extracting learning content
- Archiving valuable tutorials
- Creating reference material from videos
- Building skill development library

**Knowledge Graph:**
- Mapping relationships between concepts
- Tracking entity connections
- Building semantic knowledge structures
- Creating queryable knowledge networks

**Sequential Thinking:**
- Complex problem-solving
- Multi-step analysis
- Iterative refinement processes
- Planning and strategy development

---

## Configuration Troubleshooting

### Common Issues

**MCP Server Not Working:**
1. Check config file syntax (valid JSON)
2. Verify file location is correct
3. Restart Claude application
4. Check Docker is running (for MCP_DOCKER)
5. Review server logs if available

**Authentication Errors:**
1. Verify only one auth method configured
2. Clear conflicting credentials
3. Check API keys are valid
4. Restart after credential changes

**Tool Not Available:**
1. Confirm MCP_DOCKER is running
2. Check docker mcp gateway status
3. Restart Docker if needed
4. Verify tool is included in MCP_DOCKER

---

## Future Enhancements

**Potential Additions:**
- Additional MCP servers as needs arise
- Enhanced automation rules for email
- Expanded Obsidian organization strategies
- Integration with other productivity tools
- Custom script development for workflows

**Considerations:**
- Test thoroughly before adding new servers
- Avoid authentication conflicts
- Maintain configuration documentation
- Back up configs before changes
- Monitor performance impact

---

## Related Documents

- [[Quick Reference]] - Current email and contact info
- [[Communication Skills]] - YouTube content stored
- [[Email Writing Style]] - Email management context
- [[Email Protocols]] - Email communication tools

---

**Back to:** [[Index]]


## macOS Development Environment

### Matte Black Theme Setup

**Last Updated:** October 22, 2025

**Theme Source:**  
[Omarchy Matte Black Theme](https://github.com/basecamp/omarchy/tree/master/themes/matte-black)

---

### Current Stack

**Terminal & Shell:**
- **Terminal Emulator:** WezTerm (switched from Ghostty)
- **Shell Prompt:** Starship (with Matte Black theming)
- **Terminal Multiplexer:** Tmux (configured but not essential)

**Editor:**
- **Editor:** Neovim with LazyVim distribution
- **Colorscheme:** Custom Matte Black theme

---

### Matte Black Color Palette

**Official Omarchy Colors:**
```
Background: #1a1a1a (dark matte black)
Foreground: #e0e0e0 (light gray text)
Accent: #ff6b35 (orange/amber)
Secondary: Various shades of gray
```

**Implementation:**
- Consistent theme across all tools
- Orange accents for highlights and active elements
- Dark backgrounds for reduced eye strain
- Cohesive visual experience across terminal, editor, and system

---

### Tool Configuration Files

**Neovim/LazyVim:**
- Location: `~/.config/nvim/`
- Custom colorscheme: `matte-black.lua`
- Dashboard: Custom ASCII art (Pacman with ghost)
- Status line: Integrated Matte Black colors

**Starship:**
- Configuration: `~/.config/starship.toml`
- Themed with Matte Black palette
- Custom prompt format matching Omarchy aesthetic

**Tmux:**
- Configuration: `~/.tmux.conf`
- Prefix: `Control+a` (attempted, not essential)
- Theme: Matte Black status bar
- Note: WezTerm native panes preferred over tmux

**WezTerm:**
- Configuration: `~/.wezterm.lua` (if configured)
- Native split panes and tabs
- Matte Black theming applied
- Replaced Ghostty as primary terminal

---

### Setup Timeline

**October 22, 2025:**
- Initial request for Matte Black theme across development environment
- Configured LazyVim, Ghostty, Tmux, Starship
- Researched Omarchy theme specifications

**Key Decisions:**
- WezTerm chosen over Ghostty for better compatibility
- Tmux configured but not required (WezTerm has native features)
- Custom Neovim colorscheme created from Omarchy palette
- Starship themed to match overall aesthetic

[Configuration Conversation](https://claude.ai/chat/79cecbd8-34d1-468b-86ae-0989dd97ede5)

---

### Development Workflow

**Current Setup:**
✅ WezTerm - Modern terminal installed and configured  
✅ Neovim/LazyVim - Custom Matte Black colorscheme  
✅ Starship - Themed prompt matching Matte Black  
✅ Consistent visual experience across all tools

**Optional Enhancements:**
- Further WezTerm theming to match Matte Black exactly
- Additional LazyVim plugins with theme support
- System-wide dark mode optimization
- Menu bar and dock theming (if desired)

---

### Troubleshooting

**Common Issues:**

**Terminal Not Applying Theme:**
1. Check config file exists in correct location
2. Verify syntax (especially in TOML/Lua files)
3. Restart terminal application
4. Source config manually if needed

**Neovim Colors Not Loading:**
1. Verify colorscheme file in correct directory
2. Check for syntax errors in Lua config
3. Run `:colorscheme matte-black` in Neovim
4. Restart Neovim

**Tmux Keybindings Not Working:**
1. Verify tmux is actually running (`echo $TMUX`)
2. Source config: `tmux source-file ~/.tmux.conf`
3. Test with default prefix (`Control+b`) first
4. Consider using WezTerm native features instead

---

### Related Files

- [[LazyVim Customization]] - Dashboard and UI customization
- [[System Maintenance]] - macOS troubleshooting and fixes

