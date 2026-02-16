# Cursor-Centric OAIS Framework

A reusable **Operating AI System** pattern for AI-assisted product development in Cursor. **Use it for your own project or product:** clone or download this repo, copy the contents into your repo, and customize as needed (see [INSTALL.md](./INSTALL.md)).

This framework keeps the product repo as the source of truth, with its own context and documentation structure.

Use it as a different operating model from “canonical site” OAIS stacks: product-first, with the OAIS embedded in the same repo as the app.

---

## How this framework differs

- **Cursor-centric** — Built around Cursor IDE: `.cursor/rules`, slash commands, and agents. The product repo is the single source of truth; no separate canonical OAIS site.
- **Own context and docs** — Internal runbooks live in `project-documentation/` with a dedicated `INDEX.md` for agent navigation. You own the structure.
- **Adopt and adapt** — Copy into any repo and customize AGENTS.md, rules, and docs for your stack and product.

---

## What’s in this package

| Path | Purpose |
|------|--------|
| `AGENTS.md` | Agent entrypoint: non-negotiables, where to look first, completion contract, optional issue-tracker workflow |
| `.cursor/rules/` | Always-applied and task-scoped rules (foundation, security, handoff/docs). Add more for your stack (backend, DB, frontend). |
| `.cursor/commands/` | Slash commands (project planning, issues, docs, security, etc.). Replace or extend for your tooling. |
| `.cursor/agents/` | Agent role definitions. Customize for your workflow. |
| `project-documentation/` | Runbook index and structure: `INDEX.md` plus core/features/ops/testing as needed. |

---

## How this framework is used

- **Entrypoint** — Agents (and humans) start at `AGENTS.md` for non-negotiables, where to look first, and the completion contract.
- **Rules** — Cursor applies `.cursor/rules/` automatically (always-applied and glob-scoped). They enforce security, handoff format, and stack conventions.
- **Commands** — Slash commands (e.g. `/linear`, `/project-breakdown`, `/docs-update`) support issue tracking, planning, and docs. Use as-is or adapt for your tooling.
- **Agents** — Role definitions in `.cursor/agents/` describe planner, implementer, QA, security, docs, and DB-migration roles. Invoke when doing focused work.
- **Runbooks** — `project-documentation/INDEX.md` is the canonical map; agents open the doc that matches the task (core, features, ops, testing).

Every task ends with the **completion contract**: what changed, files touched, how to test, docs updated, risks/rollout.

---

## Quick start

See **[INSTALL.md](./INSTALL.md)** for how to install this OAIS into your project and what to customize.
