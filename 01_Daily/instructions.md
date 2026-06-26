/# 01_Daily — Instructions

## Purpose
Daily notes are your session logs. They capture what you learned, where you got stuck, what you're thinking about, and what's next.

## Format

Each daily note is named: `YYYY-MM-DD.md`

### Template

```markdown
---
created: 2026-06-17
status: open | completed
---

# June 17, 2026

## What I Intended to Do Today
- [ ] Task 1
- [ ] Task 2

## What Actually Happened
- Completed X
- Started Y but got stuck on Z
- Unexpected learning: [idea]

## Raw Thoughts / Inbox Dumped Here
(Throughout the day, raw captures go here. Claude will organize during /end-work)

## Open Questions
- What is a webhook really?
- How does MCP talk to Obsidian?

## Tomorrow's Focus
- Continue on X
- Research Y
```

## How Claude Uses This

### During the Day
- When you use `/capture`, Claude adds it here with timestamp
- You can check in with Claude: "What did I capture today?"

### On `/daily` Command
Claude reviews the daily note template and updates:
- Adds structure if raw thoughts are scattered
- Suggests what might move to Learning
- Notes any patterns

### On `/end-work` (Evening)
Claude reads the entire daily note:
- Extracts any completed tasks (mark as ✅)
- Identifies learnings worth keeping (prepare to move to Learning)
- Updates `session_handoff.md` with progress
- Notes any blockers for next session

## Style Notes
- Be honest, not polished
- If you worked 2 hours or 10 hours, record it
- "Confused about X" is valid input (don't wait for clarity)
- Mix technical and creative observations freely

## Important
Daily notes are **temporary**. During `/weekly`, high-value captures move to `05_Learning/`. This is intentional: Daily = working memory, Learning = long-term memory.
