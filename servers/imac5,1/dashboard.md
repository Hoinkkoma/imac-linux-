# DIE SCHWARZE TAFEL

## Konzept

Das integrierte iMac-Display wird als ressourcensparende technische Statusanzeige verwendet, nicht als normaler Desktop.

Arbeitstitel:

```text
DIE SCHWARZE TAFEL
```

## Ziele

Die Anzeige soll ohne vollständige Desktopumgebung funktionieren und möglichst wenig Ressourcen verbrauchen.

Lokale Daten:

- Hostname
- IP-Adresse aus der lokalen Systemabfrage
- Datum und Uhrzeit
- CPU-Last
- RAM-Nutzung
- Disk-Nutzung
- Uptime
- SSH-, Cockpit- und Wake-on-LAN-Status

Es werden keine festen privaten Adressen in der öffentlichen Dokumentation angezeigt.

Später zusätzlich:

- Proxmox-Erreichbarkeit
- Monitoring-Erreichbarkeit
- Docker-Containerstatus
- Grafana, Prometheus und Loki
- Uptime Kuma
- Jellyfin
- Vaultwarden
- Ollama

## Visualisierung

`cmatrix` ist als lokales Basiselement unter `/usr/bin/cmatrix` dokumentiert.

Geplantes Design:

```text
====================================================
                 DIE SCHWARZE TAFEL
====================================================

HOSTNAME        <lokaler-hostname>
IP              <lokale-adresse>

DATUM           <aktuelles-datum>
UHRZEIT         <aktuelle-uhrzeit>

CPU LOAD        ...
RAM             ...
DISK            ...
UPTIME          ...

SSH             AKTIV
COCKPIT         AKTIV
WAKE-ON-LAN     AKTIV

====================================================
```

## Systemd-Konzept

Für eine persistente Anzeige kann ein dedizierter Service auf `tty2` verwendet werden. `tty1` bleibt als Wartungskonsole verfügbar. Nicht gleichzeitig `getty@tty1` und Dashboard auf derselben Konsole betreiben, ohne die Auswirkungen zu prüfen.

Daten können per SSH, `curl`, Prometheus HTTP API oder einfachen TCP-/HTTP-Checks gesammelt werden.

Das Dashboard darf keine Tokens, Passwörter, privaten Schlüssel oder festen privaten Adressen anzeigen.
