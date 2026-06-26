# 05_Learning — Instructions

## Purpose
Your knowledge base. Organized, explained, interconnected. This is where raw Inbox captures become permanent learning assets.

## Structure

```
05_Learning/
├── n8n/              # Workflow automation skills
├── claude-code/      # AI development and MCP concepts
├── creative/         # Creative + AI intersections
└── tech/             # General tech concepts (JavaScript, HTTP, APIs, etc.)
```

## File Format

Every learning note follows this template:

```markdown
---
created: 2026-06-17
last-modified: 2026-06-17
tags: [n8n, webhook, http, authentication]
status: in-progress | completed | on-hold
related: [[n8n-http-nodes]], [[authentication-patterns]]
source: "[YouTube URL]" or "[Book Title]" or "[Personal Discovery]"
---

# Topic Title

## What This Is
[One sentence summary]

## Why It Matters
[Why you should care about this. Connect to your goals.]

## How It Works
[Explanation with examples]
- Concept A
- Concept B

## Examples
[Concrete examples, preferably from your own experience]

## When to Use This
[Practical guidance: when would you apply this?]

## Common Mistakes
[Pitfalls to avoid based on what you've learned]

## Related Concepts
[[another-note]] — explains the dependency
[[different-angle]] — shows a creative application

## Next Steps
[What's the natural follow-up learning?]
```

## How Claude Uses This

### During Sessions
When you have a question, Claude can check if there's already a note on it, instead of explaining from scratch.

### During /weekly
Claude reviews new captures and decides:
- Is this worth a full learning note?
- Does it add to an existing note?
- Should it be archived (useful but not critical)?

### For /connect command
When you ask "how does this relate to what I learned?", Claude searches this whole folder.

## Important Principles

### 1. Source Everything
If you learned something from a video, article, or conversation, record it. This helps you:
- Remember where to find the detailed explanation later
- Understand your learning pattern (what sources work best?)

### 2. Write for Yourself, Not the Internet
These aren't blog posts. Write like you're explaining to yourself from 6 months ago:
- Use your terminology and metaphors
- Include the "stupid" questions you had
- Mix technical and personal observations

### 3. Link Liberally
When a note explains a dependency or related concept, create a wikilink:
```
This webhook pattern mirrors [[film-pacing-concepts]] because both 
involve threshold-triggered state changes.
```

### 4. Status Matters
- **in-progress**: You understand basics but haven't fully integrated it
- **completed**: You've learned this and applied it to a real project
- **on-hold**: Important but deprioritized for now

---

## Subfolders Explained

### n8n/
Workflow automation concepts specific to n8n.
- Nodes and their configurations
- Authentication patterns
- Data transformation techniques
- Real workflows you've built

### claude-code/
AI development and automation.
- MCP concepts
- File system operations through Claude
- Prompt engineering techniques
- Debugging AI responses

### creative/
Where tech meets art.
- AI applications for filmmaking
- Creative AI tools and concepts
- Narrative structures + technical patterns
- Vision for your unique niche

### tech/
General technical foundations.
- JavaScript basics
- HTTP and APIs
- Authentication concepts
- Data structures

---

## Growth Trajectory

This folder will grow. At some point you'll have 50+ notes. That's healthy. Claude's job is to help you navigate and connect them.
