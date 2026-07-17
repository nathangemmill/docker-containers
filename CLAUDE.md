# CLAUDE.md

## README Maintenance
Always update `README.md` when adding or removing containers (i.e. when compose files are created or deleted).

## Deployment Hosts
Dockerbox is the sole host managed by this repo. Deploys all `docker-compose.yaml` files automatically via the `dockerbox` workflow.

## Naming Convention
- `docker-compose.yaml` → deploys to **dockerbox**

## Labels
All containers must include the label `managed-by=pipeline`. The deployment workflow removes any running containers that lack this label.

## Secrets
Secrets are injected at deploy time via GitHub Actions secrets as environment variables. Add new secrets to the relevant workflow `env:` block.
