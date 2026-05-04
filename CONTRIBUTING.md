# Adding New Patterns

## When to Add

After completing work in the main toramonten system, extract any new pattern that is:
- Generic (not business-specific)
- Reusable (applicable to other small teams)
- Novel (not already covered in existing patterns)

## How to Add

### New Command Pattern
1. Create the command in `examples/.claude/commands/`
2. Add the pattern to `patterns/command-patterns.md`
3. Update README.md if it introduces a new pattern category

### New Agent Pattern
1. Create the agent in `examples/.claude/agents/{dept}/`
2. If it demonstrates a new collaboration pattern, add to `patterns/agent-patterns.md`

### New Skill Pattern
1. Create the skill in `examples/.claude/skills/`
2. If it demonstrates a new knowledge structuring approach, add to `patterns/skill-patterns.md`

## Sanitization Checklist

Before committing, verify the file contains NONE of:
- [ ] Company names, client names, or personal names
- [ ] URLs to internal systems or private APIs
- [ ] API keys, tokens, or secrets (even masked ones from real systems)
- [ ] Specific revenue figures, pricing, or financial data
- [ ] Product names or brand-specific terminology
- [ ] Internal process details that reveal competitive advantage

## Commit Convention

```
feat: add [pattern-name] pattern
docs: update [section] documentation
fix: correct [issue] in [file]
```
