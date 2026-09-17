# 🔧 Wartung

Regelmäßige Aufgaben für den iMac5,1.

## Tägliche oder anlassbezogene Checks

- [ ] Erreichbarkeit per SSH prüfen
- [ ] Kritische Fehler prüfen: `systemctl --failed`
- [ ] Speicherplatz prüfen: `df -h`
- [ ] RAM und Last prüfen: `free -h` und `uptime`
- [ ] Netzwerk und Listener prüfen: `ip addr` und `ss -lntup`

## Vor Änderungen

```bash
sudo apt update
apt list --upgradable
hostnamectl
uname -a
```

Änderungen an Kernel, Netzwerk oder Boot-Verhalten kontrolliert durchführen und anschließend einen Neustart bzw. die betroffenen Dienste testen.

## Backup

Das Git-Repository ist Dokumentation und kein vollständiges Systembackup. Wichtige Konfigurationen, lokale Notizen und Wiederherstellungsinformationen müssen zusätzlich sicher gesichert werden.

## Weiterführend

- [Optimierung](../servers/imac5,1/optimization.md)
- [Wake-on-LAN](../servers/imac5,1/wake-on-lan.md)
- [LXC](../servers/imac5,1/lxc.md)
