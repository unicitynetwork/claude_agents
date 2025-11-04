# Unicity Expert Agents - Claude Code Installation Guide

Quick guide to install and use Unicity Network expert agents with Claude Code.

## What Are These Agents?

Four specialized AI agents that provide deep expertise on Unicity Network:

1. **unicity-architect** - System architecture, design principles, layer interactions
2. **consensus-expert** - PoW/BFT consensus, mining, validators
3. **proof-aggregator-expert** - Aggregator API, SMT proofs, deployment
4. **unicity-developers** - SDK usage for TypeScript, Java, Rust

## Quick Installation

### Option 1: Clone to Project (Recommended)

```bash
# Navigate to your project directory
cd your-project

# Clone agents into .claude directory
git clone https://github.com/unicitynetwork/unicity-expert-agents.git .claude-temp
mkdir -p .claude/agents
cp .claude-temp/.claude/agents/*.md .claude/agents/
rm -rf .claude-temp

# Verify installation
ls -la .claude/agents/
```

### Option 2: Global Installation (Plugin Method - Recommended)

```bash
# Clone repository
git clone https://github.com/unicitynetwork/unicity-expert-agents.git ~/unicity-agents-temp

# Create plugin directory
mkdir -p ~/.claude/plugins/user/unicity-experts

# Copy plugin files
cp ~/unicity-agents-temp/plugin.json ~/.claude/plugins/user/unicity-experts/
cp -r ~/unicity-agents-temp/agents ~/.claude/plugins/user/unicity-experts/

# Clean up
rm -rf ~/unicity-agents-temp

# Enable plugin: Add this line to ~/.claude/settings.json under "enabledPlugins":
#   "unicity-experts@user": true

# Verify installation
ls -la ~/.claude/plugins/user/unicity-experts/agents/
```

**One-liner installation:**
```bash
git clone https://github.com/unicitynetwork/unicity-expert-agents.git /tmp/ue && mkdir -p ~/.claude/plugins/user/unicity-experts && cp /tmp/ue/plugin.json ~/.claude/plugins/user/unicity-experts/ && cp -r /tmp/ue/agents ~/.claude/plugins/user/unicity-experts/ && rm -rf /tmp/ue && echo "Add '\"unicity-experts@user\": true' to ~/.claude/settings.json"
```

### Option 3: Git Submodule (For Version Control)

```bash
# Add as submodule to track updates
git submodule add https://github.com/unicitynetwork/unicity-expert-agents.git .claude-agents

# Link agents to Claude Code
mkdir -p .claude/agents
ln -s ../../.claude-agents/.claude/agents/*.md .claude/agents/

# Update submodule
git submodule update --remote
```

## Verify Installation

After installation, verify agents are recognized by Claude Code:

```bash
# List available agents
claude --list-agents

# Or within Claude Code session
/agents
```

You should see:
- `unicity-architect`
- `consensus-expert`
- `proof-aggregator-expert`
- `unicity-developers`

## Using the Agents

Claude Code will **automatically invoke** the appropriate agent based on your question:

### Example Usage

**Architecture Questions:**
```
You: "Explain Unicity's four-layer architecture"
→ Claude automatically invokes unicity-architect agent
```

**Mining/Consensus Questions:**
```
You: "How do I set up a RandomX miner?"
→ Claude automatically invokes consensus-expert agent
```

**Aggregator Questions:**
```
You: "Show me how to deploy an aggregator with Kubernetes"
→ Claude automatically invokes proof-aggregator-expert agent
```

**Development Questions:**
```
You: "How do I create a token in TypeScript?"
→ Claude automatically invokes unicity-developers agent
```

### Manual Agent Invocation (Optional)

If you want to explicitly use an agent:

```
You: "@unicity-architect compare Unicity to Ethereum"
You: "@consensus-expert explain BFT finality"
You: "@proof-aggregator-expert what's the API for inclusion proofs"
You: "@unicity-developers show Java token transfer example"
```

## What's Included

### Agent Files (in `.claude/agents/`)

