# Creating a Unicity Plugin for Claude Code

The issue: `~/.claude/agents/` is occupied by the wshobson/agents marketplace git repository, so standalone agents aren't being recognized.

## Solution: Create a Proper Unicity Plugin

### Option 1: Use Project-Level Agents (Quickest)

Instead of global installation, use project-level agents:

```bash
# In any Unicity project
cd your-unicity-project
mkdir -p .claude/agents

# Copy agents to project
cp /path/to/unicity-expert-agents/.claude/agents/*.md .claude/agents/

# Claude Code will now recognize these agents in this project
claude
/agents
```

**Pros:** Works immediately, agents available in this project
**Cons:** Must install per-project

### Option 2: Create a Claude Code Plugin (Recommended for Global Use)

Create a proper plugin structure:

```bash
# Navigate to Claude plugins directory
cd ~/.claude/plugins/marketplaces

# Create unicity-network marketplace
mkdir -p unicity-network/plugins/unicity-experts

# Create plugin structure
cd unicity-network/plugins/unicity-experts
```

#### Create `plugin.json`:

```json
{
  "name": "unicity-experts",
  "version": "1.0.0",
  "description": "Unicity Network expert agents for architecture, consensus, aggregator, and SDK development",
  "author": "Unicity Network",
  "agents": [
    "agents/unicity-architect.md",
    "agents/consensus-expert.md",
    "agents/proof-aggregator-expert.md",
    "agents/unicity-developers.md"
  ]
}
```

#### Create `agents/` directory:

```bash
mkdir agents
cp /path/to/unicity-expert-agents/.claude/agents/*.md agents/
```

#### Register the marketplace:

```bash
# In Claude Code
/plugin marketplace add unicity-network
/plugin install unicity-experts@unicity-network
```

### Option 3: Clean Installation to Dedicated Directory

If you want standalone agents without the marketplace conflict:

```bash
# Backup existing marketplace
mv ~/.claude/agents ~/.claude/agents-marketplace-backup

# Create fresh agents directory
mkdir ~/.claude/agents

# Copy Unicity agents
cp /path/to/unicity-expert-agents/.claude/agents/*.md ~/.claude/agents/

# Verify
ls -la ~/.claude/agents/
```

**Note:** This will disable the wshobson/agents marketplace. To re-enable it:

```bash
# Restore marketplace to plugins
mv ~/.claude/agents-marketplace-backup ~/.claude/plugins/marketplaces/wshobson-agents

# Agents stay in ~/.claude/agents/
```

## Debugging Agent Recognition

If agents still don't appear:

### 1. Check YAML Frontmatter

```bash
head -10 ~/.claude/agents/unicity-architect.md
```

Should show:
```yaml
---
name: unicity-architect
description: ...
---
```

### 2. Check File Permissions

```bash
chmod 644 ~/.claude/agents/*.md
```

### 3. Restart Claude Code

```bash
# Exit current session
exit

# Start fresh
claude
/agents
```

### 4. Check Claude Code Version

```bash
claude --version
```

Agents feature requires Claude Code v1.0+

### 5. Enable Debug Mode

```bash
# In Claude Code
/settings
# Look for agent debugging options
```

### 6. Check Logs

```bash
tail -f ~/.claude/debug/*.log
```

Look for agent loading errors.

## Recommended Approach

**For immediate use:** Option 1 (project-level)
**For permanent global access:** Option 2 (plugin)
**For clean slate:** Option 3 (dedicated directory)

I recommend **Option 1** to test quickly, then create **Option 2** (plugin) for permanent installation.
