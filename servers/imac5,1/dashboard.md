# DIE SCHWARZE TAFEL

## Konzept

Das integrierte iMac-Display wird als ressourcensparende technische Statusanzeige verwendet, nicht als normaler Desktop.

Lokale Daten: Hostname, IP, Datum, Uhrzeit, CPU-Last, RAM, Disk, Uptime, SSH-, Cockpit- und Wake-on-LAN-Status.

Später zusätzlich: Proxmox, Debian Monitoring, Docker, Grafana, Prometheus, Loki, Uptime Kuma, Jellyfin, Vaultwarden und Ollama.

`cmatrix` ist als lokales Basiselement unter `/usr/bin/cmatrix` dokumentiert.

## Systemd-Konzept

Für eine persistente Anzeige kann ein dedizierter Service auf `tty2` verwendet werden. `tty1` bleibt als Wartungskonsole verfügbar. Nicht gleichzeitig `getty@tty1` und Dashboard auf derselben Konsole betreiben, ohne die Auswirkungen zu prüfen.

Daten können per SSH, `curl`, Prometheus HTTP API oder einfachen TCP-/HTTP-Checks gesammelt werden.

Das Dashboard darf keine Tokens, Passwörter oder privaten Schlüssel anzeigen.
