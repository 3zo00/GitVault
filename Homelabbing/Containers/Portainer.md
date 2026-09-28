#domain/homelab

# Portainer

A web UI for managing **[[Docker]]** (and, if relevant, Docker Swarm or Kubernetes) without needing to live in the command line for routine tasks: browse running containers, view/tail logs, start/stop/restart, edit and redeploy a **[[Docker Compose]]** stack, all from a browser.

Particularly useful once a homelab has enough containers that remembering every `docker` CLI flag stops being practical, or when someone else (a less technical household member) needs to restart a stuck service without SSH access.

### Docker basics
```yaml
portainer:
  image: portainer/portainer-ce
  ports:
    - "9443:9443"
  volumes:
    - portainer_data:/data
    - /var/run/docker.sock:/var/run/docker.sock
  restart: unless-stopped
```

### Related
[[Infrastructure and Management]] [[Docker]] [[Docker Compose]]
