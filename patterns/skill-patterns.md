# Skill File Design Patterns

## Structure

```yaml
---
name: Skill Name
description: Purpose + who references it + who does NOT
version: 1.0.0
---
```

The frontmatter is critical — it tells the system when to load this skill and when NOT to.

## The Anti-Reference Pattern

Most developers only write "this is used by X." But equally important:

```yaml
description: >
  Referenced by: /seo-intel, /seo-audit, /seo-plan.
  NOT used for: article writing, social media posts, internal docs.
```

Why? Without negative scope, a skill gets loaded in wrong contexts, polluting outputs with irrelevant constraints.

## Knowledge Structuring Patterns

### Pattern 1: Decision Table
Best for: rules, criteria, guidelines

```markdown
| Condition | Action | Reason |
|-----------|--------|--------|
| If X > 100 | Do A | Because... |
| If X < 50 | Do B | Because... |
```

### Pattern 2: Taxonomy
Best for: categories, classifications

```markdown
## 1. Category A
### 1-1. Subcategory
### 1-2. Subcategory
## 2. Category B
```

### Pattern 3: Temporal Context
Best for: knowledge that expires or evolves

```markdown
| Guideline | Valid Since | Context |
|-----------|-----------|---------|
| Use X approach | 2025-03 | After algorithm update |
| Avoid Y | 2024-12 | Deprecated in v3 |
```

### Pattern 4: Comparison Matrix
Best for: tool selection, strategy comparison

```markdown
| Criteria | Option A | Option B | Option C |
|----------|----------|----------|----------|
| Cost | Low | Medium | High |
| Speed | Fast | Medium | Slow |
| Quality | Medium | High | High |
```

## Versioning Strategy

Use semantic versioning:
- **Major** (2.0.0): Fundamental restructure or paradigm shift
- **Minor** (1.1.0): New knowledge added
- **Patch** (1.0.1): Corrections or clarifications

## Key Principles

1. **Table format over prose.** LLMs parse tables more reliably than paragraphs.

2. **Time-stamp volatile knowledge.** "As of 2025-12" lets the system know when to question the information.

3. **Negative scoping prevents misuse.** "NOT for X" is as important as "FOR Y."

4. **One skill, one topic.** Don't combine SEO knowledge with brand guidelines. Separate files enable selective loading.

5. **Update log at the bottom.** Makes it easy to see what changed and when.
