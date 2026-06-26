# 🧠 Louis's Second Brain — Claude Command Center

## Who You Are
Former art house film director transitioning to AI Developer. Dual-dimensional mind: technology + creativity. Current focus: n8n and Claude Code mastery. Goal: become an AI workflow expert in the next few years with stable income.

## Vault Navigation Map
```
00_Identity/     → Your identity, background, goals (Self.md)
01_Daily/        → Daily notes and progress tracking
02_Inbox/        → Raw unprocessed thoughts and ideas
03_Projects/     → Concrete project outputs (apps, tools, deliverables — NOT learning tracks)
04_Resources/    → Reference materials, booklist, tools
05_Learning/     → All ongoing skill learning (n8n, claude-code, creative, tech)
99_System/       → System files (Skills, rules, MCP config)
```

## Claude's Behavior Rules
1. **Before entering any folder, read its instructions.md** (if present)
2. **On "Start Work"**: Read session_handoff.md, summarize progress, plan today
3. **On "End Work"**: Organize daily notes, update session_handoff.md
4. **When you need identity context**: Read 00_Identity/Self.md
5. **Before modifying notes**: Follow cow.md (conduct of operations)
6. **When a project is mentioned, use this decision tree:**

   **Step 1 — Always read automatically:**
   - `03_Projects/[name]/progress.md` → current progress and blockers
   - `00_Identity/Self.md` → life context (small file, always worth reading)

   **Step 2 — Decide if entering the project is needed:**
   - If the question involves technical details, architecture, bugs, or code → proceed to Step 3
   - If not (e.g. general life/planning questions) → stop here

   **Step 3 — Read project-map.md to get the project folder path:**
   - `03_Projects/project-map.md` → resolve the real folder path for the project

   **Step 4 — Enter the project folder, check for knowledge graphs first:**
   - Has `graphify-out/GRAPH_REPORT.md` → read it
   - Has `.understand-anything/knowledge-graph.json` → read it
   - Has both → read both
   - Has neither → only then read raw source code (ask user first)

   **Rule: Always prefer knowledge graphs over raw code. Raw code is the last resort.**

## Trigger Commands
- **Start Work** → Claude reads session_handoff.md and provides context
- **End Work** → Claude organizes notes and prepares for next session
- **/capture [thought]** → Smart capture with auto-routing (see Routing Rules below)
- **/log** → Free-form brain dump, Claude routes everything
- **/daily** → Create/update today's note (01_Daily/YYYY-MM-DD.md)
- **/weekly** → Synthesize Inbox → Learning, every week
- **/connect [idea]** → Search vault and find related connections
- **/stash [url...]** → 抓取+智慧分類網絡資源 link，存進 04_Resources/<分類>.md
- **/tool [problem]** → read-only，從 04_Resources/ deep search 建議工具/知識

## Routing Rules (apply to all input, always)
| Content | Destination |
|---------|-------------|
| Raw idea, question, unclear thought | `02_Inbox/captured.md` |
| "I learned...", concept, technique, insight | `05_Learning/[topic]/` — create or update note |
| Project progress, build update, deliverable | `03_Projects/[project]/` — must be a real output project |
| "Today I...", completed task, blocker | `01_Daily/YYYY-MM-DD.md` |
| 網絡資源 link (YouTube/IG/Threads/GitHub/文章) | `04_Resources/<分類>.md`（用 /stash） |

**Key distinction:**
- `05_Learning/` = skills you are developing over time (n8n, claude-code, creative)
- `03_Projects/` = concrete things you are building with a deliverable (app, tool, workflow)
- When unsure: default to Inbox, process during /weekly

## Token Optimization Strategy
- CLAUDE.md stays minimal (navigation only)
- Detailed content lives in each folder's instructions.md
- Claude reads on-demand through MCP, no bulk context loading
