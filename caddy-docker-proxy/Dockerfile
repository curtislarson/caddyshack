ARG CADDY_VERSION=2.6.4

FROM caddy:${CADDY_VERSION}-builder AS builder

RUN xcaddy build \
  --with github.com/lucaslorentz/caddy-docker-proxy/plugin \
  --with github.com/caddy-dns/cloudflare \
  --with github.com/greenpau/caddy-security

FROM caddy:${CADDY_VERSION}-alpine

COPY --link --from=builder /usr/bin/caddy /usr/bin/caddy

CMD ["caddy", "docker-proxy"]