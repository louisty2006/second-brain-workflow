# /connect — Find Knowledge Connections

---
name: /connect
description: Search vault and find related ideas
implemented: yes (Phase 2)
phase: 2
---

## How to Use
```
/connect [idea or question]
```

Examples:
```
/connect webhook authentication patterns
/connect How does narrative pacing relate to n8n logic?
/connect Claude Code file operations
```

## What It Does

1. **Takes** your query (a concept, question, or idea)
2. **Searches** entire vault for related notes
3. **Finds** conceptual connections (not just keyword matches)
4. **Returns** a curated list with explanations
5. **Suggests** new learning directions

## Example Interaction

```
You: /connect webhook authentication patterns

Claude:
---

Found 4 related concepts in your vault:

1. 🔗 [[http-authentication.md]] (05_Learning/n8n/)
   Direct match. You learned about HTTP headers + auth.
   
2. 🔗 [[api-security-basics.md]] (05_Learning/tech/)
   Related concept: Security principles for any API
   
3. 🔗 [[n8n-best-practices.md]] (03_Projects/n8n-learning/)
   Your project notes mention webhook security
   
4. 💡 [[knowledge-graph-as-narrative.md]] (05_Learning/creative/)
   Interesting cross-domain connection:
   "Both webhooks and film editing are about state-triggered events"
   
5. ❓ Gap identified:
   You understand webhooks but haven't practiced building one yet.
   Suggestion: Create small n8n project that uses webhook.

---
```

## Why /connect Is Powerful

**The Second Brain's core value** is not storing information. It's discovering connections.

Without /connect:
- Notes sit isolated in folders
- Knowledge stays fragmented
- You miss insights from combining ideas

With /connect:
- You see how concepts relate
- Cross-domain thinking becomes natural
- Learning compounds (each new idea builds on the old)

---

## When to Use /connect

- When learning something new: "What do I already know that relates to this?"
- When stuck: "Has another note address this?"
- When curious: "What could this idea lead to?"
- During /weekly: Claude uses /connect to find synthesis opportunities

---

## Token Optimization

/connect searches only Learning folder by default (not massive Inbox).

This makes searches fast and precise.
