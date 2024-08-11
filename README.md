# dotfiles-server

This is a collection of Ansible playbooks to deploy a Kubernetes cluster as well as run various services. I'm currently running them in my homelab. This repository contains the following services:
- Atuin (_Shell history manager_)
- Git (_Local git server to host personal stuff e.g. Obsidian notes_)
- Wireguard (_VPN_)

## 🔄 Start from scratch
You can follow the [wiki](https://github.com/Sawangg/dotfiles-server/wiki) to get started from no OS to a fully
functionnal cluster with services. If you already have a server running Linux you can just deploy the cluster.

## ☸️ Deploy our Kubernetes cluster
First, clone this repository locally and edit the `hosts.ini` file with the IPs of your infrastructure. Next, edit the
file `K3s/vars.yml` to configure your Kuberbenetes cluster according to your environment. Then, run the following command to install all of Ansible's requirements
```sh
ansible-galaxy collection install -r requirements.yml
```
You might have to install [`netaddr`](https://pypi.org/project/netaddr/) on your local machine as well.
Finally, deploy your cluster by running
```sh
ansible-playbook -k -K -e @global_vars.yml -e @K3s/vars.yml K3s/playbook-deploy.yml # Remove -k -K if no SSH password
```
This will create a fully functional cluster with MetalLB and kube-vip.

## 🔥 Reset our Kubernetes cluster
Simply run the following playbook to remove Kubernetes and your services from your infrastructure
```sh
ansible-playbook -k -K -e @global_vars.yml -e @K3s/vars.yml K3s/playbook-reset.yml
```

## 🚀 Deploy and reset services
You can find the playbooks and documentation for each service in their respective folders.
