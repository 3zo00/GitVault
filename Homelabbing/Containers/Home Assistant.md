#domain/homelab

# Home Assistant

The hub for smart home automation, integrates with thousands of device brands and protocols (Zigbee, Z-Wave, Wi-Fi devices, cloud APIs for things that need them) under one local interface, and is where actual automations get built, entirely locally if you want it to be, without depending on a manufacturer's cloud service staying online.

Runs well as a container or, for the fullest experience (including its own add-on ecosystem and OS-level integrations like Bluetooth), as its own dedicated VM/**[[LXC]]** container on **[[Proxmox]]**. Talks to a lot of devices over **[[Mosquitto (MQTT)]]**, which is commonly run alongside it.

### Docker basics
```yaml
homeassistant:
  image: ghcr.io/home-assistant/home-assistant:stable
  network_mode: host
  environment:
    - TZ=Etc/UTC
  volumes:
    - homeassistant_config:/config
  restart: unless-stopped
```
`network_mode: host` is the common setup, needed for device discovery (Bluetooth, mDNS) to work properly.

### Related
[[Smart Home]] [[Mosquitto (MQTT)]] [[Proxmox]] [[LXC]]
