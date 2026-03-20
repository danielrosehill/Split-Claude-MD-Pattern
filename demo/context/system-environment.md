# System Environment

## The Environment

- **OS**: Fedora 41
- **Desktop Environment**: GNOME 47
- **Display Server**: Wayland

## Hardware

- **CPU**: AMD Ryzen 9 7950X (16-core, 32-thread)
- **GPU**: NVIDIA GeForce RTX 4090
  - CUDA 12.4 configured
  - Driver: 550.x proprietary
- **Memory**: 128 GB DDR5 RAM

## Storage & Network

- **Filesystem**: ~8 TB total across NVMe + HDD array, ~4.1 TB available
- **Internet**: Gigabit symmetric fiber
- **NAS**: Synology DS1621+ at 192.168.1.50 (48 TB usable, RAID 6)
- **Object Storage**: Backblaze B2 for cloud backups

## Audio & Input

- **Audio**: PipeWire
- **Input Method**: Voice-to-text via Whisper (local)
  - Expect occasional transcription errors
  - Infer around obvious errors when possible
  - Ask for clarification if a transcription seems ambiguous

## LAN & Network Topology

This workstation is in Alex's home office.

There are SSH aliases configured for commonly accessed machines. Assume SSH key authentication for all bash aliases.

**Key LAN Resources:**
- **Gateway/Router (OPNsense)**: 192.168.1.1
  - SSH: `ssh admin@192.168.1.1`
  - Handles DHCP/DNS
- **Proxmox Cluster Node 1**: 192.168.1.10
  - SSH alias: `pve1`
- **Proxmox Cluster Node 2**: 192.168.1.11
  - SSH alias: `pve2`
- **Kubernetes Control Plane**: 192.168.1.20
  - SSH alias: `k8s-cp`
  - kubectl context: `homelab`
- **This Workstation**: 192.168.1.100
- **NAS (Synology)**: 192.168.1.50
  - NFS mounts at `/mnt/nas/`
- **Pi-hole DNS**: 192.168.1.53
  - Web UI: `http://192.168.1.53/admin`
- **Grafana/Prometheus Stack**: 192.168.1.30
  - Grafana: `http://192.168.1.30:3000`
  - Prometheus: `http://192.168.1.30:9090`
- **Network**: 192.168.1.0/24 subnet, Tailscale mesh for remote access
