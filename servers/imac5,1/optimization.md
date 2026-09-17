# Systemoptimierung – iMac5,1

## Sysctl-Memory-Tuning

Datei `/etc/sysctl.d/99-memory.conf`:

```text
vm.swappiness=10
vm.vfs_cache_pressure=50
vm.dirty_background_ratio=5
vm.dirty_ratio=10
```

Anwenden und prüfen:

```bash
sysctl --system
sysctl vm.swappiness vm.vfs_cache_pressure vm.dirty_background_ratio vm.dirty_ratio
```

## ZRAM

Dokumentiert ist eine ZRAM-Größe von ungefähr 75 % des verfügbaren RAM:

```text
/etc/default/zramswap
PERCENT=75
```

```bash
zramctl
swapon --show
```

Dokumentierter Zustand: `/dev/zram0` ca. 1.4G, Priorität 100; `/dev/sda3` ca. 977M, Priorität -2; Kompression `lz4`.

## Diagnose

```bash
ps aux --sort=-%mem | head -20
ps aux --sort=-%cpu | head -20
systemctl list-units --type=service --state=running
systemctl --failed
```

Nicht pauschal löschen. Vor jeder Entfernung Abhängigkeiten, Bootbedarf, Socket-Aktivierung und Netzwerkauswirkungen prüfen.
