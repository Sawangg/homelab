# Immich

Immich is an pen source photos and videos storage with tons of features.

## ☸️ Deploy
You can simply run the following playbook
```sh
ansible-playbook -k -K playbook-deploy.yml -e @../global_vars.yml
```
Then get the ip affected by the loadbalancer
```sh
kubectl describe service immish-server -n immish # LoadBalancer Ingress
```
Finally you can use the [quick start](https://immich.app/docs/overview/quick-start) guide provided by Immich. The port for the server is
`3001` so you can access the interface on the web using `http://<loadbalancer ip>:3001`

## 🔥 Reset
Simply run the following Ansible playbook
```sh
ansible-playbook -k -K playbook-reset.yml
```
_You can remove `-k -K` if you don't need a SSH password_
