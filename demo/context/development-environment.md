# Development Environment

## Python Environment Strategy

Alex prefers minimal Python environment overhead:

- **Quick projects**: Use `uv` to create lightweight venvs
- **pipx**: Installed for isolated CLI tool installations

Virtual environments are created within projects at `.venv` which is git-ignored. Check if this exists before assuming there is no virtual environment.

System python will never be used.

## Containerization

- **Docker**: Primary tool for containerization (Docker Engine, not Docker Desktop)
- **Podman**: Also available, used for rootless containers
- **Preferred Approach**: For databases, AI workloads, and dev services, **always check existing containers first** before spinning up new ones
  - Check `docker ps -a` and `podman ps -a` before creating anything new
  - Many services are already running as containers on the Proxmox cluster

## Kubernetes

- **kubectl**: Configured with `homelab` context pointing to 192.168.1.20
- **Helm**: v3 installed for chart management
- **k9s**: Terminal UI for Kubernetes, Alex's preferred way to inspect clusters
- **ArgoCD**: GitOps deployments — push to `~/code/github/homelab-manifests` triggers sync

## Other Development Tools

- **Node.js**: Managed via fnm (Fast Node Manager)
- **Go**: Primary language for CLI tools and services
- **Rust**: Used for performance-critical tooling

## Programming Languages & SDKs

- **Go**: 1.22+ (primary for backend services and CLI tools)
- **Rust**: Available (rustc and cargo)
- **TypeScript/Node.js**: For frontend and scripting
- **Python**: For automation, data, and ML workflows
- **C/C++**: GCC and Clang available

## Build Tools & Infrastructure

- **Make**: Available
- **Just**: Preferred task runner (justfiles in most projects)
- **Terraform**: For infrastructure provisioning
- **Ansible**: For configuration management
- **Packer**: For image building

## Cloud CLIs

- **aws**: AWS CLI v2 configured with SSO profiles
- **gcloud**: Google Cloud CLI installed
- **az**: Azure CLI available

## Version Control & GitHub

Alex version-controls everything, even single scripts.

- Create repos at `~/code/github/`
- Default to private unless explicitly told otherwise
- After creating the repo and adding code, push changes
- Conventional commits preferred (feat:, fix:, chore:, etc.)

## CI/CD

- **GitHub Actions**: Primary CI for open source
- **ArgoCD**: GitOps for homelab Kubernetes deployments
- **Drone CI**: Self-hosted runner on Proxmox for private projects
