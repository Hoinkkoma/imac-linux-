# Homelab Documentation

Das hier ist meine kleine, möglichst ehrliche Dokumentation für ein privates Homelab mit Fokus auf einen älteren iMac als Linux-Server, Proxmox, Tailscale und ein paar zentralen Diensten im Keller/Heimnetzwerk.

Ich schreibe das nicht als perfekt dokumentiertes Produktionssystem, sondern als laufende Sammlung von Dingen, die ich tatsächlich geprüft habe, was geplant ist und was vor Änderungen noch einmal sauber überprüft werden sollte.

## Überblick

| System | Funktion | Status |
|---|---|---|
| iMac5,1 | Lightweight Debian Server / Statusanzeige | In Entwicklung |
| Proxmox `pve` | Virtualisierung / Container / Docker | Produktiv |
| Debian Monitoring Server | Monitoring, Homepage und zentrale Dienste | Produktiv |

## Grundidee

Dieses Projekt ist bewusst praktisch gehalten:

- alte Hardware wiederverwenden
- Ressourcen sparen statt fancy Desktop-Gedöns
- klare Trennung zwischen „bestätigt“, „geplant“ und „prüfen“
- alles dokumentieren, damit man später nicht im Dunkeln steht

## Dokumentationsprinzip

- **bestätigt**: Der Zustand wurde im Verlauf des Projekts tatsächlich geprüft oder als konfiguriert dokumentiert.
- **geplant**: Das ist der gewünschte Zustand, aber noch nicht vollständig umgesetzt.
- **prüfen**: Das war einmal ein Stand, aber vor Änderungen unbedingt erneut kontrollieren.

## Inhaltsverzeichnis

- [iMac5,1](servers/imac5,1/README.md)
- [iMac Installation](servers/imac5,1/installation.md)
- [iMac Optimierung](servers/imac5,1/optimization.md)
- [iMac Dienste](servers/imac5,1/services.md)
- [iMac SSH](servers/imac5,1/ssh.md)
- [Wake-on-LAN](servers/imac5,1/wake-on-lan.md)
- [LXC](servers/imac5,1/lxc.md)
- [DIE SCHWARZE TAFEL](servers/imac5,1/dashboard.md)
- [Proxmox](servers/proxmox/README.md)
- [Monitoring](servers/monitoring/README.md)
- [Netzwerk](network/README.md)
- [Sicherheit](security/README.md)
- [Betrieb und Wartung](operations/README.md)
- [Scripts](scripts/README.md)
- [Changelog](CHANGELOG.md)

## Warum das alles?

Der iMac ist nicht der übliche „schöner Rechner“, sondern eher ein leiser Hintergrundarbeiter im Heimnetz. Er soll:

- stabil laufen
- wenig RAM fressen
- fernadministisch nutzbar sein
- als Statusanzeige dienen
- das Homelab sauber mit kleinen Services unterstützen

Wenn etwas hier nicht perfekt ist, ist das okay. Das Projekt soll eher nützlich und verständlich sein als akademisch sauber.

## Hinweis zur praktischen Nutzung

Vor größeren Änderungen immer kurz prüfen:

```bash
hostnamectl
uname -a
free -h
lsblk
ip addr
systemctl --failed
```

Wenn man etwas im System ändert, sollte man nicht blind nach „glaub ich ist das ok" handeln. Hier gilt: kurz prüfen, dokumentieren, dann ändern.
