
# Security Policy

## Supported Versions

We provide security updates for the following versions of Octarine MCP Server:

```plaintext
```

| Version | Supported |
| --- | --- |
| 1.x.x | :white_check_mark: |
| &lt; 1.0 | :x: |

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

We take security seriously and appreciate your efforts to responsibly disclose your findings.

### How to Report

Send an email to: [**security@yourproject.com**](mailto:security@yourproject.com)

Include the following information:

- **Type of issue** (e.g., buffer overflow, SQL injection, cross-site scripting)
- **Full paths** of source file(s) related to the issue
- **Location** of the affected source code (tag/branch/commit or direct URL)
- **Step-by-step instructions** to reproduce the issue
- **Proof-of-concept or exploit code** (if possible)
- **Impact** of the issue, including how an attacker might exploit it

### Response Timeline

- **Initial Response**: Within 48 hours
- **Status Update**: Within 7 days
- **Fix Timeline**: Varies by severity (see below)

### Severity Levels

```plaintext
```

| Severity | Response Time | Examples |
| --- | --- | --- |
| **Critical** | 24-72 hours | Remote code execution, authentication bypass |
| **High** | 1-2 weeks | Local privilege escalation, significant data exposure |
| **Medium** | 2-4 weeks | Limited information disclosure, denial of service |
| **Low** | 4-8 weeks | Minor issues with limited impact |

## Security Best Practices

### For Users

1. **Keep Updated**: Always use the latest stable version
2. **Secure Configuration**: 
   - Use absolute paths for workspace directories
   - Enable read-only mode for sensitive workspaces
   - Set appropriate file size limits
3. **Access Control**: Use filesystem permissions to restrict workspace access
4. **Environment Variables**: Never commit credentials or sensitive paths to version control
5. **Network Isolation**: The server uses stdio only, no network exposure by default

### For Developers

1. **Input Validation**: Always validate and sanitize user inputs
2. **Path Traversal Prevention**: Use path validation for all file operations
3. **Error Handling**: Never expose sensitive information in error messages
4. **Dependencies**: Regularly update dependencies and monitor for vulnerabilities
5. **Code Review**: All code changes require review before merging

## Known Security Considerations

### File System Access

The server has direct filesystem access within configured workspaces:

- **Mitigation**: Workspaces are isolated and validated
- **User Action**: Configure workspaces with least privilege principle
- **Limitation**: Server runs with the same permissions as the user

### Path Traversal

Potential for path traversal attacks if paths are not properly validated:

- **Mitigation**: All paths are validated and sanitized
- **Detection**: Attempts are logged
- **Prevention**: Use only the provided API, never construct paths manually

### Resource Exhaustion

Large files or searches could consume excessive resources:

- **Mitigation**: File size limits enforced
- **Rate Limiting**: Built-in rate limiting for all operations
- **Configuration**: Adjustable limits per workspace

### Workspace Isolation

Workspaces must be properly isolated to prevent cross-workspace access:

- **Implementation**: Path resolution validates workspace boundaries
- **Verification**: Unit tests verify isolation
- **Monitoring**: Suspicious access attempts are logged

## Security Features

### 1. Path Validation

All file paths are validated before any operation:

typescript

```typescript
function validatePath(path: string): void {
  // No null bytes
  if (path.includes('\0')) throw new Error('Invalid path');
  
  // No path traversal
  if (path.includes('..')) throw new Error('Path traversal detected');
  
  // No absolute paths
  if (isAbsolute(path)) throw new Error('Absolute paths not allowed');
}
```

### 2. Workspace Sandboxing

Operations are restricted to workspace boundaries:

typescript

```typescript
function resolveInWorkspace(workspace: string, path: string): string {
  const resolved = resolve(workspace, path);
  if (!resolved.startsWith(workspace)) {
    throw new Error('Path outside workspace');
  }
  return resolved;
}
```

### 3. File Size Limits

Configurable limits prevent resource exhaustion:

typescript

```typescript
const MAX_FILE_SIZE = process.env.OCTARINE_MAX_FILE_SIZE || 10485760; // 10MB
```

### 4. Read-Only Mode

Workspaces can be marked read-only:

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

### 5. Rate Limiting

Built-in rate limiting prevents abuse:

- Read: 1000 requests/minute
- Write: 100 requests/minute
- Search: 50 requests/minute
- List: 500 requests/minute

### 6. Input Sanitization

All inputs are sanitized before processing:

typescript

```typescript
function sanitizeContent(content: string): string {
  return Buffer.from(content, 'utf-8').toString('utf-8');
}
```

## Audit Log

The server maintains audit logs for security-relevant events:

- Workspace access attempts
- Permission denials
- Path traversal attempts
- Rate limit violations
- Configuration changes

Logs are written to:

- macOS: `~/Library/Logs/Octarine/`
- Linux: `~/.local/share/Octarine/logs/`
- Windows: `%APPDATA%\Octarine\logs`

## Vulnerability Disclosure Policy

### Coordinated Disclosure

We follow coordinated disclosure:

1. **Private Report**: Vulnerability reported privately to security team
2. **Acknowledgment**: We confirm receipt within 48 hours
3. **Investigation**: We investigate and develop a fix
4. **Patch Release**: We release a security patch
5. **Public Disclosure**: After patch release, we publish advisory
6. **Credit**: Reporter credited (if desired) in security advisory

### Public Disclosure Timeline

- **Embargo Period**: 90 days from report
- **Early Disclosure**: If vulnerability is being actively exploited
- **Coordinated Release**: We work with reporter on disclosure timing

### Security Advisories

Published at: [GitHub Security Advisories](https://github.com/yourusername/octarine-mcp-server/security/advisories)

Subscribe to security announcements:

- Watch the repository (Custom → Security alerts)
- Follow [@octarinemcp](https://twitter.com/octarinemcp)

## Bug Bounty Program

We currently do not have a formal bug bounty program. However, we deeply appreciate security research and will:

- Acknowledge your contribution in our security advisories
- List you in our [CONTRIBUTORS.md](http://CONTRIBUTORS.md) file
- Provide project swag for significant findings

## Security Updates

### Notification Channels

Security updates are announced through:

1. **GitHub Security Advisories**: Primary notification method
2. **Release Notes**: All releases include security information
3. **Email**: Security mailing list (subscribe at [security@yourproject.com](mailto:security@yourproject.com))
4. **Twitter**: [@octarinemcp](https://twitter.com/octarinemcp)

### Applying Updates

Critical security updates should be applied immediately:

bash

```bash
# Update to latest version
npm update -g octarine-mcp-server

# Verify version
octarine-mcp-server --version

# Restart MCP client
```

## Compliance

### Standards

The project follows security best practices:

- OWASP Top 10 guidelines
- CWE Top 25 Most Dangerous Software Weaknesses
- Node.js Security Best Practices

### Regular Security Audits

- Dependency scanning with `npm audit`
- Static analysis with ESLint security plugins
- Regular code reviews with security focus

## Contact

- **Security Issues**: [security@yourproject.com](mailto:security@yourproject.com)
- **General Questions**: [hello@yourproject.com](mailto:hello@yourproject.com)
- **PGP Key**: Available at <https://yourproject.com/pgp>

---

**Last Updated**: January 2025

Thank you for helping keep Octarine MCP Server secure!