
# Setup Guide

Complete setup and configuration guide for the Octarine MCP Server. This guide covers installation, configuration, troubleshooting, and advanced setup scenarios.

## Table of Contents

- [System Requirements](#system-requirements)
- [Installation Methods](#installation-methods)
- [Basic Configuration](#basic-configuration)
- [Advanced Configuration](#advanced-configuration)
- [MCP Client Setup](#mcp-client-setup)
- [Workspace Configuration](#workspace-configuration)
- [Troubleshooting](#troubleshooting)
- [Upgrade Guide](#upgrade-guide)

## System Requirements

### Minimum Requirements

```plaintext
```

| Component | Requirement |
| --- | --- |
| **Operating System** | macOS 10.15+, Ubuntu 20.04+, Windows 10+ |
| **Node.js** | 18.0.0 or higher |
| **npm** | 9.0.0 or higher |
| **Memory** | 512 MB RAM |
| **Disk Space** | 100 MB free space |

### Recommended Requirements

```plaintext
```

| Component | Requirement |
| --- | --- |
| **Operating System** | macOS 13+, Ubuntu 22.04+, Windows 11+ |
| **Node.js** | 20.0.0 or higher (LTS) |
| **npm** | 10.0.0 or higher |
| **Memory** | 2 GB RAM |
| **Disk Space** | 1 GB free space |

### Verify Prerequisites

bash

```bash
# Check Node.js version
node --version  # Should be >= v18.0.0

# Check npm version
npm --version   # Should be >= 9.0.0

# Check platform
node -p "process.platform"
```

## Installation Methods

### Method 1: Global Installation (Recommended)

Install globally for system-wide access:

bash

```bash
npm install -g octarine-mcp-server
```

**Verify installation:**

bash

```bash
octarine-mcp-server --version
```

**Advantages:**

- Available from anywhere
- Automatic PATH configuration
- Easy to update

**Disadvantages:**

- Requires global npm permissions
- May conflict with other versions

### Method 2: Local Project Installation

Install in a specific project:

bash

```bash
cd /path/to/your/project
npm install octarine-mcp-server
```

**Use with npx:**

bash

```bash
npx octarine-mcp-server
```

**Advantages:**

- Project-specific versions
- No global permissions needed
- Version isolation

**Disadvantages:**

- Must install per project
- Requires npx or local script

### Method 3: Install from GitHub

Install directly from the repository:

bash

```bash
# Latest release
npm install -g github:yourusername/octarine-mcp-server

# Specific version/branch
npm install -g github:yourusername/octarine-mcp-server#v1.2.3
npm install -g github:yourusername/octarine-mcp-server#develop
```

**Advantages:**

- Access to unreleased features
- Install specific commits
- Development versions

**Disadvantages:**

- May be unstable
- Requires Git
- No version guarantees

### Method 4: Build from Source

For contributors or custom builds:

bash

```bash
# Clone repository
git clone https://github.com/yourusername/octarine-mcp-server.git
cd octarine-mcp-server

# Install dependencies
npm install

# Build TypeScript
npm run build

# Link globally (optional)
npm link

# Or run directly
node dist/index.js
```

**Advantages:**

- Full control over code
- Latest development changes
- Custom modifications

**Disadvantages:**

- Requires build tools
- Manual updates
- More complex

## Basic Configuration

### Quick Start Configuration

Minimal configuration to get started:

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx",
      "args": ["-y", "octarine-mcp-server"]
    }
  }
}
```

### Environment Variables

Set up basic environment variables:

#### macOS/Linux

Create `~/.octarinerc`:

bash

```bash
export OCTARINE_WORKSPACE_PATH="$HOME/Documents/Octarine"
export OCTARINE_LOG_LEVEL="info"
```

Load in shell profile (`~/.zshrc` or `~/.bashrc`):

bash

```bash
source ~/.octarinerc
```

#### Windows

Set environment variables via PowerShell:

powershell

```powershell
[Environment]::SetEnvironmentVariable(
    "OCTARINE_WORKSPACE_PATH",
    "$env:USERPROFILE\Documents\Octarine",
    "User"
)

[Environment]::SetEnvironmentVariable(
    "OCTARINE_LOG_LEVEL",
    "info",
    "User"
)
```

Or via Command Prompt:

cmd

```cmd
setx OCTARINE_WORKSPACE_PATH "%USERPROFILE%\Documents\Octarine"
setx OCTARINE_LOG_LEVEL "info"
```

### Configuration File

Create `.octarinerc.json` in your workspace root:

json

```json
{
  "workspacePath": "/path/to/workspaces",
  "logLevel": "info",
  "maxFileSize": 10485760,
  "searchLimit": 100
}
```

## Advanced Configuration

### Custom Workspace Locations

Configure multiple workspaces with custom paths:

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/Users/username/Projects",
      "readOnly": false,
      "maxFileSize": 10485760,
      "description": "Active project notes"
    },
    "Archive": {
      "path": "/Users/username/Archive",
      "readOnly": true,
      "description": "Archived notes (read-only)"
    },
    "Work": {
      "path": "/Users/username/Work",
      "readOnly": false,
      "excludePatterns": ["**/node_modules/**", "**/.git/**"],
      "description": "Work-related notes"
    }
  }
}
```

#### Workspace Options

```plaintext
```

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `path` | string | Required | Absolute path to workspace directory |
| `readOnly` | boolean | `false` | Prevent write operations |
| `maxFileSize` | number | `10485760` | Max file size in bytes (10MB) |
| `excludePatterns` | string[] | `[]` | Glob patterns to exclude |
| `description` | string | `""` | Human-readable description |

### Search Configuration

Fine-tune search behavior:

json

```json
{
  "search": {
    "caseSensitive": false,
    "includeHidden": false,
    "maxResults": 100,
    "previewLength": 200,
    "highlightMatches": true,
    "indexing": {
      "enabled": false,
      "updateInterval": 300000
    }
  }
}
```

#### Search Options

```plaintext
```

| Option | Type | Default | Description |
| --- | --- | --- | --- |
| `caseSensitive` | boolean | `false` | Case-sensitive matching |
| `includeHidden` | boolean | `false` | Include hidden files (starting with `.`) |
| `maxResults` | number | `100` | Maximum search results |
| `previewLength` | number | `200` | Characters in preview |
| `highlightMatches` | boolean | `true` | Include match highlights |

### Logging Configuration

Configure logging for debugging and monitoring:

json

```json
{
  "logging": {
    "level": "info",
    "file": "/var/log/octarine/server.log",
    "console": true,
    "format": "json",
    "rotation": {
      "enabled": true,
      "maxSize": "10M",
      "maxFiles": 5
    }
  }
}
```

#### Log Levels

```plaintext
```

| Level | Description | Use Case |
| --- | --- | --- |
| `error` | Error messages only | Production |
| `warn` | Warnings and errors | Production |
| `info` | General information | Default |
| `debug` | Detailed debugging | Development |
| `trace` | Very detailed debugging | Deep debugging |

### Performance Tuning

Optimize for your use case:

json

```json
{
  "performance": {
    "caching": {
      "enabled": true,
      "ttl": 300000,
      "maxSize": 100
    },
    "concurrency": {
      "maxConcurrentReads": 10,
      "maxConcurrentWrites": 5,
      "maxConcurrentSearches": 3
    },
    "rateLimit": {
      "enabled": true,
      "windowMs": 60000,
      "maxRequests": {
        "read": 1000,
        "write": 100,
        "search": 50,
        "list": 500
      }
    }
  }
}
```

## MCP Client Setup

### Claude Desktop

#### macOS

1. **Locate config file:**

bash

```bash
~/Library/Application Support/Claude/claude_desktop_config.json
```

2. **Edit configuration:**

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "/Users/username/Documents/Octarine",
        "OCTARINE_LOG_LEVEL": "info"
      }
    }
  }
}
```

3. **Restart Claude Desktop**
4. **Verify in Claude:**

```plaintext
Can you list my octarine workspaces?
```

#### Windows

1. **Locate config file:**

```plaintext
%APPDATA%\Claude\claude_desktop_config.json
```

Or:

powershell

```powershell
$env:APPDATA\Claude\claude_desktop_config.json
```

2. **Edit configuration:**

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx.cmd",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "C:\Users\username\Documents\Octarine",
        "OCTARINE_LOG_LEVEL": "info"
      }
    }
  }
}
```

3. **Restart Claude Desktop**

#### Linux

1. **Locate config file:**

bash

```bash
~/.config/Claude/claude_desktop_config.json
```

2. **Edit configuration:**

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "/home/username/Documents/Octarine",
        "OCTARINE_LOG_LEVEL": "info"
      }
    }
  }
}
```

3. **Restart Claude Desktop**

### Custom MCP Client

For custom implementations:

typescript

```typescript
import { Client } from '@modelcontextprotocol/sdk/client/index.js';
import { StdioClientTransport } from '@modelcontextprotocol/sdk/client/stdio.js';

