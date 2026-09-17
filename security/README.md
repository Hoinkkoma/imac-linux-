# Netzwerk

Das Heimnetz ist hier nicht kompliziert, aber es ist trotzdem wichtig, dass man sich die Grunddaten aufschreibt. Gerade bei alten Hardware-Setups ist das ein echter Lebensretter.

## iMac

| Parameter | Wert |
|---|---|
| Interface | `enp2s0` |
| IPv4 | `192.168.80.138/24` |
| MAC | `00:17:f2:c5:b9:e9` |
| Hostname | `debian-it` |

## LXC-Netz

Dokumentiert:

```text
lxcbr0 = 10.0.3.1/24
```

## Homelab / Tailscale

Im Projekt wurden folgende Tailscale-Adressen für bestehende Homelab-Systeme dokumentiert:

```text
Debian Monitoring Server   100.113.28.9
Proxmox pve                 100.83.105.59
```

Diese Werte sollten vor Änderungen immer wieder mit `tailscale status` bestätigt werden. Das ist kein Selbstzweck, sondern verhindert hektische „Warum ist das System plötzlich nicht erreichbar?“ Stunden.

## Netzwerkdiagnose

```bash
ip addr
ip route
ping -c 3 192.168.80.1
ss -lntup
```

## Tailscale-Diagnose

Auf einem System mit Tailscale:

```bash
tailscale status
tailscale ip -4
tailscale netcheck
```

## Remotezugriff

Bevor man irgendwelche öffentlichen Portweiterleitungen einrichtet, sollte man sich fragen: Ist der Zugriff vielleicht schon sauber über das private Overlay-Netzwerk möglich? Oft ist das die angenehmere und sicherere Lösung.

Das ist im Homelab-Setup meistens die bessere Wahl als sofort „öffentliche Portforwarding-Maschine“ zu werden.
