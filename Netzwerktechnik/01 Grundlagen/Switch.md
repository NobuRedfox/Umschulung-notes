
> [!info]
> ## Bedeutung
> Ein Switch verbindet Geräte innerhalb desselben Netzwerks.

---

# Definition

Ein Switch verbindet mehrere Geräte in einem lokalen Netzwerk (LAN).

Er sorgt dafür,
dass Datenpakete an das richtige Gerät weitergeleitet werden.

---

# Beispiel

```text
PC ----\
Laptop -- Switch
Server -/
```

Alle Geräte befinden sich im selben Netzwerk.

---

# Aufgabe eines Switches

Ein Switch merkt sich:

```text
Welche MAC-Adresse an welchem Port erreichbar ist
```

Dadurch kann er Daten gezielt weiterleiten.

---

# MAC-Adressen

Switches arbeiten mit:

```text
MAC-Adressen
```

Beispiel:

```text
00:1A:2B:3C:4D:5E
```

---

# OSI-Layer

Switches arbeiten auf:

```text
Layer 2
```

also:

```text
Sicherungsschicht
```

---

# Unterschied zwischen Switch und Router

## Switch

```text
Verbindet Geräte im selben Netzwerk
```

Arbeitet mit:
- MAC-Adressen
- Layer 2

---

## Router

```text
Verbindet verschiedene Netzwerke
```

Arbeitet mit:
- IP-Adressen
- Layer 3

---

# Einfacher Aufbau

```text
PC1 ----\
PC2 ----- Switch
PC3 ----/
```

Alle Geräte können direkt miteinander kommunizieren.

---

# Switch lernt automatisch

Wenn ein Gerät Daten sendet,
merkt sich der Switch:

```text
MAC-Adresse -> Port
```

Das nennt man:

```text
MAC-Adress-Tabelle
```

---

# Unbekannte Geräte

Kennt der Switch eine MAC-Adresse noch nicht,
sendet er die Daten zunächst an alle Ports.

Das nennt man:

```text
Flooding
```

---

# Broadcast

Broadcasts werden an alle Geräte gesendet.

Beispiel-MAC-Adresse:

```text
ff:ff:ff:ff:ff:ff
```

---

# Virtueller Switch unter Linux

Linux kann virtuelle Switches erstellen.

Das geschieht mit:

```bash
ip link add br0 type bridge
```

---

# Bridge

Eine Linux-Bridge arbeitet ähnlich wie ein Switch.

Darum nennt man sie oft:

```text
Virtueller Switch
```

---

# Bridge aktivieren

```bash
ip link set br0 up
```

---

# Interface in Bridge einstecken

```bash
ip link set eth0 master br0
```

oder:

```bash
ip link set veth0 master br0
```

---

# Beispiel mit Containern

```text
Container A ---\
                Switch
Container B ---/
```

Alle Container befinden sich im selben Netzwerk.

---

# Linux-Befehle

## Interfaces anzeigen

```bash
ip link
```

---

## Bridge anzeigen

```bash
bridge link
```

---

## Virtuelle Bridge erstellen

```bash
ip link add br0 type bridge
```

---

## Bridge aktivieren

```bash
ip link set br0 up
```

---

# Switch vs Hub

## Hub

```text
Sendet alles an alle Geräte
```

---

## Switch

```text
Sendet Daten gezielt an das richtige Gerät
```

---

# Vorteile eines Switches

- Schneller als Hubs
- Weniger unnötiger Netzwerkverkehr
- Mehr Geräte möglich

---

# Typische Probleme

## Interface nicht aktiviert

Dann funktioniert die Verbindung nicht.

---

## Falsches Netzwerk

Geräte müssen im selben Netzwerk liegen.

---

## Bridge nicht aktiv

Dann arbeitet der virtuelle Switch nicht.

---

# Wichtige Merksätze

Ein Switch verbindet Geräte im selben Netzwerk.

Switches arbeiten mit MAC-Adressen.

Switches arbeiten auf Layer 2.

Linux kann virtuelle Switches mit Bridges erstellen.

Eine Bridge funktioniert ähnlich wie ein echter Switch.

---

# Fragen

## Wofür wird ein Switch verwendet?

> [!spoiler]- Lösung anzeigen
> Ein Switch verbindet Geräte innerhalb desselben Netzwerks.

---

## Auf welchem OSI-Layer arbeitet ein Switch?

> [!spoiler]- Lösung anzeigen
> Ein Switch arbeitet auf Layer 2.

---

## Wie erstellt man unter Linux einen virtuellen Switch?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip link add br0 type bridge
> ```