
> [!info]
> ## Bedeutung
> IPv6 = Internet Protocol Version 6

---

# Definition

IPv6 ist der Nachfolger von IPv4.

Es wurde entwickelt,
weil IPv4-Adressen knapp geworden sind.

IPv6 stellt extrem viele IP-Adressen bereit.

---

# Beispiel einer IPv6-Adresse

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

IPv6-Adressen bestehen aus:
- hexadecimalen Zahlen
- Doppelpunkt getrennten Blöcken
- 128 Bit

---

# Größe

IPv6 verwendet:

```text
128 Bit
```

Dadurch existieren extrem viele mögliche Adressen.

Sehr viel mehr als bei IPv4.

---

# Kurzschreibweise

IPv6-Adressen dürfen verkürzt werden.

---

## Beispiel

Lang:

```text
2001:0db8:0000:0000:0000:0000:1428:57ab
```

Kurz:

```text
2001:db8::1428:57ab
```

---

# Vergleich IPv4 vs IPv6

## IPv4

```text
32 Bit
```

Beispiel:

```text
192.168.0.1
```

---

## IPv6

```text
128 Bit
```

Beispiel:

```text
2001:db8::1
```

---

# Localhost

## IPv4

```text
127.0.0.1
```

---

## IPv6

```text
::1
```

---

# Loopback-Adresse

```text
::1
```

Bedeutet:

```text
Der eigene Computer
```

---

# Link-Local-Adressen

IPv6-Geräte bekommen oft automatisch eine lokale Adresse.

Diese beginnen meistens mit:

```text
fe80::
```

Sie funktionieren nur innerhalb des lokalen Netzwerks.

---

# Öffentliche IPv6-Adressen

Öffentliche IPv6-Adressen sind weltweit erreichbar.

Beispiel:

```text
2001:
```

Viele Internetanbieter vergeben heute IPv6-Adressen.

---

# Kein NAT nötig

IPv6 besitzt extrem viele Adressen.

Darum braucht man normalerweise kein NAT.

Bei IPv4 ist NAT oft notwendig.

---

# Linux-Befehle

## IPv6-Adressen anzeigen

```bash
ip addr
```

---

## Nur IPv6 anzeigen

```bash
ip -6 addr
```

---

## IPv6-Routing anzeigen

```bash
ip -6 route
```

---

# Verbindung testen

## IPv6-Ping

```bash
ping6 google.com
```

oder:

```bash
ping -6 google.com
```

---

# IPv6-Adresse vergeben

```bash
ip -6 addr add 2001:db8::10/64 dev eth0
```

---

# Subnetz

IPv6 verwendet häufig:

```text
/64
```

Das bedeutet:

```text
64 Bit Netzwerkanteil
```

---

# Vorteile von IPv6

- Sehr viele Adressen
- Kein NAT nötig
- Bessere automatische Konfiguration
- Moderne Netzwerkfunktionen

---

# Nachteile von IPv6

- Schwerer zu lesen
- Ältere Geräte unterstützen es manchmal nicht
- Umstellung dauert lange

---

# Typische IPv6-Bereiche

## Link-Local

```text
fe80::
```

---

## Unique Local Address (ULA)

Ähnlich wie private IPv4-Adressen:

```text
fc00::
fd00::
```

---

## Multicast

```text
ff00::
```

---

# IPv6 und Router

Router leiten IPv6-Pakete weiter,
ähnlich wie bei IPv4.

Viele Router unterstützen heute:
- IPv4
- IPv6

gleichzeitig.

Das nennt man:

```text
Dual Stack
```

---

# Wichtige Merksätze

IPv6 ist der Nachfolger von IPv4.

IPv6 verwendet 128 Bit.

IPv6 bietet extrem viele Adressen.

IPv6 benötigt normalerweise kein NAT.

IPv6 arbeitet auf Layer 3 des OSI-Modells.

---

# Fragen

## Warum wurde IPv6 entwickelt?

> [!spoiler]- Lösung anzeigen
> IPv6 wurde entwickelt,
> weil IPv4-Adressen knapp geworden sind.

---

## Wie viele Bit besitzt eine IPv6-Adresse?

> [!spoiler]- Lösung anzeigen
> Eine IPv6-Adresse besitzt 128 Bit.

---

## Wie lautet die IPv6-Loopback-Adresse?

> [!spoiler]- Lösung anzeigen
> ```text
> ::1
> ```