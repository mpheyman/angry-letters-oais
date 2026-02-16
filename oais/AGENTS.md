# AGENTS.md

This file is the **entrypoint for AI agents** working in this repo. Keep it concise and stable. Prefer linking to canonical docs over duplicating them.

## Non-negotiables (always)

- **Security/privacy first**: never add or paste real secrets anywhere (code, docs, tests). Use placeholders like `YOUR_*_HERE`.
- **No PII leakage**: never paste customer data, addresses, emails, payment IDs, or private conversations into docs/issues/PRs.
- **No remote pushes without permission**: do not push to the main remote unless the user explicitly asks.

Add project-specific non-negotiables here (e.g. CSP, Docker-first, Postgres-first, brand/UX).

## Where to look first (docs)

- **Repo overview**: `README.md`
- **Internal docs index (canonical map)**: `project-documentation/INDEX.md`
  - Foundation: `project-documentation/core/*`
  - Testing: `project-documentation/testing/*`

## Issue-tracker workflow (optional)

If you use Linear (or similar), reference work by issue key (e.g. `TEAMKEY-123`). When given a key, fetch/summarize only high-signal fields. Add slash commands for project planning, issue refinement, and status reports as needed.

## Completion contract (required on every task)

End every task with a short block:

- **What changed / why**
- **Files touched**
- **How to test** (smallest relevant commands)
- **Docs updated** (or why not)
- **Risks / rollout notes** (if relevant)

## Context budget (cost + focus)

- Prefer **links + file citations** over copying long code or logs.
- Use narrow scope: only open/read the docs relevant to the task.
- Use subagents for noisy work and bring back summaries.
