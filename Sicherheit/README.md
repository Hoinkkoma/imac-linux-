# 🔒 Sicherheit

Sicherheitsregeln für einen kleinen, remote verwalteten Server.

## SSH

- Schlüssel statt Passwörter für Automatisierung verwenden.
- Kein ungeschütztes Root-Login erlauben.
- Zugriff möglichst auf das benötigte Netz begrenzen.
- Logs regelmäßig prüfen.

```bash
ss -lntp
journalctl -u ssh --no-pager -n 100
```

## Niemals committen

- private SSH-Schlüssel
- API-Tokens und Passwörter
- Tailscale Auth Keys
- Cookies und Sessiondaten
- `.env`-Dateien mit Geheimnissen
- öffentliche IPs oder private Netzdetails, wenn sie nicht nötig sind

## Updates

```bash
sudo apt update
apt list --upgradable
```

Updates zuerst auf Auswirkungen prüfen. Nach Kernel- oder Netzwerkänderungen einen kontrollierten Neustart und Funktionstest einplanen.

## Referenz

Die ausführliche bestehende Sicherheitsdokumentation liegt weiterhin unter [`security/README.md`](../security/README.md).
