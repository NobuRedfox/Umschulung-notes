## Was ist eine Broadcastadresse?

Die Broadcastadresse wird benutzt,
um alle Geräte im Netzwerk gleichzeitig anzusprechen.

---

> [!important]
> Die Broadcastadresse ist immer die letzte Adresse im Netzwerk.

---

# Beispiel

IP-Adresse:

```text
192.168.0.15/24
```

Netzmaske:

```text
255.255.255.0
```

Netzwerkadresse:

```text
192.168.0.0
```

---

# Broadcastadresse

```text
192.168.0.255
```

---

# Warum 255?

Die Hostbits werden alle auf `1` gesetzt.

Binär:

```text
11111111
```

Das ergibt:

```text
255
```

---

# Netzwerk vs Broadcast

| Typ | Hostbits |
|---|---|
| Netzwerkadresse | alle `0` |
| Broadcastadresse | alle `1` |

---

# Beispiel

## Netzwerkadresse

```text
192.168.0.0
```

Hostbits:

```text
00000000
```

---

## Broadcastadresse

```text
192.168.0.255
```

Hostbits:

```text
11111111
```

---

# Nutzbare Hosts

Zwischen Netzwerk- und Broadcastadresse liegen die nutzbaren Geräteadressen.

Beispiel:

| Typ | Adresse |
|---|---|
| Netzwerkadresse | 192.168.0.0 |
| Erster Host | 192.168.0.1 |
| Letzter Host | 192.168.0.254 |
| Broadcastadresse | 192.168.0.255 |

---

> [!info]
> Netzwerkadresse und Broadcastadresse
> dürfen nicht an Geräte vergeben werden.

---

# Beispiel /30

```text
192.168.1.0/30
```

Hosts:

```text
2^2 - 2 = 2
```

Adressen:

| Typ | Adresse |
|---|---|
| Netzwerkadresse | 192.168.1.0 |
| Host | 192.168.1.1 |
| Host | 192.168.1.2 |
| Broadcastadresse | 192.168.1.3 |

---

# Merksätze

> [!tip]
> Netzwerkadresse:
>
> alle Hostbits = 0

---

> [!tip]
> Broadcastadresse:
>
> alle Hostbits = 1

---

> [!important]
> Die Broadcastadresse ist immer die letzte Adresse eines Netzwerks.