# Unicity Expert Agents - Claude Code Plugin

**Version:** 1.0.0
**Author:** Unicity Network
**License:** MIT

Comprehensive AI expert agents for the Unicity Network blockchain ecosystem. Provides specialized expertise in architecture, consensus mechanisms, aggregator operations, and SDK development across TypeScript, Java, and Rust.

## What's Included

Four specialized expert agents with deep knowledge:

1. **unicity-architect** - Architecture, design principles, four-layer system design
2. **consensus-expert** - PoW/BFT consensus, RandomX mining, validator operations
3. **proof-aggregator-expert** - Aggregator API, Sparse Merkle Trees, deployment
4. **unicity-developers** - SDK usage for TypeScript, Java, and Rust

**Total Knowledge Base:** 608 KB
- 4 Expert Agents (35 KB)
- 16 Research Documents (444 KB) in `.claude-agents/unicity-research/`
- 25+ Repositories Analyzed
- 100+ Code Examples

## Installation

### Method 1: Via Marketplace (Recommended)

```bash
# Add the Unicity marketplace
cd ~/.claude/plugins/marketplaces
git clone https://github.com/unicitynetwork/unicity-expert-agents.git unicity

# Restart Claude Code
claude

# Verify installation
/plugin list
```

The agents will be automatically available after restart.

### Method 2: Direct Install

```bash
# In Claude Code
/plugin marketplace add unicitynetwork/unicity-expert-agents
/plugin install unicity-experts
```

### Method 3: Manual Installation

```bash
# Clone to marketplaces directory
mkdir -p ~/.claude/plugins/marketplaces
cd ~/.claude/plugins/marketplaces
git clone https://github.com/unicitynetwork/unicity-expert-agents.git unicity

# Restart Claude Code
```

## Usage

Claude Code automatically invokes the appropriate agent based on your question:

### Example Questions

**Architecture:**
```
You: "Explain Unicity's four-layer architecture"
→ unicity-architect agent responds
```

**Consensus:**
```
You: "How do I set up RandomX mining?"
→ consensus-expert agent responds
```

**Aggregator:**
```
You: "Show me the aggregator API for state transitions"
→ proof-aggregator-expert agent responds
```

**Development:**
```
You: "How do I create a token in TypeScript?"
→ unicity-developers agent responds
```

## Agents Overview

### unicity-architect
**Expertise:** System architecture, design patterns, layer interactions
**Use for:** Architecture questions, system design, comparing Unicity to other blockchains
**Knowledge:** Five-layer architecture, off-chain execution, multi-stage finality, performance characteristics

### consensus-expert
**Expertise:** Hybrid PoW+BFT consensus mechanisms
**Use for:** Mining setup, validator operations, consensus algorithms
**Knowledge:** RandomX mining, ASERT difficulty, BFT finality, hybrid security model

### proof-aggregator-expert
**Expertise:** Proof aggregation layer and API
**Use for:** API integration, deployment, Sparse Merkle Trees
**Knowledge:** JSON-RPC API, inclusion proofs, 1M+ commits/sec throughput, MongoDB storage

### unicity-developers
**Expertise:** SDK usage across three languages
**Use for:** Token creation, state transitions, application development
**Knowledge:** TypeScript SDK v1.6.0, Java SDK v1.3.0, Rust SDK v0.1.0, code examples

## Research Documentation

The `.claude-agents/unicity-research/` directory contains 16 comprehensive technical documents:

- UNICITY_ARCHITECTURE_REPORT.md (38 KB)
- CONSENSUS_EXPERT_REPORT.md (75 KB)
- CONSENSUS_IMPLEMENTATION_GUIDE.md (30 KB)
- AGGREGATOR_RESEARCH_SUMMARY.md (16 KB)
- UNICITY_SDK_RESEARCH_REPORT.md (51 KB)
- And 11 more...

Agents automatically reference these documents for detailed technical information.

## Verification

After installation, verify agents are loaded:

```bash
# In Claude Code
/agents
```

You should see all 4 Unicity agents listed.

## Updating

```bash
# Update to latest version
cd ~/.claude/plugins/marketplaces/unicity
git pull

# Restart Claude Code
```

## Official Resources

- **GitHub:** https://github.com/unicitynetwork
- **Key Repositories:**
  - PoW Consensus: unicitynetwork/alpha
  - BFT Consensus: unicitynetwork/bft-core
  - Aggregator: unicitynetwork/proof-aggregation-go
  - TypeScript SDK: unicitynetwork/state-transition-sdk
  - Java SDK: unicitynetwork/state-transition-sdk-java
  - Rust SDK: unicitynetwork/state-transition-sdk-rust

## Support

- **Issues:** https://github.com/unicitynetwork/unicity-expert-agents/issues
- **Contributing:** See [CONTRIBUTING.md](.claude-agents/CONTRIBUTING.md)
- **Installation Guide:** See [INSTALLATION.md](INSTALLATION.md)

## License

MIT License - See [LICENSE](.claude-agents/LICENSE)

---

**Package Size:** 608 KB of expert knowledge
**Research Coverage:** 25+ repositories, 4 expert domains, 3 programming languages
**Last Updated:** November 2024