const transport = new StdioClientTransport({
  command: 'npx',
  args: ['-y', 'octarine-mcp-server'],
  env: {
    OCTARINE_WORKSPACE_PATH: '/path/to/workspaces',
  },
});

const client = new Client({
  name: 'my-mcp-client',
  version: '1.0.0',
}, {
  capabilities: {},
});

await client.connect(transport);

// Use tools
const result = await client.callTool({
  name: 'octarine_read_note',
  arguments: {
    workspace: 'Projects',
    note_path: 'README.md',
  },
});
```

## Workspace Configuration

### Creating Workspaces

#### Basic Workspace Setup

1. **Create workspace directory:**

bash

```bash
mkdir -p ~/Documents/Octarine/Projects
mkdir -p ~/Documents/Octarine/Work
mkdir -p ~/Documents/Octarine/Personal
```

2. **Configure in** `.octarinerc.json`**:**

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/Users/username/Documents/Octarine/Projects"
    },
    "Work": {
      "path": "/Users/username/Documents/Octarine/Work"
    },
    "Personal": {
      "path": "/Users/username/Documents/Octarine/Personal"
    }
  }
}
```

#### Workspace with Templates

Create a template structure:

bash

```bash
Projects/
├── .templates/
│   ├── project.md
│   ├── meeting.md
│   └── task.md
├── Active/
├── Archive/
└── Ideas/
```

