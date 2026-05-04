# /monday — Weekly Kickoff Briefing

## Usage
```
/monday $FOCUS_AREA
```
- `$FOCUS_AREA`: Optional department or topic to emphasize (e.g., "marketing", "operations")
- If omitted: generate a full cross-department briefing

## What This Command Does
Generate a structured weekly briefing that reviews last week's progress, identifies this week's priorities, and flags risks — all in one consolidated report.

### Deliverables
1. Last week's progress summary (by department)
2. This week's priority actions (max 5)
3. Risk/blocker alerts
4. Key metrics snapshot

## Important Rules
- Keep the entire briefing under 500 words
- Priorities must be specific and time-bound (not "improve marketing")
- Flag any task that has been carried over for 2+ weeks

## Execution Flow

### Phase 1: Review
Show: `[Phase 1/3] Reviewing last week...`
- Read recent git history, task files, and project notes
- Summarize completed work by department

### Phase 2: Prioritize
Show: `[Phase 2/3] Setting priorities...`
- Identify incomplete tasks and new requirements
- Rank by impact × urgency
- Select top 5 priorities

### Phase 3: Output
Show: `[Phase 3/3] Generating briefing...`

Output format:
```markdown
# Weekly Briefing — YYYY-MM-DD

## Last Week
- [Dept] Achievement (metric if available)

## This Week's Priorities
1. Priority — owner — deadline
2. ...

## Risks & Blockers
- Risk description — mitigation

## Metrics
| Metric | Last Week | This Week | Trend |
```
