# End Work — Session Closure & Synthesis

---
name: End Work
description: Close session and prepare for next one
implemented: yes
phase: 1
---

## How to Use
```
End Work
```

Or: `End session`, `Done for today`, etc.

## What It Does

1. **Reviews** today's daily note
2. **Extracts** completed tasks and learnings
3. **Identifies** blockers or open questions
4. **Updates** `session_handoff.md` with:
   - What you completed
   - What you're stuck on
   - What's next
   - Any key insights
5. **Suggests** what to prioritize tomorrow

## Example Interaction

```
You: End Work

Claude:
---

Closing session for June 17, 2026.

Today you:
✅ Created complete vault structure
✅ Configured MCP connection
✅ Set up all instructions files
⏳ Still learning: Obsidian + Claude Code integration

Your question: "How do I keep Claude in sync across sessions?"
→ Answered by setting up session_handoff.md

Updated session_handoff.md:

**Last Updated**: 2026-06-17 / 18:30  
**What You Completed Today**:
- Designed and built your Second Brain system
- Configured MCP for Obsidian + Claude integration
- Created all Phase 1 + 2 + 3 structure

**What You're Working On Now**:
- Learning first daily workflow
- Understanding how /capture, /daily, /weekly work

**Open Questions**:
- How do iPhone voice captures integrate? (Phase 3)
- Should I use Obsidian or Claude Code as primary? (Both, see MCP_SETUP.md)

**Your Current Tech Stack**:
- Claude Code + Obsidian + MCP

**Habits to Build**:
- Tomorrow: Try /capture 3 times
- Tomorrow evening: Try /daily
- Friday: Try first /weekly (if you have a week of captures)

Ready for tomorrow. See you then!
---
```

## The Session Closure Ritual

"End Work" is the mirror of "Start Work."

Together they create a **session boundary**:
- Clear beginning (Start Work)
- Productive middle (your work)
- Clear end (End Work)
- Memory transfer (session_handoff.md)

This ritual prevents:
- Context loss between sessions
- Repeated questions ("what was I doing?")
- Forgotten breakthroughs
- Momentum loss

---

## Important Note

Claude will NEVER modify `session_handoff.md` during the session. Updates only happen on "End Work" command.

This prevents mid-session context drift.

---

## Design Philosophy

Think of "End Work" as saving your game.

Without it, all progress evaporates when you close the window.  
With it, next time you open, you're exactly where you left off.
