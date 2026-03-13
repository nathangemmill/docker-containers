# multi-stage build: use xcaddy to produce a Caddy binary with the cloudflare DNS provider
FROM caddy:2-builder AS builder

# Build Caddy with the Cloudflare DNS provider
RUN xcaddy build \
--with github.com/caddy-dns/cloudflare

# Final image: copy the built binary into the official runtime image
FROM caddy:2
COPY --from=builder /usr/bin/caddy /usr/bin/caddy

# keep same entrypoint/cmd as official image
