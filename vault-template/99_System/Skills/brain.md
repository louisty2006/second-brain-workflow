# /brain

Instantly consult your Second Brain from any project — without switching context.

## Usage
```
/brain <question>
```

Examples:
```
/brain Should I continue my current project or start something new?
/brain What are my 3-month goals right now?
/brain What have I learned recently that's worth deepening?
```

## What it does

Spawns a subagent that operates inside your vault context and answers your question using your Second Brain's memory and identity.

## Subagent behaviour

The subagent always reads these three files first:
1. `[VAULT_PATH]/session_handoff.md` (current progress and state)
2. `[VAULT_PATH]/00_Identity/Self.md` (who you are and your goals)
3. `[VAULT_PATH]/CLAUDE.md` (vault rules)

Then, if the question involves a specific project:
4. Read `03_Projects/project-map.md` → get the real folder path for that project
5. Enter the project folder and check in this order:
   - Has `graphify-out/GRAPH_REPORT.md` → read it
   - Has `.understand-anything/knowledge-graph.json` → read it
   - Has both → read both
   - Has neither → only then read raw source code (ask user first)
6. Answer the question using all gathered context
7. Does NOT modify any vault files unless explicitly asked — use `/capture` or `/log` for writing

## Scope

- Reads Second Brain memory: ✅
- Answers life/goal/strategy questions: ✅
- Answers technical questions about projects (via graphs first): ✅
- Writes to vault: ❌ (read-only by default)

## Note

This skill is intentionally lightweight — a quick consultation, not a full session.
