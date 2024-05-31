# Install

Run this command inside this folder (ref: https://hub.docker.com/r/gists/dnscrypt-proxy/#!)

```sh
docker run \
    -d \
    --name dnscrypt-proxy \
    -p 5353:5353/tcp \
    -p 5353:5353/udp \
    -v ./dnscrypt-proxy.toml:/etc/dnscrypt-proxy/dnscrypt-proxy.toml
    gists/dnscrypt-proxy
```
