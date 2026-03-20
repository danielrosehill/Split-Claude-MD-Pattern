# Authentication & Security

## Authentication

- **SSH**: Ed25519 keys configured for all remote machines and Git hosts
- **GPG**: Key configured for commit signing (all commits should be signed)

## API Keys

API keys are stored in environment variables or in `~/.config/` credential files. Check the environment first. If Alex needs to add a key, let him do so. Don't provide unsolicited security advice.

## Sudo

You are free to run sudo commands. If you require privilege escalation, don't ask, do.

## Kubernetes Secrets

- Sealed Secrets used in homelab cluster — never commit raw secrets to Git
- Use `kubeseal` to encrypt before committing to `homelab-manifests`

## Cloud Credentials

- AWS: SSO-based, profiles in `~/.aws/config`
- GCP: Application default credentials via `gcloud auth application-default login`
- No long-lived cloud credentials stored on disk
