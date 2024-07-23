# dotfiles-server

This is a collection of Ansible playbooks to deploy a Kubernetes cluster as well as run various services. I'm currently running them in my homelab. This repository contains the following services:
- SearxNG (_Search engine_)
- Technitium (_DNS server_)
- Wireguard (_VPN_)

## ☸️ Deploy our Kubernetes cluster
First, clone this repository and edit the `hosts.ini` file with the IPs on your local machines. You can then edit the
file `K3s/vars.yml` to configure your environment. We can then deploy our cluster by running
```sh
ansible-playbook -k -K -e @global_vars.yml -e @K3s/vars.yml K3s/playbook-deploy.yml # Remove -k -K if no SSH password
```
This will create a fully functional cluster with MetalLB and kube-vip.

## 🔥 Reset our Kubernetes cluster
```sh
ansible-playbook -k -K -e @global_vars.yml -e @K3s/vars.yml K3s/playbook-reset.yml
```

## Deploy and reset services
You can find the playbooks and documentation for each service in their respective folders.

## Start from scratch
You can follow the [wiki](https://github.com/Sawangg/dotfiles-server/wiki) to get started from no OS to a fully
functionnal cluster with services.
