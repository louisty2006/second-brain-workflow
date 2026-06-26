---
created: 2026-06-17
last-modified: 2026-06-17
tags: [obsidian, knowledge-management, second-brain, system-design]
status: completed
related: [[building-first-skill]]
---

# Obsidian Vault Setup: Principles & Architecture

## Core Philosophy

Your vault isn't a filing cabinet. It's a **thinking partner**.

A good vault structure:
- **Captures easily** (low friction entry)
- **Connects automatically** (wikilinks reveal patterns)
- **Grows organically** (you don't force organization)
- **Survives your changing mind** (nothing is deleted)

## Your 9-Folder Structure

### Identity Layer (00_Identity/)
**Purpose**: Your north star
- `Self.md` — Who you are, what matters, your dual dimensions
- Read when: confused about direction
- Edit when: learning something new about yourself

### Capture Layer (01_Daily + 02_Inbox/)
**Purpose**: Raw input
- `01_Daily/` — Daily synthesis notes (template-driven)
- `02_Inbox/` — Timestamped raw captures (unstructured)
- Never delete from here; only archive
- Metadata (timestamps, tags) unlocks pattern discovery later

### Output Layer (03_Projects + 05_Learning/)
**Purpose**: Refined knowledge
- `03_Projects/` — Active work (n8n, Claude Code, creative explorations)
- `05_Learning/` — Organized knowledge (created during weekly synthesis)
- Wikilinks here map your thinking

### Support Layers
- `04_Resources/` — Bookmarks, links, external references
- `99_System/` — Vault documentation (read-only unless changing system)

## The Daily → Weekly → Learning Cycle

```
Day 1      /capture → 02_Inbox (raw, timestamped)
           /daily → 01_Daily (weekly, consolidation)

Day 7      /weekly → Reads daily notes + inbox
                   → Creates 05_Learning notes
                   → Finds wikilink connections
                   → Archives processed inbox
```

This cycle converts **noise into signal**.

## Metadata Hygiene

### Inbox Captures (Minimal)
```
**[HH:MM]** #tag Source: [if applicable]
- Raw thought here
```

### Learning Notes (Complete Frontmatter)
```yaml
---
created: 2026-06-17
last-modified: 2026-06-17
tags: [tag1, tag2]
status: in-progress | completed | on-hold
related: [[other-note]], [[another-note]]
---
```

### Why Metadata Matters
- Timestamps reveal your thinking rhythm
- Tags cluster related ideas
- Status prevents stale knowledge
- `related:` fields are seeds for wikilinks

## Wikilink Philosophy

Not all files deserve wikilinks. Link when:

✅ **DO link when**
- Showing conceptual similarity (`webhook-patterns` ↔ `narrative-triggers`)
- Showing progression (`intro` → `advanced`)
- Showing cross-domain connection (`n8n-technique` ↔ `creative-principle`)
- Explaining WHY you linked (use comment)

❌ **DON'T link**
- Every mention (creates noise)
- Between identical concepts (use frontmatter `related:` instead)
- Without explanation (links should teach, not just point)

## Folder Naming Convention

```
[Category]/[Topic]/[Specific-Idea].md
```

Examples:
- ✅ `05_Learning/n8n/webhook-http-auth.md`
- ✅ `05_Learning/creative/ai-film-grain-exploration.md`
- ❌ `05_Learning/random-note.md` (too vague)

Benefits:
- Findable by path
- Readable in graph view
- Discourages flat dumping

## Graph View as Thinking Tool

Your Obsidian graph should look like:
- **Dense clusters** = deep learning areas
- **Isolated nodes** = ideas needing connection
- **Bridges** = your unique synthesis points (creative + technical)

The graph is a map of your mind. Sparse = more learning needed. Dense = compound understanding.

## Timeline: What to Expect

**Week 1**: Feels like extra work (capturing is slower than thinking)  
**Week 2-3**: System disappears into routine  
**Week 4**: First `/weekly` feels magical (connections emerge)  
**Month 2-3**: Your vault becomes your thinking partner (50+ learning notes)  
**Month 6**: You're running /connect queries naturally (second brain is real)

## Common Mistakes to Avoid

1. **Forcing organization too early** — Let inbox be messy. Organization happens in /weekly.
2. **Deleting "wrong" ideas** — There are no wrong captures, only insights waiting to mature.
3. **Linking everything** — Sparse, meaningful links teach better than dense spam.
4. **Skipping daily notes** — The chain is: Daily → Weekly → Learning. Skip one link, chain breaks.
5. **Not reading your own Learning folder** — You'll be surprised by your own insights.

## Why This Matters for You (Specifically)

You're a **creator with a technical transition**. Most knowledge systems are built by engineers (linear, efficient, output-focused). 

This system is built by and for **thinkers** (generative, exploratory, connection-focused).

Your advantage: You already think in patterns (from film). Your vault amplifies that. The wikilinks aren't just connections; they're **narrative threads** in your learning story.
