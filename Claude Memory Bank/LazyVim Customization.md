# LazyVim Customization

**Last Updated:** October 24, 2025

---

## Overview

Documentation for customizing LazyVim (Neovim distribution) including dashboard modifications, ASCII art integration, and UI theming aligned with Matte Black aesthetic.

---

## Dashboard Configuration

### Plugin: alpha.nvim

**LazyVim Default:** Uses alpha.nvim for dashboard (not dashboard-nvim)

**Configuration Location:**  
`~/.config/nvim/lua/plugins/`

**Key Files:**
- `alpha.lua` - Main dashboard configuration
- `my-dashboard.lua` - Custom dashboard overrides
- `disable-dashboard.lua` - File that can block custom dashboards (remove if present)

---

### Custom Dashboard Setup

**Basic Structure:**

```lua
return {
  "goolord/alpha-nvim",
  opts = function(_, dashboard)
    -- Custom header (ASCII art)
    local header = {
      "  ▄▄▄▄▄▄▄  ",
      " ███▄▄▄███ ",
      " ███████▀  ",
      "  ▀███▀    ",
      "    █      ",
    }
    
    dashboard.section.header.val = header
    
    return dashboard
  end,
}
```

**Important:** Each line of ASCII art must be a string in a table/array format.

---

## ASCII Art Integration

### Character Techniques

**Character Density Mapping:**
- Dense characters: `█ ▓ ▒ ░ ■ ▪` (darkest/most solid)
- Medium density: `# @ & % * +` (medium fill)
- Light characters: `. · ° , ' ` (subtle details)
- Space: ` ` (empty areas)

**Professional Approach:**
1. Find high-quality ASCII art from established sources
2. Replicate exactly - don't create from scratch
3. Use proper character density for shading
4. Maintain aspect ratio and proportions
5. Test in actual terminal to verify appearance

**Recommended Sources:**
- ascii.co.uk (established ASCII art collections)
- Joan Stark's work (legendary ASCII artist)
- ASCII Art Archive
- Text-image converters for photos/images

---

## Implemented Designs

### Pacman with Ghost

**Current Dashboard:** Pacman with ghost design (gaming aesthetic)

**Implementation Notes:**
- Uses block characters for solid shapes
- Orange/yellow for Pacman (matches Matte Black accent)
- White/cyan for ghost
- Clean geometric shapes
- Balanced composition

---

### ASCII Art Request History

**October 24, 2025:**

**Initial Requests:**
1. Peace sign emoticon ✌(◕‿-)✌ → ASCII conversion
2. Large smiley face
3. Kawaii emoticon (◕‿◕) → Large ASCII version

**Design Iterations:**
- Star designs (rejected - "ugly", "takes more real estate")
- Anime girl design (rejected - "terrible")
- Ghost design (explored)
- Pacman with ghost (final implementation)

**Key Learning:**  
User prefers replication of existing high-quality ASCII art rather than original creations. Focus on finding and adapting established designs.

