# 🌐 Netzwerk

Dokumentation der Netzwerk-Anbindung des iMac5,1 im Homelab.

## Basisdaten

| Parameter | Wert |
|---|---|
| Interface | `enp2s0` |
| Hostname | `debian-it` |
| IPv4 | lokal prüfen, nicht öffentlich dokumentieren |
| MAC | lokal prüfen, nicht öffentlich dokumentieren |

## Bereiche

- Ethernet und lokale Erreichbarkeit
- optionale LXC-Bridge `lxcbr0`
- Tailscale als privates Overlay-Netzwerk
- Netzwerkdiagnose und offene Listener

## Diagnose

```bash
ip addr
ip route
ping -c 3 <lokales-gateway>
ss -lntup

# Falls Tailscale eingesetzt wird
tailscale status
tailscale ip -4
tailscale netcheck
```

Vor öffentlichen Portweiterleitungen prüfen, ob der Zugriff sicher über das private Overlay-Netzwerk gelöst werden kann.
