# multi-stage build: use xcaddy to produce a Caddy binary with the cloudflare DNS provider
FROM caddy:2-builder AS builder

# Build Caddy with the Cloudflare DNS provider
RUN xcaddy build \
--with github.com/caddy-dns/cloudflare

# Final image: copy the built binary into the official runtime image
FROM caddy:2
COPY --from=builder /usr/bin/caddy /usr/bin/caddy

# Grant the binary permission to bind to ports < 1024 without running as root
RUN apk add --no-cache libcap && \
    setcap cap_net_bind_service=+ep /usr/bin/caddy && \
    apk del libcap

USER caddy
