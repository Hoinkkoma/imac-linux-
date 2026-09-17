# Apple iMac5,1 – Lightweight Debian Server

Der iMac5,1 aus dem Jahr 2006 ist hier nicht als Retro-Desktop gedacht, sondern als kleiner, effizienter Linux-Server. Das ist ein klassischer „alte Hardware, neue Aufgabe“-Fall: wenig RAM, wenig Power, aber trotzdem nützlich genug für SSH, Monitoring, Statusanzeige und kleine Dienste.

## Ziel

Der Server soll möglichst schlank laufen:

- keine komplette Desktop-Umgebung
- keine unnötigen Hintergrunddienste
- Remote-Administration statt lokalem Desktopbetrieb
- niedriger RAM-Verbrauch
- möglichst wenig Ballast, aber genug Funktionen für das Homelab

## Hardware

| Komponente | Wert |
|---|---|
| Modell | Apple iMac5,1 |
| CPU | Intel Core 2 Duo T7400 @ 2.16 GHz |
| RAM | 2 GB DDR2-667 (2 × 1 GB) |
| DMI-Maximum | 4 GB |
| Disk | ST3250824AS_Q, ca. 232.9 GiB |
| Architektur | x86_64 |
| Netzwerk | Ethernet über `enp2s0` |
| MAC | nicht öffentlich dokumentieren |
| Hostname | `debian-it` |
| LAN-IP | nicht öffentlich dokumentieren |

## Betriebssystem

- Debian GNU/Linux 11 (Bullseye)
- Kernel: `5.10.0-32-amd64`
- Target: `multi-user.target`

> Das ist der zuletzt dokumentierte Stand. Vor einer Änderung immer kurz mit `hostnamectl`, `uname -a`, `free -h`, `lsblk` und `ip addr` prüfen.

## Rollen

Der iMac ist vorgesehen für:

- SSH-Fernverwaltung
- Cockpit-Webverwaltung
- leichte Systemdienste
- Wake-on-LAN
- optionale LXC-Nutzung
- lokales Statusdisplay „DIE SCHWARZE TAFEL“
- später: Anzeige des Zustands weiterer Homelab-Systeme

## Grundsatz

Der Server soll grundsätzlich so wenig wie möglich für sich selbst verbrauchen. Deshalb werden Desktop-, Multimedia- und Consumer-Dienste nur dann behalten, wenn sie wirklich gebraucht werden.

So einfach wie möglich, aber nicht zu einfach.
