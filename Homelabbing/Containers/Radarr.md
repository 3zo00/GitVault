#domain/homelab

# Radarr

The movie equivalent of **[[Sonarr]]**: point it at a movie (or a whole watchlist), it searches indexers via **[[Prowlarr]]**, sends the best match to a download client, then renames and files the result into your media library. Same quality-profile system as Sonarr, so it's easy to run both with a consistent standard for what counts as an acceptable release.

### Docker basics
```yaml
radarr:
  image: lscr.io/linuxserver/radarr
  environment:
    - PUID=1000
    - PGID=1000
    - TZ=Etc/UTC
  ports:
    - "7878:7878"
  volumes:
    - radarr_config:/config
    - /nas/media/movies:/movies
    - /nas/downloads:/downloads
  restart: unless-stopped
```

### Related
[[Media Management (Arr Stack)]] [[Sonarr]] [[Prowlarr]] [[Seerr]]
