# Wake-on-LAN – iMac5,1

## Hardware-Unterstützung

Dokumentiert: `Supports Wake-on: pg`, `Wake-on: g`.

```bash
ethtool enp2s0 | grep Wake-on
ethtool -s enp2s0 wol g
```

MAC-Adresse: `00:17:f2:c5:b9:e9`.

## Persistenz

Wenn ifupdown die Schnittstelle verwaltet, kann in `/etc/network/interfaces` verwendet werden:

```text
post-up ethtool -s enp2s0 wol g
```

Bei NetworkManager ist die Persistenz dort passend einzurichten. Ein erfolgreicher `wol g`-Status garantiert nicht jeden ausgeschalteten Power-State.

## Test

Sauber herunterfahren, Magic Packet senden und anschließend die Erreichbarkeit mit SSH prüfen.
