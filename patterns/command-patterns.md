# Command Design Patterns

## Pattern 1: Batch Orchestration
**When to use:** Recurring workflows that combine multiple steps (daily standup, weekly review).

```
/monday → reads tasks → reads metrics → generates briefing
```

Key principles:
- Chain existing commands/agents, don't duplicate logic
- Set a word limit to keep output scannable
- Flag stale items (e.g., "carried over 2+ weeks")

## Pattern 2: Analysis → Proposal
**When to use:** Decision-making that needs structured thinking.

```
/plan → gather context → generate options → recommend → assess risk
```

Key principles:
- Always generate 2+ options (never present one path as inevitable)
- Every milestone needs a "done" definition
- Include resource requirements (time, cost, skills)

## Pattern 3: Critical Thinking (Devil's Advocate)
**When to use:** Before committing to a major decision.

```
/devils-advocate → extract assumptions → build failure scenarios → counter-argue
```

Key principles:
- **Hard rule: never agree.** Not even "this is solid, but..."
- Criticisms must be specific and actionable
- End with the single most dangerous assumption

## Pattern 4: Self-Audit
**When to use:** Security reviews, compliance checks, quality gates.

```
/security-check → scan secrets → audit permissions → review config → report
```

Key principles:
- **Never auto-fix.** Report only. The human decides.
- **Never output secrets.** Mask values in reports.
- Phase numbers provide progress visibility

## Pattern 5: Self-Improvement
**When to use:** After completing a project phase, to improve the system itself.

```
/review → analyze past outputs → identify knowledge gaps → propose skill updates
```

Key principles:
- Base analysis on actual outputs, not hypotheticals
- Proposals must be specific diffs, not vague suggestions
- Never delete knowledge — add, refine, or restructure

## Pattern 6: CRUD Subcommand
**When to use:** Managing a list (tasks, contacts, inventory).

```
/tasks          → list all
/tasks add      → create new
/tasks update 3 → modify item
/tasks overdue  → filtered view
```

Key principles:
- No arguments = default view (usually list all)
- Subcommands mirror CRUD: add, update, complete, delete
- Include filtered views for common queries

## Universal Design Rules

1. **$ARGUMENTS are always optional.** Define default behavior when omitted.
2. **Declare deliverables upfront.** Numbered list of expected outputs.
3. **Phase-based execution.** Show progress: `[Phase 2/4] Analyzing...`
4. **Output format specification.** Exact markdown template at the end.
5. **Constraints before instructions.** Rules about what NOT to do come first.
