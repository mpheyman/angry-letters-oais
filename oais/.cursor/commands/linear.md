Fetch and summarize a Linear issue by key (e.g. `TEAMKEY-123`) using the connected Linear integration. Be token-efficient.

## Inputs
- Linear issue key: `TEAMKEY-123`

## Instructions
- Retrieve only high-signal fields: title, description, acceptance criteria, key comments/decisions, project, labels, priority.
- Do **not** paste long comment threads or raw API payloads. Summarize.
- Identify any missing info that blocks implementation; ask targeted questions (max 3).
- Link to relevant repo docs instead of copying them (e.g. `AGENTS.md`, `README.md`, `project-documentation/INDEX.md`).

## Output format
### IssueSummary
- **Key**: TEAMKEY-123
- **Title**: …
- **Goal**: …
- **AcceptanceCriteria**:
  - [ ] …
- **Constraints**:
  - Security/privacy:
  - CSP:
  - Performance:
  - UX/design:

### ExecutionNotes
- **Suggested approach**: …
- **Docs to consult**: …
- **Tests to run**: …

Tip: use `/linear-refine` to write this back into Linear as an implementation-ready spec.

