# Omni

## Prerequisites

- A domain name with the ability to validate a certificate via DNS challenge
- SSH into the machine and intall `podman` and `podman-compose` (apk add podman podman-compose # in community repo)
- Install `certbot` (apk add certbot) and a certbot provider (apk add certbot-dns-cloudflare # for Cloudflare)
- Create directories: `mkdir omni omni/etcd`

### Alpine Linux

We have extra steps if we want to run the stack on Alpine Linux:

- Install `nftables` (apk add nftables) and edit `/etc/containers/containers.conf` with:

   ```toml
   [network]
   firewall_driver = "nftables"
   ```

- Configure aardvark-dns to use a port other than 53

   ```toml
   [network]
   dns_bind_port=5000
   ```

- Setup /dev/net/tun for WireGuard:

   ```sh
    apk add --no-cache kmod
    modprobe tun
    mkdir -p /dev/net
    if [ ! -c /dev/net/tun ]; then mknod /dev/net/tun c 10 200; fi
    chmod 0666 /dev/net/tun
    cat /dev/net/tun # If you see "File descriptor in bad state", it’s working.
    rc-update add modules boot
    echo tun > /etc/modules-load.d/tun.conf
   ```

## Steps

1) Generate GPG key for etcd encryption:
  - gpg --quick-generate-key "Omni (Used for etcd data encryption) you@example.com" rsa4096 cert never

   > [!NOTE]
   > Do not add a passphrase to the key, as etcd needs to access it without user interaction.

  - gpg --list-secret-keys
  - gpg --quick-add-key <fingerprint> rsa4096 encr never
  - gpg --export-secret-key --armor you@example.com > omni/omni.asc

2) Generate TLS certificates (for localhost)
   - Get your API token from your DNS provider (e.g. Cloudflare)
   - Create a creds.ini file and paste your token in it:

     ```
     dns_cloudflare_api_token = your_token_here
     ```

   - Generate the certs with certbot:

     ```sh
     certbot certonly \
        --dns-cloudflare \
        --dns-cloudflare-credentials creds.ini \
        --dns-cloudflare-propagation-seconds 60 \
        -d omni.your-domain.com \
        --agree-tos -m your@email.com --non-interactive

3) Check the docker-compose.yml
   - Update the uuid in Omni with `uuidgen`
   - Change the ip of the wirguard interface to the one your local machine uses `ip -c addr`
   - Change the domain name in the omni configuration
   - Change the paths to your TLS certs (from step 2)

      ```
      - /etc/letsencrypt/live/omni.example.com/fullchain.pem:/tls.crt:ro
      - /etc/letsencrypt/live/omni.example.com/privkey.pem:/tls.key:ro
      ```

4) Start the compose stack:
   - podman compose up -d

5) Configure Keycloak:

   - Go to `http://<your LAN IP>:8082` (default user: admin, password: admin)

   - Follow the official docs: https://docs.siderolabs.com/omni/infrastructure-and-extensions/self-hosted/configure-keycloak-for-omni
       - Realm name: Omni (case-sensitive)
       - Client ID: https://<your domain>/saml/metadata
       - Root URL: https://<your domain>/saml/acs
       - Valid Redirect URI: https://<your domain>/*
       - Master SAML Processing URL: https://<your domain>/saml/acs

6) Access Omni:
   - Modify your `/etc/hosts` file or your DNS server to point `<your domain>` to your LAN IP

      ```
      <your LAN IP>   <your domain>
      ```
   - Now connect to `https://<your domain>` (make sure HTTPS is used).
   - Click login; you’ll be redirected to Keycloak and back.

7) When downloading the installation media (choose ISO for bare-metal), add the following kernel parameters to point back to the bundled pihole DNS server:

   ```
   ip=:::::eth0:dhcp:<your LAN IP>:9.9.9.9: net.iframes=0
   ```

8) When you create your cluster, add the following patch to the machines you want to add:

   ```
   machine:
     network:
       nameservers:
         - <your LAN IP>
         - 9.9.9.9
   ```

### Notes

- WireGuard address: `--siderolink-wireguard-advertised-addr` must be an IP (not a DNS name).
- If you get an authentification error, check the config of your client in Keycloak and make sure you use your correct LAN IP