[Dashboard Customization Conversation](https://claude.ai/chat/bb310217-5234-4cfa-81a6-5aacc2ed059c)  
[ASCII Conversion Conversation](https://claude.ai/chat/70fe123d-25e1-421a-b0aa-fd4ce5365f26)

---

## Configuration Best Practices

### File Organization

**Plugins Directory Structure:**
```
~/.config/nvim/lua/plugins/
├── alpha.lua (main dashboard config)
├── matte-black.lua (colorscheme)
└── [other plugin configs]
```

**Common Issues:**
- `disable-dashboard.lua` blocking custom dashboards → Delete this file
- Wrong plugin (dashboard-nvim vs alpha.nvim) → LazyVim uses alpha.nvim
- Syntax errors in Lua → Validate table structure
- Missing return statement → Always return the configuration

---

### Alpha.nvim Syntax

**Correct Format:**

```lua
return {
  "goolord/alpha-nvim",
  opts = function(_, dashboard)
    dashboard.section.header.val = {
      "Line 1",
      "Line 2",
      "Line 3",
    }
    return dashboard
  end,
}
```

**Key Points:**
- Header value is a table/array of strings
- Each ASCII art line is a separate string
- Return the dashboard object
- Use `opts` function for customization

---

## Dashboard Components

### Available Sections

**Standard Alpha.nvim Sections:**
- `header` - ASCII art at top
- `buttons` - Quick action buttons
- `footer` - Bottom text/info

**Customization Options:**
- Change ASCII art header
- Modify button actions and labels
- Add custom footer messages
- Adjust spacing and layout
- Apply Matte Black color scheme

---

## Matte Black Theme Integration

**Colorscheme Application:**
- Dashboard respects global colorscheme
- ASCII art uses theme colors automatically
- Orange accents highlight active elements
- Dark background matches Matte Black aesthetic

**Theme Files:**
- `matte-black.lua` in plugins directory
- Consistent with Omarchy color palette
- Applied across all LazyVim UI elements

---

## Emoticon to ASCII Conversion

### Conversion Process

**Standard Emoticons:**
- Small text emoticons (◕‿◕) → Large ASCII representations
- Maintain character and expression
- Scale proportionally
- Use appropriate character density

**Example: Kawaii Face (◕‿◕)**

```
    ▄▄▄▄▄       ▄▄▄▄▄
  ▄▀     ▀▄   ▄▀     ▀▄
 █   ●    █ █   ●    █
  ▀▄     ▄▀   ▀▄     ▄▀
    ▀▀▀▀▀       ▀▀▀▀▀
    
       ▄▀▀▀▀▀▄
      █       █
       ▀▄▄▄▄▄▀
```

**Format for Alpha.nvim:**
```lua
local header = {
  "    ▄▄▄▄▄       ▄▄▄▄▄    ",
  "  ▄▀     ▀▄   ▄▀     ▀▄  ",
  " █   ●    █ █   ●    █ ",
  "  ▀▄     ▄▀   ▀▄     ▄▀  ",
  "    ▀▀▀▀▀       ▀▀▀▀▀    ",
  "                          ",
  "       ▄▀▀▀▀▀▄      ",
  "      █       █     ",
  "       ▀▄▄▄▄▄▀      ",
}
```

---

## Resources

**Documentation:**
- [Alpha.nvim GitHub](https://github.com/goolord/alpha-nvim)
- [LazyVim Extras: UI - Alpha](alpha.md)
- [Omarchy Matte Black Theme](https://github.com/basecamp/omarchy/tree/master/themes/matte-black)

**ASCII Art Sources:**
- ascii.co.uk
- Joan Stark ASCII Art Collection
- ASCII Art Archive
- Text-to-ASCII image converters

---

## Troubleshooting

**Dashboard Not Showing:**
1. Check for `disable-dashboard.lua` file → Remove it
2. Verify alpha.nvim is installed
3. Check Lua syntax in config files
4. Restart Neovim completely

**ASCII Art Misaligned:**
1. Use monospace-friendly characters
2. Test in actual terminal
3. Ensure consistent spacing
4. Verify character encoding (UTF-8)

**Theme Not Applied:**
1. Check colorscheme is loaded
2. Verify matte-black.lua is in plugins directory
3. Source config: `:source ~/.config/nvim/init.lua`
4. Restart Neovim

---

## Future Enhancements

**Potential Additions:**
- Animated dashboard elements
- Dynamic ASCII art rotation
- Time/date display integration
- Recent files section styling
- Custom button configurations
- Seasonal theme variations

---

## Related Documents

- [[Technical Setup]] - macOS development environment
- [[System Maintenance]] - Configuration troubleshooting

---

**Back to:** [[Claude Memory Bank/Index]]
# LazyVim Customization

**Last Updated:** October 24, 2025

---

## Overview

Comprehensive knowledge of Marco's LazyVim setup, configuration preferences, and customization journey.

---

## Configuration Journey

### Initial Setup Challenges
- **Dashboard Customization Issues** - Struggled with overriding default LazyVim dashboard with custom "MORFIN" ASCII art
- Made approximately 100 different configuration attempts before finding correct solution
- Key lesson: LazyVim uses `opts` for dashboard configuration, not `config`
- Only one properly configured file needed to override defaults

**Solution:** Properly structured plugin specification format:
```lua
return {
  "nvimdev/dashboard-nvim",
  event = "VimEnter",
  opts = function()
    -- configuration here
  end
}
```

### Custom Dashboard
- Created custom ASCII art logo spelling "MORFIN"
- Uses doom theme
- Custom action buttons for common tasks (file finding, text searching)
- Footer with statistics

### Navigation Preferences
- Coming from PC gaming background, prefers WASD-style navigation
- Modified standard Vim hjkl to ijkl in configurations
- Practices hands-on learning with immediate feedback

---

## Portable Configuration

### M0RFIIN Settings Repository
- **Purpose:** Portable LazyVim configuration for easy syncing across systems
- **Approach:** Minimal overlay that adds to LazyVim without replacing base functionality
- **Key Features:**
  - Matte Black theme as default
  - Custom "M0RFIIN" dashboard header
  - Only plugins not in LazyVim base installation

### Multi-System Setup
- **Primary:** macOS (M1 MacBook)
- **Secondary:** Windows PC
- Configuration synced via GitHub repository

---

## Plugin Management

### Installed Extras
- LazyGit integration (manually installed after built-in extra showed gitui)
- System installation: `brew install lazygit`
- Plugin configuration added separately

### Theme Preferences
- **Installed Themes:**
  - catppuccin (set as default - catppuccin-mocha variant)
  - gruvbox
  - nord
  - nightfox
  - onedark
- Can switch between themes dynamically

---

## File Operations

### Markdown Workflow
- Automatic text wrapping at 80 characters for Markdown files configured
- Reformat long lines using: `ggVGgq`
- Format current paragraph: `gwap`

### Linting
- Markdown linting enabled
- Common warnings:
  - MD041: First line should be top-level heading
  - MD012: Multiple consecutive blank lines

---

## Terminal Integration

### Ghostty Terminal
- Primary terminal emulator
- Config location: `~/.config/ghostty/config`
- Theme: tokyo-night
- Had configuration errors with unsupported parameters (tab-bar-style, window-title)

---

## Learning Style

- Prefers step-by-step instructions over theoretical explanations
- Best learns through hands-on practice with immediate feedback
- Interested in replicating "beast mode" LazyVim setups from YouTube videos

---

## Integration with Octarine/Obsidian

- Uses LazyVim for both note-taking and coding
- Octarine vault path: `~/Octarine Documents/Marco-Morfin`
- Programming projects: `~/Programming`
- Shell aliases configured for quick navigation:
  - `vault='cd "$HOME/Octarine Documents/Marco-Morfin" && nvim'`
  - `code='cd "$HOME/Programming" && nvim'`

---

## Common Issues & Solutions

### "Unsupported finder" Errors
- **Cause:** Missing fd command-line tool
- **Solution:** `brew install fd`

### Dashboard Not Loading
- **Cause:** Improper plugin specification format or file structure
- **Solution:** Ensure proper return statement and LazyVim plugin spec format

---

## Future Exploration

- Interest in system-wide Vim keybindings through KindaVim (advised to master LazyVim first)
- Considering Aerospace tiling window manager for macOS workspace management

---

**Related:** [[Technical Setup]], [[System Maintenance]]
