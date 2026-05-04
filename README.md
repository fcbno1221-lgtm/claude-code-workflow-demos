# Claude Code Workflow Demos

Real-world patterns for building AI agent systems with Claude Code — commands, agents, skills, and security configurations for small teams.

## What This Is

A collection of battle-tested patterns extracted from running a 10-department AI agent system with **43 custom commands, 40+ specialized agents, and 14 skill modules** in a 2-person company for over 2 years.

These aren't toy examples. Every pattern here has been used daily in production.

## Architecture Overview

```
CLAUDE.md (Router / System Prompt)
│
├── commands/    → "What to do"  (User-invoked workflows)
├── agents/      → "Who does it" (Role definitions, called by commands)
└── skills/      → "What to know" (Knowledge base, referenced by agents)
```

**Reference flows one direction:** commands → agents → skills

```
User runs /plan
  → CLAUDE.md routes to plan.md (command)
    → Calls strategy-advisor (agent)
      → Reads brand-guide.md (skill)
        → Generates structured output
```

## Quick Start

1. Copy `examples/.claude/` into your project root
2. Copy `examples/CLAUDE.md` to your project root
3. Customize agent roles and skills for your domain
4. Run `/monday` to test

## Repository Structure

```
├── templates/           # Blank templates — start here
│   ├── command.md       # Command template
│   ├── agent.md         # Agent template
│   ├── skill.md         # Skill template
│   └── settings.json    # Security settings template
│
├── examples/            # Working example system
│   ├── CLAUDE.md        # System prompt (router)
│   └── .claude/
│       ├── commands/    # 5 workflow commands
│       ├── agents/      # 3 department agents
│       ├── skills/      # 1 shared knowledge base
│       └── settings.json
│
└── patterns/            # Design pattern documentation
    ├── command-patterns.md
    ├── agent-patterns.md
    ├── skill-patterns.md
    └── security-patterns.md
```

## Key Design Principles

### 1. Three-Layer Separation of Concerns
- **Commands** define workflows (the "what")
- **Agents** define roles and quality standards (the "who")
- **Skills** define shared knowledge (the "what we know")

### 2. Explicit Quality Gates
Every agent has role-specific quality criteria. Strategy agents require risk analysis. Data agents require source citation. No generic "be helpful" instructions.

### 3. Self-Improving System
The `/review` command analyzes past outputs and generates improvement proposals for skill files. The system gets better the more you use it.

### 4. Defense in Depth Security
Three layers of guardrails:
- `settings.json` — block destructive operations
- Command-level constraints — "never auto-fix", "never output secrets"
- `CLAUDE.md` — output format rules, forbidden patterns

### 5. Designed for Small Teams
Every pattern assumes resource constraints. Agents must provide actionable alternatives when ideal execution isn't feasible.

## Patterns at a Glance

| Pattern | Description | Example |
|---------|-------------|---------|
| **Batch Orchestration** | Chain multiple commands into one workflow | `/monday` |
| **Analysis → Proposal** | Gather data → Analyze → Generate recommendations | `/plan` |
| **Critical Thinking** | Force contrarian analysis, no agreement allowed | `/devils-advocate` |
| **Self-Audit** | Inspect system for issues without auto-fixing | `/security-check` |
| **Self-Improvement** | Review outputs and improve knowledge base | `/review` |
| **CRUD Subcommand** | Single command with multiple operations via args | `/tasks` |

## Tech Stack

- [Claude Code](https://claude.ai/claude-code) — CLI agent
- Markdown — all configuration
- No dependencies, no build step

## Author

Built by [Ryo Minakawa](https://github.com/fcbno1221-lgtm) — AI automation engineer helping small teams scale with Claude Code.

## License

MIT
