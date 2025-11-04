# Unicity Expert Agents - Marketplace Distribution Guide

This guide explains how to distribute and install the Unicity Expert Agents as a Claude Code marketplace plugin.

## Repository Structure

The repository is now structured as a **Claude Code marketplace plugin**:

```
unicity-expert-agents/
├── .claude-plugin/
│   └── plugin.json           # Marketplace metadata
├── agents/                    # Agent definitions (auto-loaded)
│   ├── unicity-architect.md
│   ├── consensus-expert.md
│   ├── proof-aggregator-expert.md
│   └── unicity-developers.md
├── .claude-agents/            # Research documentation
│   ├── unicity-experts/       # Original profiles
│   ├── unicity-research/      # 16 research documents
│   └── ...
├── README.md                  # Marketplace README
├── INSTALLATION.md            # User installation guide
└── LICENSE                    # MIT License
```

## Distribution Methods

### Method 1: GitHub Repository (Recommended)

**Setup:**
1. Push to GitHub: `github.com/unicitynetwork/unicity-expert-agents`
2. Users clone directly to marketplaces directory

**User Installation:**
```bash
# Add marketplace
cd ~/.claude/plugins/marketplaces
git clone https://github.com/unicitynetwork/unicity-expert-agents.git unicity

# Restart Claude Code
claude

# Verify
/agents
```

**Update:**
```bash
cd ~/.claude/plugins/marketplaces/unicity
git pull
```

### Method 2: Official Marketplace Registry (Future)

When/if Anthropic creates an official marketplace registry:

**Setup:**
1. Register plugin with Anthropic
2. Plugin appears in `/plugin browse`

**User Installation:**
```bash
# In Claude Code
/plugin marketplace add unicity
/plugin install unicity-experts@unicity
```

### Method 3: Direct ZIP Distribution

For users without git:

**Create Release:**
```bash
# Create distribution package
cd /home/vrogojin/claude_agents
zip -r unicity-expert-agents-v1.0.0.zip \
  .claude-plugin/ \
  agents/ \
  .claude-agents/ \
  README.md \
  INSTALLATION.md \
  LICENSE
```

**User Installation:**
```bash
# Download and extract
cd ~/.claude/plugins/marketplaces
unzip unicity-expert-agents-v1.0.0.zip -d unicity

# Restart Claude Code
```

## Testing Locally

Before publishing, test the marketplace installation:

```bash
# Create symlink for testing
ln -s /home/vrogojin/claude_agents ~/.claude/plugins/marketplaces/unicity

# Restart Claude Code
claude

# Test agents
/agents

# Test agent responses
"Explain Unicity's architecture"
```

## Publishing to GitHub

### Initial Setup

```bash
cd /home/vrogojin/claude_agents

# Create GitHub repository
gh repo create unicitynetwork/unicity-expert-agents --public \
  --description "Claude Code expert agents for Unicity Network" \
  --homepage "https://github.com/unicitynetwork"

# Push to GitHub
git add .
git commit -m "Initial release: Unicity Expert Agents marketplace plugin v1.0.0"
git branch -M main
git remote add origin https://github.com/unicitynetwork/unicity-expert-agents.git
git push -u origin main
```

### Create Release

```bash
# Tag version
git tag -a v1.0.0 -m "v1.0.0 - Initial marketplace release"
git push origin v1.0.0

# Create GitHub release
gh release create v1.0.0 \
  --title "v1.0.0 - Unicity Expert Agents" \
  --notes "Initial marketplace release with 4 expert agents"
```

## User Installation Documentation

Add this to your main project README or documentation:

````markdown
## Installing Unicity Expert Agents for Claude Code

Unicity provides expert AI agents for Claude Code that understand Unicity's architecture, consensus, aggregator, and SDKs.

### Quick Install

```bash
# Add Unicity marketplace
cd ~/.claude/plugins/marketplaces
git clone https://github.com/unicitynetwork/unicity-expert-agents.git unicity

# Restart Claude Code
claude
```

### Verify Installation

```bash
# In Claude Code
/agents
```

You should see:
- unicity-architect
- consensus-expert
- proof-aggregator-expert
- unicity-developers

### Usage

Ask Unicity questions naturally:

```
"Explain Unicity's consensus mechanism"
"How do I deploy an aggregator?"
"Show me token creation in TypeScript"
```

Claude Code automatically invokes the appropriate expert agent.
````

## Marketplace Features

### Automatic Agent Loading

Agents in the `agents/` directory are automatically loaded by Claude Code when the marketplace is in `~/.claude/plugins/marketplaces/`.

### No Manual Configuration

Unlike user plugins, marketplace plugins don't require manual entry in `settings.json` - they're auto-detected.

### Research Documentation Access

Agents can reference the full research documentation in `.claude-agents/unicity-research/` for detailed technical information.

### Version Updates

Users can update by running `git pull` in the marketplace directory.

## Marketplace Advantages

1. **Simple Installation** - Just clone to marketplaces directory
2. **No Settings Edits** - Auto-detected by Claude Code
3. **Easy Updates** - Standard `git pull` workflow
4. **Discoverable** - Shows up in `/plugin list`
5. **Professional** - Same distribution model as official plugins

## Directory Structure Comparison

### Before (User Plugin - Didn't Work)
```
~/.claude/plugins/user/unicity-experts/
├── plugin.json
└── agents/
```
❌ Required manual settings.json edit
❌ Agent detection issues

### After (Marketplace - Works)
```
~/.claude/plugins/marketplaces/unicity/
├── .claude-plugin/
│   └── plugin.json
├── agents/
└── ...
```
✅ Auto-detected
✅ No manual configuration
✅ Professional distribution

## Support and Maintenance

### Reporting Issues

Direct users to report issues:
```
https://github.com/unicitynetwork/unicity-expert-agents/issues
```

### Updating Agents

When updating agent knowledge:

```bash
# Edit agent files
vi agents/unicity-architect.md

# Update version
vi .claude-plugin/plugin.json  # Bump version to 1.0.1

# Commit and tag
git add .
git commit -m "Update: Add new consensus features"
git tag v1.0.1
git push origin main v1.0.1

# Create GitHub release
gh release create v1.0.1
```

Users update with:
```bash
cd ~/.claude/plugins/marketplaces/unicity
git pull
```

## Next Steps

1. ✅ Repository structure complete
2. ⬜ Push to GitHub
3. ⬜ Create v1.0.0 release
4. ⬜ Test marketplace installation
5. ⬜ Document in main Unicity docs
6. ⬜ Announce to community

**Your repository is now ready for marketplace distribution!** 🚀
