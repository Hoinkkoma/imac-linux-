# Betrieb und Wartung

## Schnellcheck

```bash
hostnamectl
uptime
free -h
df -h
ip addr
systemctl --failed
systemctl list-units --type=service --state=running
```

## Ressourcen und Festplatte

```bash
free -h
ps aux --sort=-%mem | head -20
ps aux --sort=-%cpu | head -20
iostat
smartctl -a /dev/sda
df -h
```

## Logs

```bash
journalctl -u ssh --since today
journalctl -u cockpit.socket --since today
journalctl -p warning..alert -b
```

Vor Neustart `uptime` und `systemctl --failed` prüfen. Danach SSH, Fehler und Swap kontrollieren. Bei Netzwerk- oder Bootänderungen immer eine zweite Zugriffsmöglichkeit bereithalten.

Nach relevanten Änderungen: Zustand prüfen, Dokumentation aktualisieren, Commit erstellen und pushen.
