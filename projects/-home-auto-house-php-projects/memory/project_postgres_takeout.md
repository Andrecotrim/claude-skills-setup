---
name: PostgreSQL via Takeout
description: PostgreSQL is managed by Takeout (Docker), not installed natively on the system
type: project
---

PostgreSQL runs via Docker managed by Takeout, container `TO--postgresql--18.3--5432`, port 5432.

Data is stored at `/var/lib/docker/volumes/postgres_data/_data` on the host.

Recovered 6 databases from old system (found at `_data/18/docker/` inside a Docker volume backup):
- `agendadobarbeiro_db`
- `primoratec_db`
- `solar-core_db`
- `solar_core_db_v2`
- `solar_core_db_v3`
- `solar_energy`

Backup copy of old data kept at `/home/auto-house/php-documents/primoratec-ao3-finance/_data`.

**Why:** User migrated from a previous Ubuntu system that broke; databases were inside a Takeout Docker volume, not in `/var/lib/postgresql`.
**How to apply:** When helping with database tasks, connect via the Takeout container. Never assume a native PostgreSQL install exists.
