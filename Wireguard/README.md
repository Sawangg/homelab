# Wireguard
WireGuard is an extremely simple yet fast and modern VPN.

## ☸️ Deploy
First, you need to modify the file `manifests/deployment.yml` with your [external IP address](https://checkip.amazonaws.com/) for the env variable called `WG_HOST`.  
Then you can run the playbook
```sh
ansible-playbook -k -K playbook-deploy.yml -e @../global_vars.yml
```
Once it's done, run this command to get the IP affected by the loadbalancer
```sh
kubectl describe service wireguard-sv -n wg # Line LoadBalancer Ingress
```
Finally, in your router, forward the port `51280` to the IP returned by the previous command.  
You can now create a client by visting in your browser of choice the IP address returned previously.

## 🔥 Reset
Simply run the following Ansible playbook
```sh
ansible-playbook -k -K playbook-reset.yml
```

_You can remove `-k -K` if you don't need a SSH password_
