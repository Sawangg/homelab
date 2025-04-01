# Homelab

GitOps repo for my bare metal Kubernetes cluster at home

## Features

- Supports 2 clusters setup with staging and production
- Talos
- FluxCD
- Cilium for the full network stack
  - Replace `Flannel` as the default CNI
  - Replace default `kube-proxy`
  - Used as default load balancer
  - Supports new gateway API instead of Ingress (don't forget to pull the SIG (yml files))
- Cert-manager using the gateway API
- Renovate
- Longhorn / Rook / Ceph

Here is a list of deployed apps:

- Atuin (_Shell history manager_)
- PiHole & Unbound (_Local recursive DNS with blocking capabilities_)
- Git (_Local git server to host personal stuff e.g. Obsidian notes_)
- Immich (_Local photo storage & more_)

## ☸️ Deploy our Kubernetes cluster

You'll need the following:

- A GitHub personal access token with repo permissions. See the GitHub documentation on creating a personal access token.
- A Cloudflare account with token to validate certificates with DNS challenges

# References

[https://docs.renovatebot.com/](https://docs.renovatebot.com/)
