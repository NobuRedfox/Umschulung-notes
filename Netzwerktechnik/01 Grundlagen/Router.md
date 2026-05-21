
> [!info]
> ## Bedeutung
> Ein Router verbindet verschiedene Netzwerke miteinander.

---

# Definition

Ein Router leitet Datenpakete zwischen verschiedenen Netzwerken weiter.

Router arbeiten mit:
- IP-Adressen
- Routingtabellen

---

# Beispiel

```text
Heimnetzwerk ---- Router ---- Internet
```

Der Router verbindet:
- das lokale Netzwerk
- das Internet

---

# Aufgabe eines Routers

Ein Router entscheidet:

```text
"Wohin soll dieses Paket geschickt werden?"
```

Dafür verwendet er eine Routingtabelle.

---

# Unterschied zwischen Switch und Router

## Switch

```text
Verbindet Geräte im selben Netzwerk
```

Arbeitet mit:
- MAC-Adressen
- Layer 2

---

## Router

```text
Verbindet verschiedene Netzwerke
```

Arbeitet mit:
- IP-Adressen
- Layer 3

---

# Beispielnetz

```text
PC ---- Router ---- Internet
```

---

## Lokales Netzwerk

```text
192.168.0.0/24
```

---

## Router-IP

```text
192.168.0.1
```

Der Router ist meistens das:

```text
Gateway
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
Sende an 192.168.0.1
```

---

# Router mit mehreren Netzwerken

Ein Router besitzt meistens mehrere Netzwerkinterfaces.

Beispiel:

```text
LAN 1 ---- Router ---- LAN 2
```

---

## Beispiel-IP-Adressen

### Linkes Netzwerk

```text
10.0.1.254
```

---

### Rechtes Netzwerk

```text
10.0.2.254
```

Der Router ist in beiden Netzwerken vorhanden.

---

# IP-Forwarding

Linux muss Routing erst erlauben.

---

## Aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

## Bedeutung

```text
Pakete zwischen Netzwerken weiterleiten
```

---

# Router in virtuellen Netzwerken

Auch Container können Router sein.

Beispiel:

```text
Apfel ---- Banane ---- Erdbeere
```

Banane arbeitet als Router.

---

# NAT und Router

Viele Router führen zusätzlich NAT aus.

Dadurch können:
- private Geräte
- eine öffentliche IP-Adresse teilen

---

# Typische Router-Aufgaben

- Routing
- NAT
- DHCP
- Firewall
- WLAN
- Portweiterleitung

---

# Linux-Befehle

## Routing anzeigen

```bash
ip route
```

---

## IP-Adressen anzeigen

```bash
ip addr
```

---

## IP-Forwarding prüfen

```bash
cat /proc/sys/net/ipv4/ip_forward
```

---

## IP-Forwarding aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

# Typische Probleme

## Kein Routing

Oft fehlt:

```text
IP-Forwarding
```

---

## Kein Internet

Mögliche Ursachen:
- Gateway falsch
- NAT fehlt
- Routingfehler

---

# Wichtige Merksätze

Ein Router verbindet verschiedene Netzwerke.

Router arbeiten mit IP-Adressen.

Router arbeiten auf Layer 3.

Ein Router verwendet Routingtabellen.

Linux benötigt IP-Forwarding für Routing.

---

# Fragen

## Wofür wird ein Router verwendet?

> [!spoiler]- Lösung anzeigen
> Ein Router verbindet verschiedene Netzwerke miteinander.

---

## Auf welchem OSI-Layer arbeitet ein Router?

> [!spoiler]- Lösung anzeigen
> Router arbeiten auf Layer 3.

---

## Welcher Linux-Befehl aktiviert Routing?

> [!spoiler]- Lösung anzeigen
> ```bash
> sysctl -w net.ipv4.ip_forward=1
> ```