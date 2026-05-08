## Was bedeutet CIDR?

CIDR steht für:

```text
Classless Inter-Domain Routing
```

CIDR ist eine Kurzschreibweise für Netzmasken.

Statt:

```text
255.255.255.0
```

schreibt man einfach:

```text
/24
```

---

# Bedeutung von /24

```text
/24
```

bedeutet:

```text
24 Netzwerkbits
```

Binär:

```text
11111111.11111111.11111111.00000000
```

Das entspricht:

```text
255.255.255.0
```

---

> [!important]
> CIDR gibt an,
> wie viele Bits zum Netzwerk gehören.

---

# Beispiele

| CIDR | Netzmaske |
|---|---|
| /8 | 255.0.0.0 |
| /16 | 255.255.0.0 |
| /24 | 255.255.255.0 |
| /30 | 255.255.255.252 |

---

# Beispiel /8

```text
10.0.0.0/8
```

Netzmaske:

```text
255.0.0.0
```

Binär:

```text
11111111.00000000.00000000.00000000
```

Nur das erste Oktett gehört zum Netzwerk.

---

# Beispiel /16

```text
10.1.0.0/16
```

Netzmaske:

```text
255.255.0.0
```

Die ersten zwei Oktette gehören zum Netzwerk.

```text
10.1.x.x
```

---

# Beispiel /24

```text
192.168.0.0/24
```

Netzmaske:

```text
255.255.255.0
```

Die ersten drei Oktette gehören zum Netzwerk.

```text
192.168.0.x
```

---

# Hostbits berechnen

Formel:

```text
32 - CIDR
```

---

## Beispiel /24

```text
32 - 24 = 8 Hostbits
```

---

## Beispiel /16

```text
32 - 16 = 16 Hostbits
```

---

# Hosts berechnen

Formel:

```text
2^Hostbits - 2
```

---

> [!info]
> Warum `-2`?
>
> Zwei Adressen sind reserviert:
>
> - Netzwerkadresse
> - Broadcastadresse

---

# Beispiel /24

```text
8 Hostbits
```

```text
2^8 - 2
= 254 Hosts
```

---

# Beispiel /16

```text
16 Hostbits
```

```text
2^16 - 2
= 65534 Hosts
```

---

# Kleine CIDR Zahl

Beispiel:

```text
/8
```

- viele Hostbits
- großes Netzwerk
- viele Geräte möglich

---

# Große CIDR Zahl

Beispiel:

```text
/30
```

- wenige Hostbits
- kleines Netzwerk
- wenige Geräte möglich

---

> [!important]
> Große CIDR Zahl
>
> → kleineres Netzwerk
>
> → weniger Hosts

---

> [!important]
> Kleine CIDR Zahl
>
> → größeres Netzwerk
>
> → mehr Hosts

---

# Häufige CIDR-Größen

| CIDR | Hosts |
|---|---|
| /30 | 2 |
| /29 | 6 |
| /28 | 14 |
| /27 | 30 |
| /26 | 62 |
| /25 | 126 |
| /24 | 254 |

---

# Merksätze

> [!tip]
> CIDR beschreibt die Anzahl der Netzwerkbits.

---

> [!tip]
> Netzmaske und CIDR bedeuten dasselbe,
> nur unterschiedlich geschrieben.

---

# Beispiel komplett

```text
192.168.0.15/24
```

Bedeutung:

- IP-Adresse: `192.168.0.15`
- Netzmaske: `255.255.255.0`
- Netzwerk: `192.168.0.x`
- 8 Hostbits
- maximal 254 Hosts