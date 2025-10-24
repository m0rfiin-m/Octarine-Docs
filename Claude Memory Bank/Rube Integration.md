# Rube & Composio Integration

**Last Updated:** October 24, 2025

---

## Overview

Marco's Rube MCP integration setup, connected services, and automation workflows using Composio's 500+ app integrations.

---

## Setup & Configuration

### MCP Server Configuration

**Config File Location:**
- **Mac:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows:** `C:\Users\marco\AppData\Roaming\Claude\claude_desktop_config.json`

**Rube Server Entry:**
```json
{
  "mcpServers": {
    "rube": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://rube.app/mcp"]
    }
  }
}
```

### Installation Process
- Automated setup via: `npx @composio/mcp@latest setup`
- Must close Claude Desktop during setup
- Restart Claude completely (Cmd+Q/Alt+F4, not just close window)
- Verification: Check MCP connections in Claude interface

---

## Connected Services

### Active Integrations (7 Apps)

1. **Google Sheets** (m.m0rfiin@gmail.com)
   - Connected: Oct 9, 2025
   - Capabilities: Read/write spreadsheets, data analysis

2. **Outlook** (marco_morfin@hotmail.com)
   - Connected: Oct 9, 2025
   - Email management, searching, sending

3. **X/Twitter** (@m0rfiino)
   - Connected: Oct 9, 2025
   - Post automation, engagement tracking

4. **YouTube** (M0RFiiN channel)
   - 16 subscribers, 2 videos
   - Connected: Oct 9, 2025
   - Video management, analytics

5. **Google Docs** (m.m0rfiin@gmail.com)
   - Connected: Oct 9, 2025
   - Document creation, editing

6. **Figma** (marco_morfin@hotmail.com)
   - Connected: Oct 9, 2025
   - Design file access

7. **Reddit** (u/M0RFIN_)
   - Connected: Oct 9, 2025
   - Comment automation, karma building

### Missing Connections
- **Gmail** - Needs separate connection from Google Docs/Sheets

---

## Automation Workflows

### Reddit Comment Automation

**Executed Workflow:**
- **Purpose:** Build karma through strategic commenting
- **Target:** 5 comments across r/technology, r/Python
- **Style:** Technical, conversational, no em dashes
- **Result:** 5 live comments posted successfully

**Comments Posted:**
1. r/technology - "Users are starting to push back" thread
2. r/technology - "Intel Arc GPU driver update" discussion  
3. r/technology - "Researcher uses AI for Epstein files" post
4. r/technology - "Intel's open source future" article
5. r/Python - "Python 3.14 new features" discussion

**Quality Standards:**
- Conversational yet technical tone
- Industry-relevant insights
- Avoids excessive jargon
- Natural integration into discussions
- No em dashes (per Marco's preference)

### Outlook Email Management

**Capabilities:**
- Search messages by sender, subject, keywords
- Read email threads
- Send emails
- Filter by date range
- Access calendar

**Example Use Case:**
- Located email from Johanna regarding Livewire job opportunity
- Searched: `from:Johanna AND Livewire`
- Alternative query methods when first search didn't work

---

## Rube Capabilities

### Communication & Collaboration
- Slack, Microsoft Teams, Discord
- Gmail, Outlook
- WhatsApp, Instagram, TikTok

### Productivity & Project Management
- Notion, Asana, Linear, Jira
- Google Workspace (Drive, Sheets, Calendar)
- Microsoft Office suite

### Development Tools
- GitHub, GitLab
- Various AI platforms and APIs

### Entertainment & Creative
- Figma, Adobe integrations
- Social media platforms (X, Meta apps)
- Content management systems

### Additional Features
- Web search
- Specialized AI tools (Nano Banana, Veo3)
- 500+ total app integrations

---

## Search & Discovery

### Tool Discovery Process
1. **Call:** `RUBE_SEARCH_TOOLS` with use case description
2. **Returns:** Available tools for task
3. **Includes:** Tool slugs, descriptions, input schemas
4. **Shows:** Active connections, required parameters

**Example Use Cases:**
- "send an email to someone" → OUTLOOK_SEND_EMAIL tool
- "create a meeting invite" → Calendar tools
- "post to social media" → X/Twitter, Instagram tools

### Session Management
- **Generate session ID** for new workflows: `{generate_id: true}`
- **Continue existing:** `{id: "SESSION_ID"}`
- Pass session_id to all subsequent meta tool calls
- Maintains workflow correlation and tracking

---

## Execution & Automation

### Multi-Execute Tool
- Execute up to 20 tools in parallel
- Batch operations across apps
- Structured outputs ready for analysis
- Don't reprocess via remote bash/code

**Memory Storage:**
- Store durable facts (stable IDs, mappings)
- Natural language format
- App-specific organization
- Avoid ephemeral data

### Remote Workbench
- Process remote files
- Script bulk tool executions
- Python code in remote Jupyter sandbox
- Use for large data, not inline content

**Helper Functions:**
- `run_composio_tool()` - Execute tools
- `invoke_llm()` - Call LLM for analysis
- `proxy_execute()` - Direct API calls
- `web_search()` - Search capability
- `upload_local_file()` - Upload to S3/R2

---

## Connection Management

### Adding New Connections
1. **Search tools:** Identify missing toolkit
2. **Manage connections:** `RUBE_MANAGE_CONNECTIONS`
3. **Get auth URL:** Returns redirect link
4. **Authenticate:** Complete OAuth flow
5. **Verify:** Check active connections

### Authentication Methods
- OAuth (default/custom)
- API Key
- Bearer Token
- Basic Auth
- Hybrid
- No-auth

---

## Best Practices

### Workflow Design
- Break complex tasks into single-app queries
- Use specific tool slugs from search results
- Provide known fields for context
- Leverage parallel execution
- Store valuable memory for future use

### Memory Guidelines
- Natural language descriptions
- Store persistent data only
- Organize by app
- Avoid temporary information
- Use complete sentences

### Error Handling
- Check connection status first
- Verify tool parameters
- Use appropriate retry logic
- Handle rate limits
- Validate responses

---

## Troubleshooting

### Common Issues
1. **Tools not appearing:** Restart Claude Desktop completely
2. **Connection failures:** Re-authenticate app
3. **API errors:** Check rate limits, verify parameters
4. **Session issues:** Generate new session ID

### Logs & Debugging
- Check Claude logs in Application Support
- Verify MCP server configuration
- Test individual tool calls
- Confirm active connections

---

**Related:** [[Technical Setup]], [[Email Protocols]], [[Social Media Strategy]]
