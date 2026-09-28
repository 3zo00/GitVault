#domain/homelab

# Netbird

An open-source mesh VPN, conceptually very similar to **[[Tailscale]]** (also built on **[[WireGuard]]**, also handles automatic key exchange and NAT traversal), but designed so the coordination/management layer itself can be self-hosted instead of relying on a third-party's servers. Netbird offers a hosted version too, similar to Tailscale, but the self-hosted option is the main reason people choose it over Tailscale specifically.

A comparable, older self-hosted approach is running **Headscale** as an open-source implementation of Tailscale's own coordination server, letting you use the official Tailscale client apps against your own infrastructure instead of Tailscale's. Netbird and Headscale solve a similar problem from slightly different angles; either is a reasonable choice when "no third party in the loop at all" is the priority.

### Docker basics
```yaml
netbird:
  image: netbirdio/netbird
  cap_add:
    - NET_ADMIN
  environment:
    - NB_SETUP_KEY=your-setup-key
  volumes:
    - netbird_client:/etc/netbird
  restart: unless-stopped
```
This is just the client joining a mesh. Self-hosting the management/signal/coturn stack itself is a separate, bigger multi-container setup.

### Related
[[VPNs and Remote Access]] [[Tailscale]] [[WireGuard]]
