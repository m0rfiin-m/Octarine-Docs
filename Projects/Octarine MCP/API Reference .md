
# API Reference

Complete API documentation for the Octarine MCP Server. This document provides detailed specifications for all available tools, including parameters, return types, error codes, and usage examples.

## Table of Contents

- [Overview](#overview)
- [Data Types](#data-types)
- [Error Handling](#error-handling)
- [Tools](#tools)
  - [octarine_read_note](#octarine_read_note)
  - [octarine_write_note](#octarine_write_note)
  - [octarine_search_notes](#octarine_search_notes)
  - [octarine_list_notes](#octarine_list_notes)
- [Best Practices](#best-practices)
- [Rate Limiting](#rate-limiting)
- [Examples](#examples)

## Overview

The Octarine MCP Server exposes four primary tools for interacting with markdown notes in workspaces. All tools follow consistent patterns for parameters, return values, and error handling.

### Base Concepts

- **Workspace**: An isolated collection of notes with its own directory structure
- **Note Path**: Relative path to a note file within a workspace (e.g., `Projects/idea.md`)
- **Content**: UTF-8 encoded markdown text with optional frontmatter

### Communication Protocol

All communication uses the MCP (Model Context Protocol) standard over stdio:

```plaintext
Client → Server: JSON-RPC Request
Server → Client: JSON-RPC Response
```

## Data Types

### Common Types

typescript

```typescript
// Success response wrapper
interface SuccessResponse<T> {
  success: true;
  data: T;
}

// Error response wrapper
interface ErrorResponse {
  success: false;
  error: string;
  code: ErrorCode;
  details?: Record<string, any>;
}

// Unified response type
type ApiResponse<T> = SuccessResponse<T> | ErrorResponse;

// Workspace identifier
type WorkspaceName = string;

// File path within workspace
type NotePath = string;

// Markdown content
type MarkdownContent = string;

// ISO 8601 timestamp
type Timestamp = string;

// File size in bytes
type FileSize = number;
```

### Metadata Types

typescript

```typescript
interface FileMetadata {
  size: FileSize;
  created: Timestamp;
  modified: Timestamp;
  accessed?: Timestamp;
  permissions?: string;
}

interface NoteInfo {
  path: NotePath;
  type: 'file' | 'directory';
  size?: FileSize;
  modified?: Timestamp;
  created?: Timestamp;
}

interface SearchResult {
  workspace: WorkspaceName;
  path: NotePath;
  matches: number;
  preview: string;
  score?: number;
  highlights?: SearchHighlight[];
}

interface SearchHighlight {
  line: number;
  column: number;
  length: number;
  context: string;
}
```

## Error Handling

### Error Codes

The server returns standardized error codes:

```plaintext
```

| Code | Description | HTTP Equivalent |
| --- | --- | --- |
| `WORKSPACE_NOT_FOUND` | Specified workspace does not exist | 404 |
| `NOTE_NOT_FOUND` | Specified note does not exist | 404 |
| `INVALID_WORKSPACE_NAME` | Workspace name contains invalid characters | 400 |
| `INVALID_NOTE_PATH` | Note path is malformed or contains path traversal | 400 |
| `PERMISSION_DENIED` | Operation not permitted (read-only workspace) | 403 |
| `FILE_TOO_LARGE` | File exceeds maximum size limit | 413 |
| `INVALID_CONTENT` | Content validation failed | 400 |
| `IO_ERROR` | File system operation failed | 500 |
| `WORKSPACE_READ_ONLY` | Cannot modify read-only workspace | 403 |
| `RATE_LIMIT_EXCEEDED` | Too many requests | 429 |

### Error Response Format

typescript

```typescript
{
  success: false,
  error: "Human-readable error message",
  code: "ERROR_CODE",
  details: {
    // Additional context-specific information
    workspace: "Projects",
    path: "invalid/../path.md",
    reason: "Path traversal detected"
  }
}
```

### Error Handling Best Practices

1. **Always check** `success` **field** before accessing data
2. **Log error codes** for debugging and monitoring
3. **Display** `error` **message** to users
4. **Use** `code` for programmatic error handling
5. **Parse** `details` for context-specific recovery

Example error handling:

typescript

```typescript
const result = await readNote("Projects", "note.md");

if (!result.success) {
  switch (result.code) {
    case "NOTE_NOT_FOUND":
      console.log("Note doesn't exist yet, creating...");
      await writeNote("Projects", "note.md", "# New Note");
      break;
    
    case "WORKSPACE_NOT_FOUND":
      console.error("Invalid workspace:", result.details?.workspace);
      break;
    
    case "PERMISSION_DENIED":
      console.error("Cannot modify read-only workspace");
      break;
    
    default:
      console.error("Unexpected error:", result.error);
  }
  return;
}

// Process successful result
const { content, metadata } = result.data;
```

## Tools

### octarine_read_note

Read the complete contents of a note from a workspace.

#### Parameters

typescript

```typescript
interface ReadNoteParams {
  workspace: WorkspaceName;  // Required
  note_path: NotePath;       // Required
}
```

```plaintext
```

| Parameter | Type | Required | Description |
| --- | --- | --- | --- |
| `workspace` | string | Yes | Name of the workspace containing the note |
| `note_path` | string | Yes | Path to the note relative to workspace root |

#### Returns

typescript

```typescript
interface ReadNoteResponse {
  content: MarkdownContent;
  metadata: FileMetadata;
  encoding: 'utf-8';
  hash?: string;  // SHA-256 hash of content
}
```

```plaintext
```

| Field | Type | Description |
| --- | --- | --- |
| `content` | string | Complete markdown content of the note |
| `metadata` | FileMetadata | File system metadata |
| `encoding` | string | Always 'utf-8' |
| `hash` | string | Optional SHA-256 hash for content verification |

#### Example Request

typescript

```typescript
{
  "workspace": "Projects",
  "note_path": "Octarine MCP/README.md"
}
```

#### Example Response

typescript

```typescript
{
  "success": true,
  "data": {
    "content": "# Octarine MCP Server\n\nA production-grade...",
    "metadata": {
      "size": 15420,
      "created": "2024-01-15T10:30:00Z",
      "modified": "2024-01-20T14:22:00Z",
      "permissions": "rw-r--r--"
    },
    "encoding": "utf-8",
    "hash": "a3f5b9c2d8e1..."
  }
}
```

#### Error Cases

```plaintext
```

| Error Code | Condition |
| --- | --- |
| `WORKSPACE_NOT_FOUND` | Workspace doesn't exist |
| `NOTE_NOT_FOUND` | Note doesn't exist at specified path |
| `INVALID_NOTE_PATH` | Path contains invalid characters or traversal |
| `PERMISSION_DENIED` | No read permission for note |
| `IO_ERROR` | File system read error |

#### Usage Notes

- The note must exist; returns error for non-existent notes
- Path is relative to workspace root
- Supports nested directories (e.g., `folder/subfolder/note.md`)
- Content is always returned as UTF-8 encoded string
- Metadata includes filesystem timestamps
- Use `hash` field for caching and change detection

---

### octarine_write_note

Create a new note or update an existing note in a workspace.

#### Parameters

typescript

```typescript
interface WriteNoteParams {
  workspace: WorkspaceName;      // Required
  note_path: NotePath;           // Required
  content: MarkdownContent;      // Required
  create_dirs?: boolean;         // Optional, default: true
  overwrite?: boolean;           // Optional, default: true
  atomic?: boolean;              // Optional, default: true
}
```

```plaintext
```

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `workspace` | string | Yes | - | Name of the workspace |
| `note_path` | string | Yes | - | Path where note should be saved |
| `content` | string | Yes | - | Markdown content to write |
| `create_dirs` | boolean | No | true | Create parent directories if needed |
| `overwrite` | boolean | No | true | Overwrite existing file |
| `atomic` | boolean | No | true | Use atomic write operation |

#### Returns

typescript

```typescript
interface WriteNoteResponse {
  path: NotePath;
  operation: 'created' | 'updated';
  size: FileSize;
  hash: string;
  backup?: NotePath;  // Path to backup if created
}
```

```plaintext
```

| Field | Type | Description |
| --- | --- | --- |
| `path` | string | Full path to the written note |
| `operation` | string | Whether note was created or updated |
| `size` | number | Size of written file in bytes |
| `hash` | string | SHA-256 hash of written content |
| `backup` | string | Path to backup file if created |

#### Example Request

typescript

```typescript
{
  "workspace": "Projects",
  "note_path": "Ideas/new-feature.md",
  "content": "# New Feature\n\n## Overview\n\nDetailed description...",
  "create_dirs": true,
  "atomic": true
}
```

#### Example Response (Created)

typescript

```typescript
{
  "success": true,
  "data": {
    "path": "Ideas/new-feature.md",
    "operation": "created",
    "size": 156,
    "hash": "7d8a3c4e5f..."
  }
}
```

#### Example Response (Updated)

typescript

```typescript
{
  "success": true,
  "data": {
    "path": "Ideas/existing-note.md",
    "operation": "updated",
    "size": 892,
    "hash": "9b2d4a6f8c...",
    "backup": "Ideas/.backups/existing-note.2024-01-20T14-30-00.md"
  }
}
```

#### Error Cases

```plaintext
```

| Error Code | Condition |
| --- | --- |
| `WORKSPACE_NOT_FOUND` | Workspace doesn't exist |
| `WORKSPACE_READ_ONLY` | Workspace is configured as read-only |
| `INVALID_NOTE_PATH` | Path contains invalid characters |
| `FILE_TOO_LARGE` | Content exceeds size limit |
| `INVALID_CONTENT` | Content validation failed |
| `PERMISSION_DENIED` | No write permission |
| `IO_ERROR` | File system write error |

#### Usage Notes

- Creates parent directories automatically unless `create_dirs` is false
- Atomic writes use temporary files and rename for safety
- Existing files are backed up before overwriting
- Content is validated for proper UTF-8 encoding
- Empty content is allowed (creates empty file)
- Supports both absolute and relative paths within workspace

---

### octarine_search_notes

Search for notes containing specific text across one or all workspaces.

#### Parameters

typescript

```typescript
interface SearchNotesParams {
  query: string;                 // Required
  workspace?: WorkspaceName;     // Optional
  case_sensitive?: boolean;      // Optional, default: false
  whole_word?: boolean;          // Optional, default: false
  regex?: boolean;               // Optional, default: false
  limit?: number;                // Optional, default: 100
  offset?: number;               // Optional, default: 0
  include_content?: boolean;     // Optional, default: true
  sort_by?: 'relevance' | 'modified' | 'created' | 'path';  // Optional
}
```

```plaintext
```

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `query` | string | Yes | - | Text to search for |
| `workspace` | string | No | null | Specific workspace (omit for all) |
| `case_sensitive` | boolean | No | false | Case-sensitive matching |
| `whole_word` | boolean | No | false | Match whole words only |
| `regex` | boolean | No | false | Treat query as regex pattern |
| `limit` | number | No | 100 | Maximum results to return |
| `offset` | number | No | 0 | Number of results to skip |
| `include_content` | boolean | No | true | Include content preview |
| `sort_by` | string | No | 'relevance' | Sort order for results |

#### Returns

typescript

```typescript
interface SearchNotesResponse {
  results: SearchResult[];
  totalResults: number;
  totalMatches: number;
  query: string;
  executionTime: number;  // milliseconds
  hasMore: boolean;
}
```

```plaintext
```

| Field | Type | Description |
| --- | --- | --- |
| `results` | SearchResult[] | Array of matching notes |
| `totalResults` | number | Total number of notes matched |
| `totalMatches` | number | Total number of text matches |
| `query` | string | Original search query |
| `executionTime` | number | Search duration in milliseconds |
| `hasMore` | boolean | Whether more results exist |

#### SearchResult Type

typescript

```typescript
interface SearchResult {
  workspace: WorkspaceName;
  path: NotePath;
  matches: number;
  preview: string;
  score: number;          // Relevance score 0-100
  highlights: SearchHighlight[];
  metadata?: FileMetadata;
}

interface SearchHighlight {
  line: number;
  column: number;
  length: number;
  context: string;        // Surrounding text
}
```

#### Example Request (Simple)

typescript

```typescript
{
  "query": "project planning",
  "workspace": "Work"
}
```

#### Example Request (Advanced)

typescript

```typescript
{
  "query": "TODO|FIXME|HACK",
  "regex": true,
  "case_sensitive": false,
  "limit": 50,
  "sort_by": "modified"
}
```

#### Example Response

typescript

```typescript
{
  "success": true,
  "data": {
    "results": [
      {
        "workspace": "Work",
        "path": "Projects/Q1-planning.md",
        "matches": 3,
        "preview": "...project planning session for Q1...",
        "score": 95.5,
        "highlights": [
          {
            "line": 15,
            "column": 10,
            "length": 16,
            "context": "The project planning session will cover..."
          },
          {
            "line": 42,
            "column": 5,
            "length": 16,
            "context": "Next project planning milestone..."
          }
        ],
        "metadata": {
          "size": 5420,
          "modified": "2024-01-18T09:15:00Z",
          "created": "2024-01-10T14:30:00Z"
        }
      }
    ],
    "totalResults": 12,
    "totalMatches": 47,
    "query": "project planning",
    "executionTime": 145,
    "hasMore": true
  }
}
```

#### Error Cases

```plaintext
```

| Error Code | Condition |
| --- | --- |
| `WORKSPACE_NOT_FOUND` | Specified workspace doesn't exist |
| `INVALID_QUERY` | Query is empty or invalid regex |
| `RATE_LIMIT_EXCEEDED` | Too many search requests |

#### Usage Notes

- Empty query returns all notes
- Regex patterns must be valid JavaScript regex
- Relevance scoring considers match frequency and position
- Preview shows context around first match
- Highlights show all match locations
- Search is performed across note content and frontmatter
- Hidden files (starting with `.`) are excluded by default
- Large workspaces may take longer to search
- Use pagination (limit/offset) for large result sets

---

### octarine_list_notes

List all notes in a workspace or specific directory.

#### Parameters

typescript

```typescript
interface ListNotesParams {
  workspace: WorkspaceName;      // Required
  directory?: NotePath;          // Optional, default: root
  recursive?: boolean;           // Optional, default: false
  include_hidden?: boolean;      // Optional, default: false
  sort_by?: 'name' | 'modified' | 'created' | 'size';  // Optional
  sort_order?: 'asc' | 'desc';   // Optional, default: 'asc'
  filter?: string;               // Optional glob pattern
}
```

```plaintext
```

| Parameter | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| `workspace` | string | Yes | - | Name of the workspace |
| `directory` | string | No | '' (root) | Subdirectory to list |
| `recursive` | boolean | No | false | Include subdirectories |
| `include_hidden` | boolean | No | false | Include hidden files |
| `sort_by` | string | No | 'name' | Sort field |
| `sort_order` | string | No | 'asc' | Sort direction |
| `filter` | string | No | null | Glob pattern filter |

#### Returns

typescript

```typescript
interface ListNotesResponse {
  notes: NoteInfo[];
  directory: NotePath;
  totalFiles: number;
  totalDirectories: number;
  totalSize: FileSize;
}
```

```plaintext
```

| Field | Type | Description |
| --- | --- | --- |
| `notes` | NoteInfo[] | Array of notes and directories |
| `directory` | string | Listed directory path |
| `totalFiles` | number | Count of files |
| `totalDirectories` | number | Count of directories |
| `totalSize` | number | Combined size in bytes |

#### NoteInfo Type

typescript

```typescript
interface NoteInfo {
  path: NotePath;
  type: 'file' | 'directory';
  size?: FileSize;
  modified?: Timestamp;
  created?: Timestamp;
  isSymlink?: boolean;
  target?: NotePath;  // For symlinks
}
```

#### Example Request (Root)

typescript

```typescript
{
  "workspace": "Projects"
}
```

#### Example Request (Subdirectory)

typescript

```typescript
{
  "workspace": "Projects",
  "directory": "Octarine MCP",
  "recursive": true,
  "sort_by": "modified",
  "sort_order": "desc"
}
```

#### Example Request (Filtered)

typescript

```typescript
{
  "workspace": "Projects",
  "recursive": true,
  "filter": "**/*.md"
}
```

#### Example Response

typescript

```typescript
{
  "success": true,
  "data": {
    "notes": [
      {
        "path": "Octarine MCP/README.md",
        "type": "file",
        "size": 15420,
        "modified": "2024-01-20T14:22:00Z",
        "created": "2024-01-15T10:30:00Z"
      },
      {
        "path": "Octarine MCP/API_REFERENCE.md",
        "type": "file",
        "size": 28936,
        "modified": "2024-01-20T15:10:00Z",
        "created": "2024-01-15T10:30:00Z"
      },
      {
        "path": "Octarine MCP/docs",
        "type": "directory",
        "modified": "2024-01-19T11:00:00Z"
      }
    ],
    "directory": "Octarine MCP",
    "totalFiles": 8,
    "totalDirectories": 3,
    "totalSize": 125840
  }
}
```

#### Error Cases

```plaintext
```

| Error Code | Condition |
| --- | --- |
| `WORKSPACE_NOT_FOUND` | Workspace doesn't exist |
| `NOTE_NOT_FOUND` | Directory doesn't exist |
| `INVALID_NOTE_PATH` | Path contains invalid characters |
| `PERMISSION_DENIED` | No read permission for directory |

#### Usage Notes

- Empty workspace returns empty array
- Directories are included in results
- Recursive listing includes all subdirectories
- Filter uses glob syntax (e.g., `*.md`, `**/test-*.md`)
- Sort is case-insensitive by default
- Hidden files start with `.` (e.g., `.gitignore`)
- Symlinks are followed unless broken

---

## Best Practices

### 1. Error Handling

Always check the `success` field before accessing data:

typescript

```typescript
const result = await readNote(workspace, path);

if (!result.success) {
  console.error(`Error: ${result.error}`);
  return;
}

const { content } = result.data;
```

### 2. Path Construction

Use proper path separators and avoid hardcoding:

typescript

```typescript
// Good
const path = ["Projects", "Octarine MCP", "README.md"].join("/");

// Bad
const path = "Projects\Octarine MCP\README.md";  // Platform-specific
```

### 3. Content Validation

Validate content before writing:

typescript

```typescript
function validateMarkdown(content: string): boolean {
  return content.length > 0 && content.length < 10_000_000;
}

if (!validateMarkdown(content)) {
  throw new Error("Invalid content");
}

await writeNote(workspace, path, content);
```

### 4. Search Optimization

Use specific workspaces and limit results:

typescript

```typescript
// Good - targeted search
const results = await searchNotes({
  query: "TODO",
  workspace: "Projects",
  limit: 50
});

// Less efficient - searches all workspaces
const results = await searchNotes({
  query: "TODO"
});
```

### 5. Pagination

Implement pagination for large result sets:

typescript

```typescript
async function getAllResults(query: string, pageSize: number = 50) {
  const allResults = [];
  let offset = 0;
  let hasMore = true;

  while (hasMore) {
    const response = await searchNotes({
      query,
      limit: pageSize,
      offset
    });

    if (response.success) {
      allResults.push(...response.data.results);
      hasMore = response.data.hasMore;
      offset += pageSize;
    } else {
      break;
    }
  }

  return allResults;
}
```

### 6. Caching

Implement content caching using hashes:

typescript

```typescript
const cache = new Map<string, { hash: string; content: string }>();

async function getCachedNote(workspace: string, path: string) {
  const key = `${workspace}:${path}`;
  const cached = cache.get(key);

  const response = await readNote(workspace, path);
  if (!response.success) return null;

  if (cached && cached.hash === response.data.hash) {
    return cached.content;
  }

  cache.set(key, {
    hash: response.data.hash,
    content: response.data.content
  });

  return response.data.content;
}
```

## Rate Limiting

The server implements rate limiting to prevent abuse:

```plaintext
```

| Operation | Limit | Window |
| --- | --- | --- |
| Read | 1000 requests | 1 minute |
| Write | 100 requests | 1 minute |
| Search | 50 requests | 1 minute |
| List | 500 requests | 1 minute |

When rate limit is exceeded, the server returns:

typescript

```typescript
{
  success: false,
  error: "Rate limit exceeded",
  code: "RATE_LIMIT_EXCEEDED",
  details: {
    limit: 50,
    window: 60,
    retryAfter: 42  // seconds
  }
}
```

Implement exponential backoff when rate limited:

typescript

```typescript
async function withRetry<T>(
  fn: () => Promise<ApiResponse<T>>,
  maxRetries: number = 3
): Promise<ApiResponse<T>> {
  let retries = 0;

  while (retries < maxRetries) {
    const result = await fn();

    if (result.success || result.code !== "RATE_LIMIT_EXCEEDED") {
      return result;
    }

    const delay = Math.pow(2, retries) * 1000;
    await new Promise(resolve => setTimeout(resolve, delay));
    retries++;
  }

  throw new Error("Max retries exceeded");
}
```

## Examples

### Example 1: Read and Update Note

typescript

```typescript
// Read existing note
const readResult = await readNote("Projects", "README.md");

if (!readResult.success) {
  console.error("Failed to read:", readResult.error);
  return;
}

// Modify content
const updatedContent = readResult.data.content + "\n\n## Updated Section\n\nNew content...";

// Write back
const writeResult = await writeNote("Projects", "README.md", updatedContent);

if (writeResult.success) {
  console.log("Note updated:", writeResult.data.operation);
}
```

### Example 2: Search and Aggregate

typescript

```typescript
// Search for all TODOs
const searchResult = await searchNotes({
  query: "TODO",
  case_sensitive: false
});

if (!searchResult.success) {
  console.error("Search failed:", searchResult.error);
  return;
}

// Aggregate by workspace
const byWorkspace = searchResult.data.results.reduce((acc, result) => {
  acc[result.workspace] = (acc[result.workspace] || 0) + result.matches;
  return acc;
}, {} as Record<string, number>);

console.log("TODOs by workspace:", byWorkspace);
```

### Example 3: Bulk Operations

typescript

```typescript
// List all notes
const listResult = await listNotes({
  workspace: "Projects",
  recursive: true,
  filter: "**/*.md"
});

if (!listResult.success) {
  console.error("List failed:", listResult.error);
  return;
}

// Process each note
for (const note of listResult.data.notes) {
  if (note.type === "file") {
    const readResult = await readNote("Projects", note.path);
    
    if (readResult.success) {
      // Process note content
      console.log(`Processing: ${note.path}`);
    }
  }
}
```

### Example 4: Safe Write with Validation

typescript

```typescript
async function safeWriteNote(
  workspace: string,
  path: string,
  content: string
): Promise<boolean> {
  // Validate inputs
  if (!workspace || !path || !content) {
    console.error("Invalid parameters");
    return false;
  }

  // Check if workspace is read-only
  const listResult = await listNotes({ workspace, directory: "" });
  if (!listResult.success) {
    console.error("Workspace not accessible");
    return false;
  }

  // Write with atomic operation
  const writeResult = await writeNote(workspace, path, content, {
    atomic: true,
    create_dirs: true
  });

  if (!writeResult.success) {
    console.error("Write failed:", writeResult.error);
    return false;
  }

  console.log(`Successfully wrote: ${writeResult.data.path}`);
  return true;
}
```

---

For more examples and tutorials, see the [examples/](../examples/) directory in the repository.