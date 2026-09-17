# Netzwerk

Private Netzwerkadressen werden in diesem Repository nicht veröffentlicht. Die konkreten Werte gehören in eine lokale, nicht versionierte Notiz oder in einen sicheren Passwort-/Dokumentationsspeicher.

## iMac

| Parameter | Wert |
|---|---|
| Interface | `enp2s0` |
| IPv4 | lokal prüfen, nicht öffentlich dokumentieren |
| MAC | lokal prüfen, nicht öffentlich dokumentieren |
| Hostname | `debian-it` |

## LXC-Netz

Die LXC-Bridge und ihre private Adresse werden nur lokal dokumentiert. Prüfen mit:

```bash
ip addr show lxcbr0
```

## Homelab / Tailscale

Die konkreten Tailscale-Adressen der Homelab-Systeme werden nicht im öffentlichen Repository gespeichert. Vor Änderungen lokal mit `tailscale status` und `tailscale ip -4` bestätigen.

## Netzwerkdiagnose

```bash
ip addr
ip route
ping -c 3 <lokales-gateway>
ss -lntup
```

## Tailscale-Diagnose

Auf einem System mit Tailscale:

```bash
tailscale status
tailscale ip -4
tailscale netcheck
```

Vor öffentlichen Portweiterleitungen prüfen, ob der Zugriff sicher über das private Overlay-Netzwerk gelöst werden kann.
