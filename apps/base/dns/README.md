# PiHole + Unbound

`PiHole` is a DNS sinkhole to block ads and more. Combined with `Unbound` configured as a recursive DNS server, we have our
own private DNS system without relying on third parties.

> [!IMPORTANT]
> If you're not running this on ARM hardware, edit the image of `manifests/deployment.conf` from `unbound-rpi` to `unbound`
