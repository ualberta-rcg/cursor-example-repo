# cursor-example-repo

This repo is for cursor to do stuff in.

## System layout and deployment

Repo root can have **`etc/`**, **`opt/`**, **`home/`**, etc. The workflow clones in the Actions workspace and copies each root dir’s **contents** into the same path on the system.

### Layout

| Repo path | Deployed to |
|-----------|-------------|
| `etc/*` | `/etc/` |
| `opt/*` | `/opt/` |
| `home/*` | `/home/` |

Add a root dir (e.g. `home/`) and put files in it; the workflow runs `cp -r home/*` into `/home/`. Only roots that exist in the repo are deployed.

### Workflow

- **File:** `.github/workflows/deploy-cursor-example-repo.yml`
- **Triggers:** Push to `main` when `opt/**`, `etc/**`, `home/**`, or the workflow file changes; or run manually (workflow_dispatch).
- **Runner:** `self-hosted` with **sudo**. For each root (`etc`, `opt`, `home`), copies that dir’s contents into the same path, backs up existing targets, sets root ownership and permissions on copied items only.
- **Manual run:** Optional branch, backup existing (yes/no), and confirm deployment.

### Adding files

1. Put files under `etc/`, `opt/`, or `home/` (and add `home/` at repo root if you want `/home` deployed).
2. Commit and push to `main` (or run the workflow manually).
3. Workflow deploys each root’s contents into `/etc`, `/opt`, `/home` on the self-hosted runner.
