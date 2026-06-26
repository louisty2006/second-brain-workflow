# 99_System — Instructions

## Purpose
System configuration, rules, and skills. This is the engine room of your second brain.

## Subfolders

### Skills/
Claude's extended commands that automate complex workflows.

Each skill file has format:
```
---
name: /skill-name
description: What it does
implemented: yes | no
phase: 1 | 2 | 3
---

## How to Use
/skill-name [parameters]

## What It Does
[Step-by-step description of the workflow]

## When to Use
[When should you trigger this?]
```

### Config/
MCP settings, vault configuration, integration points.

---

## Phase-Based Skill Activation

### Phase 1 Skills (Active Now)
- `/capture [thought]` — Save raw thought to Inbox
- `/daily` — Create/update today's daily note
- `/start-work` — Begin session (read session_handoff)
- `/end-work` — End session (update session_handoff)

### Phase 2 Skills (After 2 weeks)
- `/weekly` — Knowledge synthesis review
- `/connect [idea]` — Find related concepts
- `/archive` — Move processed Inbox to archive

### Phase 3 Skills (After 1 month)
- `/research [topic]` — Deep research and save to Learning
- `/sketch-project [idea]` — Turn idea into project structure
- `/iphone-sync` — Sync voice captures from iPhone Shortcuts

---

## Important System Files

### mcp-config.json
MCP server configuration. Enables Claude Code to read/write Obsidian vault directly.

[See MCP_SETUP.md for detailed configuration]

### vault-manifest.md
List of all current files and their purposes. Updated every week.

---

## What Claude Should Not Do in This Folder
- Don't modify these rules without permission
- Don't add new Skills without discussion
- Don't change MCP config without testing first

## What Claude CAN Do Here
- Suggest new skills based on patterns you're creating
- Propose MCP improvements
- Recommend workflow automation opportunities
