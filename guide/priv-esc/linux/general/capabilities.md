## Capabilities

### stapsgewijs

#### 1. List all capabilities of a user with.

```
getcap -r / 2>/dev/null
```

*Voorbeeld van terugkomst*

```
$ getcap -r / 2>/dev/null
/usr/lib/x86_64-linux-gnu/gstreamer1.0/gstreamer-1.0/gst-ptp-helper = cap_net_bind_service,cap_net_admin+ep
/usr/bin/traceroute6.iputils = cap_net_raw+ep
/usr/bin/mtr-packet = cap_net_raw+ep
/usr/bin/ping = cap_net_raw+ep
/home/karen/vim = cap_setuid+ep
/home/ubuntu/view = cap_setuid+ep
```

#### 2. GTFObins afzoeken naar mogelijkheid om root te worden via /home/karen/vim binary en exploit uitvoeren.