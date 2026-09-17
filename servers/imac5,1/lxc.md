# LXC – iMac5,1

Dokumentiert wurden `lxc.service`, `lxc-net.service`, `lxcfs.service` und die Bridge `lxcbr0` mit `10.0.3.1/24`.

```bash
systemctl status lxcfs
systemctl status lxc-net
ip addr show lxcbr0
lxc-ls -f
```

Der iMac besitzt nur 2 GB RAM. Container daher klein planen und nur wirklich benötigte Dienste betreiben.

Vor einer Deinstallation:

```bash
systemctl list-units --type=service | grep -E 'lxc|lxcfs'
lxc-ls -f
```

Bestehende Management-Funktionen dürfen nicht versehentlich entfernt werden.
