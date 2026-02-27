# Task Manager

A project management agent for Claude Code. Summarizes meetings, tracks action items, and syncs with external tools.

## Overview

| Component | Description |
|-----------|-------------|
| [Agents](./agents.md) | Project management agent definition |
| [Skills](./skills.md) | Reusable skill modules |
| [MCPs](./MCPs.md) | External service integrations |

## Quick Start

Install the meeting notes skill:

```bash
npx skills install https://github.com/yoochankim/task-manager/tree/main/skills/md-meeting-notes
```

Then run `/md-meeting-notes` in Claude Code.

## Folder Structure

```
task-manager/
├── README.md
├── agents.md
├── skills.md
├── MCPs.md
└── skills/
    └── md-meeting-notes/
        └── SKILL.md
```
