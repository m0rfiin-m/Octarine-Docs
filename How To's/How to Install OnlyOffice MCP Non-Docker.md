# How to Install OnlyOffice MCP Through Terminal (Non-Docker)

## Prerequisites
- Your OnlyOffice DocSpace URL (e.g., https://mm0rfiin.onlyoffice.com)
- Your API key from OnlyOffice

## Step 1: Install the OnlyOffice MCP Server

```bash
npm install -g @onlyoffice/mcp-server-onlyoffice
```

## Step 2: Open Claude Desktop Config File

**On Mac:**
```bash
nano ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

**On Windows:**
```bash
notepad %APPDATA%\Claude\claude_desktop_config.json
```

## Step 3: Add OnlyOffice MCP Configuration

Add this to your config file (replace the existing Docker ONLYOFFICE section if present):

```json
{
  "mcpServers": {
    "onlyoffice": {
      "command": "mcp-server-onlyoffice",
      "env": {
        "DOCSPACE_BASE_URL": "https://mm0rfiin.onlyoffice.com",
        "DOCSPACE_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

**Important**: Replace with your actual values:
- `DOCSPACE_BASE_URL`: Your OnlyOffice DocSpace URL
- `DOCSPACE_API_KEY`: Your actual API key

## Step 4: Save and Close

**In nano (Mac):**
- Press **Ctrl + X**
- Press **Y** to confirm
- Press **Enter** to save

**In Notepad (Windows):**
- Click **File > Save**
- Close Notepad

## Step 5: Restart Claude Desktop

1. **Completely quit** Claude Desktop (Cmd+Q on Mac, close all windows on Windows)
2. **Reopen** Claude Desktop
3. OnlyOffice should now be available as a tool

## Troubleshooting Authentication Errors

If you get an error about "multiple authentication methods," make sure you only have ONE of these in your config:

❌ **Don't use multiple:**
```json
"DOCSPACE_API_KEY": "your-key",
"DOCSPACE_AUTH_TOKEN": "some-token",
"DOCSPACE_USERNAME": "user",
"DOCSPACE_PASSWORD": "pass"
```

✅ **Use only API key:**
```json
"DOCSPACE_API_KEY": "your-key-here"
```

## How to Remove Conflicting Auth Methods

If you have multiple authentication methods set:

1. Open your config file again
2. Remove any lines with:
   - `DOCSPACE_AUTH_TOKEN`
   - `DOCSPACE_USERNAME`
   - `DOCSPACE_PASSWORD`
3. Keep only `DOCSPACE_API_KEY` and `DOCSPACE_BASE_URL`
4. Save and restart Claude Desktop

## Verifying Installation

After restarting Claude Desktop, you should be able to:
- Create documents
- Access your OnlyOffice files
- Manage folders and rooms
- Upload and download files

## Common Issues

**"Multiple authentication methods" error:**
- Remove all auth methods except API key

**"Base URL missing" error:**
- Make sure `DOCSPACE_BASE_URL` is included in your config

**Connection fails:**
- Verify your API key is correct
- Check that your DocSpace URL is accessible
- Ensure there are no trailing slashes in the URL
