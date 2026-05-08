## Was ist die Netzwerkadresse?

Die Netzwerkadresse identifiziert das gesamte Netzwerk.

Alle Geräte im selben Netzwerk besitzen dieselbe Netzwerkadresse.

---

# Beispiel

IP-Adresse:

```text
192.168.0.15
```

CIDR:

```text
/24
```

Netzmaske:

```text
255.255.255.0
```

---

# Netzwerkteil

```text
192.168.0
```

Hostteil:

```text
15
```

---

# Netzwerkadresse

```text
192.168.0.0
```

---

> [!important]
> Die Netzwerkadresse ist immer die erste Adresse im Netzwerk.

---

# Beispiel

| Gerät | Gehört zu |
|---|---|
| 192.168.0.10 | 192.168.0.0/24 |
| 192.168.0.25 | 192.168.0.0/24 |
| 192.168.0.200 | 192.168.0.0/24 |

Alle gehören zum selben Netzwerk.

---

# Hostbits auf 0 setzen

Die Netzwerkadresse entsteht,
wenn alle Hostbits `0` sind.

Beispiel:

```text
192.168.0.15
```

Binär:

```text
00001111
```

Hostbits → 0:

```text
00000000
```

Ergebnis:

```text
192.168.0.0
```

---

# Merksatz

> [!tip]
> Netzwerkadresse:
>
> alle Hostbits = 0