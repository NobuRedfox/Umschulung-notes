
> [!info]
> ## Bedeutung
> IPv4 = Internet Protocol Version 4

---

# Definition

IPv4 ist das am häufigsten verwendete Netzwerkprotokoll zur Adressierung von Geräten in Netzwerken und im Internet.

Jedes Gerät im Netzwerk benötigt eine IPv4-Adresse.

---

# Beispiel einer IPv4-Adresse

```text
192.168.0.15
```

Eine IPv4-Adresse besteht aus:
- 4 Zahlenblöcken
- getrennt durch Punkte
- jeder Block: 0 bis 255

---

# Aufbau

## Beispiel

```text
192.168.0.15
```

Die Adresse besteht aus 4 Byte:

```text
192 | 168 | 0 | 15
```

---

# Größe

IPv4 verwendet:

```text
32 Bit
```

Dadurch sind ungefähr möglich:

```text
4,3 Milliarden Adressen
```

---

# Private IPv4-Adressen

Diese Adressen werden innerhalb lokaler Netzwerke verwendet.

Sie werden nicht direkt im Internet geroutet.

---

## Private Bereiche

### Klasse A

```text
10.0.0.0 - 10.255.255.255
```

---

### Klasse B

```text
172.16.0.0 - 172.31.255.255
```

---

### Klasse C

```text
192.168.0.0 - 192.168.255.255
```

---

# Öffentliche IPv4-Adressen

Öffentliche IP-Adressen sind weltweit eindeutig
und im Internet erreichbar.

Beispiel:

```text
8.8.8.8
```

---

# Localhost

```text
127.0.0.1
```

Bedeutung:

```text
Der eigene Computer
```

Diese Adresse heißt auch:

```text
Loopback-Adresse
```

---

# Subnetzmaske

IPv4-Adressen werden oft mit einer CIDR-Notation angegeben.

Beispiel:

```text
192.168.0.15/24
```

Die:

```text
/24
```

bedeutet:

```text
24 Bit gehören zum Netzwerk
```

---

# Beispielnetz

```text
192.168.0.0/24
```

Mögliche Geräte:

```text
192.168.0.1
192.168.0.2
192.168.0.3
...
```

---

# Gateway

Das Gateway ist meistens der Router.

Beispiel:

```text
192.168.0.1
```

Wenn ein Gerät ein anderes Netzwerk erreichen will,
sendet es die Pakete an das Gateway.

---

# Linux-Befehle

## IP-Adressen anzeigen

```bash
ip addr
```

---

## Kurzform

```bash
ip a
```

---

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

# IP-Adresse hinzufügen

```bash
ip addr add 192.168.0.10/24 dev eth0
```

Vergibt eine IPv4-Adresse an ein Interface.

---

# Verbindung testen

```bash
ping 8.8.8.8
```

---

# Typische Probleme

## Doppelte IP-Adresse

Wenn zwei Geräte dieselbe IP-Adresse haben,
gibt es Netzwerkprobleme.

---

## Falsche Subnetzmaske

Dann können Geräte oft nicht miteinander kommunizieren.

---

## Kein Gateway

Dann funktioniert meistens nur das lokale Netzwerk,
aber nicht das Internet.

---

# IPv4 und Routing

Router arbeiten mit IPv4-Adressen.

Ein Router entscheidet:
- wohin Pakete geschickt werden
- welches Netzwerk erreichbar ist

---

# IPv4 und NAT

Weil IPv4-Adressen knapp sind,
verwenden viele Netzwerke NAT.

Dadurch können viele Geräte
eine öffentliche IP-Adresse gemeinsam nutzen.

---

# Wichtige Merksätze

IPv4 verwendet 32 Bit.

IPv4-Adressen identifizieren Geräte in Netzwerken.

Private IPv4-Adressen werden nicht direkt im Internet geroutet.

Router arbeiten mit IPv4-Adressen.

IPv4 arbeitet auf Layer 3 des OSI-Modells.

---

# Fragen

## Wofür wird IPv4 verwendet?

> [!spoiler]- Lösung anzeigen
> IPv4 wird verwendet, um Geräte in Netzwerken und im Internet zu adressieren.

---

## Wie viele Bit besitzt eine IPv4-Adresse?

> [!spoiler]- Lösung anzeigen
> Eine IPv4-Adresse besitzt 32 Bit.

---

## Welche IPv4-Adresse bezeichnet den eigenen Computer?

> [!spoiler]- Lösung anzeigen
> Die Loopback-Adresse:
>
> ```text
> 127.0.0.1
> ```