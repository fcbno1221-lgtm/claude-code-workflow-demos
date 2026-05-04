# /security-check — Security Audit

## Usage
```
/security-check $SCOPE
```
- `$SCOPE`: Area to audit (e.g., "env", "api-keys", "permissions", "all")
- If omitted: run full audit

## What This Command Does
Audit the project for security issues: exposed secrets, dangerous permissions, insecure configurations.

### Deliverables
1. Findings table (severity, location, description)
2. Recommended fixes
3. Settings.json improvement suggestions

## Important Rules
- **NEVER auto-fix** anything — report only
- **NEVER output** actual secret values, tokens, or keys in the report
- **NEVER modify** .env files or settings
- Show masked values only (e.g., `sk-...XXXX`)

## Execution Flow

### Phase 1: Secret Scan
Show: `[Phase 1/4] Scanning for exposed secrets...`
- Search for API keys, tokens, passwords in tracked files
- Check .gitignore covers .env, credentials, key files
- Verify no secrets in git history

### Phase 2: Permission Audit
Show: `[Phase 2/4] Auditing permissions...`
- Review settings.json deny list completeness
- Check for overly broad allow patterns
- Verify destructive operations are blocked

### Phase 3: Configuration Review
Show: `[Phase 3/4] Reviewing configurations...`
- Check file permissions (no 777)
- Review dependency security (known vulnerabilities)
- Verify HTTPS usage for external calls

### Phase 4: Report
Show: `[Phase 4/4] Generating report...`

Output format:
```markdown
# Security Audit — YYYY-MM-DD

## Findings
| # | Severity | Location | Issue | Status |
|---|----------|----------|-------|--------|
| 1 | HIGH | path/file | Description | OPEN |

## Recommended Fixes
1. Fix — reason — priority

## Settings.json Suggestions
- Add to deny: ...
- Add to allow: ...

## Score: X/10
```
