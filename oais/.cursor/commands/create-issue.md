Create a Linear issue **quickly** (capture mode) using the connected Linear integration, and return the Linear key plus a concise “Agent Brief”.

## Inputs (keep it fast)
Ask for **at most 2 things** total:
1) **Title** (short)
2) **Context** (1–3 bullets) — optional if the title is self-explanatory

If anything else is missing, **assume sensible defaults** and mark it as “needs refinement”.

## Linear behavior
- Create issue in the project the user specifies (or team backlog by default). Find by name; note if unavailable.
- Add a label like `ai-created` (or closest existing label).
- Add a label like `needs-refinement` if it exists (optional/best-effort).
- If the user provided a Linear key already, **do not create a new issue**—default to adding the capture template as a **comment** (do not overwrite their description unless they ask).

## Issue body template (Capture)
Paste the following structure into Linear:

### Summary
<1-2 sentences>

### Context
- <why now / what triggered>

### Goals (draft)
- [ ] <goal (draft)>

### Acceptance criteria (draft)
- [ ] <observable outcome (draft)>

### Notes (for later refinement)
- **Open questions**:
  - <max 3>
- **Constraints**:
  - Security/privacy: <placeholder>
  - CSP: no inline scripts/styles
  - Performance: <placeholder>
  - UX/design: follow brand + frontend guidelines
- **Follow-up**: run `/linear-refine TEAMKEY-123` when you have time.

### Security & privacy
- No PII in the issue body.
- No secrets/tokens/keys.

### Test plan
- [ ] TBD (fill during implementation)

### Links
- Repo: (this repo)
- Docs: `project-documentation/INDEX.md` (and any relevant doc links)

## Output (in chat)
Return:
1) **Linear**: `TEAMKEY-123` + link (if available)\n
2) **Agent Brief** (token-light): title, what you meant, draft AC, and suggested next step (`/linear-refine`)\n
