#domain/homelab

# Immich

A self-hosted photo and video backup platform built as a direct Google Photos alternative: automatic background backup from a mobile app, a fast timeline view, face recognition and object/scene search, shared albums, and live photo/video support. By 2026 it's become the clear default in this space, thanks to fast, active development and mobile apps genuinely comparable to the commercial services it replaces.

Runs as a small stack (the main server, a Postgres database with a vector-search extension, Redis, and a machine-learning container for face/object recognition) rather than a single container, worth budgeting a bit more RAM than a typical single-purpose service, especially if the ML features are enabled.

### Docker basics
```yaml
immich-server:
  image: ghcr.io/immich-app/immich-server:release
  ports:
    - "2283:2283"
  volumes:
    - /nas/photos:/usr/src/app/upload
  depends_on:
    - immich-postgres
    - immich-redis
  restart: unless-stopped
```
Just the main server here, a real deploy also needs a Postgres (with the pgvector extension) and Redis service alongside it, plus the machine-learning container if you want face/object recognition.

### Related
[[Photos and Files]] [[Nextcloud]] [[NAS]] [[Homelab Backups and Maintenance]]
