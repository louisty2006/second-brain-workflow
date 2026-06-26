# Index — Decision Log & Important Rationales

This file records major decisions you've made and WHY. This helps Claude understand your thinking patterns and avoid suggesting contradictory advice.

## Why This System Exists (June 17, 2026)
**Decision**: Build a Claude Code + Obsidian second brain instead of using Notion/other all-in-one tools.

**Why**:
- Wanted local-first storage (no vendor lock-in)
- Needed native MCP integration for tight Claude coupling
- Obsidian's visual graph feels natural to someone with visual design background
- Markdown files are universal and future-proof
- Token efficiency: Progressive Disclosure means Claude only reads what's needed

---

## Tech Stack Choices

### n8n as Primary Automation Tool
**Decision**: Focus on n8n (not Make, not Zapier, not custom coding initially)

**Why**:
- Visual workflow builder matches your visual thinking
- Lower barrier to starting (UI vs. code)
- Good for learning automation concepts before diving into code
- Plan to combine with Claude Code later for AI-enhanced workflows

---

### Claude Code Over VS Code
**Decision**: Use Claude Code as primary development environment (not VS Code)

**Why**:
- Integrated with Claude AI directly
- Faster iteration for your learning phase
- Can pair AI assistance with coding naturally
- Better for exploring AI workflow automation concepts

---

### English for This System
**Decision**: Keep this entire vault in English (even though you're bilingual)

**Why**:
- All technical documentation is in English
- Reduces code-switching friction when learning from English resources
- Professional consistency for portfolio/sharing later
- AI models work better with English documentation

---

## Learning Approach Decisions

### Not Full-Stack, Not Too Narrow
**Decision**: Learn both n8n AND Claude Code simultaneously, not sequentially

**Why**:
- They reinforce each other (n8n for workflow, Claude for logic)
- Prevents analysis paralysis ("which should I learn first?")
- You can immediately see how they work together
- Matches your creative problem-solving style

---

### Creative Applications First, Not Pure Engineering
**Decision**: When learning new tech, always ask "how could this serve a creative project?"

**Why**:
- Keeps motivation high
- Makes learning concrete (not abstract)
- Builds portfolio that's unique (not generic dev portfolio)
- Aligns with your competitive advantage

---

## Format Notes
- This file is updated when you make significant choices
- Not every micro-decision goes here — only things Claude should understand about your strategy
- Helps avoid recurring "should I do X or Y?" questions
