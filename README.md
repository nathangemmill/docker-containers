# Docker Compose Home Lab

This repository is a collection of Docker Compose files for managing and deploying various self-hosted services in my home lab environment. Each subdirectory contains a `docker-compose.yaml` (or `docker-compose.yml`) file for a specific service or stack.

## Purpose
- **Centralized Management:** Track and version control all Docker Compose configurations in one place.
- **Automation:** Intended for use with GitHub Actions to automate deployment and updates of containers in the home lab.
- **Documentation:** Serve as a reference for service configurations and deployment practices.

## Structure
Each folder represents a different service or stack. For example:

- `audiobookshelf/` — Audiobook server
- `beszel/` — Container/performance monitoring
- `caddy/` — Caddy web server and reverse proxy with authelia added authentication provider
- `cloudflared/` — Cloudflare Tunnels
- `docker-volume-backup/` — Automated Docker volume backups
- `invio/` — Invoicing platform
- `it-tools/` — IT Tools web suite
- `mealie/` — Mealie recipe manager
- `papra/` — Papra document management
- `pihole/` — Pi-hole network-wide ad blocker and DNS provider for tailscale clients
- `plex/` — Plex media server
- `qbittorrent/` — qBittorrent client
- `tailscale/` — Tailscale VPN
- `uptime-kuma/` — Uptime Kuma monitoring
- `vaultwarden/` — Vaultwarden password manager
- `unifi/` — Unifi network controller *(docker3 only)*
- `watchtower/` — Watchtower for automatic container updates

## Usage
1. **Clone the repository:**
   ```sh
   git clone https://github.com/yourusername/docker-containers.git
   cd docker-containers
   ```
2. **Navigate to a service directory:**
   ```sh
   cd plex
   ```
3. **Deploy the stack:**
   ```sh
   docker compose up -d
   ```

## Automation
Two GitHub Actions workflows handle deployment:

- **dockerbox** — runs on the `dockerbox` host. Deploys every service that has a `docker-compose.yaml` on every push to `main`.
- **docker3** — runs on the `docker3` host. Deploys only services with a `docker-compose.docker3.yaml` file (currently `unifi`, `watchtower`, `docker-volume-backup`), triggered on changes to those paths.

Both workflows remove any running containers that are not labelled `managed-by=pipeline`, keeping each host clean.

## Contributing
- Update or add new service folders as needed.
- Ensure each service has a valid `docker-compose.yaml` (or `.yml`) file.
- Update this README with new services or changes.

## License
This repository is for personal use in a home lab environment. See individual service licenses for more information.
