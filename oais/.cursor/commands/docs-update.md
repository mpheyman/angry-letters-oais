Update documentation after development. Apply targeted edits only; keep it concise and safe.

## Inputs (use what’s available)
- Linear key (optional): `TEAMKEY-123`
- PR/commit summary (optional)
- Files changed (if known)

## Rules
- Update docs when behavior/workflows/endpoints/testing steps change.
- Prefer updating **canonical internal docs** under `project-documentation/**` and keep `README.md` / `TESTING_*` accurate.
- Never include real secrets or tokens in docs. Use placeholders like `YOUR_*_HERE`.
- Never include PII.
- Make the **actual doc edits** when you have enough information. If you do not, output a short checklist of the exact edits needed and what information is missing.

## What to update (common targets)
- `project-documentation/core/development-standards.md` (runbooks, architecture conventions)
- `project-documentation/core/frontend-guidelines.md` (UI conventions, CSP-safe patterns)
- `project-documentation/core/configuration.md` (env var *names* only)
- `project-documentation/testing/testing.md` and `TESTING_CHECKLIST.md` (new smoke steps / commands)
- `TESTING_SECURITY.md` (prompt injection/security testing changes)

## Output format
### DocsImpact
- **Docs updated**:
  - <file>: <what changed>
- **Docs not updated** (and why):
  - <file>: <reason>

### NotesForReview
- <any places the human should double-check>

