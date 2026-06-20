# Second Brain Setup Guide (Single User Guide)

This is the only setup guide you need.

It is written for humans, step-by-step:
- what to run in CLI
- what to copy/paste to Claude
- how to verify setup is successful

---

## What Is This App?

This repo gives you a **Second Brain + AI coding workflow** in one package.

### The three parts

| Part | What it is | What it does for you |
|------|------------|----------------------|
| **Vault** | A folder of markdown files (Obsidian-compatible) | Stores who you are, daily notes, ideas, projects, and learning |
| **Claude Code skills** | Slash commands like `/capture`, `/daily`, `/brain` | Automates capture, daily logs, and session memory without manual filing |
| **Graph tools** (optional) | `graphify` + `understand-anything` | Lets Claude understand your codebase from graphs instead of reading every file |

### How they connect

```
Your life context (vault)          Your code (projects)
        |                                  |
        v                                  v
   /brain /capture /daily          /graphify /understand
        |                                  |
        +-------- project-map.md ---------+
```

- **`/brain`** can answer life questions ("What are my goals?") and project questions ("How does auth work?") by reading your vault first, then project knowledge graphs.
- **`/daily`** writes to both your daily note and project progress when you work inside a registered project folder.
- **Graph tools** are optional. Setup works without them; add them when you want deep code understanding.

### Vault folders (what goes where)

| Folder | Purpose |
|--------|---------|
| `00_Identity/` | Who you are and your goals (`Self.md`) |
| `01_Daily/` | One note per day |
| `02_Inbox/` | Raw captures before processing |
| `03_Projects/` | Active builds with progress logs |
| `04_Resources/` | Reference links and materials |
| `05_Learning/` | Structured knowledge over time |
| `99_System/` | Skills definitions and system notes |

Template lives in `vault-template/`. Copy it to `~/Documents/[YourName]-Brain/`.

---

## What You Will Set Up

You will set up:
- a personal vault (from `vault-template/`)
- core Claude skills for daily workflow
- optional graph tools for codebase understanding

Core skills (required):
- `daily`, `capture`, `log`, `start-work`, `end-work`, `weekly`, `brain`

Optional skill:
- `connect`

---

## Step 0 — Decide Your Vault Path

Choose your vault path now. Example:

`~/Documents/Alex-Brain`

You will use this same path in all steps.

---

## Step 1 — Install Prerequisites (CLI)

Run these in terminal:

```bash
node --version || brew install node
npm install -g @anthropic-ai/claude-code
python3 --version || brew install python
pnpm --version || npm install -g pnpm
```

Optional:

```bash
brew install --cask obsidian
```

Check Claude is available:

```bash
claude --version
```

---

## Step 2 — Copy Vault Template (CLI)

From this repo folder:

```bash
cp -R "/Users/lautinyam/Documents/second-brain-workflow/vault-template" "~/Documents/[YourName]-Brain"
```

Replace `[YourName]-Brain` with your real vault name.

---

## Step 3 — Start Claude (CLI)

```bash
cd "/Users/lautinyam/Documents/second-brain-workflow"
claude
```

---

## Step 4 — Paste Bootstrap Prompt to Claude

Copy/paste this:

```text
Set up my Second Brain system step-by-step.

My name: [Your Name]
Vault path: ~/Documents/[YourName]-Brain
Projects: [project-name -> absolute-path] or "later"

Please do this in order and confirm each step:
1) Check environment
2) Verify vault template structure
3) Install core skills (daily, capture, log, start-work, end-work, weekly, brain)
4) Install optional connect skill (if available)
5) Update ~/.claude/CLAUDE.md with triggers and vault path
6) Verify setup with /start-work, /capture, /daily, /brain
```

---

## Step 5 — Paste Identity Prompt to Claude

After bootstrap, paste this:

```text
Help me write 00_Identity/Self.md from natural language.

I will describe myself: background, current focus, 3-month goals, 1-year vision, strengths, what I am learning, and my working style.

Draft the file, show me for approval, then save.
Also update vault CLAUDE.md with my name and vault path.
```

---

## Step 6 — (Optional) Install Graph Tools

If you want codebase graph understanding, paste:

