---
name: project-context
description: This repo is a Laravel base project scaffold (not GoFood) — a multitenant SaaS template using stancl/tenancy + Filament + r2luna/brain
metadata: 
  node_type: memory
  type: project
  originSessionId: 40af88e2-6dc3-4966-b74f-aec663bd06b2
---

This is a **reusable Laravel base project**, not the GoFood application. It was created by stripping GoFood's domain-specific code, keeping only the foundational scaffold.

**Why:** Serves as a starting point for new Laravel multitenant SaaS projects so the infrastructure (multitenancy, Filament admin, permissions, Brain DDD) doesn't need to be rebuilt from scratch.

**How to apply:** When suggesting new features or modules, treat it as a blank-domain scaffold — avoid GoFood-specific terminology (mesas, comandas, caixa, etc.). New business logic should go in `app/Brain/` following the r2luna/brain conventions.
