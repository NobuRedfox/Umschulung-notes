## Was ist IPv4?

IPv4 steht für:

```
Internet Protocol Version 4
```

Es ist das klassische Adresssystem im Netzwerk und sorgt dafür, dass Geräte eindeutig identifiziert werden können.

Beispiele für Geräte:
- PCs
- Smartphones
- Router
- Server
- Drucker
Jedes Gerät im Netzwerk benötigt eine IP-Adresse.

---

## Aufbau einer IPv4-Adresse

Eine IPv4-Adresse besteht aus:

**32 Bit = 4 ⋅ 8 Bit**

Das bedeutet:
- 32 einzelne Bits
- aufgeteilt in 4 **Oktette**

---
## Beispiel

```
192.168.0.1
```

Aufgeteilt:

```
192 | 168 | 0 | 1
```

Diese Blöcke heißen:

```
Oktette
```

---
## Wertebereich

Jedes Oktett besitzt:

#### 8 Bit

Dadurch sind Werte möglich von:

#### 0 bis 2550

weil:

#### 2⁸ = 256

und gezählt wird von:

- 0  
    bis
- 255

---

## Binärdarstellung

Computer arbeiten intern binär.

Beispiel:

```
192.168.0.1
```

in Binär:

```
11000000.10101000.00000000.00000001
```

---

## Beispiel Umrechnung

### Dezimal → Binär

```
192
```

entspricht:

```
11000000
```

Denn:

```
128 + 64 = 192
```

Bitübersicht:

```
128 64 32 16 8 4 2 1 
  1  1  0  0 0 0 0 0
```

---
# Öffentliche und private IP-Adressen

## Öffentliche IP

- weltweit eindeutig
- im Internet erreichbar

Beispiel:

```
8.8.8.8
```

---

## Private IP

- nur im lokalen Netzwerk
- nicht direkt im Internet erreichbar

Private Bereiche:

```
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

Diese werden häufig zuhause oder in Firmen genutzt.

---

# localhost

Besondere Adresse:

```
127.0.0.1
```

Das bedeutet:

- der eigene Rechner
- Verbindung zu sich selbst

Name:

```
localhost
```

---

# Anzahl möglicher IPv4-Adressen

IPv4 besitzt:

#### 2³² = 4294967296

mögliche Adressen.

Da das Internet immer größer wurde, reichen diese Adressen heute nicht mehr aus.

Deshalb wurde IPv6 entwickelt.

---

# Wichtige Begriffe

|Begriff|Bedeutung|
|---|---|
|IPv4|Internet Protocol Version 4|
|IP-Adresse|Adresse eines Geräts|
|Oktett|8 Bit|
|Binär|Zahlensystem mit 0 und 1|
|Private IP|nur lokal nutzbar|
|Öffentliche IP|weltweit erreichbar|
|localhost|eigener Rechner|

---
# Merksätze

```
IPv4:
32 Bit
4 Oktette
0–255 pro Oktett
```

```
1 Oktett = 8 Bit
```

```
IPv4 wird intern binär gespeichert
```