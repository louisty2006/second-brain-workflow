# /daily — Daily Note Management

---
name: /daily
description: Create or update today's daily note
implemented: yes
phase: 1
---

## How to Use
```
/daily
```

Just type `/daily` with no parameters. Claude handles the rest.

## What It Does

1. **On first use of day**: Creates `01_Daily/YYYY-MM-DD.md` (uses today's date)
2. **If note already exists**: Updates and consolidates
3. **Dual-write**: Also updates `03_Projects/[name]/progress.md` if a project is active

## Step-by-Step Behaviour

### Step 1 — Detect current project
- Read `03_Projects/project-map.md` to see if the current working directory matches any known project
- If yes → dual-write mode (both 01_Daily and project progress.md)
- If no match → ask user "Which project is this for?" then register it in project-map.md before continuing

### Step 2 — Detect git activity (coding projects)
- Run `git log --oneline -5` and `git diff --stat HEAD` in the current folder
- If git output exists → use it to auto-fill "What Actually Happened" (no need to ask user)
- If no git → ask user: "What did you work on today?"

### Step 3 — Write to 01_Daily/YYYY-MM-DD.md
Use this template:
```
---
created: YYYY-MM-DD
status: open
project: [project-name or none]
---

# [Month Day, Year]

## What I Intended to Do Today
- [ ] Task 1

## What Actually Happened
[auto-filled from git log, or user input]

## Raw Captures (from /capture today)
[Claude adds today's /capture entries here]

## Open Questions
- [any blockers or unknowns]

## Tomorrow's Focus
- [next steps]
```

### Step 4 — Dual-write to project progress.md
If a project was detected in Step 1, append to `03_Projects/[name]/progress.md`:
```
## [YYYY-MM-DD]
[same summary as daily note — git-derived or user-provided]
Blockers: [if any]
Next: [tomorrow's focus]
```

### Step 5 — Auto-register new projects
If the current folder is NOT in project-map.md:
- Ask user: "This looks like a new project. Register it as [folder-name]?"
- On confirm: add a row to `03_Projects/project-map.md`
- Create `03_Projects/[name]/progress.md` with today's entry

## When to Use

- **Morning (optional)**: Run `/daily` to set intentions
- **Evening (recommended)**: Run `/daily` to consolidate the day

---

**Why dual-write matters:**
`01_Daily/` = your personal timeline. `03_Projects/[name]/progress.md` = the project's memory. Both need to stay in sync so Claude can answer questions about either context.
