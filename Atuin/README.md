# Atuin
Atuin is a shell history replacement with end to end sync between machines. This is Atuin's sync server using PostgreSQL.

## ☸️ Deploy
Run the following playbook
```sh
ansible-playbook -k -K playbook-deploy.yml -e @../global_vars.yml
```
Then get the ip affected by the loadbalancer
```sh
kubectl describe service atuin -n atuin # LoadBalancer Ingress
```
Finally, update your local atuin's `config.toml` with the line
```toml
sync_address = http://<loadbalancer ip>
```
You can then follow the documentation [here](https://docs.atuin.sh/guide/sync/) to finish syncing your machine.

## 🔥 Reset
Simply run the following Ansible playbook
```sh
ansible-playbook -k -K playbook-reset.yml
```
_You can remove `-k -K` if you don't need a SSH password_
