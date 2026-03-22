# Maintenance

### Host Permissions (required on new/migrated hosts)

Caddy runs as UID 1000 (rootless). The bind-mounted volumes must be owned by that user before starting the container, otherwise Caddy will fail to write TLS certificates and config.

```bash
sudo chown -R 1000:1000 /opt/backed-up-volumes/caddy
```

Run this after provisioning a new host or restoring from backup, before deploying the stack.

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
