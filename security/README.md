# Sicherheit

Sicherheit darf nicht zugunsten von Bequemlichkeit abgeschaltet werden.

## SSH und Netzwerk

- Schlüssel statt Passwörter für Automatisierung
- kein ungeschütztes Root-Login
- Firewall-Regeln auf benötigte Netze begrenzen
- Logs regelmäßig prüfen
- nicht benötigte Ports nicht veröffentlichen

```bash
ss -lntp
journalctl -u ssh --no-pager -n 100
ss -lntup
```

## Secrets

Nie committen: private SSH-Keys, API-Tokens, Passwörter, Tailscale Auth Keys, Cookies, Sessiondaten oder geheime `.env`-Dateien. Das Repository ist Dokumentation und ersetzt kein System-Backup.

## Updates

```bash
apt update
apt list --upgradable
```

Vor produktiven Änderungen Auswirkungen prüfen und nach Kernel-/Netzwerkänderungen einen kontrollierten Neustart planen.
