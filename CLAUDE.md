# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is Marco Morfin's personal knowledge repository synced with Octarine note-taking system. It contains educational materials, technical documentation, career materials, and learning resources primarily in Markdown format.

**Repository:** git@github.com:m0rfiin-m/Octarine-Docs.git

**Local Paths:**
- macOS: `/Users/marcomorfin/Octarine Documents/Marco-Morfin`
- Windows: `D:\Octarine`

## Repository Structure

```
Marco-Morfin/
├── AAS in AI Software Engineering/  # Academic coursework (Python PY101)
│   └── PY101/                       # Python fundamentals lessons by week
├── AI-Agents/                       # AI agent prompts and configurations
├── Career/                          # Resume and professional materials
├── Claude Memory Bank/              # Long-term context for Claude interactions
│   ├── *.md                         # Various technical knowledge documents
│   └── Templates/                   # Reusable templates
├── Daily/                           # Daily note storage (empty, generated as needed)
├── How To's/                        # Step-by-step guides and tutorials
├── Telos/                           # Goal-oriented planning documents
├── Web-Development/                 # Web development learning materials
│   ├── HTML Fundamentals/
│   ├── Labs/
│   └── Theory/
├── .octarine/                       # Octarine system configuration
│   └── properties.json              # Document metadata schema
└── .templates/                      # Note templates
    ├── Daily Standup.md
    └── Gratitude.md
```

## Git Workflow

### Sync Method
- **Automated:** Obsidian Git plugin handles commits/pushes every 10-30 minutes
- **Manual Operations:** Use LazyGit when available (keybindings: `p` = pull, `P` = push)

### Important Considerations
- Changes are auto-committed by Octarine/Obsidian Git plugin
- Folder names must NOT have trailing spaces (Windows compatibility issue)
- Always pull before making changes to avoid branch divergence
- SSH authentication is configured (passwordless)

### Common Commands
```bash
# Check status
git status

# View recent commits
git log --oneline -10

# Pull latest changes (if needed manually)
git pull --rebase origin main

# View remote
git remote -v
```

## Working with Files

### File Format
All content files use Markdown (.md) with:
- Frontmatter properties defined in `.octarine/properties.json`
- Common properties: tags, Status, Word Count, Due Date, Last Edited, Published, Author, date

### Naming Conventions
- Spaces in filenames are standard (e.g., "How to Setup Automatic Daily Notes Template.md")
- No trailing spaces in folder names (critical for Windows sync)
- Descriptive, human-readable names

### Templates
Located in `.templates/`:
- **Daily Standup.md** - Simple three-section daily note (Morning/Throughout/End of Day)
- **Gratitude.md** - Gratitude journaling template

## Content Categories

### Claude Memory Bank
Long-term context documents that provide Claude with persistent knowledge about:
- Technical setup and workflows (Git, LazyVim, Obsidian)
- Writing style and preferences
- System configurations (Windows, Linux)
- Professional materials (resumes, cover letters, interviews)

**Key Files:**
- `Obsidian Vault Management.md` - Vault structure, templates, sync config
- `Git Workflow.md` - Repository patterns and common issues
- `LazyVim Customization.md` - Neovim configuration
- `Email Protocols.md` / `Email Writing Style.md` - Communication preferences

### AI Agents
Specialized prompts for different tasks:
- **Coding-Agent.md** - Casey Muratori-inspired verification-first programming approach
- **Content Strategy Agent.md** - Content planning and strategy
- **Finance Agent.md** - Financial management
- **Personal Assistant.md** - General assistance tasks

### Educational Content
- **AAS in AI Software Engineering/PY101/** - Python programming course materials organized by week
- **Web-Development/** - HTML fundamentals, theory, and lab exercises
- **How To's/** - Technical guides (MCP servers, system setup, automation)

### Personal Documents
- **Career/** - Resume and professional materials
- **Telos/** - Goal-oriented planning (Career, Health, Projects, Learning, Personal)
- **Daily/** - Daily notes (auto-generated, not committed to repo)

## Writing Style Preferences

Based on analysis of existing documents in Claude Memory Bank:

- No em dashes (—) - use regular dashes or alternative punctuation
- Direct, conversational tone
- Avoid filler phrases and hedging language (might, could, perhaps)
- Use emojis for visual organization in technical docs
- Comprehensive table of contents structures
- Step-by-step numbered instructions with troubleshooting sections
- ASCII diagrams for technical documentation
- Bold emphasis for UI elements and important terms
- Horizontal rules (---) between major sections

## Common Tasks

### Adding New Content
```bash
# Navigate to appropriate directory
cd "How To's"  # or other category

# Create new file (use quotes for spaces)
touch "How to [Task Name].md"

# Files auto-sync via Octarine/Obsidian Git
```

### Searching Content
```bash
# Find files by pattern
find . -name "*keyword*" -type f

# Search content across all markdown files
grep -r "search term" --include="*.md"

# Search specific directory
grep -r "search term" "Claude Memory Bank" --include="*.md"
```

### Viewing Recent Changes
```bash
# See what's changed recently
git log --since="1 week ago" --oneline

# View changes in specific file
git log -p "path/to/file.md"
```

## LazyVim Integration

When working in LazyVim (if available):
- File finding: `Space + f + f`
- Grep search: `Space + s + g`
- File tree: `Space + e`
- LazyGit: `Space + g + g`
- Vertical split: `Space + |`
- Horizontal split: `Space + -`

Reference: `lazyvim-navigation-guide.md` for complete shortcuts

## Important Notes

1. **Cross-Platform Sync:** This vault syncs between macOS and Windows - avoid trailing spaces in folder names
2. **Auto-Commits:** Changes are automatically committed by Octarine - manual commits rarely needed
3. **Document Metadata:** Files may have frontmatter properties from Octarine system
4. **Daily Notes:** Generated dynamically, not stored in repo (`.gitignore` excludes them)
5. **No Build Process:** This is a documentation repository - no compilation, testing, or deployment steps
6. **Read-Only External Content:** `Claude Memory Bank/lazyvim.github.io-main/` is reference material, do not modify

## Special Considerations

### When Adding Technical Documentation
- Follow existing format in "How To's" directory
- Include troubleshooting sections
- Use clear step-by-step instructions
- Reference related documents at bottom

### When Updating Claude Memory Bank
- These files inform Claude's long-term understanding
- Be comprehensive but concise
- Include "Last Updated" date at top
- Use structured sections with horizontal rules
- Add "Related:" links at bottom

### When Working with Educational Content
- Maintain lesson numbering and organization
- Keep week-based structure intact
- Preserve markdown formatting and code blocks
