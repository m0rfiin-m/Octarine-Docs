# LazyVim Navigation Guide

## Essential Navigation Shortcuts

### File & Project Navigation

```
Space + f + f    Find files (fuzzy search current project)
Space + f + r    Recent files
Space + f + g    Find files in git repo
Space + f + p    Switch between projects
Space + s + g    Search text across all files (grep)
Space + s + w    Search word under cursor
Space + ,        Switch between open buffers
Space + e        Toggle file explorer (left sidebar)
```

### Window Splits

```
Space + |        Vertical split (side by side)
Space + -        Horizontal split (top/bottom)
Ctrl + w + h     Move to left split
Ctrl + w + l     Move to right split
Ctrl + w + j     Move to bottom split
Ctrl + w + k     Move to top split
Ctrl + w + q     Close current split
Ctrl + w + =     Make all splits equal size
Ctrl + w + >     Make split wider
Ctrl + w + <     Make split narrower
```

### Terminal

```
Space + f + t    Toggle floating terminal
Ctrl + \         Toggle terminal (may vary by config)
:terminal        Open terminal in current window
```

### Buffer Management

```
Space + b + d    Delete/close current buffer
Space + b + p    Pin/unpin buffer
[ + b            Previous buffer
] + b            Next buffer
Space + ,        Show all open buffers (quick switch)
```

### Movement Within Files

```
g + g            Go to top of file
G                Go to bottom of file
Ctrl + d         Scroll down half page
Ctrl + u         Scroll up half page
Ctrl + o         Jump to previous location
Ctrl + i         Jump to next location
{ / }            Jump between paragraphs/code blocks
% 	             Jump to matching bracket/parenthesis
```

### Copy, Paste & Selection (Visual Mode)

#### Visual Mode (Selecting/Highlighting)

```
v                Enter visual mode (character selection)
V                Enter visual line mode (select entire lines)
Ctrl + v         Enter visual block mode (column/rectangular selection)
```

#### Expanding Selection (once in visual mode)

```
h/j/k/l          Move to expand selection
w                Select to next word
b                Select to previous word
$                Select to end of line
0                Select to start of line
G                Select to end of file
g + g            Select to start of file
}                Select to end of paragraph
{                Select to start of paragraph
```

#### Yanking (Copying)

```
y                Yank (copy) selected text
yy               Yank entire current line (no visual mode needed)
y + w            Yank word under cursor
y + $            Yank from cursor to end of line
y + G            Yank from cursor to end of file
y + i + "        Yank text inside quotes
y + i + (        Yank text inside parentheses
y + i + {        Yank text inside braces
y + a + "        Yank text around quotes (includes quotes)
```

#### Pasting

```
p                Paste after cursor / below line
P                Paste before cursor / above line
```

#### Cutting (Delete = Cut)

```
d                Delete selected text (also copies to clipboard)
dd               Delete/cut entire line
d + w            Delete/cut word
d + $            Delete/cut from cursor to end of line
c                Change (delete and enter insert mode)
cc               Change entire line
```

#### System Clipboard

```
" + y            Yank to system clipboard
" + p            Paste from system clipboard
" + d            Delete to system clipboard
```

Use system clipboard to copy/paste between LazyVim and other applications (browser, notes apps, etc.)

#### Common Copy/Paste Workflows

**Copy a line:**
```
yy               Yank line
j or k           Move to destination
p                Paste below current line
```

**Copy multiple lines:**
```
V                Visual line mode
jjj              Select 3 lines (or use 3j)
y                Yank selection
                 (move to destination)
p                Paste
```

**Copy a word:**
```
y + w            Yank word
                 (move to destination)
p                Paste
```

**Copy paragraph:**
```
v                Visual mode
}                Jump to end of paragraph
y                Yank
p                Paste
```

**Copy text inside quotes/brackets:**
```
v + i + "        Select inside quotes
y                Yank
                 (move to destination)
p                Paste
```

**Cut and paste line:**
```
dd               Delete/cut line
                 (move to destination)
p                Paste
```

**Visual block selection (columns):**
```
Ctrl + v         Visual block mode
jjjj             Select down 4 lines
lll              Extend right 3 columns
y                Yank block
                 (move to destination)
p                Paste block
```

**Copy to system clipboard and paste in browser:**
```
V                Visual line mode
jj               Select lines
" + y            Yank to system clipboard
                 Switch to browser
Ctrl + v         Paste (standard system paste)
```

### Line Navigation

```
0                Go to start of line
^                Go to first non-blank character
$                Go to end of line
w                Jump forward to start of word
b                Jump backward to start of word
e                Jump to end of word
```

### Search & Replace

```
/search-term     Search forward
?search-term     Search backward
n                Next search result
N                Previous search result
*                Search for word under cursor
#                Search backward for word under cursor
:%s/old/new/g    Replace all occurrences in file
```