### Linking Existing Directories

Link existing note directories:

json

```json
{
  "workspaces": {
    "Obsidian": {
      "path": "/Users/username/Documents/Obsidian Vault"
    },
    "Notion": {
      "path": "/Users/username/Documents/Notion Export"
    },
    "Dropbox": {
      "path": "/Users/username/Dropbox/Notes"
    }
  }
}
```

### Workspace Permissions

#### Read-Only Workspace

Protect sensitive or archived notes:

json

```json
{
  "workspaces": {
    "Archive": {
      "path": "/path/to/archive",
      "readOnly": true
    }
  }
}
```

#### Workspace Access Control

Use filesystem permissions:

bash

```bash
# Owner read/write, group read, others none
chmod 750 /path/to/workspace

# Owner read/write/execute on directories
chmod 700 /path/to/sensitive-workspace
```

## Troubleshooting

### Common Issues

#### Server Not Starting

**Symptom:** MCP client can't connect to server

**Solutions:**

1. **Check Node.js version:**

bash

```bash
node --version  # Must be >= 18.0.0
```

2. **Verify installation:**

bash

```bash
which octarine-mcp-server
# or
npm list -g octarine-mcp-server
```

3. **Check configuration syntax:**

bash

```bash
# Validate JSON
python -m json.tool claude_desktop_config.json
# or
jq . claude_desktop_config.json
```

4. **View error logs:**

bash

```bash
# macOS
tail -f ~/Library/Logs/Claude/mcp*.log

# Windows
Get-Content "$env:APPDATA\Claude\logs\mcp*.log" -Wait

# Linux
tail -f ~/.local/share/Claude/logs/mcp*.log
```

#### Workspace Not Found

**Symptom:** "Workspace not found" error

**Solutions:**

1. **Check workspace path:**

bash

```bash
# Verify directory exists
ls -la /path/to/workspace

# Check permissions
ls -ld /path/to/workspace
```

