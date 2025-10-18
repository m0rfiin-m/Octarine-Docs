
# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased](https://github.com/yourusername/octarine-mcp-server/compare/v1.0.0...HEAD)

### Added

- Feature roadmap for v1.1-v2.0

### Changed

- None

### Deprecated

- None

### Removed

- None

### Fixed

- None

### Security

- None

## [1.0.0](https://github.com/yourusername/octarine-mcp-server/releases/tag/v1.0.0) - 2025-01-15

### Added

- Initial release of Octarine MCP Server
- Four core tools: `octarine_read_note`, `octarine_write_note`, `octarine_search_notes`, `octarine_list_notes`
- Multi-workspace support with complete isolation
- Atomic file write operations
- Content-based search with relevance ranking
- Directory browsing and navigation
- Comprehensive error handling with structured error codes
- Path traversal protection
- File size limits (configurable, default 10MB)
- Read-only workspace support
- Configuration via `.octarinerc.json` file
- Environment variable configuration support
- Rate limiting for all operations
- Comprehensive documentation (README, API_REFERENCE, ARCHITECTURE, SETUP_GUIDE, CONTRIBUTING)
- MIT License
- TypeScript implementation with full type definitions
- Jest test suite with 80%+ coverage
- ESLint and Prettier configuration
- GitHub Actions CI/CD pipeline
- Cross-platform support (macOS, Linux, Windows)

### Technical Details

- Node.js 18+ required
- MCP SDK 1.0 compliant
- Stdio-based transport layer
- Zero external dependencies (except MCP SDK)
- Asynchronous I/O throughout
- Structured logging support

### Documentation

- Complete README with badges and quick start
- Detailed API reference with examples
- Architecture overview with diagrams
- Comprehensive setup guide
- Contributing guidelines
- Security policy
- Code of conduct

---

## Release Notes

### Version 1.0.0 - Initial Release

This is the first stable release of the Octarine MCP Server, providing production-ready integration between AI assistants and Octarine note-taking workspaces.

#### Key Features

**Multi-Workspace Management**

- Create and manage multiple isolated workspaces
- Each workspace has independent configuration
- Support for read-only workspaces
- Custom file size limits per workspace

**Full CRUD Operations**

- Read notes with metadata
- Create and update notes atomically
- Search across workspaces with ranking
- List and browse directory structures

**Security**

- Path traversal prevention
- Workspace isolation enforcement
- Configurable file size limits
- Rate limiting on all operations
- Input validation and sanitization

**Performance**

- Async/await throughout
- Efficient file I/O
- Search result pagination
- Configurable concurrency limits

#### Breaking Changes

- None (initial release)

#### Migration Guide

- None (initial release)

#### Known Issues

- Search indexing not yet implemented (planned for v1.1)
- No plugin system yet (planned for v2.0)
- Limited to local filesystems (cloud storage planned for v1.2)

#### Upgrade Instructions

Install via npm:

bash

```bash
npm install -g octarine-mcp-server
```

Configure your MCP client:

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

#### Credits

Thanks to all contributors who made this release possible:

- Marco Morfin (@yourusername) - Initial development

Built with:

- [Model Context Protocol](https://modelcontextprotocol.io) by Anthropic
- [TypeScript](https://www.typescriptlang.org/)
- [Jest](https://jestjs.io/)

---

## Version History

```plaintext
```

| Version | Release Date | Highlights |
| --- | --- | --- |
| 1.0.0 | 2025-01-15 | Initial release with core functionality |

---

## Upcoming Releases

### v1.1.0 (Planned: Q1 2025)

- Full-text search indexing
- Workspace templates
- Note linking and backlinks
- Tag management
- Performance improvements

### v1.2.0 (Planned: Q2 2025)

- Real-time sync support
- Conflict resolution
- Batch operations
- Custom metadata fields
- Cloud storage backends (S3, GCS)

### v2.0.0 (Planned: Q3 2025)

- Plugin system
- Web interface
- Collaborative editing
- Version control integration
- Advanced search features

---

## Maintenance

- **Supported Versions**: 1.x.x receives security updates
- **EOL Policy**: Major versions supported for 1 year after next major release
- **Update Frequency**: Patch releases as needed, minor releases quarterly

---

For detailed release information, see [GitHub Releases](https://github.com/yourusername/octarine-mcp-server/releases).