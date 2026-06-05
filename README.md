# rmctl (rmd)

CLI tool for managing RapidMiner AI Hub with Docker Compose.

## Setup

```bash
# 1. Install rmctl
./install.sh
source /etc/environment

# 2. Install dependencies (Docker, zip/unzip, wget, easy-rsa, yq)
rmd tools

# 3. Configure settings (license, hostname, proxy, language, etc.)
rmd conf

# 4. Create template & deploy
rmd install <version>          # e.g. rmd install 2025.1.1 max y
rmd deploy                     # e.g. rmd deploy 2025.1.1-max

# 5. Start (first time)
rmd up init

# 6. Check status
rmd status
```

## Upgrade

```bash
rmd install <new_version>          # e.g. rmd install 2026.0.0 max y
rmd upgrade                        # e.g. rmd upgrade 2026.0.0-max
rmd up init
```

## Commands

| Command | Description |
|---------|-------------|
| `rmd version` | Show version |
| `rmd install <version> [profile] [y]` | Create template (profile: min/max/default, SSL auto for 2025+) |
| `rmd deploy <template>` | Deploy |
| `rmd upgrade <template>` | Upgrade (PG migration auto-supported) |
| `rmd up [init/list/service]` | Start containers (init for first time, service for individual) |
| `rmd down [list/service]` | Stop containers (service for individual) |
| `rmd start [service]` | Start containers |
| `rmd stop [service]` | Stop containers |
| `rmd restart [service]` | Restart containers |
| `rmd reup [service]` | Recreate containers |
| `rmd status` | Show status |
| `rmd logs [wso] [keyword]` | Show logs (w:wait, s:search, o:file output, combinable) |
| `rmd ssl` | Enable SSL |
| `rmd backup [restore]` | Backup/Restore |
| `rmd snapshot [restore]` | Snapshot/Restore |
| `rmd rollback` | Restore from backup |
| `rmd pgmigrate [dump/restore]` | PostgreSQL migration (14→17) |
| `rmd clean [i]` | Delete all Docker resources (i includes images) |
| `rmd tools [rm]` | Manage dependencies (rm to uninstall) |
| `rmd proxy` | Proxy settings |
| `rmd conf` | Edit settings |
| `rmd update` | Apply conf settings to deploy .env |
| `rmd undeploy` | Undeploy |
| `rmd uninstall [template]` | Delete template |
| `rmd list [t/b/s/i/p/v]` | List (t:templates, b:backups, s:snapshots, i:images, p:services, v:volumes) |
| `rmd file [list/e/d/filename]` | Deploy file operations (list:show, e:edit .env, d:edit docker-compose.yml) |
| `rmd pull` | Pull images |
| `rmd help` | Show help |

## Options

- `rmd -y <command>` — Non-interactive mode (auto-approve all confirmations)
