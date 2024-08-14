# PiHole + Unbound

PiHole is a DNS sinkhole to block ads and more. Combined with Unbound configured as a recursive DNS server, we have our
own private DNS system.

> If you're not running this on ARM hardware, edit the image of the deployment of unbound from `unbound-rpi` to `unbound`

## ☸️ Deploy
Use the following playbook
```sh
ansible-playbook -k -K playbook-deploy.yml -e @../global_vars.yml
```
Then get the ip affected by the loadbalancer
```sh
kubectl describe service pihole-sv -n dns-resolver # LoadBalancer Ingress
```
You can then access the admin interface in your browser at `http://<loadbalancer ip>/admin`. Feel free to assign the
loadbalancer ip as your DNS server in your router or any machine.

## 🔥 Reset
Simply run the following Ansible playbook
```sh
ansible-playbook -k -K playbook-reset.yml
```
_You can remove `-k -K` if you don't need a SSH password_
