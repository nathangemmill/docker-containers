# multi-stage build: use xcaddy to produce a Caddy binary with the cloudflare DNS provider
FROM caddy:2-builder AS builder

# Build Caddy with the Cloudflare DNS provider
RUN xcaddy build \
--with github.com/caddy-dns/cloudflare

# Final image: copy the built binary into the official runtime image
FROM caddy:2
COPY --from=builder /usr/bin/caddy /usr/bin/caddy

# Grant the binary permission to bind to ports < 1024 without running as root
RUN apt-get update && apt-get install -y libcap2-bin && \
    setcap cap_net_bind_service=+ep /usr/bin/caddy && \
    apt-get remove -y libcap2-bin && apt-get autoremove -y && rm -rf /var/lib/apt/lists/*

USER caddy
