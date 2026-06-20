# /log

Conversational brain dump — just talk, Claude figures out where everything goes.

## Usage
```
/log
```
No arguments needed. Claude asks "What's on your mind?" and you free-talk.

## What it does

Claude listens to whatever you say — progress updates, ideas, learnings, blockers, new project ideas — then:

1. **Classifies each piece** into one of:
   - Inbox (raw, unclear, needs processing later)
   - Learning (new concept, technique, insight worth keeping)
   - Project update (progress on existing or new project)
   - Daily note (today's task/completion/blocker)

2. **Writes to the correct place** in the vault

3. **Creates new files/folders if needed:**
   - New Learning note → creates `05_Learning/[category]/[topic].md`
   - New project → asks first before setting up `03_Projects/[name]/`
   - Updates existing note → appends or merges, never silently overwrites

4. **Shows a routing summary** at the end:
```
Inbox (2): raw idea about X, question about Y
Learning (1): created 05_Learning/claude-code/mcp-patterns.md
Project (1): updated 03_Projects/my-project/progress.md
Daily (1): added to today's Completed section
```

## Vault
Always uses the configured vault path in your global `~/.claude/CLAUDE.md`, regardless of current working directory.

## Important rules Claude must follow
- Never delete or overwrite existing content — always append or create new sections
- When creating a new Learning note, follow the frontmatter standard from `cow.md`
- When updating a project that doesn't exist yet, ask before creating
- If no category fits, suggest a new Learning subfolder and ask for confirmation
- After routing, always show a summary of what was written where
- Keep the interaction natural — this is a brain dump, not a rigid form
