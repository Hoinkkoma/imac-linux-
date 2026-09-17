# Scripts

Kleine, nachvollziehbare Hilfsskripte für iMac und Homelab.

## Regeln

Scripts sollen, wenn passend, `set -euo pipefail` verwenden, keine Geheimnisse enthalten, vor destruktiven Änderungen warnen, Statusmeldungen ausgeben und möglichst idempotent sein.

Geplante Scripts: `imac-dashboard.sh`, `server-health.sh`, `check-services.sh`.

## Beispiel

```bash
#!/bin/bash
set -euo pipefail
printf '=== %s ===\n' "$(hostname)"
printf 'IP: %s\n' "$(hostname -I | awk '{print $1}')"
printf 'Uptime: %s\n' "$(uptime -p)"
printf '\nRAM:\n'
free -h
printf '\nDisk:\n'
df -h /
printf '\nFailed services:\n'
systemctl --failed --no-pager || true
```
