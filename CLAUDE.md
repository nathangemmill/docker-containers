# CLAUDE.md

## README Maintenance
Always update `README.md` when adding or removing containers (i.e. when compose files are created or deleted).

## Deployment Hosts
Two hosts are managed by this repo:

- **dockerbox** — primary host. Deploys all `docker-compose.yaml` files automatically via the `dockerbox` workflow.
- **docker3** — secondary host. Only deploys services with a `docker-compose.docker3.yaml` file (currently: `unifi`, `docker-volume-backup`, `beszel`).

## Naming Convention
- `docker-compose.yaml` → deploys to **dockerbox**
- `docker-compose.docker3.yaml` → deploys to **docker3**

## Labels
All containers must include the label `managed-by=pipeline`. The deployment workflows remove any running containers that lack this label.

## Secrets
Secrets are injected at deploy time via GitHub Actions secrets as environment variables. Add new secrets to the relevant workflow `env:` block.
