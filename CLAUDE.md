# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This repository contains the **Unicity Expert Agents** package - a comprehensive collection of AI assistant expert profiles and research documentation for the Unicity Network blockchain ecosystem.

**Package Size:** 608 KB of expert knowledge
- 4 Expert Agent Profiles (148 KB) in `.claude-agents/unicity-experts/`
- 16 Research Documents (444 KB) in `.claude-agents/unicity-research/`
- 25+ Repositories Analyzed
- 100+ Code Examples (TypeScript, Java, Rust)

## Repository Structure

```
.claude/
└── agents/                   # Claude Code agent profiles (auto-loaded)
    ├── unicity-architect.md          # Architecture expert
    ├── consensus-expert.md           # Consensus expert
    ├── proof-aggregator-expert.md    # Aggregator expert
    └── unicity-developers.md         # SDK expert

.claude-agents/
├── unicity-experts/          # Original expert profiles (reference)
│   ├── unicity-architect.md          # Architecture & design (19 KB)
│   ├── consensus-expert.md           # PoW & BFT consensus (21 KB)
│   ├── proof-aggregator-expert.md    # Aggregator layer & API (61 KB)
│   └── unicity-developers.md         # SDK guides (TypeScript/Java/Rust) (34 KB)
│
├── unicity-research/         # 16 supporting research documents
│   ├── UNICITY_ARCHITECTURE_REPORT.md
│   ├── CONSENSUS_EXPERT_REPORT.md
│   ├── UNICITY_SDK_RESEARCH_REPORT.md
│   └── [13 more research documents]
│
├── README.md                 # Main documentation & installation guide
├── EXAMPLES.md               # Usage examples & integration patterns
├── CONTRIBUTING.md           # Contribution guidelines
├── SETUP_STANDALONE_REPO.md  # Git repository setup guide
├── CHANGELOG.md              # Version history
├── LICENSE                   # MIT License
└── VERSION                   # Current version (1.0.0)

INSTALLATION.md               # Claude Code installation guide
CLAUDE.md                     # This file
```

## Working with This Repository

### Important: This is Documentation Only

This repository contains **only markdown documentation** - no source code, build systems, or tests. All files are expert profiles and research documentation for the Unicity Network.

### Claude Code Agent System

This repository includes **Claude Code subagents** in `.claude/agents/` that are automatically invoked based on user questions:

- **unicity-architect** - Architecture, design principles, system integration
- **consensus-expert** - PoW/BFT consensus, mining, validators
- **proof-aggregator-expert** - Aggregator API, SMT proofs, deployment
- **unicity-developers** - SDK usage for TypeScript, Java, Rust

Claude Code automatically selects the appropriate agent based on question context. Users can also manually invoke agents with `@agent-name`.

### File Navigation for Direct Reading

When manually exploring documentation, use these paths:

- **Architecture questions** → `.claude-agents/unicity-experts/unicity-architect.md`
- **Consensus questions** → `.claude-agents/unicity-experts/consensus-expert.md`
- **Aggregator questions** → `.claude-agents/unicity-experts/proof-aggregator-expert.md`
- **Development questions** → `.claude-agents/unicity-experts/unicity-developers.md`

Agent files in `.claude/agents/` are formatted for Claude Code with YAML frontmatter.

### Common Tasks

#### Searching Documentation

```bash
# Find specific topics across all expert profiles
grep -r "search term" .claude-agents/unicity-experts/

# Search research documentation for deeper details
grep -r "search term" .claude-agents/unicity-research/

# Find code examples in a specific language
grep -A 20 "TypeScript\|Java\|Rust" .claude-agents/unicity-experts/unicity-developers.md
```

#### Updating Documentation

When updating expert profiles or research docs:

1. Ensure markdown formatting is consistent
2. Test all code examples
3. Update version references (TypeScript v1.6.0, Java v1.3.0, Rust v0.1.0)
4. Cite sources (repository links, commits, releases)
5. Update CHANGELOG.md with changes

