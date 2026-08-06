# Homelab Documentation

Project docs for the house infrastructure, written 2026-07-09. One file per project.
Credentials are **never** stored here — they live in root-only files on `star`
(`/root/.unifi.env`, `/root/.ha.env`, `/etc/nut/unvr-shutdown.env`).

| File | Project |
|---|---|
| `01-network-zones-and-vlans.md` | UniFi zone firewall, VLAN map, device management pattern |
| `02-dns-technitium.md` | Technitium DNS server + Advanced Blocking (Pi-hole replacement) |
| `03-trusted-vlan-and-content-filtering.md` | Trusted VLAN 25, kids' filtering, YouTube Restricted Mode fix |
| `04-ups-nut-shutdown-chain.md` | GoldenMate UPS, NUT, staged graceful shutdown, killpower recovery |
| `05-home-assistant.md` | HA integrations, UPS automations, phone + TV dashboards |
| `06-camera-wifi-streaming.md` | Reolink streaming fix: DFS channels, band selection |
| `07-udb-wireless-bridge.md` | UDB IoT mesh bridge: the stranding bug and its rules |
| `08-unvr-api-access.md` | UNVR accounts, API keys, firewall pinholes |
| `09-backups-and-storage-roadmap.md` | Backup strategy, UNAS plan, Florida offsite project |
| `10-radon-monitoring.md` | SDP811 radon/pressure node, ESPHome, HA dashboard |
| `11-xgspon-ont-replacement.md` | Replacing the Surf ONT with an ONU SFP+ stick in the UCG |
| `12-reolink-ptz-patrol.md` | Custom PTZ patrol for "Run" (E1 Outdoor Pro, no native patrol) |
| `15-radon-vacuum-sensor-howto.md` | Shareable how-to: build the SDP811/QT Py radon vacuum sensor |

## The `files` share this lives on

`\\10.10.15.15\files` → 500 GB thin LVM volume (`pve/files`) mounted at `/mnt/files`,
created 2026-07-09. Same login as the media share (user `media`).

```
/mnt/files
├── docs/homelab/       ← these documents
├── logs/               ← exported logs & reports worth keeping
├── software/           ← installers (windows / linux / android)
├── games/              ← game installers & archives
├── isos/               ← OS install ISOs
├── vm-images/          ← proxmox-templates / docker images & compose files
├── scripts/            ← shared utility scripts
└── config-backups/     ← manual config exports (UniFi backups, HA snapshots, …)
```

Host `star` = Proxmox VE, 10.10.15.15 (Server VLAN 15). Guests: HA OS VM 100,
Technitium DNS LXC 102, Jellyfin LXC 103 (Pi-hole LXC 101 retired).
