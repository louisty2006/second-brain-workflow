# Start Work — Session Initialization

---
name: Start Work
description: Begin a new session with context continuity
implemented: yes
phase: 1
---

## How to Use
```
Start Work
```

Or: `Start work` or `Let's begin` — Claude recognizes variations.

## What It Does

1. **Reads** `session_handoff.md` (what you were doing last time)
2. **Reads** `00_Identity/Self.md` (who you are and what matters to you)
3. **Summarizes** what was in progress
4. **Asks** what you want to focus on today
5. **Plans** your session in context of your broader goals

## Example Interaction

```
You: Start Work

Claude:
---

Welcome back, Louis. Last session (June 17):
- You created the second brain vault system
- You were learning about webhook authentication in n8n
- You had a question: "Why does webhook need a test URL?"

Your broader goal: Become n8n + Claude Code expert within 6 months.

So far this week:
- Monday: Started webhook learning
- Tuesday-Wednesday: [gaps in notes]
- Thursday: Got HTTP auth working

What would you like to focus on today?
A) Continue webhook authentication
B) Start a new n8n concept
C) Work on a project
D) Something else?

---
```

## Why This Ritual Matters

Without this, every session starts cold. You have to:
- Remember what you were doing
- Reorient yourself
- Lose momentum

With "Start Work," Claude instantly has context and you can jump back into flow.

---

## Token Efficiency

Claude only reads what's necessary:
- session_handoff.md (~300 tokens)
- Self.md (~400 tokens)
- Total: ~700 tokens, 1-time per session

Saves enormous amounts vs. copy-pasting context every time.

## Philosophy

"Start Work" is more than a command. It's a ritual that says:
*"This time is protected. Your second brain has your back."*
