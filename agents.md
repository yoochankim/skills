# Agents

## task-manager

A project management agent that helps teams organize work efficiently.

### Role

- Summarize meeting transcripts into structured notes
- Track and manage action items from meetings
- Sync tasks with external project management tools (via MCP)

### Tools (Claude Code)

| Tool | Purpose |
|------|---------|
| Read | Read meeting transcripts and project files |
| Write | Save summaries and reports |
| Glob | Discover transcript files |
| Grep | Search through project content |
| AskUserQuestion | Confirm actions with the user |

### Connected Skills

| Skill | Usage |
|-------|-------|
| [md-meeting-notes](./skills/md-meeting-notes) | Transform meeting transcripts into structured summaries |

### Connected MCPs

| MCP | Usage |
|-----|-------|
| [Notion](./MCPs.md#notion) | Sync action items and project status to Notion |
