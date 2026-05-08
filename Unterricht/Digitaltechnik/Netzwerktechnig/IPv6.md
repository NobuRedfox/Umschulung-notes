## Was ist IPv6?

IPv6 ist der Nachfolger von IPv4.

Es wurde entwickelt,
weil IPv4 zu wenige Adressen besitzt.

---

# Größe von IPv6

IPv4:

```text
32 Bit
```

IPv6:

```text
128 Bit
```

---

> [!important]
> IPv6 besitzt extrem viel mehr Adressen als IPv4.

---

# Beispiel IPv6-Adresse

```text
2001:0db8:85a3:0000:0000:8a2e:0370:7334
```

---

# Aufbau

IPv6 benutzt:

```text
Hexadezimalzahlen
```

Also:

```text
0–9
A–F
```

---

# Schreibweise

IPv6 besteht aus:

```text
8 Blöcken
```

Jeder Block besitzt:

```text
4 Hex-Zeichen
```

---

# Beispiel

```text
2001 : 0db8 : 85a3 : 0000 : 0000 : 8a2e : 0370 : 7334
```

---

# Abkürzen von IPv6

Führende Nullen dürfen entfernt werden.

Beispiel:

```text
0db8
→
db8
```

---

# Nullblöcke zusammenfassen

Mehrere `0000` Blöcke dürfen einmalig ersetzt werden durch:

```text
::
```

---

# Beispiel

```text
2001:0db8:0000:0000:0000:0000:1428:57ab
```

wird zu:

```text
2001:db8::1428:57ab
```

---

> [!warning]
> `::`
> darf nur einmal pro Adresse verwendet werden.

---

# Warum IPv6?

IPv4 besitzt ungefähr:

```text
4,3 Milliarden Adressen
```

IPv6 besitzt:

```text
2^128
```

Das sind unfassbar viele Adressen.

---

# Vorteile von IPv6

- sehr viele Adressen
- effizienteres Routing
- bessere Strukturierung
- kein NAT notwendig
- moderner Standard

---

# IPv4 vs IPv6

| IPv4 | IPv6 |
|---|---|
| 32 Bit | 128 Bit |
| Dezimal | Hexadezimal |
| Punkte | Doppelpunkte |
| z.B. 192.168.0.1 | z.B. 2001:db8::1 |

---

# localhost bei IPv6

IPv4:

```text
127.0.0.1
```

IPv6:

```text
::1
```

---

# Häufige IPv6-Bereiche

| Bereich | Bedeutung |
|---|---|
| ::1 | localhost |
| fe80:: | Link Local |
| 2000::/3 | öffentliche IPv6 |
| fc00::/7 | private IPv6 |

---

# Merksätze

> [!important]
> IPv6 benutzt Hexadezimalzahlen.

---

> [!important]
> IPv6 besitzt 128 Bit.

---

> [!tip]
> `::`
>
> ersetzt zusammenhängende Nullblöcke.

---

> [!tip]
> IPv6 wurde entwickelt,
> weil IPv4 zu wenige Adressen besitzt.