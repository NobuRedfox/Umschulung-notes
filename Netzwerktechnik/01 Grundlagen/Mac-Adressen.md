
> [!info]
> ## Bedeutung
> MAC = Media Access Control

---

# Definition

Eine MAC-Adresse ist die eindeutige Hardware-Adresse
einer Netzwerkkarte.

Jedes Netzwerkinterface besitzt normalerweise eine eigene MAC-Adresse.

---

# Beispiel

```text
00:1A:2B:3C:4D:5E
```

Eine MAC-Adresse besteht aus:
- 6 Byte
- hexadecimalen Zahlen
- insgesamt 48 Bit

---

# Aufgabe einer MAC-Adresse

MAC-Adressen werden verwendet,
um Geräte innerhalb eines lokalen Netzwerks eindeutig zu identifizieren.

---

# Vergleich mit IP-Adressen

## MAC-Adresse

```text
Identifiziert ein Gerät innerhalb eines LANs
```

Arbeitet auf:

```text
OSI Layer 2
```

---

## IP-Adresse

```text
Identifiziert Geräte zwischen Netzwerken
```

Arbeitet auf:

```text
OSI Layer 3
```

---

# Beispiel im Netzwerk

```text
Laptop ---- Switch ---- Router
```

Innerhalb des LANs kommunizieren Geräte über MAC-Adressen.

Für Kommunikation ins Internet werden zusätzlich IP-Adressen verwendet.

---

# Aufbau einer MAC-Adresse

## Beispiel

```text
00:1A:2B:3C:4D:5E
```

Die ersten Teile gehören meistens zum Hersteller.

Beispiele:
- Intel
- Realtek
- NVIDIA

---

# Linux-Befehle

## Netzwerkschnittstellen anzeigen

```bash
ip link
```

---

## Kurzform

```bash
ip l
```

---

# Beispielausgabe

```text
2: enp2s0:
    link/ether 00:1a:2b:3c:4d:5e
```

Die Zeile:

```text
link/ether
```

zeigt die MAC-Adresse an.

---

# MAC-Adresse ändern

Temporär möglich mit:

```bash
ip link set dev eth0 address 02:11:22:33:44:55
```

Das nennt man:

```text
MAC-Spoofing
```

---

# Broadcast-MAC-Adresse

```text
ff:ff:ff:ff:ff:ff
```

Bedeutung:

```text
Alle Geräte im Netzwerk
```

---

# MAC und Switches

Switches arbeiten mit MAC-Adressen.

Ein Switch merkt sich:
- welche MAC-Adresse
- an welchem Port erreichbar ist

Dadurch kann er Daten gezielt weiterleiten.

---

# ARP

ARP verbindet:
- IP-Adressen
- MAC-Adressen

Beispiel:

```text
192.168.0.5 -> 00:1A:2B:3C:4D:5E
```

---

# Typische Eigenschaften

MAC-Adressen sind normalerweise:
- weltweit eindeutig
- fest in Hardware gespeichert

Sie können aber softwareseitig geändert werden.

---

# Wichtige Merksätze

MAC-Adressen identifizieren Geräte innerhalb eines LANs.

MAC-Adressen arbeiten auf Layer 2.

Switches arbeiten mit MAC-Adressen.

IP-Adressen und MAC-Adressen arbeiten zusammen.

MAC-Adressen bestehen aus 48 Bit.

---

# Fragen

## Wofür wird eine MAC-Adresse verwendet?

> [!spoiler]- Lösung anzeigen
> Eine MAC-Adresse identifiziert ein Gerät innerhalb eines lokalen Netzwerks.

---

## Auf welchem OSI-Layer arbeiten MAC-Adressen?

> [!spoiler]- Lösung anzeigen
> MAC-Adressen arbeiten auf Layer 2.

---

## Womit zeigt man unter Linux MAC-Adressen an?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip link
> ```
>
> oder kurz:
>
> ```bash
> ip l
> ```