#domain/homelab

# Watchtower

Watches running **[[Docker]]** containers and automatically pulls newer images, then recreates the container to apply the update, on a schedule you define (nightly, weekly, etc). Removes the manual `docker compose pull && docker compose up -d` chore across a large stack.

### The tradeoff worth knowing
Fully automatic updates mean a breaking change in an upstream image applies itself while you're not watching. Common mitigations: pin specific containers to exclude them from Watchtower's scope (labels control this), snapshot before update windows if running on **[[Proxmox]]**, and keep tested backups current regardless, see **[[Homelab Backups and Maintenance]]**.

### Docker basics
```yaml
watchtower:
  image: containrrr/watchtower
  volumes:
    - /var/run/docker.sock:/var/run/docker.sock
  environment:
    - WATCHTOWER_CLEANUP=true
    - WATCHTOWER_SCHEDULE=0 0 4 * * *
  restart: unless-stopped
```

### Related
[[Infrastructure and Management]] [[Docker]] [[Homelab Backups and Maintenance]]
