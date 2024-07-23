# dotfiles-server

This is a collection of Ansible playbooks to run services on a Kubernetes cluster. I'm currently running them on my
homelab. This repository contains the following services:
- SearxNG
- Technitium
- Wireguard

## ☸️ Deploy our cluster
We can deploy our Kubernetes cluster by running
```sh
ansible-playbook -k -K -e @global_vars.yml -e @K3s/vars.yml K3s/playbook-deploy.yml
```
## 🔥 Reset our cluster
```sh
ansible-playbook -k -K -e @global_vars.yml -e @K3s/vars.yml K3s/playbook-reset.yml
```

## Deploy and reset services
You can find the playbooks and documentation for each service in their respective folders.

_You can remove `-k -K` if you don't need a SSH password on your hosts_
