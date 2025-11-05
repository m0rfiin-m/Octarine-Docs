# Git & GitHub Workflow

**Last Updated:** October 24, 2025

---

## Overview

Marco's Git workflow patterns, repository management, and GitHub collaboration understanding.

---

## Repository Management

### Octarine-Docs Repository
- **Location:** `git@github.com:m0rfiin-m/Octarine-Docs.git`
- **Local Paths:**
  - Mac: `~/Octarine Documents/Marco-Morfin`
  - Windows: `D:\Octarine`
- **Sync Method:** Obsidian Git plugin for automated commits/pushes

### Blog Repository
- **Repository:** m0rfiin-blog
- **Purpose:** Hugo static site
- **Deployment:** GitHub Pages
- **Workflow Issue:** Created GitHub Pages workflow directly on GitHub, causing branch divergence
  - Required rebase: `git pull --rebase origin main`

### Common Sync Issues
- **Folder Naming Problems:** Trailing spaces in folder names (e.g., "AI Agents /") invalid on Windows
  - Solution: Rename folders on Mac to remove trailing spaces before cloning on Windows
- **Branch Divergence:** Local edits + GitHub web changes = diverged branches
  - Solution: Always pull before making local changes

---

## LazyVim Notes Repository Sync

### Initial Problem
- Local changes not syncing to GitHub repo (m0rfiin-m/Octarine-Docs)
- **Root Cause:** Editing files in parent "Octarine Documents" folder while git repository in subfolder "Marco-Morfin"
- Had 4 local commits ahead of origin/main that weren't pushed

### Solution
- Identified correct git repository location
- Successfully pushed commits using LazyGit
- Learned terminal navigation (`cd` commands) during troubleshooting

---

## SSH Authentication

### Setup Process
- Generated SSH key: `ssh-keygen -t ed25519 -C "m.m0rfiin@gmail.com"`
- Configured SSH agent on Windows
- Added public key to GitHub account
- Enables passwordless authentication across Mac and Windows

---

## GitHub Collaboration Philosophy

### Current Understanding
- Questions why GitHub lacks real-time collaboration like Google Docs
- Interest in "sync system where two people can see where other person is typing"

### Claude's Perspective Shared
- Git designed for distributed, asynchronous work (not real-time)
- Commit-based workflow provides:
  - Accountability and attribution
  - Branching for safe experimentation
  - Code review checkpoints
  - Offline work capability
- GitHub Codespaces now supports real-time collaboration (Live Share)
- Real-time editing works for documents, problematic for code (one character can break application)

### Industry Comparison
- Entertainment industry analogy: Hollywood production pipeline (sequential, reviewed stages)
- Git optimizes for large open-source projects (thousands of contributors)
- Small teams (5-10 people) might benefit from different collaboration model
- AI could potentially resolve semantic conflicts (not just text diffs)

---

## Repository Cleanup

### Fresh Start Protocol
- Successfully cleared all Git repos from Mac: `find ~ -name ".git" -type d -exec rm -rf {} +`
- Deleted GitHub repos remotely first
- Local Git tracking removed while preserving project files
- Can reinitialize repos as needed: `git init`

---

## LazyGit Usage

### Keybindings
- **CORRECT:** `p` = pull, `P` = push (Marco confirmed correction)
- Initially confused keybindings
- Used for committing changes and pushing to remote

### Workflow
- Stage files with space
- Commit with `c`
- Push with `P`
- Visual interface for diffs and commit history

---

## Common Patterns

### When Things Go Wrong
1. Check git status
2. Verify correct repository location (`git remote -v`)
3. Check for unpushed commits (`git log origin/main..HEAD`)
4. Pull before making changes to avoid divergence
5. Use rebase for cleaner history when appropriate

---

## Future Considerations

- Potential CS degree project: AI-powered semantic merge conflict resolver
- Interest in understanding operational transformation (how Google Docs multiplayer works)
- Curiosity about why Mercurial/Darcs/Fossil failed despite technical superiority
- Game industry's rejection of Git (Perforce model)

---

**Related:** [[LazyVim Customization]], [[Technical Setup]], [[Obsidian Vault Management]]
