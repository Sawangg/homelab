# Wireguard
WireGuard is an extremely simple yet fast and modern VPN.

## ☸️ Deploy
First, you need to modify the file `data/deployment.yml` with the correct value for the env variable called `WG_HOST`.  
Then you can run the playbook
```sh
ansible-playbook -k -K playbook-deploy.yml -e @../global_vars.yml
```
Once it's done, run this command to get the IP affected by the loadbalancer
```sh
kubectl describe service wireguard-sv -n wg # Line LoadBalancer Ingress
```
Finally, in your router, forward the port `51280` to the IP returned by the previous command.  
You can now create a client by visting the IP address returned in your browser and connect to your VPN server.

## 🔥 Reset
Simply run the following Ansible playbook
```sh
ansible-playbook -k -K playbook-reset.yml
```

_You can remove `-k -K` if you don't need a SSH password_
