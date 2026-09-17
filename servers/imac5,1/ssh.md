# SSH – iMac5,1

SSH ist eine der wichtigsten Funktionen für den ganzen Aufbau. Ohne SSH wäre der iMac nur ein lokaler Kasten mit ein bisschen Technik auf der Platte. Mit SSH wird er ein echtes Server-Objekt im Heimnetz.

## Status prüfen

```bash
systemctl status ssh
ss -lntp | grep ':22'
```

SSH wurde als laufender Dienst auf Port 22 dokumentiert.

## Verbindung aus dem LAN

Die konkrete Zieladresse wird hier absichtlich nicht veröffentlicht. Verwende beim Zugriff den lokalen Hostnamen oder eine private Adresse aus deiner eigenen Umgebung:

```bash
ssh it@<imac-hostname-oder-private-ip>
```

## SSH-Key

Für den Benutzer `it` wurde ein ED25519-Schlüsselpaar dokumentiert:

```text
/home/it/.ssh/id_ed25519
/home/it/.ssh/id_ed25519.pub
```

Erzeugen:

```bash
ssh-keygen -t ed25519
```

Prüfen:

```bash
ls -la ~/.ssh
ssh-keygen -lf ~/.ssh/id_ed25519.pub
```

## Public Key verteilen

Der Public Key wird auf das Zielsystem verteilt, nicht auf dem iMac selbst:

```bash
ssh-copy-id <user>@<ziel>
```

Oder ganz manuell:

```bash
cat ~/.ssh/id_ed25519.pub | ssh <user>@<ziel> 'mkdir -p ~/.ssh && chmod 700 ~/.ssh && cat >> ~/.ssh/authorized_keys && chmod 600 ~/.ssh/authorized_keys'
```

## Ein paar gute Gewohnheiten

- keine Passwörter in Scripts speichern
- für Automatisierung eigene Schlüssel verwenden
- bei Monitoring-SSH `BatchMode=yes` nutzen
- Host Keys nicht mit `StrictHostKeyChecking=no` deaktivieren, außer in bewusst isolierten Tests
- Root-SSH nur nach Prüfung und aus nachvollziehbarer Sicherheitslogik freigeben

Kurz gesagt: SSH ist genial, aber nur dann, wenn man es sauber und verantwortungsvoll einrichtet.
