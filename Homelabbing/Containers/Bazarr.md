#domain/homelab

# Bazarr

Automatic subtitle downloading, paired with **[[Sonarr]]** and **[[Radarr]]** so it knows exactly which files exist and which languages are wanted. Searches a wide range of subtitle providers, downloads the best match, and keeps watching for better ones (e.g. a synced release) even after a file is already tagged.

Saves the manual "find and rename a .srt file" step that would otherwise apply to every single episode or movie individually, minor on its own but compounds quickly across a large library.

### Docker basics
```yaml
bazarr:
  image: lscr.io/linuxserver/bazarr
  environment:
    - PUID=1000
    - PGID=1000
    - TZ=Etc/UTC
  ports:
    - "6767:6767"
  volumes:
    - bazarr_config:/config
    - /nas/media/movies:/movies
    - /nas/media/tv:/tv
  restart: unless-stopped
```

### Related
[[Media Management (Arr Stack)]] [[Sonarr]] [[Radarr]]
