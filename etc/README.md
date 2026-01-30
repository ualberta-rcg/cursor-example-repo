# System /etc

Repo `etc/` is copied into **`/etc/`** on the target. The workflow runs in the Actions workspace (clone) and copies things into place.

- `etc/nginx/` → `/etc/nginx/` (dummy nginx.conf included)
- `etc/ssl/` → `/etc/ssl/`
- `etc/sysctl.d/` → `/etc/sysctl.d/`

Add or edit files under these dirs; push to deploy.
