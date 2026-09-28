#domain/homelab

# Grocy

A self-hosted household management tool centered on groceries and consumables: tracks what's in the pantry/fridge, expiry dates, shopping lists that update as items run low, and can extend into a broader chore/task tracker for the household. A niche but genuinely useful pick for anyone who wants the "smart fridge inventory" experience without a smart fridge or a subscription app.

### Docker basics
```yaml
grocy:
  image: lscr.io/linuxserver/grocy
  environment:
    - PUID=1000
    - PGID=1000
    - TZ=Etc/UTC
  ports:
    - "80:80"
  volumes:
    - grocy_config:/config
  restart: unless-stopped
```

### Related
[[Miscellaneous]] [[Self-Hosted Service Stack]]
