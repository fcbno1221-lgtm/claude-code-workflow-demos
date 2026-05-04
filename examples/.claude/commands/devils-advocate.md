# /devils-advocate — Contrarian Analysis

## Usage
```
/devils-advocate $PROPOSAL
```
- `$PROPOSAL`: The idea, plan, or decision to challenge
- If omitted: challenge the most recent plan or decision in context

## What This Command Does
Force a rigorous contrarian analysis. No agreement, no praise, no "that said, it's still a good idea." Pure critical examination.

### Deliverables
1. Three failure scenarios (specific, not generic)
2. Hidden assumptions that could be wrong
3. Opportunity cost analysis
4. The strongest counter-argument

## Important Rules
- **NEVER agree** with the proposal, even partially
- **NEVER** use phrases like "while this has merit" or "this is a solid plan, but"
- Every criticism must be specific and actionable, not vague
- End with the single most dangerous assumption

## Execution Flow

### Phase 1: Assumption Extraction
Show: `[Phase 1/3] Extracting assumptions...`
- List every implicit assumption in the proposal
- For each: what happens if this assumption is wrong?

### Phase 2: Failure Scenarios
Show: `[Phase 2/3] Constructing failure scenarios...`
- Scenario 1: What's the most likely way this fails?
- Scenario 2: What's the most catastrophic way this fails?
- Scenario 3: What's the subtle, slow-burn failure mode?

### Phase 3: Counter-Argument
Show: `[Phase 3/3] Building counter-argument...`
- What would a smart, well-informed opponent say?
- What's the opportunity cost of pursuing this?
- What alternative would the opponent propose instead?

Output format:
```markdown
# Devil's Advocate: $PROPOSAL

## Hidden Assumptions
1. Assumption — what breaks if wrong

## Failure Scenarios
### 1. Most Likely Failure
### 2. Worst Case
### 3. Slow Burn

## Opportunity Cost
What you're NOT doing by pursuing this.

## Strongest Counter-Argument
...

## Most Dangerous Assumption
The single assumption that, if wrong, invalidates the entire plan.
```
