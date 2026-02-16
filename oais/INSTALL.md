# Installing this OAIS

Use this framework in any repo to get a Cursor-centric operating model: agent entrypoint, rules, commands, and runbook structure.

---

## 1. Get the package

- **Download ZIP** from this repo, or clone it.
- You need: `AGENTS.md`, `.cursor/` (rules, commands, agents), and `project-documentation/` (at least `INDEX.md`).

---

## 2. Copy into your project

Copy (or merge) these into your **project root**:

- `AGENTS.md`
- `.cursor/` (entire directory)
- `project-documentation/` (entire directory, or merge with existing docs)

---

## 3. Customize for your project

**AGENTS.md**

- Set “where to look first” to your `README.md` and `project-documentation/INDEX.md`.
- Adjust non-negotiables (e.g. Docker, Postgres, CSP) to match your stack.
- Add or remove issue-tracker commands (e.g. Linear) if you use something else.

**`.cursor/rules/00-foundation.mdc`**

- Point to your README and doc index.
- Replace placeholder “project non-negotiables” with your own (security, CSP, storage, brand/UX, etc.).

**`project-documentation/`**

- Edit `INDEX.md` to list your core, feature, ops, and testing docs.
- Add or remove runbooks so the index reflects your product and workflows.

**Commands and agents**

- Keep, remove, or add slash commands and agent definitions to match your process and tools.

---

## 4. What to keep

These patterns work across projects:

- **Completion contract** — End tasks with: what changed, files touched, how to test, docs updated, risks/rollout.
- **Security rule** — No secrets in repo; no PII in code/docs/issues; prompt injection safeguards if using AI.
- **Permission gates** — No pushing to main without explicit request; test plan + rollback notes for sensitive changes.

Adapt the rest (Docker, Postgres, CSP, brand) to your stack.

---

## Requirements

- **Cursor** (or an editor that respects `.cursor/rules` and slash commands).
- **Issue tracker** (optional) — Commands reference Linear; swap or remove if you use another system.
