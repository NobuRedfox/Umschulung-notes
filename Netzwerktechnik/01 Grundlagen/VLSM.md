
> [!info]
> ## Bedeutung
> VLSM = Variable Length Subnet Mask
>
> Unterschiedlich große Subnetze innerhalb eines Netzwerks.

---

# Definition

VLSM erlaubt,
Subnetze unterschiedlich groß aufzuteilen.

Dadurch werden IP-Adressen effizienter genutzt.

---

# Warum braucht man VLSM?

Nicht jedes Netzwerk benötigt gleich viele Geräte.

---

# Beispiel ohne VLSM

```text
Abteilung A -> 5 Geräte
Abteilung B -> 200 Geräte
```

Ohne VLSM könnten beide dieselbe Subnetzgröße bekommen.

Dadurch würden viele IP-Adressen verschwendet.

---

# Mit VLSM

Jedes Netzwerk erhält:
- genau die passende Größe
- passende Anzahl an Hosts

Dadurch spart man IP-Adressen.

---

# Beispiel

## Großes Netz

```text
192.168.0.0/24
```

---

# Aufteilung mit VLSM

## Netzwerk A

```text
192.168.0.0/26
```

Hosts:

```text
62
```

---

## Netzwerk B

```text
192.168.0.64/27
```

Hosts:

```text
30
```

---

## Netzwerk C

```text
192.168.0.96/28
```

Hosts:

```text
14
```

---

# Vorteil

Große Netzwerke erhalten:
- viele Hosts

Kleine Netzwerke erhalten:
- kleine Subnetze

Dadurch wird nichts verschwendet.

---

# CIDR und VLSM

VLSM basiert auf:

```text
CIDR
```

CIDR erlaubt flexible Netzgrößen.

---

# Typische Netzgrößen

## /24

```text
254 Hosts
```

---

## /25

```text
126 Hosts
```

---

## /26

```text
62 Hosts
```

---

## /27

```text
30 Hosts
```

---

## /28

```text
14 Hosts
```

---

## /29

```text
6 Hosts
```

---

# Vorgehensweise bei VLSM

## 1. Größtes Netzwerk zuerst

Das größte Subnetz wird zuerst geplant.

---

## 2. Benötigte Hosts bestimmen

Beispiel:

```text
50 Hosts
```

---

## 3. Passende CIDR-Größe wählen

Für 50 Hosts benötigt man:

```text
/26
```

---

## 4. Restliches Netzwerk weiter aufteilen

Der übrige Bereich wird für kleinere Netze verwendet.

---

# Beispielaufgabe

## Ausgangsnetz

```text
192.168.1.0/24
```

---

## Anforderungen

### Netzwerk A

```text
100 Hosts
```

---

### Netzwerk B

```text
50 Hosts
```

---

### Netzwerk C

```text
10 Hosts
```

---

# Lösung

## Netzwerk A

```text
192.168.1.0/25
```

Hosts:

```text
126
```

---

## Netzwerk B

```text
192.168.1.128/26
```

Hosts:

```text
62
```

---

## Netzwerk C

```text
192.168.1.192/28
```

Hosts:

```text
14
```

---

# Broadcastadresse

Jedes VLSM-Subnetz besitzt:
- Netzwerkadresse
- Broadcastadresse
- Hostbereich

---

# Beispiel

## Netz

```text
192.168.1.192/28
```

---

## Broadcast

```text
192.168.1.207
```

---

# Vorteile von VLSM

- Spart IP-Adressen
- Flexible Netzgrößen
- Effizientere Netzwerke
- Weniger Verschwendung

---

# Nachteile

- Komplexer
- Mehr Planung nötig
- Fehleranfälliger

---

# VLSM und Routing

Router müssen alle Subnetze kennen.

Darum werden Routingtabellen größer.

---

# Typische Einsatzgebiete

- Firmennetzwerke
- VLANs
- Routing
- WAN-Verbindungen
- IPv4-Optimierung

---

# Typische Probleme

## Falsche Netzgrößen

Zu wenige Hosts verfügbar.

---

## Überlappende Netzwerke

Routing funktioniert nicht.

---

## Broadcastadresse falsch

Kommunikationsprobleme entstehen.

---

# Unterschied zwischen klassischem Subnetting und VLSM

## Klassisches Subnetting

```text
Alle Subnetze gleich groß
```

---

## VLSM

```text
Subnetze unterschiedlich groß
```

---

# Linux-Bezug

Linux arbeitet problemlos mit VLSM-Netzen.

Beispiel:

```bash
ip addr add 192.168.1.1/27 dev eth0
```

---

# Wichtige Merksätze

VLSM erlaubt unterschiedlich große Subnetze.

VLSM spart IPv4-Adressen.

Das größte Netzwerk wird zuerst geplant.

VLSM basiert auf CIDR.

VLSM wird häufig in großen Netzwerken verwendet.

---

# Fragen

## Wofür wird VLSM verwendet?

> [!spoiler]- Lösung anzeigen
> VLSM wird verwendet,
> um unterschiedlich große Subnetze zu erstellen.

---

## Was ist der Vorteil von VLSM?

> [!spoiler]- Lösung anzeigen
> VLSM spart IP-Adressen
> und nutzt Netzwerke effizienter.

---

## Was ist der Unterschied zwischen klassischem Subnetting und VLSM?

> [!spoiler]- Lösung anzeigen
> Beim klassischen Subnetting sind alle Subnetze gleich groß.
>
> Bei VLSM können Subnetze unterschiedlich groß sein.