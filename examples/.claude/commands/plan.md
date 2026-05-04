# /plan — Strategic Planning Workflow

## Usage
```
/plan $TOPIC
```
- `$TOPIC`: The initiative, problem, or decision to plan for
- If omitted: review current project state and suggest what needs planning

## What This Command Does
Analyze a topic from multiple angles and produce an actionable plan with risk assessment.

### Deliverables
1. Situation analysis (current state + constraints)
2. Options with pros/cons
3. Recommended plan with milestones
4. Risk matrix

## Important Rules
- Never present only one option
- Every milestone must have a concrete "done" definition
- Include resource requirements (time, cost, skills)
- Plans must be executable by a small team

## Execution Flow

### Phase 1: Situation Analysis
Show: `[Phase 1/4] Analyzing situation...`
- Read relevant project files and context
- Identify constraints (budget, time, team size)
- Invoke **strategy-advisor** agent for strategic framing

### Phase 2: Option Generation
Show: `[Phase 2/4] Generating options...`
- Generate 2-4 distinct approaches
- For each: effort, impact, risk, timeline

### Phase 3: Recommendation
Show: `[Phase 3/4] Formulating recommendation...`
- Select recommended option with rationale
- Break into milestones (max 5)
- Define success criteria for each milestone

### Phase 4: Risk Assessment
Show: `[Phase 4/4] Assessing risks...`
- Identify top 3 risks
- For each: probability (H/M/L), impact (H/M/L), mitigation

Output format:
```markdown
# Plan: $TOPIC

## Situation
...

## Options
### Option A: ...
### Option B: ...

## Recommendation: Option X
### Why
### Milestones
1. Milestone — done when — deadline

## Risks
| Risk | Probability | Impact | Mitigation |
```
