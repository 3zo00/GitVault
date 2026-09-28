#domain/homelab

# Sonarr

Automates TV show acquisition: point it at a series, it monitors for new episodes, searches configured indexers (via **[[Prowlarr]]**) when one airs, sends the best match to a download client (**[[qBittorrent]]** or **[[SABnzbd]]**), and renames/moves the finished file into the media library folder your server (**[[Plex]]**/**[[Jellyfin]]**) watches.

Supports quality profiles (so it only grabs, say, 1080p releases and upgrades later if a better one appears) and season-pack vs per-episode handling. Almost always paired with **[[Bazarr]]** for automatic subtitles on the same files.

### Docker basics
```yaml
sonarr:
  image: lscr.io/linuxserver/sonarr
  environment:
    - PUID=1000
    - PGID=1000
    - TZ=Etc/UTC
  ports:
    - "8989:8989"
  volumes:
    - sonarr_config:/config
    - /nas/media/tv:/tv
    - /nas/downloads:/downloads
  restart: unless-stopped
```

### Related
[[Media Management (Arr Stack)]] [[Radarr]] [[Prowlarr]] [[Bazarr]]
