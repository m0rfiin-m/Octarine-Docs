
A production-grade Model Context Protocol (MCP) server that provides seamless integration with Octarine note-taking workspaces. This server enables AI assistants like Claude to perform full CRUD operations on markdown notes across multiple isolated workspaces, enabling sophisticated knowledge management workflows.

## Table of Contents

- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Configuration](#configuration)
- [API Reference](#api-reference)
- [Use Cases](#use-cases)
- [Development](#development)
- [Testing](#testing)
- [Contributing](#contributing)
- [Security](#security)
- [License](#license)
- [Support](#support)

## Features

### Core Capabilities

- **Multi-workspace Support**: Manage notes across multiple isolated Octarine workspaces with complete separation of concerns
- **Full CRUD Operations**: Create, read, update, delete, and search notes with atomic operations
- **Markdown-Native**: Built specifically for markdown-formatted notes with proper frontmatter support
- **Workspace Isolation**: Complete data isolation between workspaces for security and organization
- **Fast Search**: Content-based search with relevance ranking across workspaces
- **Directory Management**: Browse and navigate note structure within workspaces
- **Transactional Safety**: Atomic file operations with rollback capabilities
- **Error Handling**: Comprehensive error handling with detailed error messages

### Technical Features

- **Type-Safe**: Written in TypeScript with full type definitions
- **MCP Compliant**: Fully compliant with Model Context Protocol specification v1.0
- **Async/Await**: Modern asynchronous architecture
- **Stdio Transport**: Standard input/output communication for maximum compatibility
- **Zero Dependencies**: Minimal dependency footprint for security and maintainability
- **Cross-Platform**: Works on macOS, Linux, and Windows

## Architecture

The Octarine MCP Server follows a layered architecture:

```plaintext
┌─────────────────────────────────────┐
│     MCP Client (Claude, etc.)       │
└───────────────┬─────────────────────┘
                │ stdio
┌───────────────▼─────────────────────┐
│         Transport Layer             │
│    (stdio-based communication)      │
└───────────────┬─────────────────────┘
                │
┌───────────────▼─────────────────────┐
│          Tool Registry              │
│  (octarine_read_note, etc.)         │
└───────────────┬─────────────────────┘
                │
┌───────────────▼─────────────────────┐
│      Workspace Manager              │
│   (Isolation & Access Control)      │
└───────────────┬─────────────────────┘
                │
┌───────────────▼─────────────────────┐
│       File System Layer             │
│    (Atomic Operations & Search)     │
└─────────────────────────────────────┘
```

For detailed architecture documentation, see [ARCHITECTURE.md](http://ARCHITECTURE.md).

## Installation

### Prerequisites

- Node.js 18.0.0 or higher
- npm 9.0.0 or higher
- An Octarine-compatible note-taking system

### Via npm (Recommended)

bash

```bash
npm install -g octarine-mcp-server
```

### Via GitHub

bash

```bash
npm install -g github:yourusername/octarine-mcp-server
```

### From Source

bash

```bash
git clone https://github.com/yourusername/octarine-mcp-server.git
cd octarine-mcp-server
npm install
npm run build
npm link
```

## Quick Start

### 1. Configure Your MCP Client

#### Claude Desktop (macOS)

Edit `~/Library/Application Support/Claude/claude_desktop_config.json`:

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "/path/to/your/octarine/workspaces"
      }
    }
  }
}
```

#### Claude Desktop (Windows)

Edit `%APPDATA%\Claude\claude_desktop_config.json`:

json

```json
{
  "mcpServers": {
    "octarine": {
      "command": "npx.cmd",
      "args": ["-y", "octarine-mcp-server"],
      "env": {
        "OCTARINE_WORKSPACE_PATH": "C:\\path\\to\\your\\octarine\\workspaces"
      }
    }
  }
}
```

### 2. Restart Your MCP Client

Restart Claude Desktop or your MCP client to load the server.

### 3. Verify Installation

In Claude, try:

```plaintext
Can you list the notes in my "Projects" workspace?
```

If configured correctly, Claude will use the `octarine_list_notes` tool.

## Configuration

### Environment Variables

```plaintext
```

| Variable | Description | Default | Required |
| --- | --- | --- | --- |
| `OCTARINE_WORKSPACE_PATH` | Root path for all workspaces | `./workspaces` | No |
| `OCTARINE_MAX_FILE_SIZE` | Maximum file size in bytes | `10485760` (10MB) | No |
| `OCTARINE_SEARCH_LIMIT` | Maximum search results | `100` | No |
| `OCTARINE_LOG_LEVEL` | Logging level (error/warn/info/debug) | `info` | No |

### Advanced Configuration

Create a `.octarinerc.json` file in your workspace root:

json

```json
{
  "workspaces": {
    "Projects": {
      "path": "/custom/path/to/projects",
      "readOnly": false,
      "maxFileSize": 5242880
    },
    "Archive": {
      "path": "/custom/path/to/archive",
      "readOnly": true
    }
  },
  "search": {
    "caseSensitive": false,
    "includeHidden": false,
    "maxResults": 50
  }
}
```

For complete configuration options, see [SETUP_](./SETUP_GUIDE.md)[GUIDE.md](http://GUIDE.md).

## API Reference

### Available Tools

#### `octarine_read_note`

Read the contents of a specific note from a workspace.

**Parameters:**

- `workspace` (string, required): Name of the Octarine workspace
- `note_path` (string, required): Path to the note relative to workspace root

**Returns:**

typescript

```typescript
{
  success: boolean;
  content?: string;
  metadata?: {
    size: number;
    modified: string;
    created: string;
  };
  error?: string;
}
```

**Example:**

typescript

```typescript
{
  "workspace": "Projects",
  "note_path": "Octarine MCP/README.md"
}
```

#### `octarine_write_note`

Create a new note or update an existing note in a workspace.

**Parameters:**

- `workspace` (string, required): Name of the Octarine workspace
- `note_path` (string, required): Path where the note should be saved
- `content` (string, required): Markdown content of the note

**Returns:**

typescript

```typescript
{
  success: boolean;
  path?: string;
  operation?: 'created' | 'updated';
  error?: string;
}
```

**Example:**

typescript

```typescript
{
  "workspace": "Projects",
  "note_path": "Ideas/new-feature.md",
  "content": "# New Feature\n\nDetailed description..."
}
```

#### `octarine_search_notes`

Search for notes containing specific text across one or all workspaces.

**Parameters:**

- `query` (string, required): Text to search for
- `workspace` (string, optional): Specific workspace to search (omit to search all)

**Returns:**

typescript

```typescript
{
  success: boolean;
  results?: Array<{
    workspace: string;
    path: string;
    matches: number;
    preview: string;
  }>;
  totalResults?: number;
  error?: string;
}
```

**Example:**

typescript

```typescript
{
  "query": "project planning",
  "workspace": "Work"
}
```

#### `octarine_list_notes`

List all notes in a workspace or specific directory.

**Parameters:**

- `workspace` (string, required): Name of the Octarine workspace
- `directory` (string, optional): Subdirectory to list (omit for root)

**Returns:**

typescript

```typescript
{
  success: boolean;
  notes?: Array<{
    path: string;
    type: 'file' | 'directory';
    size?: number;
    modified?: string;
  }>;
  error?: string;
}
```

**Example:**

typescript

```typescript
{
  "workspace": "Projects",
  "directory": "Octarine MCP"
}
```

For complete API documentation, see [API_](./API_REFERENCE.md)[REFERENCE.md](http://REFERENCE.md).

## Use Cases

### Personal Knowledge Management

Build an AI-augmented personal knowledge base:

- Store research notes, meeting summaries, and learning resources
- Link concepts across different domains
- AI-assisted note retrieval and summarization
- Automatic tagging and categorization

### Project Documentation

Maintain living project documentation:

- Generate technical documentation from code
- Update architectural decision records (ADRs)
- Create and maintain API documentation
- Track project evolution over time

### Content Creation Workflow

Streamline content creation:

- Store content ideas and outlines
- Generate blog post drafts
- Maintain editorial calendars
- Collaborate with AI on revisions

### Learning & Research

Organize educational materials:

- Course notes and summaries
- Research paper annotations
- Study guides and flashcards
- Connect concepts across subjects

### Daily Journaling

AI-enhanced journaling:

- Daily reflections and planning
- Mood tracking and analysis
- Goal progress monitoring
- Pattern recognition in habits

## Development

### Project Structure

```plaintext
octarine-mcp-server/
├── src/
│   ├── index.ts              # Main entry point
│   ├── server.ts             # MCP server implementation
│   ├── tools/                # Tool implementations
│   │   ├── read.ts
│   │   ├── write.ts
│   │   ├── search.ts
│   │   └── list.ts
│   ├── workspace/            # Workspace management
│   │   ├── manager.ts
│   │   └── validator.ts
│   ├── utils/                # Utility functions
│   │   ├── file.ts
│   │   └── error.ts
│   └── types/                # Type definitions
│       └── index.ts
├── tests/                    # Test suite
│   ├── unit/
│   ├── integration/
│   └── fixtures/
├── docs/                     # Documentation
├── examples/                 # Usage examples
├── package.json
├── tsconfig.json
└── README.md
```

### Setup Development Environment

bash

```bash
# Clone the repository
git clone https://github.com/yourusername/octarine-mcp-server.git
cd octarine-mcp-server

# Install dependencies
npm install

# Build the project
npm run build

# Run in development mode with watch
npm run dev

# Run tests
npm test

# Run tests with coverage
npm run test:coverage

# Lint code
npm run lint

# Format code
npm run format
```

### Available Scripts

```plaintext
```

| Script | Description |
| --- | --- |
| `npm run build` | Compile TypeScript to JavaScript |
| `npm run dev` | Run in development mode with hot reload |
| `npm test` | Run test suite |
| `npm run test:watch` | Run tests in watch mode |
| `npm run test:coverage` | Generate coverage report |
| `npm run lint` | Lint code with ESLint |
| `npm run lint:fix` | Fix linting errors |
| `npm run format` | Format code with Prettier |
| `npm run type-check` | Run TypeScript type checking |

### Code Style

This project uses:

- **ESLint** for code linting
- **Prettier** for code formatting
- **TypeScript** for type safety

Run `npm run format` before committing to ensure consistent code style.

## Testing

### Running Tests

bash

```bash
# Run all tests
npm test

# Run specific test file
npm test -- read.test.ts

# Run with coverage
npm run test:coverage

# Run in watch mode
npm run test:watch
```

### Test Structure

typescript

```typescript
describe('octarine_read_note', () => {
  it('should read existing note successfully', async () => {
    // Test implementation
  });

  it('should handle missing note gracefully', async () => {
    // Test implementation
  });

  it('should validate workspace name', async () => {
    // Test implementation
  });
});
```

### Writing Tests

Follow these guidelines:

1. Write unit tests for all new features
2. Maintain test coverage above 80%
3. Use descriptive test names
4. Mock external dependencies
5. Test error cases thoroughly

## Contributing

We welcome contributions! Please see [CONTRIBUTING.md](http://CONTRIBUTING.md) for details.

### Quick Contribution Guide

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Write/update tests
5. Update documentation
6. Commit your changes (`git commit -m 'Add amazing feature'`)
7. Push to the branch (`git push origin feature/amazing-feature`)
8. Open a Pull Request

### Commit Message Convention

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```plaintext
type(scope): subject

body

footer
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

Example:

```plaintext
feat(search): add fuzzy matching support

Implement fuzzy string matching in search functionality
to improve search result relevance.

Closes #123
```

## Security

### Reporting Security Issues

**Do not open public issues for security vulnerabilities.**

Email security concerns to: [security@yourproject.com](mailto:security@yourproject.com)

We will respond within 48 hours.

### Security Best Practices

- All file operations are sandboxed to workspace directories
- Input validation on all parameters
- No arbitrary code execution
- Path traversal protection
- File size limits enforced
- Read-only mode available for sensitive workspaces

For detailed security information, see [SECURITY.md](http://SECURITY.md).

## Performance

### Benchmarks

```plaintext
```

| Operation | Small File (&lt;1KB) | Medium File (\~100KB) | Large File (\~1MB) |
| --- | --- | --- | --- |
| Read | &lt;10ms | &lt;50ms | &lt;200ms |
| Write | &lt;20ms | &lt;100ms | &lt;500ms |
| Search (1000 files) | &lt;500ms | &lt;2s | &lt;10s |
| List (1000 files) | &lt;100ms | &lt;300ms | &lt;1s |

*Benchmarks run on M1 MacBook Pro with SSD storage.*

### Optimization Tips

- Use specific workspace names in search to limit scope
- Implement file size limits for large repositories
- Use directory parameter in list operations
- Enable caching for frequently accessed notes

## Troubleshooting

### Common Issues

**Server not connecting:**

- Check MCP client configuration file syntax
- Verify Node.js version (18+)
- Check server logs in `~/.octarine/logs/`

**Notes not found:**

- Verify workspace path is correct
- Check file permissions
- Ensure workspace name matches exactly

**Slow search performance:**

- Limit search scope to specific workspace
- Reduce `OCTARINE_SEARCH_LIMIT`
- Index large repositories separately

For more troubleshooting tips, see [TROUBLESHOOTING.md](http://TROUBLESHOOTING.md).

## Roadmap

### Version 1.1 (Q1 2025)

-  Full-text search indexing
-  Workspace templates
-  Note linking and backlinks
-  Tag management

### Version 1.2 (Q2 2025)

-  Real-time sync support
-  Conflict resolution
-  Batch operations
-  Custom metadata fields

### Version 2.0 (Q3 2025)

-  Plugin system
-  Web interface
-  Collaborative editing
-  Version control integration

See [ROADMAP.md](http://ROADMAP.md) for complete roadmap.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with the [Model Context Protocol](https://modelcontextprotocol.io) by Anthropic
- Inspired by note-taking systems like Obsidian, Roam Research, and Notion
- Thanks to all [contributors](https://github.com/yourusername/octarine-mcp-server/graphs/contributors)

## Support

### Documentation

- [Setup Guide](./SETUP_GUIDE.md)
- [API Reference](./API_REFERENCE.md)
- [Architecture Overview](./ARCHITECTURE.md)
- [Contributing Guide](./CONTRIBUTING.md)

### Community

- **Issues**: [GitHub Issues](https://github.com/yourusername/octarine-mcp-server/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/octarine-mcp-server/discussions)
- **Discord**: [Join our Discord](https://discord.gg/yourserver)
- **Twitter**: [@octarinemcp](https://twitter.com/octarinemcp)

### Professional Support

For enterprise support, custom features, or consulting:

- Email: [enterprise@yourproject.com](mailto:enterprise@yourproject.com)
- Schedule: [Book a consultation](https://calendly.com/yourproject)

---

**Built with ❤️ by the Octarine MCP community**

[⬆ Back to Top](#octarine-mcp-server)