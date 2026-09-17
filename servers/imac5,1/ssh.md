# SSH – iMac5,1

## Status

```bash
systemctl status ssh
ss -lntp | grep ':22'
ssh it@192.168.80.138
```

Für Benutzer `it` wurde ein ED25519-Schlüsselpaar dokumentiert:

```text
/home/it/.ssh/id_ed25519
/home/it/.ssh/id_ed25519.pub
```

```bash
ssh-keygen -t ed25519
ls -la ~/.ssh
ssh-keygen -lf ~/.ssh/id_ed25519.pub
```

## Grundsätze

- keine Passwörter in Scripts speichern
- eigene Schlüssel für Automatisierung verwenden
- bei Monitoring `BatchMode=yes` einsetzen
- Host-Key-Prüfung nicht mit `StrictHostKeyChecking=no` abschalten
- Root-SSH nur mit klarer Sicherheitsbegründung freigeben
