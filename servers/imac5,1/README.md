# Apple iMac5,1 – Lightweight Debian Server

## Ziel

Der iMac5,1 aus dem Jahr 2006 wird als ressourcensparender Linux-Server weiterverwendet. Der Fokus liegt auf einem schlanken System ohne klassische Desktopumgebung, Fernverwaltung und niedriger RAM-Auslastung.

## Hardware

| Komponente | Wert |
|---|---|
| Modell | Apple iMac5,1 |
| CPU | Intel Core 2 Duo T7400 @ 2.16 GHz |
| RAM | 2 GB DDR2-667 (2 × 1 GB) |
| DMI-Maximum | 4 GB |
| Disk | ST3250824AS_Q, ca. 232.9 GiB |
| Architektur | x86_64 |
| Netzwerk | `enp2s0` Ethernet |
| MAC | `00:17:f2:c5:b9:e9` |
| Hostname | `debian-it` |
| LAN-IP | `192.168.80.138` |

## Betriebssystem

- Debian GNU/Linux 11 (Bullseye)
- Kernel: `5.10.0-32-amd64`
- Standard-Target: `multi-user.target`

Vor Änderungen mit `hostnamectl`, `uname -a`, `free -h`, `lsblk` und `ip addr` verifizieren.

## Rollen

SSH-Fernverwaltung, Cockpit, leichte Systemdienste, Wake-on-LAN, optionale LXC-Nutzung und das lokale Statusdisplay **DIE SCHWARZE TAFEL**.

## Grundsatz

Nicht benötigte Desktop-, Multimedia- und Consumer-Dienste werden entfernt oder deaktiviert, sofern sie nicht von einer benötigten Funktion abhängen.
