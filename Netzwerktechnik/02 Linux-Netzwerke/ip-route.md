
> [!info]
> ## Bedeutung
> `ip route`
>
> zeigt und verwaltet Routingtabellen unter Linux.

---

# Definition

Der Befehl:

```bash
ip route
```

zeigt,
wie Pakete durch Netzwerke weitergeleitet werden.

Die Ausgabe enthält die:

```text
Routingtabelle
```

---

# Kurzform

```bash
ip r
```

---

# Routingtabelle

Eine Routingtabelle enthält Regeln:

```text
Welches Netzwerk ist über welches Interface erreichbar?
```

---

# Beispiel

```bash
ip route
```

---

# Beispielausgabe

```text
default via 192.168.0.1 dev eth0
192.168.0.0/24 dev eth0
```

---

# Erklärung

## default via

```text
Standardroute
```

Bedeutung:

```text
Wenn Ziel unbekannt:
schicke das Paket an 192.168.0.1
```

---

## dev eth0

```text
Benutze Interface eth0
```

---

## Direkt verbundenes Netzwerk

```text
192.168.0.0/24 dev eth0
```

Bedeutung:

```text
Dieses Netzwerk ist direkt erreichbar.
```

---

# Gateway

Das Gateway ist meistens:
- der Router
- die Standardroute

Beispiel:

```text
192.168.0.1
```

---

# Default Route setzen

```bash
ip route add default via 192.168.0.1
```

---

# Bedeutung

```text
Unbekannte Ziele an 192.168.0.1 schicken
```

---

# Route hinzufügen

## Beispiel

```bash
ip route add 10.0.2.0/24 via 10.0.1.254
```

---

# Bedeutung

```text
Um 10.0.2.0/24 zu erreichen,
verwende 10.0.1.254 als Zwischenstation.
```

---

# Route löschen

```bash
ip route del 10.0.2.0/24
```

---

# Routing in virtuellen Netzwerken

## Beispiel

```text
Apfel ---- Banane ---- Erdbeere
```

Banane arbeitet als Router.

---

## Route setzen

```bash
ip netns exec Apfel ip route add default via 10.0.1.254
```

Apfel sendet unbekannte Netzwerke an Banane.

---

# IPv6-Routing

## IPv6-Routen anzeigen

```bash
ip -6 route
```

---

# Routing und IP-Forwarding

Damit Linux als Router arbeitet:

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

# Typische Routingarten

## Direkt verbunden

```text
Netzwerk direkt erreichbar
```

---

## Default Route

```text
Alles an den Router schicken
```

---

## Statische Route

```text
Bestimmtes Netzwerk über festen Router erreichen
```

---

# Typische Probleme

## Keine Default Route

Dann funktioniert oft:
- kein Internet
- nur lokales Netzwerk

---

## Falsches Gateway

Pakete landen im falschen Netzwerk.

---

## Fehlendes IP-Forwarding

Linux arbeitet nicht als Router.

---

# Linux-Befehle

## Routingtabelle anzeigen

```bash
ip route
```

---

## Kurzform

```bash
ip r
```

---

## Default Route hinzufügen

```bash
ip route add default via 192.168.0.1
```

---

## Route hinzufügen

```bash
ip route add 10.0.2.0/24 via 10.0.1.254
```

---

## Route löschen

```bash
ip route del 10.0.2.0/24
```

---

# Unterschied zwischen ip addr und ip route

## ip addr

```text
Zeigt IP-Adressen
```

---

## ip route

```text
Zeigt Routingwege
```

---

# Wichtige Merksätze

`ip route` zeigt die Routingtabelle an.

Die Routingtabelle bestimmt,
wohin Pakete geschickt werden.

Die Default Route zeigt meistens auf den Router.

`ip r` ist die Kurzform von `ip route`.

Routing arbeitet auf Layer 3.

---

# Fragen

## Wofür wird `ip route` verwendet?

> [!spoiler]- Lösung anzeigen
> `ip route` zeigt und verwaltet Routingtabellen unter Linux.

---

## Was bedeutet `default via`?

> [!spoiler]- Lösung anzeigen
> Unbekannte Ziele sollen an den angegebenen Router geschickt werden.

---

## Wie lautet die Kurzform von `ip route`?

> [!spoiler]- Lösung anzeigen
> ```bash
> ip r
> ```