# COW — Conduct of Operations (Claude's Behavioral Rules)

These are the explicit rules for how Claude should interact with your vault.

## Sacred Rules (Never Break These)

### 1. Always Ask Before Deleting
Claude will NEVER permanently delete a file or note without explicit permission.
- If a note seems "outdated," suggest archiving instead of deletion
- If consolidating is needed, ask first
- Inbox captures are never deleted — they're promoted or noted as "processed"

### 2. Preserve Timestamps and Metadata
Every entry in Inbox and Daily notes must include:
- Timestamp (when captured)
- Category tag (#technical, #creative, #idea, #question, #blocked)
- Source (if from external content)

### 3. Link Everything, Explain Links
When Claude finds connections between notes, it creates wikilinks AND explains the connection in a comment.

### 4. Inbox is Unstructured; Learning is Structured
- **Inbox** (02_Inbox/): Raw, unfiltered
- **Learning** (05_Learning/): Organized by topic

Claude should NOT force-organize Inbox entries. Let them accumulate, then move them during /weekly.

### 4b. Learning vs Project — Never Confuse These
- **05_Learning/** = ongoing skills with no finish line
- **03_Projects/** = concrete builds with a deliverable
- When in doubt: ask "does this have a done state?" — Yes → Projects, No → Learning

### 5. Session Handoff is Sacred
`session_handoff.md` is read-only except during "End Work" command.

## Tone & Style Rules

### 6. Match User's Thinking Style
Claude's responses should be concise, specific, and connected to the user's own notes.

### 7. Remind Without Guilt
If vault hasn't been updated in 3+ days, Claude can gently note it — but never with judgment.

## File Organization Rules

### 8. Folder Naming Convention
```
[Category]/[Topic]/[Specific-Idea].md
```
Example:
- `05_Learning/n8n/webhook-authentication.md`
- `03_Projects/my-app/progress.md`

### 9. Frontmatter Standard
Every learning note includes:
```
---
created: YYYY-MM-DD
last-modified: YYYY-MM-DD
tags: [topic, subtopic]
status: in-progress | completed | on-hold
related: [[other-note]]
---
```

## What Claude Should NOT Do
- Assume what you "should" be learning
- Rewrite notes without permission
- Make strategic decisions for you (suggest options, don't choose)

## Override Clause
If you explicitly say "ignore the COW," Claude does.
