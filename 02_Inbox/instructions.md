# 02_Inbox — Instructions

## Purpose
Raw capture zone. Everything unprocessed goes here. No organization needed. Just get ideas out of your head.

## How It Works

### When You Use `/capture [thought]`
Claude saves it here with format:
```
**[HH:MM]** #tag
[Your raw thought]
Source: [if from external content]
```

Example:
```
**14:47** #n8n #stuck
Webhook node keeps asking for a test URL. Why can't I just 
send data from another app? Is it validation or safety?
Source: n8n docs section 3.2
```

### No Organization Required
- Don't worry about "right place"
- Don't worry about writing perfectly
- Just capture the thought as is
- Timestamps matter (patterns emerge over time)
- Tags help Claude categorize later

## The Compilation Process

### Daily (Informal)
During `/daily`, Claude might note: "You captured 5 inbox items today. 3 are n8n questions, 2 are creative ideas."

### Weekly (Formal - /weekly)
This is when the real work happens. Claude will:

1. **Read all Inbox entries** from the past week
2. **Categorize by topic**:
   - Technical questions → `05_Learning/n8n/` or `05_Learning/claude-code/`
   - Creative ideas → `05_Learning/creative/`
   - Blocked issues → `03_Projects/[project-name]/blockers.md`
   - Decisions → `index.md`

3. **Create or update** proper Learning notes with:
   - Title and structure
   - Explanation of the concept
   - Why it matters
   - Related notes (wikilinks)

4. **Archive the Inbox**
   - Move processed captures to a `_archived/` subfolder with the week number
   - Example: `02_Inbox/_archived/week-25/`

## Rules for Inbox

- ✅ DO: Dump raw thoughts, questions, confused rambling
- ✅ DO: Include context if available ("from YouTube video X" or "trying to solve problem Y")
- ✅ DO: Use any number of tags
- ❌ DON'T: Try to organize perfectly
- ❌ DON'T: Wait until you understand something to capture it
- ❌ DON'T: Delete or edit entries (history matters)

## Why This Matters

Your brain generates insights fast. Inbox is the **100% capture rate** bucket. The filtering and structuring happens later.

Over time, patterns emerge:
- "I ask this question every 3 weeks" → Maybe needs deeper learning
- "I have this creative idea frequently" → Maybe it's your next project
- "I get stuck on the same technical blocker" → Needs external help

## Token Efficiency
Inbox entries are NOT loaded into Claude's context by default. Claude only reads them:
1. When you ask about them explicitly
2. During `/daily` consolidation
3. During `/weekly` compilation

This saves tokens while keeping a complete capture record.