#### Git Workflow

```bash
# Create feature branch for updates
git checkout -b update-documentation

# Make changes to markdown files
# ... edit files ...

# Commit with descriptive message
git commit -m "Update consensus docs with latest BFT changes"

# Push to remote
git push origin update-documentation
```

## Expert Agent Profiles

### 1. Unicity Architect
**File:** `.claude-agents/unicity-experts/unicity-architect.md`
**Expertise:** Overall Unicity Network architecture, design principles, and system integration
**Key Topics:** Off-chain execution, four-layer architecture, architectural innovations

### 2. Consensus Expert
**File:** `.claude-agents/unicity-experts/consensus-expert.md`
**Expertise:** Hybrid Proof of Work and Byzantine Fault Tolerance consensus mechanisms
**Key Topics:** RandomX mining, BFT validators, state root anchoring, security model

### 3. Proof Aggregator Expert
**File:** `.claude-agents/unicity-experts/proof-aggregator-expert.md`
**Expertise:** Aggregator layer operation, API specification, deployment
**Key Topics:** Sparse Merkle Trees, JSON-RPC API, inclusion proofs, 1M+ commits/sec throughput

### 4. Unicity Developers
**File:** `.claude-agents/unicity-experts/unicity-developers.md`
**Expertise:** Language-specific SDK implementation across TypeScript, Java, and Rust
**Key Topics:** Token creation, state transitions, predicates, cryptographic operations

## Research Documentation

The `.claude-agents/unicity-research/` directory contains 16 comprehensive technical reports:

- **Architecture:** UNICITY_ARCHITECTURE_REPORT.md, UNICITY_VISUAL_ARCHITECTURE.md
- **Consensus:** CONSENSUS_EXPERT_REPORT.md, CONSENSUS_IMPLEMENTATION_GUIDE.md
- **Aggregator:** AGGREGATOR_RESEARCH_SUMMARY.md, UNICITY_AGGREGATOR_RESEARCH_INDEX.md
- **SDKs:** UNICITY_SDK_RESEARCH_REPORT.md (51 KB with 37+ code examples)

## Key Concepts

### Unicity Network Architecture

Unicity uses a four-layer architecture:
1. **Consensus Layer:** PoW (RandomX) + BFT hybrid
2. **Proof Aggregation Layer:** Sparse Merkle Trees for state commitments
3. **Token State Transition Layer:** Off-chain token execution
4. **Agentic Layer:** Autonomous execution framework

### SDK Coverage

- **TypeScript:** v1.6.0 (Production) - `@unicitylabs/state-transition-sdk`
- **Java:** v1.3.0 (Production) - `com.unicitylabs:state-transition-sdk`
- **Rust:** v0.1.0 (Experimental) - `unicity-state-transition`

All SDKs provide feature parity and interoperable token formats.

## Contributing Guidelines

See `.claude-agents/CONTRIBUTING.md` for detailed contribution guidelines.

### Quick Guidelines

- Use clear, concise markdown formatting
- Include code examples where appropriate
- Reference official Unicity repositories
- Test all code examples before committing
- Update CHANGELOG.md for all changes
- Follow semantic versioning for releases

## External Resources

### Official Unicity Links
- **GitHub Organization:** https://github.com/unicitynetwork
- **Key Repositories:**
  - PoW Consensus: unicitynetwork/alpha
  - BFT Consensus: unicitynetwork/bft-core
  - Aggregator: unicitynetwork/proof-aggregation-go
  - TypeScript SDK: unicitynetwork/state-transition-sdk
  - Java SDK: unicitynetwork/state-transition-sdk-java
  - Rust SDK: unicitynetwork/state-transition-sdk-rust

## Version Information

**Current Version:** 1.0.0 (see VERSION file)
**Last Updated:** November 2024
**Research Coverage:** 25+ repositories, 4 expert domains, 3 programming languages
