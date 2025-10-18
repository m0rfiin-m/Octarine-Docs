
# Architecture Overview

This document provides a comprehensive overview of the Octarine MCP Server architecture, including system design, component interactions, data flow, and technical decisions.

## Table of Contents

- [System Architecture](#system-architecture)
- [Components](#components)
- [Data Flow](#data-flow)
- [Design Decisions](#design-decisions)
- [Security Model](#security-model)
- [Performance Considerations](#performance-considerations)
- [Extensibility](#extensibility)

## System Architecture

### High-Level Architecture

```plaintext
┌───────────────────────────────────────────────────────────┐
│                     MCP Client Layer                       │
│              (Claude Desktop, Custom Clients)              │
└─────────────────────────┬─────────────────────────────────┘
                          │
                          │ stdio (JSON-RPC)
                          │
┌─────────────────────────▼─────────────────────────────────┐
│                   Transport Layer                          │
│  ┌─────────────────────────────────────────────────────┐  │
│  │         StdioServerTransport                        │  │
│  │  - Request parsing                                  │  │
│  │  - Response serialization                           │  │
│  │  - Error handling                                   │  │
│  └─────────────────────────────────────────────────────┘  │
└─────────────────────────┬─────────────────────────────────┘
                          │
┌─────────────────────────▼─────────────────────────────────┐
│                    MCP Server Core                         │
│  ┌──────────────────┐  ┌──────────────────┐              │
│  │  Tool Registry   │  │ Request Router   │              │
│  │  - Tool metadata │  │ - Route requests │              │
│  │  - Validation    │  │ - Auth checks    │              │
│  └──────────────────┘  └──────────────────┘              │
└─────────────────────────┬─────────────────────────────────┘
                          │
┌─────────────────────────▼─────────────────────────────────┐
│                    Tool Handlers                           │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐    │
│  │   Read   │ │  Write   │ │  Search  │ │   List   │    │
│  │ Handler  │ │ Handler  │ │ Handler  │ │ Handler  │    │
│  └────┬─────┘ └────┬─────┘ └────┬─────┘ └────┬─────┘    │
└───────┼────────────┼────────────┼────────────┼───────────┘
        │            │            │            │
┌───────▼────────────▼────────────▼────────────▼───────────┐
│                 Workspace Manager                          │
│  ┌─────────────────────────────────────────────────────┐  │
│  │  - Workspace resolution                             │  │
│  │  - Path validation                                  │  │
│  │  - Permission checking                              │  │
│  │  - Isolation enforcement                            │  │
│  └─────────────────────────────────────────────────────┘  │
└─────────────────────────┬─────────────────────────────────┘
                          │
┌─────────────────────────▼─────────────────────────────────┐
│                 File System Layer                          │
│  ┌──────────────────┐  ┌──────────────────┐              │
│  │  File Operations │  │ Search Engine    │              │
│  │  - Atomic write  │  │ - Text indexing  │              │
│  │  - Safe read     │  │ - Query parsing  │              │
│  │  - Directory ops │  │ - Ranking        │              │
│  └──────────────────┘  └──────────────────┘              │
└─────────────────────────┬─────────────────────────────────┘
                          │
┌─────────────────────────▼─────────────────────────────────┐
│                    Operating System                        │
│                   File System (ext4, APFS, NTFS)          │
└───────────────────────────────────────────────────────────┘
```

### Component Responsibilities

```plaintext
```

| Component | Responsibility | Technologies |
| --- | --- | --- |
| Transport Layer | Handle stdio communication | MCP SDK, Node streams |
| MCP Server Core | Route requests, manage tools | MCP SDK, TypeScript |
| Tool Handlers | Implement tool logic | Custom TypeScript |
| Workspace Manager | Manage workspace isolation | Custom TypeScript |
| File System Layer | Execute file operations | Node.js fs/promises |

## Components

### 1. Transport Layer

The transport layer handles communication between the MCP client and server.

typescript

```typescript
class StdioServerTransport {
  private stdin: NodeJS.ReadableStream;
  private stdout: NodeJS.WritableStream;
  
  constructor() {
    this.stdin = process.stdin;
    this.stdout = process.stdout;
  }
  
  async start(handler: RequestHandler): Promise<void> {
    // Set up stdin/stdout pipes
    // Parse incoming JSON-RPC requests
    // Route to request handler
    // Serialize and send responses
  }
}
```

**Key Features:**

- JSON-RPC 2.0 protocol compliance
- Streaming request/response handling
- Error recovery and logging
- Graceful shutdown support

### 2. MCP Server Core

The core server manages tool registration and request routing.

typescript

```typescript
class OctarineMCPServer {
  private tools: Map<string, Tool>;
  private transport: StdioServerTransport;
  
  constructor() {
    this.tools = new Map();
    this.transport = new StdioServerTransport();
    this.registerTools();
  }
  
  private registerTools(): void {
    this.registerTool({
      name: "octarine_read_note",
      description: "Read note from workspace",
      inputSchema: ReadNoteSchema,
      handler: readNoteHandler
    });
    // ... register other tools
  }
  
  async run(): Promise<void> {
    await this.transport.start(this.handleRequest.bind(this));
  }
}
```

**Key Features:**

- Tool registration and discovery
- Input validation using JSON Schema
- Request routing to handlers
- Centralized error handling
- Logging and monitoring

### 3. Tool Handlers

Each tool has a dedicated handler implementing its logic.

#### Read Note Handler

typescript

```typescript
async function readNoteHandler(params: ReadNoteParams): Promise<ReadNoteResponse> {
  // 1. Validate parameters
  validateWorkspaceName(params.workspace);
  validateNotePath(params.note_path);
  
  // 2. Resolve workspace path
  const workspacePath = workspaceManager.resolve(params.workspace);
  
  // 3. Check permissions
  await workspaceManager.checkReadPermission(workspacePath, params.note_path);
  
  // 4. Read file
  const content = await fileSystem.readFile(
    path.join(workspacePath, params.note_path)
  );
  
  // 5. Get metadata
  const metadata = await fileSystem.getMetadata(
    path.join(workspacePath, params.note_path)
  );
  
  // 6. Return response
  return {
    content,
    metadata,
    encoding: 'utf-8',
    hash: computeHash(content)
  };
}
```

#### Write Note Handler

typescript

```typescript
async function writeNoteHandler(params: WriteNoteParams): Promise<WriteNoteResponse> {
  // 1. Validate parameters
  validateWorkspaceName(params.workspace);
  validateNotePath(params.note_path);
  validateContent(params.content);
  
  // 2. Resolve workspace path
  const workspacePath = workspaceManager.resolve(params.workspace);
  
  // 3. Check permissions
  await workspaceManager.checkWritePermission(workspacePath);
  
  // 4. Create parent directories if needed
  if (params.create_dirs) {
    await fileSystem.mkdirp(path.dirname(fullPath));
  }
  
  // 5. Check if file exists
  const exists = await fileSystem.exists(fullPath);
  const operation = exists ? 'updated' : 'created';
  
  // 6. Write atomically
  await fileSystem.atomicWrite(fullPath, params.content);
  
  // 7. Return response
  return {
    path: params.note_path,
    operation,
    size: Buffer.byteLength(params.content),
    hash: computeHash(params.content)
  };
}
```

#### Search Notes Handler

typescript

```typescript
async function searchNotesHandler(params: SearchNotesParams): Promise<SearchNotesResponse> {
  // 1. Validate parameters
  validateSearchQuery(params.query);
  
  // 2. Determine search scope
  const workspaces = params.workspace 
    ? [params.workspace]
    : await workspaceManager.listWorkspaces();
  
  // 3. Build search index
  const searchEngine = new SearchEngine({
    caseSensitive: params.case_sensitive,
    wholeWord: params.whole_word,
    regex: params.regex
  });
  
  // 4. Search each workspace
  const allResults: SearchResult[] = [];
  
  for (const workspace of workspaces) {
    const workspacePath = workspaceManager.resolve(workspace);
    const notes = await fileSystem.listFiles(workspacePath, {
      recursive: true,
      filter: '**/*.md'
    });
    
    for (const note of notes) {
      const content = await fileSystem.readFile(note);
      const matches = searchEngine.search(params.query, content);
      
      if (matches.length > 0) {
        allResults.push({
          workspace,
          path: path.relative(workspacePath, note),
          matches: matches.length,
          preview: generatePreview(content, matches[0]),
          score: calculateRelevance(matches, content),
          highlights: matches
        });
      }
    }
  }
  
  // 5. Sort and paginate
  const sorted = sortByRelevance(allResults);
  const paginated = sorted.slice(params.offset, params.offset + params.limit);
  
  // 6. Return response
  return {
    results: paginated,
    totalResults: sorted.length,
    totalMatches: allResults.reduce((sum, r) => sum + r.matches, 0),
    query: params.query,
    executionTime: performance.now() - startTime,
    hasMore: sorted.length > params.offset + params.limit
  };
}
```

#### List Notes Handler

typescript

```typescript
async function listNotesHandler(params: ListNotesParams): Promise<ListNotesResponse> {
  // 1. Validate parameters
  validateWorkspaceName(params.workspace);
  if (params.directory) {
    validateNotePath(params.directory);
  }
  
  // 2. Resolve paths
  const workspacePath = workspaceManager.resolve(params.workspace);
  const targetPath = params.directory
    ? path.join(workspacePath, params.directory)
    : workspacePath;
  
  // 3. Check permissions
  await workspaceManager.checkReadPermission(targetPath);
  
  // 4. List directory
  const entries = await fileSystem.readdir(targetPath, {
    withFileTypes: true,
    recursive: params.recursive
  });
  
  // 5. Filter and transform
  let notes = entries
    .filter(entry => {
      if (!params.include_hidden && entry.name.startsWith('.')) {
        return false;
      }
      if (params.filter) {
        return minimatch(entry.name, params.filter);
      }
      return true;
    })
    .map(async entry => {
      const fullPath = path.join(targetPath, entry.name);
      const stats = await fileSystem.stat(fullPath);
      
      return {
        path: path.relative(workspacePath, fullPath),
        type: entry.isDirectory() ? 'directory' : 'file',
        size: stats.size,
        modified: stats.mtime.toISOString(),
        created: stats.birthtime.toISOString()
      };
    });
  
  notes = await Promise.all(notes);
  
  // 6. Sort
  notes = sortNotes(notes, params.sort_by, params.sort_order);
  
  // 7. Calculate totals
  const totalFiles = notes.filter(n => n.type === 'file').length;
  const totalDirectories = notes.filter(n => n.type === 'directory').length;
  const totalSize = notes
    .filter(n => n.type === 'file')
    .reduce((sum, n) => sum + (n.size || 0), 0);
  
  // 8. Return response
  return {
    notes,
    directory: params.directory || '',
    totalFiles,
    totalDirectories,
    totalSize
  };
}
```

### 4. Workspace Manager

Manages workspace isolation and access control.

typescript

```typescript
class WorkspaceManager {
  private workspaces: Map<string, WorkspaceConfig>;
  private basePath: string;
  
  constructor(basePath: string) {
    this.basePath = basePath;
    this.workspaces = new Map();
    this.loadConfiguration();
  }
  
  resolve(workspaceName: string): string {
    const config = this.workspaces.get(workspaceName);
    if (!config) {
      throw new WorkspaceNotFoundError(workspaceName);
    }
    return config.path;
  }
  
  async checkReadPermission(workspacePath: string, notePath?: string): Promise<void> {
    // Verify path is within workspace
    const resolvedPath = notePath 
      ? path.join(workspacePath, notePath)
      : workspacePath;
    
    if (!resolvedPath.startsWith(workspacePath)) {
      throw new PathTraversalError(notePath);
    }
    
    // Check file system permissions
    try {
      await fs.access(resolvedPath, fs.constants.R_OK);
    } catch (error) {
      throw new PermissionDeniedError('read', resolvedPath);
    }
  }
  
  async checkWritePermission(workspacePath: string): Promise<void> {
    const config = Array.from(this.workspaces.values())
      .find(c => c.path === workspacePath);
    
    if (config?.readOnly) {
      throw new WorkspaceReadOnlyError(config.name);
    }
    
    try {
      await fs.access(workspacePath, fs.constants.W_OK);
    } catch (error) {
      throw new PermissionDeniedError('write', workspacePath);
    }
  }
}
```

**Key Features:**

- Workspace resolution and validation
- Path traversal prevention
- Read-only workspace enforcement
- Permission checking
- Configuration management

### 5. File System Layer

Handles low-level file operations safely.

typescript

```typescript
class FileSystemLayer {
  async readFile(filePath: string): Promise<string> {
    try {
      return await fs.readFile(filePath, 'utf-8');
    } catch (error) {
      if (error.code === 'ENOENT') {
        throw new NoteNotFoundError(filePath);
      }
      throw new IOError('read', filePath, error);
    }
  }
  
  async atomicWrite(filePath: string, content: string): Promise<void> {
    const tempPath = `${filePath}.tmp.${Date.now()}`;
    
    try {
      // Write to temp file
      await fs.writeFile(tempPath, content, 'utf-8');
      
      // Rename atomically
      await fs.rename(tempPath, filePath);
    } catch (error) {
      // Clean up temp file
      try {
        await fs.unlink(tempPath);
      } catch {}
      
      throw new IOError('write', filePath, error);
    }
  }
  
  async getMetadata(filePath: string): Promise<FileMetadata> {
    try {
      const stats = await fs.stat(filePath);
      
      return {
        size: stats.size,
        created: stats.birthtime.toISOString(),
        modified: stats.mtime.toISOString(),
        accessed: stats.atime.toISOString(),
        permissions: stats.mode.toString(8).slice(-3)
      };
    } catch (error) {
      throw new IOError('stat', filePath, error);
    }
  }
}
```

**Key Features:**

- Atomic file writes
- Safe file reads with error handling
- Metadata retrieval
- Directory operations
- Path sanitization

## Data Flow

### Read Operation Flow

```plaintext
1. Client Request
   ↓
2. Transport Layer (parse JSON-RPC)
   ↓
3. MCP Server Core (route to handler)
   ↓
4. Read Handler (validate params)
   ↓
5. Workspace Manager (resolve & check permissions)
   ↓
6. File System Layer (read file)
   ↓
7. Read Handler (format response)
   ↓
8. MCP Server Core (serialize response)
   ↓
9. Transport Layer (send JSON-RPC)
   ↓
10. Client Response
```

### Write Operation Flow

```plaintext
1. Client Request
   ↓
2. Transport Layer (parse JSON-RPC)
   ↓
3. MCP Server Core (route to handler)
   ↓
4. Write Handler (validate params & content)
   ↓
5. Workspace Manager (resolve & check permissions)
   ↓
6. File System Layer (create dirs if needed)
   ↓
7. File System Layer (atomic write)
   ↓
8. Write Handler (format response)
   ↓
9. MCP Server Core (serialize response)
   ↓
10. Transport Layer (send JSON-RPC)
   ↓
11. Client Response
```

### Search Operation Flow

```plaintext
1. Client Request
   ↓
2. Transport Layer (parse JSON-RPC)
   ↓
3. MCP Server Core (route to handler)
   ↓
4. Search Handler (validate query)
   ↓
5. Workspace Manager (determine search scope)
   ↓
6. For each workspace:
   ├─→ File System Layer (list files)
   ├─→ File System Layer (read files)
   └─→ Search Engine (find matches)
   ↓
7. Search Handler (rank & paginate)
   ↓
8. MCP Server Core (serialize response)
   ↓
9. Transport Layer (send JSON-RPC)
   ↓
10. Client Response
```

## Design Decisions

### 1. Stdio Transport

**Decision:** Use stdio (standard input/output) for client-server communication.

**Rationale:**

- MCP specification standard
- Simple, reliable, well-tested
- No network complexity
- Works across platforms
- Easy to debug

**Alternatives Considered:**

- HTTP/REST API: More complex, unnecessary network overhead
- WebSockets: Overkill for local communication
- gRPC: Too heavyweight for this use case

### 2. TypeScript Implementation

**Decision:** Implement server in TypeScript.

**Rationale:**

- Type safety prevents runtime errors
- Better IDE support and autocomplete
- Easier refactoring
- Self-documenting code
- Compiles to portable JavaScript

**Alternatives Considered:**

- JavaScript: Less type safety
- Python: MCP SDK primarily Node.js focused
- Go: Steeper learning curve, less MCP tooling

### 3. Workspace Isolation

**Decision:** Complete isolation between workspaces with no cross-workspace references.

**Rationale:**

- Security: Prevent unauthorized access
- Organization: Clear separation of concerns
- Performance: Limit search scope
- Simplicity: Easier to reason about

**Alternatives Considered:**

- Shared workspaces: Security risks
- Tag-based organization: Less clear boundaries
- Single workspace: Doesn't scale

### 4. Atomic Writes

**Decision:** Use atomic write operations (write to temp + rename).

**Rationale:**

- Prevent corruption on crash
- Ensure file is either old or new, never partial
- Standard practice for reliable file writes
- Minimal performance overhead

**Alternatives Considered:**

- Direct writes: Risk of corruption
- Journaling: Too complex for this use case
- Database: Unnecessary complexity

### 5. Markdown Focus

**Decision:** Optimize specifically for markdown files.

**Rationale:**

- Clear target use case
- Enables markdown-specific features
- Simpler than generic file handling
- Aligns with note-taking workflows

**Alternatives Considered:**

- Generic file support: Too broad
- Rich text: Unnecessary complexity
- Binary files: Different use case

### 6. Search Implementation

**Decision:** In-memory text search without persistent index.

**Rationale:**

- Simple implementation
- No index maintenance overhead
- Acceptable performance for typical use
- No state to manage

**Alternatives Considered:**

- Full-text index: Complex to maintain
- Database: Overkill for file-based notes
- External search engine: Unnecessary dependency

### 7. Error Handling Strategy

**Decision:** Structured errors with codes, messages, and details.

**Rationale:**

- Programmatic error handling
- Clear error communication
- Debugging support
- User-friendly messages

**Alternatives Considered:**

- Generic errors: Less actionable
- HTTP status codes: Not applicable to stdio
- Exceptions only: Less structured

## Security Model

### Threat Model

1. **Path Traversal**: Malicious paths attempting to access files outside workspace
2. **Workspace Escape**: Attempts to access other workspaces
3. **Resource Exhaustion**: Large files or searches consuming excessive resources
4. **Code Injection**: Malicious content in note files
5. **Permission Bypass**: Attempts to write to read-only workspaces

### Security Controls

#### 1. Path Validation

typescript

```typescript
function validateNotePath(notePath: string): void {
  // Check for null bytes
  if (notePath.includes('\0')) {
    throw new InvalidPathError('Path contains null bytes');
  }
  
  // Check for path traversal
  if (notePath.includes('..')) {
    throw new PathTraversalError(notePath);
  }
  
  // Check for absolute paths
  if (path.isAbsolute(notePath)) {
    throw new InvalidPathError('Absolute paths not allowed');
  }
  
  // Check for unsafe characters
  if (/[<>:"|?*]/.test(notePath)) {
    throw new InvalidPathError('Path contains unsafe characters');
  }
}
```

#### 2. Workspace Sandboxing

typescript

```typescript
function ensureWithinWorkspace(workspacePath: string, filePath: string): void {
  const resolvedPath = path.resolve(workspacePath, filePath);
  const normalizedWorkspace = path.resolve(workspacePath);
  
  if (!resolvedPath.startsWith(normalizedWorkspace + path.sep)) {
    throw new WorkspaceEscapeError(filePath);
  }
}
```

#### 3. File Size Limits

typescript

```typescript
async function checkFileSize(filePath: string, maxSize: number): Promise<void> {
  const stats = await fs.stat(filePath);
  
  if (stats.size > maxSize) {
    throw new FileTooLargeError(filePath, stats.size, maxSize);
  }
}
```

#### 4. Read-Only Enforcement

typescript

```typescript
async function enforceReadOnly(workspace: WorkspaceConfig): Promise<void> {
  if (workspace.readOnly) {
    throw new WorkspaceReadOnlyError(workspace.name);
  }
}
```

#### 5. Input Sanitization

typescript

```typescript
function sanitizeContent(content: string): string {
  // Ensure valid UTF-8
  const buffer = Buffer.from(content, 'utf-8');
  return buffer.toString('utf-8');
}
```

## Performance Considerations

### 1. File I/O Optimization

- Use streaming for large files
- Implement read-ahead caching
- Batch operations when possible
- Use async I/O throughout

### 2. Search Performance

- Limit concurrent searches
- Implement search result caching
- Use worker threads for large searches
- Optimize regex compilation

### 3. Memory Management

- Stream large file reads
- Limit in-memory caching
- Clean up resources promptly
- Monitor memory usage

### 4. Concurrency

- Use connection pooling
- Implement request queuing
- Limit concurrent operations
- Use worker threads for CPU-intensive tasks

## Extensibility

### Plugin System (Future)

typescript

```typescript
interface OctarinePlugin {
  name: string;
  version: string;
  
  initialize(server: OctarineMCPServer): Promise<void>;
  registerTools(): Tool[];
  onShutdown(): Promise<void>;
}

class PluginManager {
  private plugins: Map<string, OctarinePlugin>;
  
  async loadPlugin(pluginPath: string): Promise<void> {
    const plugin = await import(pluginPath);
    await plugin.initialize(this.server);
    this.plugins.set(plugin.name, plugin);
  }
}
```

### Custom Tool Registration

typescript

```typescript
interface ToolDefinition {
  name: string;
  description: string;
  inputSchema: JSONSchema;
  handler: (params: any) => Promise<any>;
}

class ToolRegistry {
  private tools: Map<string, ToolDefinition>;
  
  register(tool: ToolDefinition): void {
    this.validateTool(tool);
    this.tools.set(tool.name, tool);
  }
}
```

### Workspace Backends (Future)

typescript

```typescript
interface WorkspaceBackend {
  read(path: string): Promise<string>;
  write(path: string, content: string): Promise<void>;
  list(path: string): Promise<FileInfo[]>;
  search(query: string): Promise<SearchResult[]>;
}

class S3WorkspaceBackend implements WorkspaceBackend {
  // Implementation for S3 storage
}

class GitWorkspaceBackend implements WorkspaceBackend {
  // Implementation for Git repositories
}
```

---

For implementation details, see the source code in the `src/` directory.