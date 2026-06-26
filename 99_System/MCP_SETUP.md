# MCP Setup — Connecting Claude Code to Obsidian

## What Is MCP?
Model Context Protocol (MCP) is Anthropic's standard for connecting Claude to external systems. It lets Claude read and write your Obsidian vault directly.

## Why You Need This
Without MCP: You have to `cd` into vault folder and type commands  
With MCP: Claude can access vault from anywhere in Claude Code

## Installation Steps

### Step 1: Install Obsidian MCP Server
The recommended Obsidian MCP server is available here:
https://github.com/mark-adams/obsidian-mcp-server

Install via npm:
```bash
npm install -g obsidian-mcp-server
```

### Step 2: Configure Claude Code Settings

Open Claude Code settings file (or use `/update-config` if you have access):

**Location**: `~/.claude/settings.json` or `.claude/settings.local.json`

**Add this section**:
```json
{
  "mcp_servers": {
    "obsidian": {
      "command": "obsidian-mcp-server",
      "args": [
        "--vault-path", 
        "/Users/lautinyam/Documents/Louis-Brain"
      ],
      "disabled": false
    }
  }
}
```

Replace `/Users/lautinyam/Documents/Louis-Brain` with your actual vault path.

### Step 3: Restart Claude Code

Close Claude Code completely and reopen it. Claude should now have access to your Obsidian vault.

### Step 4: Test the Connection

In Claude Code, try:
```
Read the file CLAUDE.md from my vault
```

If Claude returns the contents, the MCP connection is working.

---

## What Claude Can Do Through MCP

✅ **Read**: Any file in the vault  
✅ **Write**: Create and update files  
✅ **Search**: Find files by name or content  
✅ **List**: Browse vault structure  
✅ **Create**: New folders and files  

---

## Troubleshooting

### Claude says "I can't find the file"
- Check that vault path is correct
- Verify Obsidian isn't open (might lock the folder)
- Try restarting Claude Code

### Commands seem slow
- Normal if vault is large (100+ files)
- MCP searches are comprehensive but take time

### Changes don't show in Obsidian UI
- Reload Obsidian (cmd+R or Ctrl+R)
- Changes made through MCP are written to disk immediately

---

## Best Practices

### 1. Keep Vault on Local Disk
MCP works best with local files. Don't use iCloud or Dropbox sync for vault folder.

### 2. One Claude Code Instance
Open only one Claude Code window per vault to avoid conflicts.

### 3. Let Obsidian Auto-Refresh
Obsidian detects external file changes automatically. No manual refresh needed.

---

## Phase 3: Advanced Integration

Once you're comfortable, you can:
- Set up iPhone Shortcuts to capture voice → vault via MCP
- Create automated workflows that trigger Claude operations
- Build custom skills that combine MCP + Claude reasoning

For now, focus on getting basic MCP working.
