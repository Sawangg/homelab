# Homelab 🏡

State of the art multi-cluster GitOps repository for homelab use. Currently used with my bare metal Kubernetes clusters
at home to host a bunch of useful open-source apps.

## 🏗️ Infrastructure

<table>
  <tr>
    <th>Apps</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><a href="https://talos.dev/" title="Talos" target="_blank"> <img src="https://avatars.githubusercontent.com/u/13804887" alt="talos" width="35" height="35" /></a></td>
    <td>Immutable Linux distro for Kubernetes, allowing to deploy clusters with <code>Omni</code></td>
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
    <td>Manage secrets remotely & securely from a large list of providers</td>
  </tr>
  <tr>
    <td><a href="https://cert-manager.io/" title="Cert-Manager" target="_blank"> <img src="https://avatars.githubusercontent.com/u/39950598" alt="cert-manager" width="40" height="40" /></a></td>
    <td>Automatic x.509 certificates management with Gateway API support</td>
  </tr>
  <tr>
    <td><a href="https://kubernetes-sigs.github.io/external-dns/latest/" title="ExternalDNS" target="_blank"> <img src="https://raw.githubusercontent.com/kubernetes-sigs/external-dns/master/docs/img/external-dns.png" alt="externaldns" width="50" height="45" /></a></td>
    <td>Manage automatically the DNS records of domains listed in the Gateway API's routes</td>
  </tr>
  <tr>
    <td><a href="https://pi-hole.net/" title="Pi-hole" target="_blank"> <img src="https://avatars.githubusercontent.com/u/16827203" alt="pi-hole" width="40" height="40" /></a></td>
    <td>Custom DNS server with blocking capabilities to route internal traffic</td>
  </tr>
  <tr>
    <td><a href="https://rook.io/" title="Rook" target="_blank"> <img src="https://avatars.githubusercontent.com/u/22860722" alt="rook" width="40" height="40" /></a></td>
    <td>Storage Orchestrator to manage a <code>Ceph</code> cluster</td>
  </tr>
  <tr>
    <td><a href="https://cloudnative-pg.io/" title="CloudNativePG" target="_blank"> <img src="https://avatars.githubusercontent.com/u/100373852" alt="cloudnative-pg" width="40" height="40" /></a></td>
    <td>Operator for running PostgreSQL databases clusters with high availability</td>
  </tr>
  <tr>
    <td><a href="https://valkey.io" title="Valkey" target="_blank"> <img src="https://avatars.githubusercontent.com/u/164458127" alt="valkey" width="35" height="35" /></a></td>
    <td>Open-source high-performance key/value datastore</td>
  </tr>
  <tr>
    <td><a href="https://goauthentik.io/" title="Authentik" target="_blank"> <img src="https://avatars.githubusercontent.com/u/82976448" alt="authentik" width="40" height="40" /></a></td>
    <td>Identity provider to allow Single-Sign-On for any apps</td>
  </tr>
</table>

## 📦 Applications

