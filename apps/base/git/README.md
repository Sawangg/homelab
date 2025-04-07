# Git

This is a simple Git server used with SSH to host my private repositories such as Obsidian notes and more.  
⚠️ This server should never be exposed to the internet, it is not secure.

## ☸️ Deploy
First, you need to change the value of `SSH_AUTHORIZED_KEYS_URL` in `manifests/deployment.yml` with your url (https://github.com/username.keys)  
Then use the following playbook
```sh
ansible-playbook -k -K playbook-deploy.yml -e @../global_vars.yml
```
Then get the ip affected by the loadbalancer
```sh
kubectl describe service git-sv -n git # LoadBalancer Ingress
```
You will need to create your repository inside the server
```sh
ssh git@<loadbalancer ip> # Password is 12345
mkdir /srv/git/your-repo.git
git-init --bare /srv/git/your-repo.git
```

You can then use it like so
```sh
git clone ssh://git@<loadbalancer ip>/your-repo.git
```

## 🔥 Reset
Simply run the following Ansible playbook
```sh
ansible-playbook -k -K playbook-reset.yml
```
_You can remove `-k -K` if you don't need a SSH password_
