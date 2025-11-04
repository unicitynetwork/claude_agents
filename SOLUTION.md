# Solution: Why Agents Weren't Loading

## The Problem

Your `~/.claude/agents/` directory was actually the **wshobson/agents** plugin marketplace git repository, not a standard agents directory. Claude Code couldn't recognize individual agent files mixed within this repository structure.

## What We Did

We created a proper **Claude Code plugin** structure for Unicity agents:

```
~/.claude/plugins/user/unicity-experts/
├── plugin.json                    # Plugin configuration
└── agents/
    ├── unicity-architect.md
    ├── consensus-expert.md
    ├── proof-aggregator-expert.md
    └── unicity-developers.md
```

And enabled it in `~/.claude/settings.json`:
```json
{
  "enabledPlugins": {
    ...
    "unicity-experts@user": true
  }
}
```

## Next Steps

1. **Restart Claude Code** to load the new plugin:
   ```bash
   # Exit current session
   exit

   # Start fresh
   claude
   ```

2. **Verify agents are loaded**:
   ```bash
   /agents
   ```

   You should now see:
   - unicity-architect
   - consensus-expert
   - proof-aggregator-expert
   - unicity-developers

3. **Test an agent**:
   ```
   You: "Explain Unicity's architecture"
   → unicity-architect should respond automatically
   ```

## Why This Works

- **Plugin structure**: Claude Code recognizes plugins in `~/.claude/plugins/user/`
- **plugin.json**: Declares agents to load
- **Enabled in settings**: Plugin must be enabled to load agents
- **Separate from marketplace**: Doesn't conflict with wshobson/agents repo

## If It Still Doesn't Work

### Option 1: Check Plugin Structure
```bash
# Verify files exist
ls -la ~/.claude/plugins/user/unicity-experts/agents/

# Check plugin.json
cat ~/.claude/plugins/user/unicity-experts/plugin.json
```

### Option 2: Check Settings
```bash
# Verify plugin is enabled
grep "unicity-experts" ~/.claude/settings.json
```

### Option 3: Use Project-Level Instead

If global plugin doesn't work, use project-level agents:

```bash
# In your Unicity project
mkdir -p .claude/agents
cp ~/.claude/plugins/user/unicity-experts/agents/*.md .claude/agents/

# Agents will work in this project
```

### Option 4: Check Claude Code Version

```bash
claude --version
```

Make sure you're using a recent version that supports plugins/agents.

## Directory Structure Explained

### Before (Problematic)
```
~/.claude/agents/                # Git repo (wshobson/agents)
├── .git/                        # Git repository
├── plugins/                     # Marketplace plugins
├── docs/                        # Documentation
├── README.md                    # Marketplace readme
├── consensus-expert.md          # Your agents (mixed in!)
├── unicity-architect.md         # Your agents (mixed in!)
└── ...                          # Other marketplace files
```
❌ Claude Code confused by git repo structure

### After (Working)
```
~/.claude/
├── agents/                      # Marketplace repo (unchanged)
│   └── [wshobson/agents files]
│
└── plugins/
    └── user/
        └── unicity-experts/     # Your plugin
            ├── plugin.json      # Configuration
            └── agents/          # Your agents
                ├── unicity-architect.md
                ├── consensus-expert.md
                ├── proof-aggregator-expert.md
                └── unicity-developers.md
```
✅ Claude Code recognizes plugin structure

## For Repository Distribution

When distributing the unicity-expert-agents repository, update INSTALLATION.md to use the plugin method by default:

```markdown
## Quick Installation

```bash
# Create plugin directory
mkdir -p ~/.claude/plugins/user/unicity-experts/agents

# Clone and install
git clone https://github.com/unicitynetwork/unicity-expert-agents.git
cd unicity-expert-agents
cp .claude/agents/*.md ~/.claude/plugins/user/unicity-experts/agents/
cp plugin.json ~/.claude/plugins/user/unicity-experts/

# Enable in Claude Code
echo 'Add "unicity-experts@user": true to ~/.claude/settings.json'
```
```

## Alternative: Standalone Agents Directory

If you want to use `~/.claude/agents/` for standalone agents (not plugins):

```bash
# Move marketplace to plugins
mv ~/.claude/agents ~/.claude/plugins/marketplaces/wshobson-agents

# Create fresh agents directory
mkdir ~/.claude/agents

# Copy Unicity agents
cp /path/to/unicity-expert-agents/.claude/agents/*.md ~/.claude/agents/
```

This way:
- `~/.claude/agents/` = Your standalone agents
- `~/.claude/plugins/marketplaces/wshobson-agents/` = Marketplace repo

But the plugin method (what we implemented) is cleaner and more standard.
