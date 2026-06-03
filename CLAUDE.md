# memphis-k8s

## COLD-START RITUAL (read on the first message of every session)

1. Read this entire file.
2. Read `memory-bank/activeContext.md` for the live state — what the last session did, where things stand, what open questions are blocking, what's next.
3. If working on a deliverable, also read `memory-bank/lessons.md` for any repo-specific dos/don'ts.
4. If `memory-bank/activeContext.md` and this file conflict, trust `activeContext.md` for state and trust this file for rules / standing instructions.
5. At session end, run `/wrap-session` to refresh `memory-bank/activeContext.md` and audit in-flow captures.

## What this is

This is a mirror of the official **Memphis.dev Kubernetes deployment repo** (`memphisdev/memphis-k8s`), forked into Jarred's `Winnsolutionsadmin` GitHub org. It packages Memphis — a cloud-native, cloud-agnostic message broker (a next-generation alternative to traditional brokers, a CNCF Silver member project) — as a **Helm chart** for one-command deployment to any Kubernetes cluster on any cloud.

The repo's substance lives in the `memphis/` Helm chart (Chart `v0.4.5`, appVersion `0.4.5`): templates for the broker StatefulSet, REST gateway, metadata store (Bitnami `metadata`/Postgres dependency v15.2.0), RBAC, services, PDB, ServiceMonitor, and credentials. `charts/` holds packaged `.tgz` releases (0.2.0 → 0.4.5) plus the Helm repo `index.yaml`, and the repo is served as a Helm/chart registry via GitHub Pages (`CNAME = k8s.memphis.dev`, Jekyll minimal theme). A `Jenkinsfile` and `.github/workflows/` cover CI.

**Type:** infra (third-party Helm chart / deployment tooling). **Status:** upstream looks-archived from Jarred's perspective — latest commit is `eecf250 Update values.yaml` (Apr 2023); this is a reference/mirror, not active in-house development. Treat upstream files as read-only reference; do not "fix" the chart as if it were a Winn.solutions-authored artifact.

## Memory

State and accumulated context live in `memory-bank/`:
- `memory-bank/activeContext.md` — where the last session left off (read first)
- `memory-bank/projectbrief.md` — what this repo is and why it's here
- `memory-bank/lessons.md` — repo-specific dos/don'ts
- `memory-bank/progress.md` — what works / what's broken / what's queued
- `memory-bank/decisions/` — ADRs

Behavior rules (how to act, response style, honesty protocol) come from the macro global fileset, not from this file. This file holds repo-local context only.
