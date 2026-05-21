
> [!info]
> ## Bedeutung
> Routing = Weiterleitung von Paketen zwischen Netzwerken

---

# Definition

Routing beschreibt den Prozess,
wie Datenpakete ihren Weg durch Netzwerke finden.

Router entscheiden dabei:

```text
"Wohin soll dieses Paket geschickt werden?"
```

---

# Beispiel

```text
PC ---- Router ---- Internet
```

Wenn ein Gerät ein fremdes Netzwerk erreichen möchte,
schickt es die Pakete an den Router.

Der Router leitet sie weiter.

---

# Lokales Netzwerk

## Beispiel

```text
192.168.0.0/24
```

Geräte innerhalb desselben Netzwerks
können direkt miteinander kommunizieren.

---

# Fremdes Netzwerk

Wenn das Ziel nicht im eigenen Netzwerk liegt,
wird das Paket an das Gateway geschickt.

---

# Gateway

Das Gateway ist meistens der Router.

Beispiel:

```text
192.168.0.1
```

---

# Routingtabelle

Eine Routingtabelle enthält Regeln:

```text
Welches Netzwerk ist über welches Interface erreichbar?
```

---

# Routing anzeigen

```bash
ip route
```

oder kurz:

```bash
ip r
```

---

# Beispiel einer Routingtabelle

```text
default via 192.168.0.1 dev eth0
192.168.0.0/24 dev eth0
```

---

# Bedeutung

## default via

```text
Wenn Ziel unbekannt:
Sende Paket an 192.168.0.1
```

---

## dev eth0

```text
Benutze Netzwerkinterface eth0
```

---

# Direkt verbundenes Netzwerk

```text
192.168.0.0/24 dev eth0
```

Bedeutung:

```text
Dieses Netzwerk ist direkt erreichbar.
```

---

# Default Route

Die Default Route wird verwendet,
wenn kein genauerer Eintrag existiert.

Sie zeigt meistens auf:
- den Router
- das Gateway

---

# Beispiel mit mehreren Netzwerken

```text
LAN 1 ---- Router ---- LAN 2
```

---

## Linkes Netzwerk

```text
10.0.1.0/24
```

---

## Rechtes Netzwerk

```text
10.0.2.0/24
```

Der Router verbindet beide Netzwerke.

---

# Routing in Linux

Linux kann selbst als Router arbeiten.

Dafür benötigt man:

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

# Bedeutung von IP-Forwarding

```text
Pakete zwischen Netzwerken weiterleiten
```

Ohne IP-Forwarding:
- empfängt Linux Pakete
- leitet sie aber nicht weiter

---

# Route hinzufügen

## Beispiel

```bash
ip route add 10.0.2.0/24 via 10.0.1.254
```

Bedeutung:

```text
Um 10.0.2.0/24 zu erreichen,
nutze 10.0.1.254 als Zwischenstation.
```

---

# Routing in virtuellen Netzwerken

Auch Container können Routing verwenden.

Beispiel:

```text
Apfel ---- Banane ---- Erdbeere
```

Banane arbeitet als Router.

---

# Linux-Befehle

## Routing anzeigen

```bash
ip route
```

---

## Kurzform

```bash
ip r
```

---

## Route hinzufügen

```bash
ip route add 10.0.2.0/24 via 10.0.1.254
```

---

## Default Route setzen

```bash
ip route add default via 192.168.0.1
```

---

## IP-Forwarding aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

# Typische Probleme

## Kein Gateway gesetzt

Dann funktioniert oft:
- nur das lokale Netzwerk
- aber nicht das Internet

---

## IP-Forwarding deaktiviert

Dann arbeitet Linux nicht als Router.

---

## Falsche Routingtabelle

Pakete landen im falschen Netzwerk
oder verschwinden.

---

# Routing vs Switch

## Switch

```text
Layer 2
MAC-Adressen
gleiches Netzwerk
```

---

## Routing

```text
Layer 3
IP-Adressen
verschiedene Netzwerke
```

---

# Wichtige Merksätze

Routing leitet Pakete zwischen Netzwerken weiter.

Router arbeiten mit IP-Adressen.

Routing verwendet Routingtabellen.

Die Default Route zeigt meistens auf den Router.

Linux benötigt IP-Forwarding für Routing.

Routing arbeitet auf Layer 3.

---

# Fragen

## Was ist Routing?

> [!spoiler]- Lösung anzeigen
> Routing ist die Weiterleitung von Paketen zwischen Netzwerken.

---

## Wofür wird eine Routingtabelle verwendet?

> [!spoiler]- Lösung anzeigen
> Eine Routingtabelle bestimmt,
> wohin Pakete geschickt werden sollen.

---

## Welcher Linux-Befehl zeigt die Routingtabelle an?

> [!spoiler]- Lösung anzeigen
> ```bash
> ip route
> ```
>
> oder kurz:
>
> ```bash
> ip r
> ```