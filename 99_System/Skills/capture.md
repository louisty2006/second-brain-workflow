# /capture — Smart Capture with Auto-Routing

---
name: /capture
description: Smart capture with automatic routing to the right vault location
implemented: yes
phase: 1
---

## How to Use
```
/capture <your thought> [#tag]
```

## What It Does
1. Reads the content and auto-routes to the correct location
2. Adds timestamp and tag
3. Confirms where it was saved

## Routing Table
| Signal in content | Destination |
|------------------|-------------|
| `#idea`, `#question`, unclear thought | `02_Inbox/captured.md` |
| "I learned", "concept", "technique", `#technical`, `#creative` | `05_Learning/[topic]/` |
| "progress", "working on", "building", `#project` | `03_Projects/[project]/progress.md` |
| "today", "completed", "blocked", `#blocked` | `01_Daily/YYYY-MM-DD.md` |

## Examples
```
/capture "Webhook needs test URL because n8n can't simulate external calls" #technical
→ 05_Learning/n8n/

/capture "Idea: use n8n to auto-tag Inbox captures" #idea
→ 02_Inbox/captured.md

/capture "Finished routing logic for /capture skill today" #blocked
→ 01_Daily/YYYY-MM-DD.md
```

## Important Notes
- Saves to `02_Inbox/captured.md` (single file, chronological)
- Never deletes existing content — always appends
- When creating a new Learning note: uses frontmatter standard from cow.md
- When routing to a Project that doesn't exist: asks for confirmation first
- When unsure: defaults to Inbox, processes during /weekly

## Design Philosophy
Lower the friction between "having a thought" and "recording it."
Speed matters more than perfect categorization — /weekly handles the rest.
