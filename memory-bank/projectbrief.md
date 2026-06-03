---
name: project brief — memphis-k8s
description: What this repo is, why it exists. Populated over time, not at scaffold.
type: infra
---

# memphis-k8s

**Type:** infra (third-party Helm chart / Kubernetes deployment tooling)
**Status:** looks-archived (mirror of upstream; latest commit Apr 2023; no in-house changes)
**Origin:** `https://github.com/Winnsolutionsadmin/memphis-k8s.git` (mirror of `memphisdev/memphis-k8s`)

## Purpose

Official Memphis.dev Kubernetes deployment repo, mirrored into Jarred's `Winnsolutionsadmin` GitHub org. It packages **Memphis** — a cloud-native, cloud-agnostic message broker positioned as a next-generation alternative to traditional brokers (CNCF Silver member) — as a **Helm chart** so it can be deployed to any Kubernetes cluster with a single command:

```bash
helm repo add memphis https://k8s.memphis.dev/charts/ --force-update && \
  helm install memphis memphis/memphis --create-namespace --namespace memphis --wait
```

## Key tech / layout

- **`memphis/`** — the Helm chart itself. `Chart.yaml` (apiVersion v2, version `0.4.5`, appVersion `0.4.5`), `values.yaml`, and `templates/`:
  - `memphis_statefulset.yaml` — the broker StatefulSet (largest template)
  - `memphis-rest-gateway.yaml` — REST gateway
  - `memphis_configmap.yaml`, `memphis_service.yaml`, `memphis_rbac.yaml`, `memphis_pdb.yaml`, `memphis_serviceMonitor.yaml`, `memphis-creds.yaml`, `memphis_helpers.tpl`, `NOTES.txt`
  - Dependency: Bitnami `metadata` (Postgres-family metadata store), version `15.2.0`, gated by `metadata.enabled`
- **`charts/`** — packaged chart releases (`memphis-0.2.0.tgz` … `memphis-0.4.5.tgz`) plus Helm repo `index.yaml` and `artifacthub-repo.yml`. This repo doubles as the Helm chart registry.
- **GitHub Pages serving:** `CNAME = k8s.memphis.dev`, `_config.yml` = Jekyll minimal theme. The Helm repo (`https://k8s.memphis.dev/charts/`) is served from this repo.
- **CI:** `Jenkinsfile` + `.github/workflows/`.
- **Deployment modes:** Dev (single broker) and Production (3-broker cluster mode, `global.cluster.enabled=true`), with optional TLS/SSL, Prometheus exporter, and configurable auth (user+pass or connection token).

## Context not obvious from files

<!--
Fill in when known:
- Why this is mirrored into Winnsolutionsadmin (reference for a deployment? eval of Memphis? archived clone?)
- Whether any in-house deployment depends on this, or if it's pure reference
- Note: Memphis.dev the company wound down / the project's upstream activity stalled around 2023 — treat as a frozen artifact unless told otherwise.
-->

## Out of scope

- Modifying the upstream chart as if it were a Winn.solutions-authored artifact. Treat chart files as read-only reference unless there is an explicit reason and a fork strategy.