### Git Integration

```
Space + g + g    Open LazyGit (visual git interface)
Space + g + h    Git hunk preview
Space + g + s    Stage hunk
Space + g + u    Unstage hunk
Space + g + b    Blame line
] + h            Next git hunk
[ + h            Previous git hunk
```

### Code Navigation

```
g + d            Go to definition
g + r            Go to references
g + I            Go to implementation
K                Show documentation/hover info
Space + c + a    Code actions
Space + c + r    Rename symbol
[ + d            Previous diagnostic/error
] + d            Next diagnostic/error
```

### File Explorer (when open)

```
a                Add new file/folder (use / for folder)
r                Rename
d                Delete
x                Cut
c                Copy
p                Paste
y + y            Copy filename
Y                Copy relative path
g + y            Copy absolute path
Ctrl + v         Open in vertical split
Ctrl + x         Open in horizontal split
```

### Tabs (if using)

```
Space + Tab + l  Last accessed tab
Space + Tab + n  New tab
Space + Tab + ]  Next tab
Space + Tab + [  Previous tab
Space + Tab + d  Close tab
```

### Quick Actions

```
Space + Space    Find files (alternative)
Space + /        Search in current buffer
Space + :        Command history
Space + k        Show keymaps (this shows ALL shortcuts!)
:q               Quit
:w               Save
:wq              Save and quit
:q!              Quit without saving
```

## Pro Tips

### Combining Commands
- `Ctrl + w + v` then `Space + f + f` = split and open file
- `Space + e` + `a` = open explorer and create new file
- `:cd path` then `Space + f + f` = change directory and find files

### Workspace Navigation Flow
```
1. Space + f + p      Switch to project/repo
2. Space + e          Open file tree to see structure  
3. Space + f + f      Find specific file quickly
4. Space + |          Split if you need reference
5. Ctrl + w + h/l     Jump between splits
```

### Notes + Code Workflow
```
1. Start in vault: cd ~/octarine-vault && nvim
2. Space + e          File tree shows note folders
3. Navigate to note
4. Space + |          Vertical split
5. :cd ~/repos/code-project   Switch project in split
6. Space + f + f      Find code file
7. Now: notes left, code right
8. Ctrl + w + l/h     Jump between them
```

### Terminal Workflow
```
1. Coding in main window
2. Space + -          Horizontal split
3. :terminal          Open terminal below
4. Run tests/commands in terminal
5. Ctrl + w + k       Jump back to code
6. Make changes
7. Ctrl + w + j       Jump to terminal
8. Re-run tests
```

## Learning Path

### Week 1: Core Movement
- `Space + f + f` (find files)
- `Space + e` (file tree)
- `Space + |` and `Space + -` (splits)
- `Ctrl + w + h/j/k/l` (move between splits)
- `:w` and `:q` (save and quit)

### Week 2: Buffer Management
- `Space + ,` (switch buffers)
- `Space + b + d` (close buffer)
- `[ + b` and `] + b` (navigate buffers)

### Week 3: Advanced Navigation
- `Space + s + g` (grep search)
- `Space + f + p` (project switching)
- `g + d` (go to definition)
- `Space + g + g` (lazygit)

### Week 4: Workflow Integration
- Terminal integration (`:terminal`)
- Git workflow (`Space + g + g`)
- Multiple projects open simultaneously
- Custom workflows for your specific needs

## Troubleshooting

**"Nothing happens when I press Space"**
- Wait a moment, popup should appear showing options
- If not, your leader key might be different: try `:echo mapleader`

**"My shortcuts are different"**
- Press `Space + k` to see all your actual keybindings
- LazyVim configs can be customized
- Check `~/.config/nvim/` for custom mappings

**"How do I get back to normal mode?"**
- Press `Esc` or `Ctrl + [`
- You need to be in normal mode for most navigation shortcuts

**"I'm stuck in a split and can't close it"**
- `Ctrl + w + q` closes current split
- `:only` closes all splits except current one
- `Ctrl + w + o` also closes other splits

## Quick Reference Card

Keep this handy while learning:

```
MOST USED (Master These First)
Space + f + f    Find file
Space + e        File tree
Space + |        Vertical split
Ctrl + w + h/l   Move between splits
:w               Save
:q               Quit

DAILY WORKFLOW
Space + s + g    Search all files
Space + ,        Switch buffers
Space + g + g    Git interface
:terminal        Open terminal

CODE NAVIGATION  
g + d            Go to definition
K                Documentation
Space + c + a    Code actions
```

---

**Remember**: Press `Space` and wait to see available commands. LazyVim shows you what's possible.

**Most Important Tip**: Don't memorize everything. Learn 5-6 shortcuts, use them daily until automatic, then add more. Build muscle memory gradually.
