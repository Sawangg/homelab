# Homelab 🏡

State of the art multi-cluster GitOps repository for homelab use. Currently used with my bare metal Kubernetes clusters
at home to host a bunch of useful apps.

## Features

- Supports 2 Kubernetes clusters staging and production
- Fully managed by `FluxCD`, adhering to GitOps principles
- Supports any Git provider, simply change the repository `FluxCD` watches
- Uses `External Secrets Operator` to manage secrets remotely & securely from a list of providers
- `Cilium` for the full network stack
  - Replace `Flannel` as the default CNI
  - Replace `kube-proxy` as the default proxy
  - Used as the default load balancer
  - Using the Gateway API
- `Cert-manager` for automatic SSL certificates
- `External-DNS` to manage automatically my DNS records
- `Renovate` to automatically inform of new updates
- `Rook + Ceph` for distributed storage across the cluster

Here is a list of deployed apps:

- Atuin (_Shell history manager_)
- PiHole & Unbound (_Local recursive DNS with blocking capabilities_)
- Git (_Local git server to host personal stuff e.g. Obsidian notes_)
- Immich (_Local photo storage & more_)

## ☸️ Deploy the Kubernetes clusters

I'm using [Sidero Omni](https://github.com/siderolabs/omni) to manage and deploy my Kubernetes clusters.

You'll need the following:

- A [GitHub PAT](https://github.com/settings/personal-access-tokens) to be used by `Flux`, with Read-Write permissions
for Admnistration & Contents
- Any secret provider supported by [External Secrets Operator](https://external-secrets.io/), this repository uses `GitLab`
- An API token of your a provider that will make DNS challenges to create certificates. This repository uses a `Cloudflare` token with the permissions: Zone - DNS - Edit, Zone - Zone - Read & Include - All Zones
- Another API token of the same provider to manage DNS records. Using `Cloudflare`, the token should have the same
permissions as above.

### Secrets

Add the following secrets to your secret provider of choice: `dns_provider_challenge_token` &
`dns_provider_management_token`

# References

[https://docs.renovatebot.com/](https://docs.renovatebot.com/)  
[https://external-secrets.io/latest/provider/gitlab-variables/](https://external-secrets.io/latest/provider/gitlab-variables/)
