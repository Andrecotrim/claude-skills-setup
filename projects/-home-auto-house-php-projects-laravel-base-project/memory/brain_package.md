---
name: brain-package
description: "r2luna/brain v4.1 is installed — DDD package with Workflows, Actions, Queries under app/Brain/"
metadata: 
  node_type: memory
  type: project
  originSessionId: 40af88e2-6dc3-4966-b74f-aec663bd06b2
---

`r2luna/brain` v4.1.0 is installed. Organizes business logic into:

- **Workflow** — orchestrates Actions in a DB transaction (`MyWorkflow::run($payload)`)
- **Action** — single unit of work that mutates state (`MyAction::run($payload)`)
- **Query** — read-only, returns data (`MyQuery::run(named: $args)`)

Classes live in `app/Brain/`. `Process` and `Task` are deprecated aliases for Workflow and Action.

Key artisan commands: `brain:make:workflow`, `brain:make:action`, `brain:make:query`, `brain:show`, `brain:run`.

Config: `config/brain.php` (env vars: `BRAIN_ROOT`, `BRAIN_USE_DOMAINS`, `BRAIN_USE_SUFFIX`, `BRAIN_LOG_ENABLED`).

**Why:** Added as the standard DDD layer for this base project so new projects built from it start with clean business logic separation.

**How to apply:** New business logic should be implemented as Brain classes, not fat controllers or models.