<table>
  <tr>
    <th>Apps</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><a href="https://www.nlnetlabs.nl/projects/unbound/about/" title="Unbound" target="_blank"> <img src="https://netdata.cloud/img/unbound.png" alt="unbound" width="35" height="35" /></a></td>
    <td>Recursive DNS server used with Pi-hole to provide more privacy</td>
  </tr>
  <tr>
    <td><a href="https://github.com/glanceapp/glance" title="Glance" target="_blank"> <img src="https://avatars.githubusercontent.com/u/159397742" alt="glance" width="40" height="40" /></a></td>
    <td>Dashboard with a bunch of features that I use as my browser starting page</td>
  </tr>
  <tr>
    <td><a href="https://git-scm.com/" title="Git" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/refs/heads/master/icons/git/git-original.svg" alt="git" width="40" height="40" /></a></td>
    <td>Git server to host personal stuff likes notes etc.</td>
  </tr>
  <tr>
    <td><a href="https://www.home-assistant.io/" title="Home Assistant" target="_blank"> <img src="https://avatars.githubusercontent.com/u/13844975" alt="home-assistant" width="35" height="35" /></a></td>
    <td>Home automation that puts local control and privacy first</td>
  </tr>
  <tr>
    <td><a href="https://github.com/SoftFever/OrcaSlicer" title="Orca Slicer" target="_blank"> <img src="https://raw.githubusercontent.com/SoftFever/OrcaSlicer/refs/heads/main/resources/images/OrcaSlicer.ico" alt="orca-slicer" width="40" height="40" /></a></td>
    <td>3D printing slicer based on Bambu Studio and PrusaSlicer with enhanced features</td>
  </tr>
  <tr>
    <td><a href="https://prowlarr.com/" title="Prowlarr" target="_blank"> <img src="https://avatars.githubusercontent.com/u/73049443" alt="prowlarr" width="35" height="35" /></a></td>
    <td>Prowlarr is an indexer manager/proxy that supports management of both torrent trackers and usenet indexers</td>
  </tr>
  <tr>
    <td><a href="https://www.qbittorrent.org/" title="qBittorrent" target="_blank"> <img src="https://avatars.githubusercontent.com/u/2131270" alt="qbittorrent" width="35" height="35" /></a></td>
    <td>Torrent client to download legal stuff :)</td>
  </tr>
  <tr>
    <td><a href="https://readarr.com/" title="Readarr" target="_blank"> <img src="https://avatars.githubusercontent.com/u/57576474" alt="readarr" width="35" height="35" /></a></td>
    <td>Readarr is an eBook and audiobook collection manager</td>
  </tr>
</table>

## 🔭 Monitoring

<table>
  <tr>
    <th>Apps</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><a href="https://grafana.com/" title="Grafana" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/refs/heads/master/icons/grafana/grafana-original.svg" alt="graphana" width="40" height="40" /></a></td>
    <td>Open-source analytics and interactive visualization web application</td>
  </tr>
  <tr>
    <td><a href="https://prometheus.io/" title="Prometheus" target="_blank"> <img src="https://raw.githubusercontent.com/devicons/devicon/refs/heads/master/icons/prometheus/prometheus-original.svg" alt="prometheus" width="40" height="40" /></a></td>
    <td>Monitoring system with a dimensional data model, flexible query language & more</td>
  </tr>
  <tr>
    <td><a href="https://docs.mend.io/renovate/latest/" title="Renovate" target="_blank"> <img src="https://avatars.githubusercontent.com/u/38656520" alt="renovate" width="35" height="35" /></a></td>
    <td>Automatically inform and updates deployed apps in the clusters</td>
  </tr>
</table>

## ☸️ Deploy the Kubernetes clusters

I'm using [Sidero Omni](https://github.com/siderolabs/omni) to manage and deploy my Kubernetes clusters.

You'll need the following:

- A static public IP address with a router able to forward ports
- A domain name with a DNS provider usable with [ExternalDNS](https://kubernetes-sigs.github.io/external-dns/latest/#the-latest-release)
- Any secret provider supported by [External Secrets Operator](https://external-secrets.io/). This repository uses `GitLab` as it's secrets provider
- An API token of the DNS provider that will allow challenges to create certificates. This repository uses a `Cloudflare` token with the permissions: Zone - DNS - Edit, Zone - Zone - Read & Include - All Zones
- Another API token of the same provider to manage DNS records. Using `Cloudflare`, the token should have the same
permissions as above
- A [GitHub PAT](https://github.com/settings/personal-access-tokens) to be used by `FluxCD`, with Read-Write permissions
for Admnistration & Contents

### 🔑 Secrets

Here is the following list of secrets you need to add in your external secrets provider of choice before starting the
cluster:

<table>
  <tr>
    <th>Name</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>dns_provider_challenge_token</code></td>
    <td>API token of your DNS management provider of your domain, used to generate the x.509 certificates</td>
  </tr>
  <tr>
    <td><code>dns_provider_management_token</code></td>
    <td>API token of your DNS management provider of your domain, used to manage your DNS records</td>
  </tr>
  <tr>
    <td><code>authentik_key</code></td>
    <td>Random string of atleast 50 caracters long (ex: <code>openssl rand -base64 50</code>)</td>
  </tr>
  <tr>
    <td><code>renovate_token</code></td>
    <td>Git token for the Renovate account</td>
  </tr>
</table>
