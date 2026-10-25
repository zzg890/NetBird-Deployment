# NetBird-Deployment
## Workflows

1. **Generate SSH Key** (`generate-ssh-key.yml`): creates an ed25519 key pair, stores the private key in secret `SSH_PRIVATE_KEY` and the public key in variable `SSH_PUBLIC_KEY`. Needs secret `ADMIN_TOKEN` (PAT able to write secrets/variables). Add the public key to the server's `authorized_keys`.
2. **Deploy NetBird** (`deploy-netbird.yml`): over SSH installs the NetBird agent and registers it (`NETBIRD_SETUP_KEY`), writes `/etc/nginx/conf.d/<DOMAIN>.conf` reverse proxy (to `127.0.0.1:NETBIRD_UPSTREAM_PORT`), and sets a proxied (orange cloud) Cloudflare A record for `DOMAIN` using `CLOUDFLARE_API_TOKEN`. Default server: 43.133.38.112.
