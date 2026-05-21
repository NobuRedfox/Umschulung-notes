
> [!info]
> ## Bedeutung
> NAT = Network Address Translation

---

# Definition

NAT übersetzt private IP-Adressen in öffentliche IP-Adressen.

Dadurch können viele Geräte gemeinsam eine einzige öffentliche IP-Adresse verwenden.

---

# Warum braucht man NAT?

Private IP-Adressen sind im Internet nicht direkt erreichbar.

Beispiele für private Netzwerke:

```text
192.168.x.x
10.x.x.x
172.16.x.x - 172.31.x.x
```

Der Router übersetzt diese privaten Adressen beim Zugriff auf das Internet.

---

# Beispiel

## Zuhause

```text
Laptop:
192.168.0.15
```

---

## Öffentliche IP des Routers

```text
84.123.55.10
```

---

# Ablauf

```text
Laptop -> Router -> Internet
```

Der Router ersetzt:

```text
192.168.0.15
```

durch:

```text
84.123.55.10
```

---

# Einfacher Aufbau

```text
PC 1 ----\
PC 2 ----- Router ---- Internet
PC 3 ----/
```

Alle Geräte teilen sich die öffentliche IP-Adresse des Routers.

---

# Arten von NAT

## SNAT

```text
Source NAT
```

Die Quelladresse wird verändert.

---

## DNAT

```text
Destination NAT
```

Die Zieladresse wird verändert.

Wird oft für:
- Portweiterleitungen
- Server
- Docker

verwendet.

---

# Masquerading

Eine spezielle Form von NAT unter Linux.

Beispiel:

```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

Bedeutung:

```text
Pakete sollen über die öffentliche IP-Adresse von eth0 übersetzt werden.
```

---

# NAT unter Linux

## IP-Forwarding aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

Erlaubt Routing zwischen Netzwerken.

---

## NAT aktivieren

```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

# Beispiel mit Containern

```text
Container -> Host -> Internet
```

Der Host arbeitet als Router
und führt NAT durch.

Dadurch bekommen Container Internetzugriff.

---

# Portweiterleitung

NAT kann auch eingehende Verbindungen weiterleiten.

Beispiel:

```text
Internet -> Router -> Heimserver
```

Das nennt man:

```text
Port Forwarding
```

---

# Vorteile von NAT

- Spart öffentliche IPv4-Adressen
- Geräte im LAN sind nicht direkt sichtbar
- Viele Geräte können eine IP teilen

---

# Nachteile von NAT

- Zusätzliche Komplexität
- Manche Programme funktionieren schlechter
- Portweiterleitungen nötig

---

# NAT und IPv6

IPv6 besitzt extrem viele Adressen.

Darum ist NAT dort meistens nicht nötig.

---

# Linux-Befehle

## Routing anzeigen

```bash
ip route
```

---

## NAT-Regeln anzeigen

```bash
iptables -t nat -L
```

---

## IP-Forwarding prüfen

```bash
cat /proc/sys/net/ipv4/ip_forward
```

---

# Typische Probleme

## Kein Internet trotz Routing

Oft fehlt:
- NAT
- Masquerading
- IP-Forwarding

---

## Container haben kein Internet

Häufig:
- NAT-Regel fehlt
- Gateway falsch
- DNS fehlt

---

# Wichtige Merksätze

NAT übersetzt private IP-Adressen in öffentliche IP-Adressen.

Viele Geräte können dadurch eine öffentliche IP gemeinsam nutzen.

Masquerading ist eine Form von NAT unter Linux.

NAT wird vor allem bei IPv4 verwendet.

IPv6 benötigt normalerweise kein NAT.

---

# Fragen

## Wofür wird NAT verwendet?

> [!spoiler]- Lösung anzeigen
> NAT übersetzt private IP-Adressen in öffentliche IP-Adressen.

---

## Warum wird NAT bei IPv4 oft benötigt?

> [!spoiler]- Lösung anzeigen
> Weil öffentliche IPv4-Adressen knapp sind.

---

## Wie heißt die Linux-Funktion für einfaches NAT?

> [!spoiler]- Lösung anzeigen
> ```text
> Masquerading
> ```