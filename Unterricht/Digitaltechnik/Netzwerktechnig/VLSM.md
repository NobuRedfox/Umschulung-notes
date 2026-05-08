## Was bedeutet VLSM?

VLSM steht für:

```text
Variable Length Subnet Mask
```

---

# Idee von VLSM

Nicht jedes Netzwerk braucht gleich viele Hosts.

Mit VLSM kann man:

- große Subnetze
- kleine Subnetze

kombinieren.

---

> [!important]
> VLSM benutzt unterschiedlich große Subnetze.

---

# Warum ist das sinnvoll?

Ohne VLSM:

```text
Alle Netzwerke gleich groß
```

→ viele IP-Adressen werden verschwendet.

Mit VLSM:

```text
Jedes Netzwerk bekommt nur so viele Hosts wie nötig.
```

---

# Beispiel

Gegeben:

```text
192.168.0.0/24
```

Benötigt werden:

| Abteilung | Hosts |
|---|---|
| Büro | 100 |
| Lager | 30 |
| Server | 2 |

---

# Schritt 1 — Großes Netz

Für 100 Hosts:

```text
/25
```

Denn:

```text
2^7 - 2 = 126 Hosts
```

Netz:

```text
192.168.0.0/25
```

---

# Schritt 2 — Mittleres Netz

Für 30 Hosts:

```text
/27
```

Denn:

```text
2^5 - 2 = 30 Hosts
```

Netz:

```text
192.168.0.128/27
```

---

# Schritt 3 — Kleines Netz

Für 2 Hosts:

```text
/30
```

Denn:

```text
2^2 - 2 = 2 Hosts
```

Netz:

```text
192.168.0.160/30
```

---

# Vorteil

Die IP-Adressen werden effizient genutzt.

---

# Typische Größen

| CIDR | Hosts |
|---|---|
| /30 | 2 |
| /29 | 6 |
| /28 | 14 |
| /27 | 30 |
| /26 | 62 |
| /25 | 126 |

---

# Wichtige Regel

> [!important]
> Erst immer die größten Netzwerke planen.
>
> Danach die kleineren.

---

# Warum?

Große Netzwerke brauchen mehr zusammenhängende Adressen.

---

# Unterschied zu normalem Subnetting

## Normales Subnetting

```text
Alle Subnetze gleich groß
```

---

## VLSM

```text
Subnetze unterschiedlich groß
```

---

# Merksätze

> [!tip]
> VLSM spart IP-Adressen.

---

> [!tip]
> Große CIDR Zahl
>
> → kleines Netzwerk

---

> [!tip]
> Kleine CIDR Zahl
>
> → großes Netzwerk