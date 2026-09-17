# 🛠️ Fehlerbehebung

Kurze Diagnosewege für typische Probleme am iMac5,1.

## Server nicht erreichbar

1. Stromversorgung und Link-LED prüfen.
2. `ping <hostname-oder-lokale-ip>` testen.
3. Lokal `ip addr` und `ip route` prüfen.
4. SSH-Status und Logs prüfen:

```bash
systemctl status ssh
journalctl -u ssh --no-pager -n 100
```

## Dienst funktioniert nicht

```bash
systemctl status <dienst>
systemctl --failed
journalctl -u <dienst> --no-pager -n 100
ss -lntup
```

## Zu wenig Ressourcen

```bash
free -h
uptime
df -h
systemd-analyze blame
```

Nicht benötigte Dienste stoppen und dauerhaft deaktivieren. Vor einer Deinstallation die Abhängigkeiten und die Dokumentation prüfen.

## Netzwerkprobleme

```bash
ip addr
ip route
ping -c 3 <gateway>
resolvectl status
```

Private Adressen und Zugangsdaten niemals in Fehlermeldungen oder Issues veröffentlichen.
