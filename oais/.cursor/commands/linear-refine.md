Refine a Linear issue (e.g. `ANG-9`) into a high-signal, implementation-ready spec, then update the Linear issue description.

## Inputs
- Linear issue key (required): `TEAMKEY-123`
- Mode (optional): `overwrite` | `prepend` (default) | `comment-only`

## Steps
1) Fetch the Linear issue by key (title, description, status, project, labels, priority, and key comments/decisions).
2) Produce a refined spec with the template below.
3) Update Linear:
   - Default (`prepend`): prepend the refined spec to the top of the issue description and preserve the original description under an “Original description” section.
   - `overwrite`: replace the description entirely (only if the user explicitly asks).
   - `comment-only`: leave description unchanged; add the refined spec as a comment.

## Refined spec template (paste into Linear)
### Summary
<1-2 sentences>

### Goal
<what success means>

### Context
- <why now / what triggered>

### Acceptance criteria
- [ ] <observable outcome>

### Constraints
- **Security/privacy**: …
- **CSP**: …
- **Performance**: …
- **UX/design**: …

### Execution notes
- **Suggested approach**: …
- **Docs to consult**:
  - `AGENTS.md`
  - `project-documentation/INDEX.md`
  - <other relevant docs>
- **Tests to run**:
  - …
- **Open questions (max 3)**:
  - …

### Original description (preserved)
<paste or keep below>

## Output (in chat)
Return:
- The refined spec
- What was updated in Linear (description/comment) and a link to the issue

