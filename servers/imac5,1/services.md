# Dienste – iMac5,1

| Funktion | Zweck | Port / Hinweis |
|---|---|---|
| SSH | Remote-Administration | TCP 22 |
| Cockpit | Webverwaltung | TCP 9090, HTTPS |
| Nginx | optionaler Webserver | projektspezifisch |
| smartd | HDD-SMART-Überwachung | kein externer Port |
| cron | zeitgesteuerte Aufgaben | kein externer Port |
| rsyslog | lokale Logs | kein externer Port |
| systemd-timesyncd | Zeitsynchronisation | kein eigener Listener |

Dokumentiert entfernt/deaktiviert: Bluetooth, ofono, dundee, Avahi, ModemManager, PackageKit, Exim4, rtkit, LightDM sowie verschiedene Desktop-/Multimedia-Reste.

Vor Netzwerkbereinigung:

```bash
systemctl is-active NetworkManager
systemctl is-enabled NetworkManager
nmcli device status
ip addr
ip route
```

Tatsächlichen Zustand prüfen:

```bash
dpkg -l | grep -E 'pulseaudio|pipewire|gvfs'
ps aux | grep -E 'pulseaudio|pipewire|gvfs'
systemctl list-units --type=service --state=running
systemctl list-unit-files --state=enabled
systemctl --failed
```
