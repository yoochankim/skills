---
name: meeting-notes
description: |
  Transform Google Meet transcripts (Gemini-generated MD files) into structured summaries.
  Reads meeting notes, organizes them into summary/decisions/action items,
  and saves as markdown after user confirmation.
allowed-tools:
  - Read
  - Write
  - Glob
  - Grep
  - AskUserQuestion
---

# Meeting Notes Summarizer

Transforms Google Meet transcripts (Gemini-generated MD files) into structured meeting summaries.

## Workflow

### Step 1: Discover & Select Transcript Files

1. Search the project's `Meeting notes/` folder for files matching `*meeting-notes.md` pattern (using Glob)
2. **Always** present the list of found files to the user via AskUserQuestion and let them choose which file(s) to process
3. Never auto-select, even if only one file is found

### Step 2: Read Transcript & Extract Metadata

1. Read the selected MD file using Read (split into chunks if the file is large)
2. Extract metadata:
   - **Meeting title**: First part of the filename (e.g., `Weekly Product Sync`)
   - **Meeting date**: Date from the filename or the first line of the MD (e.g., `2026_02_10` → `2026-02-10`)
   - **Attendees**: Extract unique names from `**Name:**` patterns. Search with Grep using `\*\*\w+ \w+:\*\*` pattern
   - **Meeting duration**: Calculate from first/last timestamps (`### HH:MM:SS`)

### Step 3: Generate Structured Summary

Read the entire transcript and generate a summary in the format below.

**Important Rules:**
- Only include information explicitly mentioned in the transcript. No speculation or fabricated content
- Ask the user via AskUserQuestion if anything is unclear
- Always use **full names** as they appear in the transcript (e.g., "Jane Smith", never first names or nicknames)
- Write the summary in the same language as the transcript

**Output Format:**

```markdown
# {Meeting Title} - {YYYY-MM-DD}

## Attendees
- {Attendee Full Name 1}
- {Attendee Full Name 2}
- ...

## Summary
1. **{Topic}**: {Summary of discussion}
2. **{Topic}**: {Summary of discussion}
...

## Decisions
1. {Decision made}
2. {Decision made}
...

## Action Items
| # | Owner | Task | Deadline |
|---|-------|------|----------|
| 1 | {Full Name} | {Task description} | {Deadline or TBD} |
| 2 | {Full Name} | {Task description} | {Deadline or TBD} |
```

### Step 4: User Review

1. Display the generated summary in the chat
2. Ask the user via AskUserQuestion: "Is this summary accurate? Let me know if anything needs to be revised."
3. If revisions are requested, apply changes and re-confirm

### Step 5: Save File

After user approval:
1. Create `Meeting notes/summary/` folder if it doesn't exist
2. Filename: `{YYYY-MM-DD} {Meeting Title} - Summary by Claude.md`
3. Example: `2026-03-15 Weekly Product Sync - Summary by Claude.md`
4. Save using Write and inform the user of the saved file path
