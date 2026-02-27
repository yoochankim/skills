# MCPs

## Available MCP Servers

| MCP | Type | Purpose |
|-----|------|---------|
| [Notion](#notion) | HTTP | Sync tasks and projects with Notion |

## Notion

Connects to Notion for task and project management.

### Purpose

- Create and update tasks from meeting action items
- Map action items to existing Notion projects
- Track project status across meetings

### Required Environment Variables

| Variable | Description |
|----------|-------------|
| `NOTION_TOKEN` | Notion integration token |

### Configuration

```json
{
  "mcpServers": {
    "notion": {
      "type": "http",
      "url": "https://mcp.notion.com/mcp",
      "headers": {
        "Authorization": "Bearer ${NOTION_TOKEN}"
      }
    }
  }
}
```

## Adding a New MCP

1. Define the MCP server name, type, and purpose
2. Document required environment variables
3. Add the configuration snippet
4. Update this file and `README.md`
