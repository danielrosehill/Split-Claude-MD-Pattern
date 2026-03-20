# File & Directory Organization

## Repository Organization

- **Repo base**: `~/code`
- **GitHub repos**: `~/code/github`
- **GitLab repos**: `~/code/gitlab`
- **Forks**: `~/code/forks`
- **Work repos**: `~/code/work`

## Infrastructure as Code

- **Terraform**: `~/infrastructure/terraform/` (organized by provider/project)
- **Ansible**: `~/infrastructure/ansible/` (playbooks, roles, inventories)
- **Kubernetes manifests**: `~/code/github/homelab-manifests/` (ArgoCD-managed)
- **Packer templates**: `~/infrastructure/packer/`

## Programs Organization

External tools and programs cloned from GitHub go in `~/opt`. Alex keeps `~/code` for his own projects only.

## Scripts Organization

System scripts are located in `~/bin` with organized subdirectories for:
- System administration and maintenance
- Container management helpers
- Backup automation
- Network diagnostics
- GPU/CUDA management

After adding scripts, push to GitHub.

## Backup Workflows

- **Backup scripts**: Located in `~/bin/backup/`
- **NAS backups**: Primary target at 192.168.1.50 via NFS (`/mnt/nas/backups/`)
- **Cloud backups**: Backblaze B2 for critical data (restic-based)
- **Automated backups**: systemd timers for scheduled jobs
- **Database dumps**: Cron jobs for Postgres/MySQL containers → NAS

## AI-Specific File Conventions

When working in repositories, handle these directories by purpose:

- **`task.md`**: Defines tasks for the AI agent to complete
- **`context.md`** or **`/context/`**: Provides project-specific context
- **`/for-ai/`**: Files intended to be parsed and processed by the AI agent
- **`/from-ai/`**: Directory where the AI agent should place generated outputs
