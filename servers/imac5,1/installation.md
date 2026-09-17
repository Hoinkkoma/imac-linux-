# Installation – iMac5,1

## System prüfen

```bash
hostnamectl
cat /etc/os-release
uname -a
lscpu
free -h
lsblk
ip addr
ip route
```

Erwarteter dokumentierter Stand: Debian GNU/Linux 11 (Bullseye), Kernel `5.10.0-32-amd64`, `x86_64`.

## Server-Target

```bash
systemctl get-default
systemctl set-default multi-user.target
```

Der iMac soll ohne grafische Login-Umgebung starten. Vor jedem weiteren Purge Abhängigkeiten prüfen:

```bash
apt remove <paket>
apt autoremove --dry-run
apt autoremove --purge
```

## Netzwerk

Aktive Ethernet-Schnittstelle: `enp2s0`; dokumentierte Adresse: `192.168.80.138/24`.

```bash
ip addr show enp2s0
ip route
systemctl is-active NetworkManager
systemctl is-enabled NetworkManager
```

Netzwerkänderungen nicht blind durchführen.
