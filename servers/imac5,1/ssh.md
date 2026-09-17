# Dienste – iMac5,1

Das System ist bewusst klein gehalten. Der iMac soll nicht zu einem „Diensteschrank voller Zufallssoftware“ werden. Deshalb ist der Sinn hinter den Services klar: ein paar wichtige Funktionen, keine unnötige Betriebsamkeit.

## Kerndienste / Funktionen

| Funktion | Zweck | Port / Hinweis |
|---|---|---|
| SSH | Remote-Administration | TCP 22 |
| Cockpit | Webverwaltung | TCP 9090, HTTPS |
| Nginx | optionaler Webserver | projektspezifisch |
| smartd | HDD-SMART-Überwachung | kein externer Port |
| cron | zeitgesteuerte Aufgaben | kein externer Port |
| rsyslog | lokale Logs | kein externer Port |
| systemd-timesyncd | Zeitsynchronisation | kein eigener Listener erforderlich |

## Bereits entfernt oder deaktiviert

Im Verlauf des Projekts wurden unter anderem diese Dinge beseitigt oder deaktiviert:

- Bluetooth
- ofono
- dundee
- Avahi
- ModemManager
- PackageKit
- Exim4
- rtkit
- LightDM
- verschiedene LXDE/Openbox-Reste
- mehrere nicht mehr benötigte Desktop-/Multimedia-Pakete

Das ist kein „alles weg damit“-Mantra, sondern eher die logische Folge aus dem Wunsch, ein kleines, stabiles Server-Setup zu bauen.

## Vorsicht bei Netzwerkdiensten

Ein wichtiger Hinweis: Es gab schon einmal einen Zwischenstand, in dem `NetworkManager` aktiv war, während gleichzeitig `ifupdown`-Konfigurationen benutzt wurden. Das ist ein klassischer Bereich, in dem man mit gezielten Prüfungen aufpassen muss.

```bash
systemctl is-active NetworkManager
systemctl is-enabled NetworkManager
nmcli device status
ip addr
ip route
```

## Audio und Desktop-Reste

Manchmal bleiben bei einem Serverumbau noch Dinge zurück, die man nicht sofort als problematisch erkennt. Zum Beispiel PulseAudio, PipeWire oder GVFS.

Prüfen:

```bash
dpkg -l | grep -E 'pulseaudio|pipewire|gvfs'
ps aux | grep -E 'pulseaudio|pipewire|gvfs'
```

Wenn man schon etwas bereinigt hat, ist genau dieses Nachprüfen wichtig, damit man keine „ghost packages“ oder Prozesse im Hintergrund übrig lässt.

## Laufende Dienste vollständig prüfen

```bash
systemctl list-units --type=service --state=running
systemctl list-unit-files --state=enabled
systemctl --failed
```

Je weniger Ballast, desto leichter wird die Fehlersuche später.
