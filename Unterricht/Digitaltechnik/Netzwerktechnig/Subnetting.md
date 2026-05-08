## Was ist Subnetting?

Subnetting bedeutet:

```text
Ein großes Netzwerk
in mehrere kleinere Netzwerke aufteilen
```

---

# Warum macht man das?

Vorteile:

- bessere Übersicht
- weniger Broadcastverkehr
- höhere Sicherheit
- effizientere Netzwerke

---

# Beispiel

Gegebenes Netzwerk:

```text
192.168.0.0/24
```

Dieses Netzwerk besitzt:

```text
254 Hosts
```

---

# Aufteilen in kleinere Netzwerke

Aus:

```text
/24
```

machen wir:

```text
/25
```

---

# Was ändert sich?

```text
/24
=
24 Netzwerkbits
8 Hostbits
```

```text
/25
=
25 Netzwerkbits
7 Hostbits
```

---

> [!important]
> Mehr Netzwerkbits
>
> → kleinere Netzwerke
>
> → weniger Hosts

---

# Neue Netzwerke

## Erstes Subnetz

```text
192.168.0.0/25
```

Hostbereich:

```text
192.168.0.1 - 192.168.0.126
```

Broadcast:

```text
192.168.0.127
```

---

## Zweites Subnetz

```text
192.168.0.128/25
```

Hostbereich:

```text
192.168.0.129 - 192.168.0.254
```

Broadcast:

```text
192.168.0.255
```

---

# Warum beginnt das zweite Netz bei 128?

```text
/25
```

bedeutet:

```text
255.255.255.128
```

Binär:

```text
11111111.11111111.11111111.10000000
```

Der Sprung beträgt:

```text
128
```

Darum entstehen Netze bei:

```text
0
128
```

---

# Hosts berechnen

Formel:

```text
2^Hostbits - 2
```

Bei `/25`:

```text
7 Hostbits
```

```text
2^7 - 2
= 126 Hosts
```

---

# Typische Aufteilungen

| CIDR | Hosts |
|---|---|
| /24 | 254 |
| /25 | 126 |
| /26 | 62 |
| /27 | 30 |
| /28 | 14 |
| /29 | 6 |
| /30 | 2 |

---

# Wichtige Idee

Beim Subnetting:

```text
Hostbits → Netzwerkbits
```

Dadurch entstehen mehrere kleinere Netzwerke.

---

# Merksätze

> [!important]
> Große CIDR Zahl
>
> → kleineres Netzwerk
>
> → weniger Hosts

---

> [!tip]
> Subnetting bedeutet:
>
> ein Netzwerk aufteilen.

---

> [!tip]
> Netzwerkadresse:
>
> erste Adresse im Subnetz

---

> [!tip]
> Broadcastadresse:
>
> letzte Adresse im Subnetz