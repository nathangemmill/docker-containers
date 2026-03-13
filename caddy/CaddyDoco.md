# Maintenance

### Update Caddy

```bash
# Pull latest Caddy base image
docker compose pull caddy

## Quick Reference Commands

```bash
# Validate Caddyfile
docker exec -it caddy caddy validate --config /etc/caddy/Caddyfile

# Format Caddyfile
docker exec -it caddy caddy fmt --overwrite --config /etc/caddy/Caddyfile

# Reload Caddy config
docker exec -it caddy caddy reload --config /etc/caddy/Caddyfile

# Rebuild after module changes
docker compose up -d --build
