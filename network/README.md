# Netzwerk

## iMac

| Parameter | Wert |
|---|---|
| Interface | `enp2s0` |
| IPv4 | `192.168.80.138/24` |
| MAC | `00:17:f2:c5:b9:e9` |
| Hostname | `debian-it` |

## LXC und Tailscale

`lxcbr0 = 10.0.3.1/24`

| System | Tailscale |
|---|---|
| Debian Monitoring Server | `100.113.28.9` |
| Proxmox pve | `100.83.105.59` |

Vor Änderungen mit `tailscale status` bestätigen.

```bash
ip addr
ip route
ping -c 3 192.168.80.1
ss -lntup
tailscale status
tailscale ip -4
tailscale netcheck
```

Vor öffentlichen Portweiterleitungen prüfen, ob der Zugriff sicher über das private Overlay-Netz gelöst werden kann.
