# NetBird-Deployment
## Workflows

1. **Generate SSH Key** (`generate-ssh-key.yml`): creates an ed25519 key pair, stores the private key in secret `SSH_PRIVATE_KEY` and the public key in variable `SSH_PUBLIC_KEY`. Needs secret `ADMIN_TOKEN` (PAT able to write secrets/variables). Add the public key to the server's `authorized_keys`.
2. **Deploy NetBird** (`deploy-netbird.yml`): over SSH installs the self-hosted NetBird server using the official setup script with built-in Traefik TLS, and sets a proxied (orange cloud) Cloudflare A record for `DOMAIN` using `CLOUDFLARE_API_TOKEN`. Configure repository variables `DOMAIN` and `NETBIRD_LETSENCRYPT_EMAIL`, and secrets `SSH_PRIVATE_KEY` and `CLOUDFLARE_API_TOKEN`. Default server: 43.133.38.112.
