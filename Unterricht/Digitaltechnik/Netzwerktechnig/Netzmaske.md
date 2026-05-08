## Was ist eine Netzmaske?

Die Netzmaske bestimmt:

- welcher Teil der IP-Adresse zum Netzwerk gehört
- welcher Teil zum Gerät (Host) gehört

Aufteilung:

```text
Netzwerkteil | Hostteil
```

---

## Beispiel

IP-Adresse:

```text
192.168.0.15
```

Netzmaske:

```text
255.255.255.0
```

---

## Binärdarstellung

```text
255.255.255.0
=
11111111.11111111.11111111.00000000
```

---

> [!important]
> `1 = Netzwerkbit`
>
> `0 = Hostbit`

---

## Bedeutung

```text
11111111.11111111.11111111.00000000
```

Die ersten 24 Bits gehören zum Netzwerk.

Die letzten 8 Bits gehören zum Host.

---

## Netzwerk und Host

```text
192.168.0 | .15
 Netzwerk   Host
```

---

## Warum 255?

```text
255
=
11111111
```

Alle 8 Bits sind gesetzt.

---

> [!info]
> Ein Oktett besitzt:
>
> - 8 Bit
> - Werte von 0–255
>
> Denn:
>
> ```text
> 2^8 = 256 Möglichkeiten
> ```

---

# Typische Netzmasken

| Netzmaske | Bedeutung |
|---|---|
| 255.0.0.0 | großes Netzwerk |
| 255.255.0.0 | mittleres Netzwerk |
| 255.255.255.0 | kleines Netzwerk |

---

## Beispiele

### 255.0.0.0

```text
11111111.00000000.00000000.00000000
```

Nur das erste Oktett gehört zum Netzwerk.

---

### 255.255.0.0

```text
11111111.11111111.00000000.00000000
```

Die ersten zwei Oktette gehören zum Netzwerk.

---

### 255.255.255.0

```text
11111111.11111111.11111111.00000000
```

Die ersten drei Oktette gehören zum Netzwerk.

---

# Wofür braucht man Netzmasken?

Damit Geräte wissen:

- wer im selben Netzwerk ist
- wann ein Router benötigt wird

---

# Beispiel Netzwerk

Gerät A:

```text
192.168.0.10
```

Gerät B:

```text
192.168.0.20
```

Netzmaske:

```text
255.255.255.0
```

Beide Geräte befinden sich im selben Netzwerk:

```text
192.168.0.x
```

Sie können direkt miteinander kommunizieren.

---

# Beispiel anderes Netzwerk

```text
192.168.1.5
```

liegt in einem anderen Netzwerk.

Dann wird normalerweise ein Router benötigt.

---

# Merksätze

> [!important]
> Mehr `1en`
>
> → kleineres Netzwerk
>
> → weniger Hosts

---

> [!important]
> Mehr `0en`
>
> → größeres Netzwerk
>
> → mehr Hosts

---

> [!tip]
> Netzmasken immer binär denken.
>
> Dann versteht man CIDR und Subnetting viel einfacher.