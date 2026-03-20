# Common Troubleshooting Patterns

## NVIDIA GPU Issues

- **Driver mismatch**: After kernel updates, NVIDIA driver may need rebuilding — check `nvidia-smi` first
- **CUDA not found**: Ensure `CUDA_HOME=/usr/local/cuda` and `PATH` includes `/usr/local/cuda/bin`
- **GPU memory**: Use `nvidia-smi` to check VRAM usage before launching large models
- **Wayland + NVIDIA**: Use `__NV_PRIME_RENDER_OFFLOAD=1` for hybrid rendering if needed

## Audio Device Management

- **Device switching**: Devices may need explicit selection in PipeWire
- **USB audio**: Check device permissions and PipeWire routing when mics aren't detected
- **Tools**: Use `pactl`, `wpctl`, and `pw-cli` for audio debugging

## Container Issues

- **Docker socket permissions**: User should be in `docker` group; if not, use `sudo`
- **Port conflicts**: Check `ss -tlnp` before binding ports
- **Volume mounts**: NFS mounts from NAS may need `no_root_squash` for container access
- **Podman vs Docker**: Some compose files may need `podman-compose` instead of `docker compose`

## Kubernetes Troubleshooting

- **Context switching**: Verify with `kubectl config current-context` before running commands
- **Pod issues**: `k9s` is preferred over raw kubectl for debugging
- **ArgoCD sync**: Check `argocd app list` if deployments seem stuck
- **DNS resolution**: CoreDNS logs at `kubectl logs -n kube-system -l k8s-app=kube-dns`

## Network Issues

- **Tailscale**: Check `tailscale status` for mesh connectivity
- **DNS**: Pi-hole at 192.168.1.53 handles local DNS; check its logs for resolution failures
- **Firewall**: OPNsense at 192.168.1.1 — SSH in to check rules if traffic is blocked
