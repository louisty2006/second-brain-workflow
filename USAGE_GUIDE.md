# 📚 Complete Usage Guide — Your Second Brain Handbook

Welcome to your second brain, Louis. This guide teaches you how to use the system you just built.

---

## Quick Start (First Day)

### 1. Open Obsidian
```
Open Obsidian → File → Open Vault → Select "Louis-Brain"
```

You should see the folder structure in the left sidebar.

### 2. Open Claude Code
```
Open Claude Code in terminal
cd ~/Documents/Louis-Brain
claude
```

Or if MCP is configured:
```
Just open Claude Code (MCP connects to vault automatically)
```

### 3. Your First Command
```
Start Work
```

Claude will:
- Read `CLAUDE.md` (navigation)
- Read `00_Identity/Self.md` (who you are)
- Read `session_handoff.md` (what you were doing)
- Say hello and ask what you want to do today

---

## Core Daily Workflow

### The Rhythm

```
Morning:  Start Work
          (10 seconds)
          
Throughout Day: /capture [thought]
                (30 seconds each)
                
Evening: /daily
         (5 minutes)
         
End of Day: End Work
            (5 minutes)
```

Total time per day: ~20 minutes (mostly passive).

### Example Day

**9:00 AM**
```
You: Start Work

Claude: [Shows yesterday's progress and suggests today's focus]
```

**10:30 AM** (Learning n8n)
```
You: /capture Why does the webhook node need a test URL? Is it validation?

Claude: [Saves to Inbox with timestamp and #n8n tag]
```

**12:00 PM** (Another thought)
```
You: /capture What if I combined n8n with Claude for creative filtering?

Claude: [Saves to Inbox with timestamp and #creative tag]
```

**6:00 PM** (Evening reflection)
```
You: /daily

Claude: [Creates/updates today's note, shows all your captures, asks what you completed]

You: Spent 2 hours learning webhook concepts, got stuck on HTTP auth headers
```

**6:10 PM**
```
You: End Work

Claude: [Reviews today, updates session_handoff.md, suggests tomorrow's focus]
```

---

## Weekly Workflow (Sunday Evening)

```
You: /weekly

Claude: [Does the magic]
```

What happens:
1. Reads 7 days of Daily notes
2. Reads all Inbox captures
3. Creates/updates Learning notes
4. Finds connections you missed
5. Checks: "Are you on track with your goals?"
6. Archives processed Inbox items
7. Suggests what to focus on next week

Example output from earlier in this guide.

---

## How to Use Each Folder

### 00_Identity/Self.md
**Read**: Whenever you need to remember who you are and what matters  
**Edit**: When goals change, when you learn something new about yourself

### 01_Daily/
**Create**: /daily command creates these automatically (one per day)  
**Read**: Review during /weekly  
**Edit**: Directly in Obsidian as the day goes

