# How to Set Up Perplexity MCP Server

## Step 1: Get Your API Key

1. Go to: **https://www.perplexity.ai/settings/api**
2. **Sign in** to Perplexity (create account if you don't have one)
3. Click **"Generate"** or **"Create New API Key"**
4. **Copy** the API key and save it somewhere safe

## Step 2: Add to Your MCP Configuration

The config file location depends on your client:

### For Claude Desktop

**Mac**: `~/Library/Application Support/Claude/claude_desktop_config.json`

**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

### Configuration Structure

Add this to your config file:

```json
{
  "mcpServers": {
    "perplexity": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-perplexity"],
      "env": {
        "PERPLEXITY_API_KEY": "your-api-key-here"
      }
    }
  }
}
```

Replace `your-api-key-here` with your actual API key from Step 1.

## Step 3: Restart Claude Desktop

1. Completely quit Claude Desktop (Cmd+Q on Mac, close all windows on Windows)
2. Reopen Claude Desktop
3. Perplexity will now be available as a tool

## What Perplexity Adds

- **AI-synthesized answers** with citations
- **Better for research-heavy queries** compared to standard web search
- **Works alongside** built-in web search tools
- Uses Perplexity's AI-powered search capabilities

## Key Difference from Built-in Search

- **Built-in web_search**: Fast, direct search results
- **Perplexity MCP**: AI-synthesized answers with citations, better for research

## Troubleshooting

If you get authentication errors:
1. Verify your API key is correct (no extra spaces)
2. Make sure the JSON syntax is valid
3. Restart Claude Desktop completely
4. Check that the API key hasn't expired

## Note on Unverified Apps

Some users may encounter Google OAuth verification blocks. If this happens:
- The app is still in beta and may not be fully verified
- Consider waiting for official verification
- Or use alternative search methods through other MCP servers
