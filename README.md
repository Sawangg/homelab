# Homelab 🏡

State of the art multi-cluster GitOps repository for homelab use. Currently used with my bare metal Kubernetes clusters
at home to host a bunch of useful apps.

## 🏗️ Infrastructure

<table>
  <tr>
    <td>Apps</td>
    <td>Description</td>
  </tr>
  <tr>
    <td><a href="https://talos.dev/" title="Talos" target="_blank"> <img src="https://avatars.githubusercontent.com/u/13804887" alt="talos" width="35" height="35" /></a></td>
    <td>Immutable Linux distro for Kubernetes, deployed with <code>Omni</code></td>
  </tr>
  <tr>
    <td><a href="https://cilium.io/" title="Cilium" target="_blank"> <img src="https://avatars.githubusercontent.com/u/21054566" alt="cilium" width="40" height="40" /></a></td>
    <td>Full network stack, replaces <code>Flannel</code> as the CNI and <code>kube-proxy</code> from <code>Talos</code>. Also used as the Load Balancer with Gateway API support</td>
  </tr>
  <tr>
    <td><a href="https://fluxcd.io/" title="FluxCD" target="_blank"> <img src="https://avatars.githubusercontent.com/u/52158677" alt="fluxcd" width="50" height="40" /></a></td>
    <td>Fully managed Kubernetes deployment using <code>GitOps</code> practices</td>
  </tr>
  <tr>
    <td><a href="https://external-secrets.io/" title="External Secrets Operator" target="_blank"> <img src="https://avatars.githubusercontent.com/u/68335991" alt="eso" width="35" height="35" /></a></td>
    <td>Manage secrets remotely & securely from a list of providers</td>
  </tr>
  <tr>
    <td><a href="https://cert-manager.io/" title="Cert-Manager" target="_blank"> <img src="https://avatars.githubusercontent.com/u/39950598" alt="cert-manager" width="40" height="40" /></a></td>
    <td>Automatic SSL certificates with Gateway API support</td>
  </tr>
  <tr>
    <td><a href="https://kubernetes-sigs.github.io/external-dns/latest/" title="ExternalDNS" target="_blank"> <img src="https://raw.githubusercontent.com/kubernetes-sigs/external-dns/master/docs/img/external-dns.png" alt="externaldns" width="50" height="45" /></a></td>
    <td>Manage automatically the DNS records of domains listed in the Gateway API's routes</td>
  </tr>
  <tr>
    <td><a href="https://docs.mend.io/renovate/latest/" title="Renovate" target="_blank"> <img src="https://avatars.githubusercontent.com/u/38656520" alt="renovate" width="35" height="35" /></a></td>
    <td>Automatically inform of new updates for deployed apps in the cluster</td>
  </tr>
</table>
  
## 📦 Apps

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