2. **Verify configuration:**

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/absolute/path/to/Projects"  // Must be absolute
    }
  }
}
```

3. **Check for typos:**

bash

```bash
# Case-sensitive on Unix
/Users/username/projects  ≠  /Users/username/Projects
```

#### Permission Denied

**Symptom:** "Permission denied" when reading/writing

**Solutions:**

1. **Check file permissions:**

bash

```bash
ls -la /path/to/workspace
```

2. **Fix permissions:**

bash

```bash
# Give yourself access
chmod -R u+rw /path/to/workspace

# For directories
find /path/to/workspace -type d -exec chmod u+x {} \;
```

3. **Check read-only setting:**

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/path/to/Projects",
      "readOnly": false  // Ensure not read-only
    }
  }
}
```

#### Search Performance Issues

**Symptom:** Searches are slow

**Solutions:**

1. **Limit search scope:**

typescript

```typescript
// Search specific workspace instead of all
await searchNotes({
  query: "TODO",
  workspace: "Projects"  // Much faster
});
```

2. **Exclude large directories:**

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/path/to/Projects",
      "excludePatterns": [
        "**/node_modules/**",
        "**/.git/**",
        "**/build/**"
      ]
    }
  }
}
```

3. **Reduce result limit:**

json

```json
{
  "search": {
    "maxResults": 50  // Lower than default 100
  }
}
```

#### File Too Large Error

**Symptom:** "File too large" when reading/writing

**Solutions:**

1. **Increase file size limit:**

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/path/to/Projects",
      "maxFileSize": 20971520  // 20MB instead of 10MB
    }
  }
}
```

2. **Split large files:**

bash

```bash
# Split large markdown file
split -l 1000 large-file.md split-
```

### Debug Mode

Enable debug logging for troubleshooting:

json

```json
{
  "env": {
    "OCTARINE_LOG_LEVEL": "debug",
    "NODE_DEBUG": "octarine*"
  }
}
```

View debug logs:

bash

```bash
# Follow logs in real-time
tail -f ~/.octarine/logs/debug.log

# Search logs
grep "ERROR" ~/.octarine/logs/debug.log
```

### Health Check

Test server health:

bash

```bash
# Create test script
cat > test-health.js << 'EOF'
const { Client } = require('@modelcontextprotocol/sdk/client/index.js');
const { StdioClientTransport } = require('@modelcontextprotocol/sdk/client/stdio.js');

async function healthCheck() {
  const transport = new StdioClientTransport({
    command: 'npx',
    args: ['-y', 'octarine-mcp-server'],
  });

  const client = new Client({
    name: 'health-check',
    version: '1.0.0',
  }, { capabilities: {} });

  try {
    await client.connect(transport);
    console.log('✅ Server is healthy');
    process.exit(0);
  } catch (error) {
    console.error('❌ Server is unhealthy:', error.message);
    process.exit(1);
  }
}

healthCheck();
EOF

# Run health check
node test-health.js
```

## Upgrade Guide

### Upgrading from npm

bash

```bash
# Check current version
npm list -g octarine-mcp-server

# Update to latest
npm update -g octarine-mcp-server

# Or install specific version
npm install -g octarine-mcp-server@1.2.3

# Verify new version
octarine-mcp-server --version
```

### Migration Checklist

When upgrading major versions:

-  Read [CHANGELOG.md](http://CHANGELOG.md) for breaking changes
-  Back up configuration files
-  Back up workspace data
-  Test in development environment
-  Update MCP client configuration if needed
-  Restart MCP client
-  Verify functionality

### Rollback Procedure

If upgrade causes issues:

bash

```bash
# Install previous version
npm install -g octarine-mcp-server@1.1.0

# Restore backed-up configuration
cp ~/.octarinerc.json.backup ~/.octarinerc.json

# Restart MCP client
```

## Next Steps

- Read the [API Reference](./API_REFERENCE.md) for detailed API documentation
- Review [Architecture](./ARCHITECTURE.md) to understand system design
- Check [Examples](../examples/) for usage patterns
- Join the community on [Discord](https://discord.gg/yourserver)

---

Need help? [Open an issue](https://github.com/yourusername/octarine-mcp-server/issues) or join our [Discord community](https://discord.gg/yourserver).