# Installation – iMac5,1

## Ausgangspunkt

Der iMac wurde in der Vergangenheit als normaler Linux-Arbeitsplatz betrieben und danach auf einen Serverbetrieb umgebaut. Das heißt: Die Installation war nicht von Anfang an „sauber wie neu“, sondern eher ein schrittweiser Umbau.

## Erstes Prüfprogramm

Vor Änderungen und vor jeder kleinen „Wartung“ sollte man kurz alles abfragen, was man als Basis braucht:

```bash
hostnamectl
cat /etc/os-release
uname -a
lscpu
free -h
lsblk
ip addr
ip route
```

Typischer dokumentierter Stand:

```text
Debian GNU/Linux 11 (bullseye)
Kernel 5.10.0-32-amd64
x86_64
```

## Server-Target statt Desktop-Login

Damit der iMac nicht mit einem grafischen Login hochfährt, sollte das Standardziel auf `multi-user.target` stehen:

```bash
systemctl get-default
systemctl set-default multi-user.target
```

Wenn man mal ein bisschen über den Tellerrand schaut: Das ist genau die richtige Entscheidung für einen Server, der nur noch Admin-Zwecken und Hintergrundfunktionen dienen soll.

## Desktop-Stack entfernen

Im Projekt wurden unter anderem LightDM und verschiedene LXDE/Openbox-Komponenten entfernt. Danach wurde `apt autoremove` genutzt, um nicht mehr benötigte Pakete zu bereinigen.

Das ist wichtig: Nicht einfach alles wegwerfen. Vor dem Purge lieber eine kleine Abhängigkeitsprüfung machen:

```bash
apt remove <paket>
apt autoremove --dry-run
```

Und erst dann wirklich bereinigen:

```bash
apt autoremove --purge
```

## Netzwerk

Aktive Schnittstelle:

```text
enp2s0
```

Dokumentierte LAN-Adresse:

```text
192.168.80.138/24
```

Vor jeder Netzwerkanpassung kurz prüfen:

```bash
ip addr show enp2s0
ip route
systemctl is-active NetworkManager
systemctl is-enabled NetworkManager
```

Das ist wichtig, weil man bei so alter Hardware schnell in einen schönen Fall von „funktioniert im Prinzip, aber plötzlich nicht mehr aus der Ferne“ gerät.

## Grundsatz

Wenn man einen alten Rechner für Serverzwecke umrüstet, sollte man nicht nur ein Paket nach dem anderen löschen. Man sollte im Kopf behalten: Das Gerät muss bleiben, erreichbar bleiben und im Ernstfall wieder sauber erreichbar sein.
