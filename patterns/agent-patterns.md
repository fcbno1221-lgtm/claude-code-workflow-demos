# Agent Design Patterns

## The 5-Section Structure

Every agent follows this exact structure:

```markdown
# Role Name
## Role          — one sentence
## Scope         — 5-7 bullet points
## Output Quality Standards — 4-5 specific rules
## Referenced Skills — file paths
## Collaborating Agents — names + relationship
```

## Quality Standards by Role Type

### Strategy / Advisory Agents
- "Every recommendation includes: premise, expected outcome, risk, required resources"
- "Provide optimistic / base / pessimistic scenarios"
- "If infeasible, provide scaled-down alternative"

### Data / Analysis Agents
- "Every data point: number → interpretation → action recommendation"
- "Cite source and time period"
- "Distinguish statistically significant from noise"

### Content / Creative Agents
- "Match brand voice guidelines from skill file"
- "Include SEO metadata (title, description, keywords)"
- "Provide 2-3 variants for A/B testing"

### Operations / Execution Agents
- "Include step-by-step runbook"
- "Define rollback procedure"
- "Estimate time and dependencies"

## Collaboration Patterns

### Hub-and-Spoke
One coordinator agent delegates to specialists:
```
strategy-advisor (hub)
  → data-analyst (data)
  → seo-specialist (visibility)
  → operations (execution)
```

### Pipeline
Agents process sequentially:
```
researcher → analyst → writer → reviewer
```

### Peer Review
Agents critique each other's output:
```
agent-A generates → agent-B critiques → agent-A revises
```

## Key Principles

1. **Role-specific quality gates.** Generic "be helpful" is useless. Each role needs concrete, measurable standards.

2. **Explicit skill references.** Agents don't guess — they read specific files. This prevents hallucination and ensures consistency.

3. **Collaboration is declared, not implicit.** "Provides data for strategic decisions" tells the system exactly how agents interact.

4. **Small-team constraint.** Every agent assumes limited resources. If it can't be done with the team you have, it must propose an alternative.

5. **No agent is an island.** Every agent connects to at least one other. Isolated agents become stale.