```text
Install and verify graph tools:
1) graphify
2) understand-anything

Use /install if available, or CLI fallback.
Then verify commands are usable.
```

CLI fallback examples:

```bash
uv tool install graphifyy
```

In Claude:

```text
/install graphify
/install understand-anything
```

---

## Step 7 — Final Verification

Ask Claude to run this checklist:

```text
Run final verification and report pass/fail:
1) /start-work reads session_handoff.md and Self.md
2) /capture adds a test line to 02_Inbox/captured.md
3) /daily writes today's note in 01_Daily
4) /brain answers from vault context without writing
5) project-map.md is valid (if projects were provided)
```

If all pass, setup is complete.

---

## Daily Usage (After Setup)

Use this rhythm:

```text
Morning: /start-work
During work: /capture <thought>
Need context: /brain <question>
Evening: /daily
End session: /end-work
Weekly: /weekly
```

Optional discovery:

```text
/connect <idea>
```

---

## Skill Reference — Second Brain

Install core skills during setup. Type these inside Claude Code from any folder; they always write to your configured vault.

### Core skills (required for setup)

| Command | When to use | What it does |
|---------|-------------|--------------|
| `/start-work` | Start of work session | Reads `session_handoff.md` and `Self.md`, summarizes where you left off, asks what to focus on today |
| `/end-work` | End of work session | Summarizes the day, updates `session_handoff.md` for tomorrow (only command that writes handoff) |
| `/daily` | Morning or evening | Creates/updates today's note; if you're in a registered project folder, also appends project `progress.md` and can read git log automatically |
| `/capture <thought>` | Any time you have an idea | Saves and auto-routes: inbox, learning, project, or daily note based on content |
| `/log` | Brain dump, too much in your head | You talk freely; Claude routes everything to the right vault places and shows a summary |
| `/weekly` | Once a week (e.g. Sunday) | Reads inbox + daily notes, promotes good captures to Learning notes, finds patterns |
| `/brain <question>` | Need life or project context while coding elsewhere | Answers from vault + optional project graphs. **Does not write** to vault by default |

### Examples

```text
/start-work
/capture I think we should use SSE instead of WebSockets here
/capture I learned that webhooks need explicit response nodes #technical
/daily
/end-work
/weekly
/brain Should I continue this project or start something new?
/brain How does the auth system in my-app work?
/log
```

### Optional skill

| Command | When to use | What it does |
|---------|-------------|--------------|
| `/connect <idea>` | Exploring how ideas relate | Searches your Learning folder for related notes and suggests connections (Phase 2; not required for setup) |

Example:

```text
/connect webhook authentication patterns
```

---

## Skill Reference — graphify

**Install:** `/install graphify` or CLI: `uv tool install graphifyy`

**One skill, multiple subcommands** — all use `/graphify ...`. Best for **fast** orientation and daily code questions. Works on code, docs, PDFs, video, GitHub URLs.

**Output:** `graphify-out/GRAPH_REPORT.md`, `graphify-out/graph.json`, interactive HTML in your project folder.

### Build and update

| Command | Purpose |
|---------|---------|
| `/graphify` | Full analysis of current folder |
| `/graphify <path>` | Analyze a specific folder |
| `/graphify https://github.com/owner/repo` | Clone repo and analyze |
| `/graphify <path> --update` | Incremental rebuild (only changed files) |
| `/graphify <path> --mode deep` | Thorough extraction, richer relationships |
| `/graphify <path> --cluster-only` | Re-run clustering on existing graph (no re-extract) |
| `/graphify <path> --watch` | Watch folder; auto-rebuild on file changes |

### Query (use after graph is built)

| Command | Purpose |
|---------|---------|
| `/graphify query "how does auth work?"` | Ask a question via graph traversal (instant if `graph.json` exists) |
| `/graphify query "..." --dfs` | Trace one specific path through the graph |
| `/graphify path "ConceptA" "ConceptB"` | Shortest path between two concepts |
| `/graphify explain "NodeName"` | Plain-language explanation of one node |
| `/graphify add <url>` | Fetch a URL into the corpus and update the graph |

### Examples

