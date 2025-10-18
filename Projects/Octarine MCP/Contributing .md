
# Contributing to Octarine MCP Server

Thank you for your interest in contributing to the Octarine MCP Server! This document provides guidelines and instructions for contributing to the project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Documentation](#documentation)
- [Pull Request Process](#pull-request-process)
- [Release Process](#release-process)

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inspiring community for all. Please be respectful and constructive in all interactions.

### Expected Behavior

- Use welcoming and inclusive language
- Be respectful of differing viewpoints
- Accept constructive criticism gracefully
- Focus on what is best for the community
- Show empathy towards other community members

### Unacceptable Behavior

- Harassment, trolling, or derogatory comments
- Public or private intimidation
- Publishing others' private information
- Other conduct inappropriate in a professional setting

### Enforcement

Violations may result in temporary or permanent ban from the project. Report violations to the project maintainers.

## Getting Started

### Prerequisites

Before contributing, ensure you have:

- Node.js 18.0.0 or higher
- npm 9.0.0 or higher
- Git 2.0 or higher
- A code editor (VS Code recommended)
- Basic knowledge of TypeScript and MCP

### Fork and Clone

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:

bash

```bash
git clone https://github.com/YOUR_USERNAME/octarine-mcp-server.git
cd octarine-mcp-server
```

3. **Add upstream remote**:

bash

```bash
git remote add upstream https://github.com/ORIGINAL_OWNER/octarine-mcp-server.git
```

4. **Install dependencies**:

bash

```bash
npm install
```

5. **Verify setup**:

bash

```bash
npm run build
npm test
```

### Development Environment Setup

#### VS Code Configuration

Install recommended extensions:

json

```json
{
  "recommendations": [
    "dbaeumer.vscode-eslint",
    "esbenp.prettier-vscode",
    "ms-vscode.vscode-typescript-next",
    "orta.vscode-jest"
  ]
}
```

#### Editor Settings

Create `.vscode/settings.json`:

json

```json
{
  "editor.formatOnSave": true,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  },
  "typescript.tsdk": "node_modules/typescript/lib",
  "jest.autoRun": "off"
}
```

## Development Workflow

### Branch Strategy

We use a modified Git Flow:

- `main`: Stable, production-ready code
- `develop`: Integration branch for features
- `feature/*`: New features
- `fix/*`: Bug fixes
- `docs/*`: Documentation updates
- `refactor/*`: Code refactoring
- `test/*`: Test improvements

### Creating a Feature Branch

bash

```bash
# Update your fork
git checkout develop
git pull upstream develop

# Create feature branch
git checkout -b feature/amazing-feature

# Make your changes
# ...

# Commit with conventional commits
git add .
git commit -m "feat(search): add fuzzy matching support"

# Push to your fork
git push origin feature/amazing-feature
```

### Keeping Your Fork Updated

bash

```bash
# Fetch upstream changes
git fetch upstream

# Merge into your local branch
git checkout develop
git merge upstream/develop

# Update your fork
git push origin develop
```

## Coding Standards

### TypeScript Style Guide

#### General Principles

1. **Type Safety**: Prefer explicit types over `any`
2. **Immutability**: Use `const` and `readonly` where possible
3. **Pure Functions**: Favor pure functions over stateful code
4. **Clear Naming**: Use descriptive, self-documenting names
5. **Small Functions**: Keep functions focused and concise

#### Naming Conventions

typescript

```typescript
// Interfaces: PascalCase with descriptive names
interface NoteMetadata {
  size: number;
  modified: string;
}

// Types: PascalCase
type WorkspaceName = string;

// Classes: PascalCase
class WorkspaceManager {
  // Private fields: camelCase with underscore prefix
  private _workspaces: Map<string, Workspace>;
  
  // Public methods: camelCase
  async resolveWorkspace(name: string): Promise<string> {
    // Local variables: camelCase
    const workspacePath = this._workspaces.get(name);
    return workspacePath;
  }
}

// Functions: camelCase
function validateNotePath(path: string): boolean {
  return path.length > 0;
}

// Constants: SCREAMING_SNAKE_CASE
const MAX_FILE_SIZE = 10_485_760;
const DEFAULT_WORKSPACE = 'default';

// Enum: PascalCase for enum, SCREAMING_SNAKE_CASE for values
enum ErrorCode {
  NOTE_NOT_FOUND = 'NOTE_NOT_FOUND',
  PERMISSION_DENIED = 'PERMISSION_DENIED'
}
```

#### Type Annotations

typescript

```typescript
// Always annotate function parameters and return types
function readNote(workspace: string, path: string): Promise<string> {
  // Implementation
}

// Use interface for object parameters
interface SearchOptions {
  caseSensitive?: boolean;
  limit?: number;
}

function search(query: string, options: SearchOptions): SearchResult[] {
  // Implementation
}

// Avoid 'any' - use unknown or specific types
function processData(data: unknown): void {
  if (typeof data === 'string') {
    // Handle string
  }
}
```

#### Error Handling

typescript

```typescript
// Use custom error classes
class NoteNotFoundError extends Error {
  constructor(path: string) {
    super(`Note not found: ${path}`);
    this.name = 'NoteNotFoundError';
  }
}

// Always handle errors appropriately
async function readNote(path: string): Promise<string> {
  try {
    return await fs.readFile(path, 'utf-8');
  } catch (error) {
    if (error.code === 'ENOENT') {
      throw new NoteNotFoundError(path);
    }
    throw error;
  }
}
```

#### Async/Await

typescript

```typescript
// Prefer async/await over promises
async function fetchNotes(): Promise<Note[]> {
  const paths = await listNotePaths();
  const notes = await Promise.all(
    paths.map(path => readNote(path))
  );
  return notes;
}

// Handle errors in async functions
async function safeReadNote(path: string): Promise<string | null> {
  try {
    return await readNote(path);
  } catch (error) {
    console.error(`Failed to read note: ${error.message}`);
    return null;
  }
}
```

### Code Formatting

We use Prettier for automatic formatting:

bash

```bash
# Format all files
npm run format

# Check formatting
npm run format:check
```

**Prettier Configuration** (`.prettierrc`):

json

```json
{
  "semi": true,
  "trailingComma": "es5",
  "singleQuote": true,
  "printWidth": 100,
  "tabWidth": 2,
  "arrowParens": "always"
}
```

### Linting

We use ESLint for code quality:

bash

```bash
# Run linter
npm run lint

# Fix auto-fixable issues
npm run lint:fix
```

**Key ESLint Rules**:

- No unused variables
- Explicit function return types
- No `any` types without comment
- Consistent naming conventions
- No console.log in production code

## Testing Guidelines

### Test Structure

typescript

```typescript
describe('WorkspaceManager', () => {
  describe('resolveWorkspace', () => {
    it('should resolve existing workspace', async () => {
      // Arrange
      const manager = new WorkspaceManager('/workspaces');
      
      // Act
      const result = await manager.resolveWorkspace('Projects');
      
      // Assert
      expect(result).toBe('/workspaces/Projects');
    });
    
    it('should throw error for non-existent workspace', async () => {
      // Arrange
      const manager = new WorkspaceManager('/workspaces');
      
      // Act & Assert
      await expect(manager.resolveWorkspace('NonExistent'))
        .rejects
        .toThrow(WorkspaceNotFoundError);
    });
  });
});
```

### Test Coverage Requirements

- **Minimum coverage**: 80% for all metrics
- **Critical paths**: 100% coverage required
- **Error cases**: Must test all error conditions
- **Edge cases**: Test boundary conditions

### Running Tests

bash

```bash
# Run all tests
npm test

# Run specific test file
npm test -- workspace.test.ts

# Run with coverage
npm run test:coverage

# Run in watch mode
npm run test:watch

# Run integration tests
npm run test:integration
```

### Writing Good Tests

#### Do's

✅ **Test behavior, not implementation**

typescript

```typescript
// Good - tests behavior
it('should return note content', async () => {
  const content = await readNote('workspace', 'note.md');
  expect(content).toContain('# Title');
});

// Bad - tests implementation
it('should call fs.readFile', async () => {
  const spy = jest.spyOn(fs, 'readFile');
  await readNote('workspace', 'note.md');
  expect(spy).toHaveBeenCalled();
});
```

✅ **Use descriptive test names**

typescript

```typescript
// Good
it('should throw WorkspaceNotFoundError when workspace does not exist', () => {
  // ...
});

// Bad
it('should throw error', () => {
  // ...
});
```

✅ **Keep tests focused and independent**

typescript

```typescript
// Good - one assertion per test
it('should create new note', async () => {
  const result = await writeNote('workspace', 'note.md', 'content');
  expect(result.operation).toBe('created');
});

it('should return correct path', async () => {
  const result = await writeNote('workspace', 'note.md', 'content');
  expect(result.path).toBe('note.md');
});

// Bad - multiple unrelated assertions
it('should write note', async () => {
  const result = await writeNote('workspace', 'note.md', 'content');
  expect(result.operation).toBe('created');
  expect(result.path).toBe('note.md');
  expect(result.size).toBeGreaterThan(0);
});
```

#### Don'ts

❌ **Don't test external libraries**

typescript

```typescript
// Bad - testing fs library
it('should read file from filesystem', async () => {
  await fs.writeFile('test.txt', 'content');
  const content = await fs.readFile('test.txt', 'utf-8');
  expect(content).toBe('content');
});
```

❌ **Don't use real file system in unit tests**

typescript

```typescript
// Bad - uses real filesystem
it('should read note', async () => {
  await fs.writeFile('/tmp/note.md', 'content');
  const content = await readNote('/tmp', 'note.md');
  expect(content).toBe('content');
  await fs.unlink('/tmp/note.md');
});

// Good - uses mocks
it('should read note', async () => {
  jest.spyOn(fs, 'readFile').mockResolvedValue('content');
  const content = await readNote('workspace', 'note.md');
  expect(content).toBe('content');
});
```

❌ **Don't have test interdependencies**

typescript

```typescript
// Bad - tests depend on each other
describe('NoteManager', () => {
  let noteId: string;
  
  it('should create note', async () => {
    noteId = await createNote('content');
    expect(noteId).toBeDefined();
  });
  
  it('should read note', async () => {
    const content = await readNote(noteId);  // Depends on previous test!
    expect(content).toBe('content');
  });
});
```

## Documentation

### Code Comments

typescript

```typescript
/**
 * Reads a note from a workspace.
 * 
 * @param workspace - Name of the workspace
 * @param notePath - Path to the note relative to workspace root
 * @returns Promise resolving to note content
 * @throws {WorkspaceNotFoundError} If workspace does not exist
 * @throws {NoteNotFoundError} If note does not exist
 * @throws {PermissionDeniedError} If read permission is denied
 * 
 * @example
 * ```typescript
 * const content = await readNote('Projects', 'README.md');
 * console.log(content);
 * ```
 */
async function readNote(workspace: string, notePath: string): Promise<string> {
  // Implementation
}
```

### README Updates

When adding features, update:

1. Feature list in [README.md](http://README.md)
2. API reference documentation
3. Usage examples
4. Configuration options

### Changelog

Follow [Keep a Changelog](https://keepachangelog.com/) format:

markdown

```markdown
## [Unreleased]

### Added
- New feature description

### Changed
- Changed feature description

### Deprecated
- Deprecated feature description

### Removed
- Removed feature description

### Fixed
- Bug fix description

### Security
- Security fix description
```

## Pull Request Process

### Before Submitting

✅ **Checklist**:

- Code follows style guidelines
- All tests pass
- Test coverage meets requirements
- Documentation updated
- Changelog updated
- Commits follow conventional commits
- Branch is up to date with develop

### PR Title Format

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```plaintext
type(scope): subject

Examples:
feat(search): add fuzzy matching support
fix(workspace): correct path resolution on Windows
docs(api): update search endpoint documentation
refactor(core): simplify error handling
test(workspace): add permission check tests
```

**Types**:

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation only
- `style`: Code style changes (formatting)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `perf`: Performance improvements

### PR Description Template

markdown

```markdown
## Description
Brief description of changes

## Motivation
Why is this change necessary?

## Changes
- List of specific changes
- Made in this PR

## Testing
How was this tested?

## Screenshots (if applicable)
Visual changes

## Checklist
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] Changelog updated
- [ ] Breaking changes documented
```

### Review Process

1. **Automated Checks**: CI must pass
2. **Code Review**: At least one approval required
3. **Discussion**: Address all review comments
4. **Updates**: Make requested changes
5. **Approval**: Maintainer approves
6. **Merge**: Squash and merge to develop

### After Merge

1. Delete your feature branch
2. Update your local repository
3. Close related issues

## Release Process

### Version Numbering

We follow [Semantic Versioning](https://semver.org/):

- **MAJOR**: Breaking changes
- **MINOR**: New features (backwards compatible)
- **PATCH**: Bug fixes (backwards compatible)

### Creating a Release

1. **Update version** in `package.json`
2. **Update [CHANGELOG.md](http://CHANGELOG.md)**
3. **Create release branch**: `release/v1.2.3`
4. **Run full test suite**
5. **Create PR** to main
6. **After merge, tag release**: `git tag -a v1.2.3 -m "Release v1.2.3"`
7. **Push tag**: `git push origin v1.2.3`
8. **Publish to npm**: `npm publish`
9. **Create GitHub release** with changelog

## Questions?

- **Issues**: [GitHub Issues](https://github.com/yourusername/octarine-mcp-server/issues)
- **Discussions**: [GitHub Discussions](https://github.com/yourusername/octarine-mcp-server/discussions)
- **Discord**: [Join our Discord](https://discord.gg/yourserver)

## Recognition

Contributors are recognized in:

- [CONTRIBUTORS.md](http://CONTRIBUTORS.md)
- Release notes
- Project README

Thank you for contributing! 🎉