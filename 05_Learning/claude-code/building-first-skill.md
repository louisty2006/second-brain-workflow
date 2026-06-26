---
created: 2026-06-17
last-modified: 2026-06-17
tags: [claude-code, skills, automation, tutorial]
status: completed
related: [[obsidian-vault-setup-principles]]
---

# Building Your First Claude Code Skill

## What is a Claude Code Skill?

A skill is a custom slash command (like `/daily`, `/capture`) that executes a shell script when invoked. It lives in `~/.claude/skills/` and consists of two files:

1. **SKILL.md** — Description shown to Claude
2. **run.sh** — The actual executable script

## Architecture Pattern

```
~/.claude/skills/
├── daily/
│   ├── SKILL.md      (help text)
│   └── run.sh        (executable)
└── capture/
    ├── SKILL.md      (help text)
    └── run.sh        (executable)
```

## Creating a Skill: Step-by-Step

### 1. Create Directory
```bash
mkdir -p ~/.claude/skills/{skill-name}
```

### 2. Write SKILL.md
Keep it concise. This becomes the `/help` documentation.

```markdown
# /capture

Quick capture of thoughts into your vault.

## Usage
/capture <your thought>

Appends to 02_Inbox/captured.md with timestamp.
```

### 3. Write run.sh
- Use `set -e` for fail-on-error
- Accept arguments via `"$@"`
- Echo progress to user
- Make executable: `chmod +x run.sh`

### 4. Test It
```bash
bash ~/.claude/skills/capture/run.sh "test thought"
```

## Key Learnings

### Argument Passing
```bash
# $@ expands all arguments
# $1 is first arg, $2 is second, etc.
THOUGHT="$@"  # Get all args as one string
```

### File Manipulation
Use `awk` for in-place text insertion (cleaner than temp files):

```bash
awk '/target-line/ { print $0; print "new-line"; next } { print }' file.txt
```

### Shell Best Practices
- Quote variables: `"$VAR"` not `$VAR`
- Use `mkdir -p` to create dirs safely
- Echo status messages for user feedback
- Set `-e` flag to exit on error

## Future Improvements

- [ ] Add tag support to `/capture` (`/capture "thought" #tag`)
- [ ] Create `/weekly` skill for knowledge synthesis
- [ ] Create `/connect` skill for smart search across learning notes
- [ ] Add optional arguments to `/daily` for quick entry

## Why This Pattern?

By making automation repeatable (skills), you remove friction from knowledge capture. Every thought gets funneled the same way → system becomes trustworthy → you use it consistently.

The technical skill (shell scripting) serves the meta-skill: **building systems that think with you**.