```text
cd ~/path/to/my-project
/graphify
/graphify query "what calls the auth middleware?"
/graphify query "trace data flow from webhook to database" --dfs
/graphify path "AuthModule" "Database"
/graphify explain "UserService"
/graphify --update
```

**Tip:** If `graphify-out/graph.json` already exists, asking a codebase question can go straight to `/graphify query` without rebuilding.

---

## Skill Reference — understand-anything (UA)

**Install:** `/install understand-anything` (requires Node ≥ 22, pnpm ≥ 10)

**Eight separate skills** — each is its own command. Best for **deep** architecture understanding, layers, and visual exploration. Run `/understand` once per major codebase, then use the others daily.

**Output:** `.understand-anything/knowledge-graph.json` (+ optional dashboard, domain graph, diff overlay)

### Skill overview

| Command | When to use | What it does | Prerequisite |
|---------|-------------|--------------|--------------|
| `/understand` | First time in a repo, or major refresh | 7-phase deep analysis → saves knowledge graph | None |
| `/understand-chat "<question>"` | Daily code questions | Searches graph for nodes/edges; answers without reading whole codebase | Graph built |
| `/understand-dashboard` | Visual exploration | Opens interactive browser dashboard (layers, tour, connections) | Graph built |
| `/understand-explain <file-or-symbol>` | Deep dive on one file/function | Explains component + neighbors + reads source | Graph built |
| `/understand-diff` | Before commit or PR review | Maps git changes → affected components + risk assessment | Graph built |
| `/understand-domain` | Business flows, not just code structure | Extracts domains and process steps → `domain-graph.json` | Graph optional |
| `/understand-onboard` | Onboarding doc for a repo | Generates `docs/ONBOARDING.md` from graph + tour | Graph built |
| `/understand-knowledge [wiki-dir]` | Karpathy-style LLM wiki | Analyzes wiki + entities; not for normal code repos | Wiki folder |

### `/understand` flags

| Flag | Purpose |
|------|---------|
| `--full` | Force full rebuild |
| `--language zh` | Chinese summaries (also `ja`, `ko`, `en`, etc.) |
| `--auto-update` | Rebuild graph on git commit |
| `--review` | Slower, higher-quality graph review |

### Examples

```text
cd ~/path/to/my-project
/understand
/understand-chat "how does the payment webhook flow work?"
/understand-explain src/auth/login.ts
/understand-explain src/auth/login.ts:verifyToken
/understand-diff
/understand-dashboard
/understand-domain
/understand-onboard
```

---

## graphify vs understand-anything — which to use?

| Situation | Use |
|-----------|-----|
| Just cloned a repo; need quick orientation | graphify |
| "What calls this function?" | `/graphify query` |
| Mixed content: code + docs + papers + video | graphify |
| Before a big refactor; need architectural layers | `/understand` once |
| Want a visual dashboard to explore structure | `/understand-dashboard` |
| Review PR impact and blast radius | `/understand-diff` |
| Daily quick structure questions | graphify (fast path) |

**Together:** Run `/understand` once for depth, use `/graphify query` for speed. `/brain` reads both when answering project questions.

---

## Exactly What Runs Where

### You run in CLI
- install dependencies (`node`, `claude`, `python`, `pnpm`)
- copy template folder
- launch `claude`

### You copy/paste to Claude
- bootstrap prompt (Step 4)
- identity prompt (Step 5)
- optional graph-tools prompt (Step 6)
- verification prompt (Step 7)

---

## Troubleshooting

### Claude says skill not found
Check:
- folder exists: `~/.claude/skills/<skill-name>/`
- `run.sh` is executable
- trigger lines exist in `~/.claude/CLAUDE.md`

### `/daily` does not map your project
Update `03_Projects/project-map.md` with absolute path and rerun `/daily`.

### `/brain` gives generic answers
Make sure these files have real content:
- `00_Identity/Self.md`
- `session_handoff.md`

### Graph commands unavailable
Re-run `/install graphify` and `/install understand-anything`, or use CLI fallback for graphify.

---

## Important

- This repository now uses this `README.md` as the single setup guide.
- Deleted older setup guides on purpose to avoid conflicting instructions.
