# /review — Self-Improvement Review

## Usage
```
/review $TARGET
```
- `$TARGET`: Specific skill file, agent, or command to review (e.g., "skills/brand-guide.md")
- If omitted: review the 3 most recently used skill files

## What This Command Does
Analyze past outputs and interactions to identify gaps in the knowledge base, then generate concrete improvement proposals for skill files.

### Deliverables
1. Quality assessment of recent outputs
2. Knowledge gaps identified
3. Specific update proposals for skill files (with diffs)

## Important Rules
- Base analysis on actual outputs, not hypothetical scenarios
- Proposals must be specific: "Add row X to table Y in skill Z", not "improve the skill"
- Never delete existing knowledge — only add, refine, or restructure

## Execution Flow

### Phase 1: Output Analysis
Show: `[Phase 1/3] Analyzing recent outputs...`
- Read recent conversation outputs and generated files
- Identify patterns: what worked well, what was weak
- Note any corrections or re-dos requested by user

### Phase 2: Gap Analysis
Show: `[Phase 2/3] Identifying knowledge gaps...`
- Compare outputs against referenced skill files
- Where did the agent lack knowledge?
- Where was knowledge present but poorly structured?

### Phase 3: Improvement Proposals
Show: `[Phase 3/3] Generating improvement proposals...`

Output format:
```markdown
# Review Report — YYYY-MM-DD

## Output Quality
| Output | Quality | Issue |
|--------|---------|-------|

## Knowledge Gaps
1. Gap — which skill — impact

## Proposals
### Proposal 1: Update skills/X.md
**Reason:** ...
**Change:**
\```diff
- old content
+ new content
\```

### Proposal 2: ...
```
