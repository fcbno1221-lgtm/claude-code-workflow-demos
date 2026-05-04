# Security Patterns for Claude Code

## The Two-File Strategy

```
.claude/settings.json       → Committed to git (shared security rules)
.claude/settings.local.json → Git-ignored (personal accumulated permissions)
```

**Why two files?**
- `settings.json` defines the security baseline everyone on the team agrees to
- `settings.local.json` grows organically as you approve commands during daily use
- Separation prevents one person's broad permissions from affecting everyone

## Deny List: The Non-Negotiables

```json
{
  "deny": [
    "Bash(rm -rf *)",           // Recursive delete
    "Bash(git push --force*)",  // Force push (destroys remote history)
    "Bash(git reset --hard*)",  // Hard reset (destroys local changes)
    "Bash(chmod 777 *)",        // World-writable permissions
    "Bash(git push*--no-verify*)", // Skip pre-push hooks
    "Bash(sed*-i*.env*)",       // In-place edit of .env
    "Bash(*> .env*)",           // Overwrite .env
    "Bash(*>> .env*)"           // Append to .env
  ]
}
```

### Why These Specific Rules?

| Rule | Threat | Real-World Scenario |
|------|--------|-------------------|
| `rm -rf *` | Data loss | Claude misinterprets "clean up" as "delete everything" |
| `git push --force` | Team disruption | Rewrites shared history, breaks colleagues' branches |
| `git reset --hard` | Work loss | Discards uncommitted changes permanently |
| `chmod 777` | Security hole | Makes files world-readable/writable on shared servers |
| `--no-verify` | Policy bypass | Skips linting, testing, secret scanning hooks |
| `.env` writes | Secret exposure | Could overwrite tokens or expose them in git history |

## Allow List: Minimum Viable Permissions

Start with read-only git commands only:

```json
{
  "allow": [
    "Bash(git status*)",
    "Bash(git log*)",
    "Bash(git diff*)"
  ]
}
```

Then add incrementally as needed:
- External API calls → through wrapper scripts only
- File operations → specific paths, not wildcards
- Build tools → explicit commands (`npm run build`, not `npm *`)

## The Wrapper Script Pattern

Instead of allowing direct API calls:

```json
// BAD: Allows Claude to use any token
"allow": ["Bash(curl -H 'Authorization: Bearer *'*)"]

// GOOD: Token stays inside the script
"allow": ["Bash(bash scripts/api-wrapper.sh *)"]
```

The wrapper script:
1. Reads tokens from `.env` internally
2. Validates the requested action
3. Logs the call
4. Never exposes the raw token to Claude's context

## Defense in Depth: Three Layers

```
Layer 1: settings.json (deny list)
  → Blocks dangerous commands before execution

Layer 2: Command-level rules
  → "/security-check: NEVER auto-fix, NEVER output secrets"

Layer 3: CLAUDE.md rules
  → "Never present a single option as inevitable"
  → "Never say 'no issues found' without evidence"
```

Each layer catches what the others miss.

## .gitignore for Security

```gitignore
# Always ignore
.env
.env.*
*.pem
*.key
credentials.json
.claude/settings.local.json
```

## Audit Checklist

Run `/security-check` monthly. Verify:
- [ ] No secrets in git history (`git log -p | grep -i "api_key\|token\|secret"`)
- [ ] .gitignore covers all sensitive files
- [ ] settings.json deny list is up to date
- [ ] No overly broad patterns in allow list
- [ ] Wrapper scripts don't log tokens
