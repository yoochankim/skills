# Skills

## Available Skills

| Skill | Command | Description |
|-------|---------|-------------|
| [md-meeting-notes](./skills/md-meeting-notes) | `/md-meeting-notes` | Transform meeting transcripts into structured summaries |

## md-meeting-notes

Transforms markdown meeting transcripts into structured summaries with summary, decisions, and action items.

- **Input**: Markdown meeting transcript (optimized for Google Meet/Gemini)
- **Output**: Structured summary saved as markdown
- **Workflow**: Discover files → Read transcript → Generate summary → User review → Save

### Installation

```bash
npx skills add https://github.com/yoochankim/task-manager --skill md-meeting-notes
```

## Adding a New Skill

1. Create a folder under `skills/` with the skill name
2. Add a `SKILL.md` with YAML frontmatter (`name`, `description`, `allowed-tools`)
3. Document the workflow steps in the SKILL.md body
4. Update this file and `README.md`
