#domain/homelab

# Readarr

The Arr-stack app for books, ebooks and, depending on setup, audiobooks (though **[[Audiobookshelf]]** is more commonly used as the actual audiobook server). Works the same way as **[[Sonarr]]**/**[[Radarr]]**: monitor an author or series, search indexers via **[[Prowlarr]]**, download, and file the result automatically. Less actively maintained than Sonarr/Radarr historically, worth checking current project status before building a whole workflow around it.

### Docker basics
```yaml
readarr:
  image: lscr.io/linuxserver/readarr
  environment:
    - PUID=1000
    - PGID=1000
    - TZ=Etc/UTC
  ports:
    - "8787:8787"
  volumes:
    - readarr_config:/config
    - /nas/media/books:/books
    - /nas/downloads:/downloads
  restart: unless-stopped
```

### Related
[[Media Management (Arr Stack)]] [[Audiobookshelf]] [[Prowlarr]]
