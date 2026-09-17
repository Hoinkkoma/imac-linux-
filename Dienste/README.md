# ⚙️ Dienste

Übersicht der auf dem iMac vorgesehenen Dienste. Jeder Dienst benötigt einen dokumentierten Zweck und sollte mit dem knappen Ressourcenbudget vereinbar sein.

## Vorgesehene Dienste

| Dienst | Zweck | Status |
|---|---|---|
| SSH | Remote-Administration | vorgesehen |
| Cockpit | Webverwaltung | vorgesehen |
| Wake-on-LAN | Einschalten bzw. Aufwecken | in Prüfung |
| DIE SCHWARZE TAFEL | Lokales Statusdisplay | geplant |
| LXC | Leichte isolierte Workloads | optional |
| Monitoring | Zustand weiterer Homelab-Systeme anzeigen | geplant |

## Betriebsgrundsatz

Nicht benötigte Dienste deaktivieren und nach jeder Änderung prüfen:

```bash
systemctl --type=service --state=running
ss -lntup
systemctl --failed
```

Details zu den einzelnen Komponenten stehen im Verzeichnis [`servers/imac5,1/`](../servers/imac5,1/).