- `unicity-architect.md` (19 KB)
- `consensus-expert.md` (21 KB)
- `proof-aggregator-expert.md` (61 KB)
- `unicity-developers.md` (34 KB)

### Research Documentation (in `.claude-agents/unicity-research/`)

16 comprehensive research documents (444 KB):
- Architecture reports and diagrams
- Consensus implementation guides
- Aggregator research summaries
- SDK research with 37+ code examples

Agents automatically reference these docs for detailed information.

## Updating Agents

### For Git Clone Installation

```bash
# Navigate to project
cd your-project

# Re-clone latest version
rm -rf .claude-temp
git clone https://github.com/unicitynetwork/unicity-expert-agents.git .claude-temp
cp .claude-temp/.claude/agents/*.md .claude/agents/
rm -rf .claude-temp
```

### For Git Submodule Installation

```bash
# Update submodule to latest
git submodule update --remote

# Commit the update
git add .claude-agents
git commit -m "Update Unicity expert agents"
```

### For Global Installation

```bash
# Re-download latest
rm -rf ~/unicity-agents-temp
git clone https://github.com/unicitynetwork/unicity-expert-agents.git ~/unicity-agents-temp
cp ~/unicity-agents-temp/.claude/agents/*.md ~/.claude/agents/
rm -rf ~/unicity-agents-temp
```

## Troubleshooting

### Agents Not Showing Up

**Check installation location:**
```bash
# Project-level (preferred)
ls -la .claude/agents/

# Global level
ls -la ~/.claude/agents/
```

**Verify YAML frontmatter:**
```bash
# Each agent file should start with:
---
name: agent-name
description: ...
---
```

**Restart Claude Code:**
```bash
# Exit and restart Claude Code session
exit
claude
```

### Agents Not Being Invoked

**Check agent descriptions match your question:**
- Architecture → unicity-architect
- Mining/Consensus → consensus-expert
- Aggregator/API → proof-aggregator-expert
- SDKs/Development → unicity-developers

**Try manual invocation:**
```
@unicity-architect <your question>
```

### Research Documents Not Found

**Ensure research docs are in correct location:**
```bash
# Should be at:
.claude-agents/unicity-research/*.md

# If missing, clone full repo:
git clone https://github.com/unicitynetwork/unicity-expert-agents.git .claude-agents
```

## System Requirements

- Claude Code CLI installed
- Git (for clone/submodule methods)
- 5 MB disk space for agents
- 500 MB for full research documentation

## Project Structure After Installation

```
your-project/
├── .claude/
│   └── agents/                    # Claude Code agent directory
│       ├── unicity-architect.md
│       ├── consensus-expert.md
│       ├── proof-aggregator-expert.md
│       └── unicity-developers.md
│
├── .claude-agents/                # Full research documentation
│   ├── unicity-experts/           # Original expert profiles
│   ├── unicity-research/          # 16 research documents
│   ├── README.md
│   ├── EXAMPLES.md
│   └── ...
│
└── ... (your project files)
```

## Testing Your Installation

Run these test questions to verify agents work:

```bash
# Start Claude Code
claude

# Test architecture agent
You: "What are the five layers of Unicity?"

# Test consensus agent
You: "Explain RandomX mining"

# Test aggregator agent
You: "What's the RegisterStateTransition API?"

# Test developers agent
You: "Show me TypeScript token minting"
```

If agents respond with detailed, expert knowledge, installation successful! 🎉

## Getting Help

**Issues with installation:**
- Check [GitHub Issues](https://github.com/unicitynetwork/unicity-expert-agents/issues)
- Review [CONTRIBUTING.md](CONTRIBUTING.md)

**Questions about Unicity:**
- Ask the agents! They're here to help.
- Visit official Unicity repositories on GitHub

**Agent improvements:**
- Submit issues or PRs
- See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines

## Next Steps

1. ✅ Verify installation with `/agents` command
2. ✅ Test with sample questions
3. ✅ Start building on Unicity!

For usage examples, see [EXAMPLES.md](EXAMPLES.md).
For architecture overview, see [README.md](README.md).
