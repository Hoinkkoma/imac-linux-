# 🐧 Debian-System

Zentrale Dokumentation für das schlanke Debian-System auf dem Apple iMac5,1.

## Systemstand

- Debian GNU/Linux 11 (Bullseye)
- Kernel `5.10.0-32-amd64` (zuletzt dokumentiert)
- Architektur `x86_64`
- Ziel `multi-user.target`
- Hostname `debian-it`
- Netzwerkinterface `enp2s0`

Vor jeder Änderung den tatsächlichen Zustand prüfen:

```bash
hostnamectl
uname -a
free -h
lsblk
ip addr
```

## Dokumentation

- [Installation](../servers/imac5,1/installation.md)
- [Optimierung](../servers/imac5,1/optimization.md)
- [Dienste](../servers/imac5,1/services.md)
- [SSH](../servers/imac5,1/ssh.md)
- [LXC](../servers/imac5,1/lxc.md)
- [Statusdisplay](../servers/imac5,1/dashboard.md)

## Ressourcenprinzip

Der iMac hat nur 2 GB RAM. Desktop-, Multimedia- und Consumer-Dienste werden deshalb nur installiert oder aktiviert, wenn sie für das Homelab wirklich benötigt werden.
