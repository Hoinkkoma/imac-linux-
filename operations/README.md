# Sicherheit

Der iMac ist eine alte Maschine mit kleinem Ressourcenbudget. Genau deshalb ist Sicherheit hier keine Frage von „glaub ich mach ich mal schnell“ – sondern ein echtes Grundprinzip. Kein System ist automatisch sicher nur weil es privat ist.

## SSH

Empfehlungen:

- Schlüssel statt Passwörter für Automatisierung
- kein ungeschütztes Root-Login
- Firewall-Regeln möglichst auf die benötigten Netze begrenzen
- Logs regelmäßig prüfen

Prüfen:

```bash
ss -lntp
journalctl -u ssh --no-pager -n 100
```

## Netzwerkexposition

Nicht benötigte Ports sollten nicht offen sein.

```bash
ss -lntup
```

Jeder Listener sollte zu einer klar dokumentierten Funktion gehören. Wenn das nicht der Fall ist, ist man im Zweifel schon zu weit gegangen.

## Secrets

Nie in Git committen:

- private SSH-Keys
- API-Tokens
- Passwörter
- Tailscale Auth Keys
- Cookies / Sessiondaten
- `.env` mit Geheimnissen

Empfohlene `.gitignore`-Einträge:

```gitignore
.env
*.key
*.pem
id_rsa
id_ed25519
id_ed25519.pub
secrets/
credentials/
```

Der öffentliche SSH-Key darf dokumentiert werden. Der private Schlüssel nicht.

## Updates

Vor produktiven Änderungen:

```bash
apt update
apt list --upgradable
```

Updates immer erst auf Verfügbarkeit und mögliche Auswirkungen prüfen. Nach Kernel- oder Netzwerkänderungen einen kontrollierten Neustart einplanen.

## Backup

Konfigurationsdateien und wichtige Einstellungen sollten versioniert oder anderweitig gesichert werden. Das Git-Repository ist Dokumentation, aber kein Ersatz für ein ernsthaftes Backup der Systeme.

Bei Homelab-Setups gilt: Das Risiko entsteht oft nicht durch einen wilden Ausfall, sondern durch das „Ach, das war eh nur eine kleine Änderung“-Problem.
