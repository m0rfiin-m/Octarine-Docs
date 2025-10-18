
# Quick Start Guide

Get up and running with Octarine MCP Server in 5 minutes.

## Prerequisites

- Node.js 18+ installed
- Claude Desktop or another MCP client
- Basic terminal knowledge

## Installation

bash

```bash
npm install -g octarine-mcp-server
```

## Configuration

### Step 1: Create Workspace Directory

bash

```bash
mkdir -p ~/Documents/Octarine/Projects
```

### Step 2: Configure Claude Desktop

**macOS:** Edit `~/Library/Application Support/Claude/claude_desktop_config.json`:

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "/Users/YOUR_USERNAME/Documents/Octarine"
      }
    }
  }
}
```

**Windows:** Edit `%APPDATA%\Claude\claude_desktop_config.json`:

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx.cmd",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "C:\\Users\\YOUR_USERNAME\\Documents\\Octarine"
      }
    }
  }
}
```

### Step 3: Restart Claude Desktop

Close and reopen Claude Desktop to load the server.

## Usage

### Create Your First Note

In Claude:

```plaintext
Create a note in my Projects workspace called "ideas.md" with a heading and list of three project ideas.
```

### Read a Note

```plaintext
Show me the contents of ideas.md from my Projects workspace.
```

### Search Notes

```plaintext
Search all my notes for the word "innovation"
```

### List Notes

```plaintext
List all notes in my Projects workspace
```

## Common Commands

```plaintext
```

| Task | Example Prompt |
| --- | --- |
| Create note | "Create a meeting notes file in Projects workspace" |
| Read note | "Read the contents of [README.md](http://README.md) from Projects" |
| Update note | "Add a new section to my [ideas.md](http://ideas.md) file" |
| Search | "Find all notes mentioning 'deadline'" |
| List files | "Show me all notes in the Work workspace" |

## Next Steps

- **Full Documentation**: Read [README.md](http://README.md) for complete features
- **API Reference**: Check [API_](./API_REFERENCE.md)[REFERENCE.md](http://REFERENCE.md) for detailed API docs
- **Advanced Setup**: See [SETUP_](./SETUP_GUIDE.md)[GUIDE.md](http://GUIDE.md) for advanced configuration

## Troubleshooting

**Server not connecting?**

1. Check Node.js version: `node --version` (must be 18+)
2. Verify installation: `npx octarine-mcp-server --version`
3. Check config file JSON syntax

**Workspace not found?**

1. Verify the workspace path exists
2. Use absolute paths, not relative
3. Check path matches your OS (/ for Unix, \\ for Windows)

**Permission denied?**

1. Check directory permissions: `ls -la ~/Documents/Octarine`
2. Ensure you can read/write: `touch ~/Documents/Octarine/test.txt`

## Support

- [GitHub Issues](https://github.com/yourusername/octarine-mcp-server/issues)
- [Discord Community](https://discord.gg/yourserver)
- [Documentation](./README.md)

---

**Ready to go deeper?** Check out the [full documentation](./README.md)!