# task-manager

Project management skills for AI agents — meeting notes, action item tracking, and task management.

## Skills

| Skill | Command | Description |
|-------|---------|-------------|
| [meeting-transcript-notes](./skills/meeting-transcript-notes) | `/meeting-transcript-notes` | Transform meeting transcripts into structured notes |
| [action-item-extractor](./skills/action-item-extractor) | `/action-item-extractor` | Extract action items from meeting notes into todos.md |
| [task-tracker](./skills/task-tracker) | `/task-tracker` | Manage todos.md — list, complete, query, and alert on tasks |

## How They Work Together

```
meeting transcript
      ↓
meeting-transcript-notes   →   structured notes (summary, decisions, action items)
                                          ↓
                               action-item-extractor   →   todos.md
                                                                ↓
                                                        task-tracker (list / complete / alert)
```

## Installation

Install all skills:

```bash
npx skills add https://github.com/yoochankim/task-manager
```

Install a single skill:

```bash
npx skills add https://github.com/yoochankim/task-manager --skill meeting-transcript-notes
npx skills add https://github.com/yoochankim/task-manager --skill action-item-extractor
npx skills add https://github.com/yoochankim/task-manager --skill task-tracker
```

## Folder Structure

```
~/
├── meeting-notes/
│   ├── inbox/      ← drop transcripts here
│   ├── summary/    ← generated notes saved here
│   └── archive/    ← processed originals moved here
└── todos.md        ← managed by action-item-extractor & task-tracker
```

## Compatibility

Built and tested on [OpenClaw](https://openclaw.ai) and [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Also compatible with other AI agents that support the skills format.

## Recommended Models

| Model | Provider | Best For |
|-------|----------|----------|
| Claude Opus 4.6 | Anthropic | Complex tasks, best quality |
| Claude Sonnet 4.6 | Anthropic | Daily use, recommended default |
| Qwen 32B | Ollama | Local or budget option |
