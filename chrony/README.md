# Chrony

An NTS server to sync the time of all your machines. Feel free to change your timezone and upstream NTP server.
```sh
docker run --name=ntp                                   \
           --restart=always                             \
           --detach                                     \
           --env=TZ="Europe/Paris"                      \
           --env=NTP_SERVERS="paris.time.system76.com"  \
           --env=ENABLE_NTS="true"                      \
           --publish=123:123/udp                        \
           --read-only                                  \
           --tmpfs=/etc/chrony:rw,mode=1750             \
           --tmpfs=/run/chrony:rw,mode=1750             \
           --tmpfs=/var/lib/chrony:rw,mode=1750         \
           cturra/ntp
```