### 02_Inbox/
**Write**: Only via /capture command  
**Read**: During /daily (Claude shows you captures)  
**Edit**: Never (Claude will if needed, but don't manually edit)

### 03_Projects/
**Create**: When you start a significant project (n8n, Claude Code, etc.)  
**Track**: Update project README and progress.md as you work  
**Review**: During /weekly

### 05_Learning/
**Create**: Claude creates these during /weekly from your best Inbox captures  
**Read**: During /connect searches  
**Edit**: You can refine these anytime  
**Grow**: This folder grows over time (healthy to have 50+ notes after a few months)

### 04_Resources/
**Create**: Manually add reference materials, books, links  
**Read**: When you need to remind yourself of a resource

### 99_System/
**Edit**: Don't change these without reason  
**Read**: When you need to understand how the system works

---

## Commands Reference

### Phase 1 (Start Here)
- **Start Work** — Begin session
- **/capture [thought]** — Save raw thought
- **/daily** — Create/update daily note
- **End Work** — Close session

### Phase 2 (After 1 Week)
- **/weekly** — Knowledge synthesis
- **/connect [idea]** — Find related notes
- **/archive** — Move processed Inbox to archive

### Phase 3 (After 1 Month)
- iPhone voice capture integration
- Web Clipper for saving articles
- Advanced MCP automations

---

## Common Questions

### Q: What if I forget to do /capture and remember later?
**A**: Just type `/capture [thought]` whenever you remember. The timestamp will be when you do it, not when you had the thought. That's OK — capturing is better than not capturing.

### Q: Do I have to do /daily every day?
**A**: No, but consistency matters. Even 2 minutes of /daily helps. It's the glue that connects captures to learning.

### Q: What if I miss a /weekly?
**A**: Captures don't disappear. When you do /weekly, Claude will process all unprocessed captures. You can do /weekly biweekly or monthly if needed.

### Q: Can I manually create files in Obsidian?
**A**: Yes, but it's better to let Claude handle creation (through commands). Manual files work, but they won't have proper frontmatter/structure.

### Q: What if I want to delete something?
**A**: Tell Claude "delete [filename]" and follow the COW rules. Claude won't delete without confirmation.

### Q: How do I search across the vault?
**A**: 
- In Obsidian: Use Ctrl+Shift+F (Cmd+Shift+F on Mac) to search
- In Claude: Use /connect command for smart search

### Q: Will my vault backup?
**A**: Not automatically. Since it's local files, you can:
- Use Time Machine (Mac)
- Manually push to a private GitHub repo
- Use Obsidian Sync (paid, official Obsidian service)

---

## Success Metrics

After 1 week:
- ✅ You're doing /capture at least once daily
- ✅ You're doing /daily at least 3x a week
- ✅ Session handoff feels accurate

After 1 month:
- ✅ First /weekly feels like magic (Claude found connections you missed)
- ✅ Your Learning folder has 10+ notes
- ✅ You're asking /connect questions naturally

After 3 months:
- ✅ Your vault has 50+ learning notes
- ✅ You see your own thinking patterns
- ✅ Ideas compound (new learning connects to old)

---

## Pro Tips

### 1. Capture First, Organize Never
It's better to have 100 raw captures than 10 perfectly organized ones. Organization happens in /weekly.

### 2. Don't Skip Daily Notes
The magic happens in /daily → /weekly chain. Skipping daily notes breaks the chain.

### 3. Read Your Own Learning Folder
Every two weeks, browse your Learning folder. You'll be surprised by:
- How much you've learned
- Patterns in what interests you
- Ideas waiting to be developed

### 4. Use Obsidian Graph View
In Obsidian, enable Graph View (top right). You'll see your knowledge as a network.  
More wikilinks = stronger connections = better thinking.

### 5. Talk to Your Second Brain
Treat Claude as a real collaborator. Ask:
- "What do you notice about my learning patterns?"
- "What connections am I missing?"
- "Should I go deeper on X or start learning Y?"

Claude's job is to notice things you can't.

---

## Troubleshooting

### Claude doesn't recognize /capture
- Make sure you're in the Louis-Brain folder
- Make sure MCP is configured (see MCP_SETUP.md)
- Try: `cd ~/Documents/Louis-Brain && claude`

### Daily note won't create
- Check date format (should work automatically)
- Try `/daily` again
- If stuck: manually create `01_Daily/2026-06-17.md` in Obsidian

### Inbox items aren't appearing
- They save even if you don't see confirmation
- Check `02_Inbox/` directly in Obsidian
- Run `/daily` to see captures in today's note

### MCP not connecting
- See MCP_SETUP.md for full setup
- Restart Claude Code
- Verify vault path is correct in settings.json

---

## Next Steps

1. **Today**: Do "Start Work" + try 1 /capture
2. **This Week**: Get comfortable with /capture + /daily + End Work
3. **Next Week**: Try your first /weekly
4. **After 1 Month**: Evaluate what's working, what needs adjustment

You've built something powerful. Use it.

---

## One Final Thought

This second brain is not a productivity system.

It's not about "getting more done."

It's about capturing who you are, how you think, and where your ideas lead.

Over time, your vault becomes a map of your mind. And that map is the foundation of everything you build next.

Welcome to the system.

---

**Questions?**  
Ask Claude: "How do I...?"  
Claude will always help you navigate your own brain.
