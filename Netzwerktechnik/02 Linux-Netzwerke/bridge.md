
> [!info]
> ## Bedeutung
> Eine Bridge verbindet mehrere Netzwerkinterfaces miteinander.

---

# Definition

Eine Bridge arbeitet ähnlich wie ein Switch.

Sie verbindet mehrere Netzwerkinterfaces,
sodass sie sich wie ein gemeinsames Netzwerk verhalten.

---

# Beispiel

```text
PC1 ----\
         \
          Bridge
         /
PC2 ----/
```

Beide Geräte befinden sich im selben Netzwerk.

---

# Virtueller Switch

Unter Linux wird eine Bridge oft als:

```text
Virtueller Switch
```

verwendet.

---

# Unterschied zwischen Bridge und Router

## Bridge

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

# Einsatzgebiete

Bridges werden oft verwendet für:
- virtuelle Netzwerke
- Container
- virtuelle Maschinen
- Docker
- KVM
- VLANs

---

# Bridge erstellen

```bash
ip link add br0 type bridge
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
                Bridge
Container B ---/
```

Beide Container befinden sich danach im selben Netzwerk.

---

# Beispiel mit veth

```bash
ip link add veth-A type veth peer name veth-B
```

Ein Ende kann in die Bridge gesteckt werden:

```bash
ip link set veth-A master br0
```

---

# Bridge und MAC-Adressen

Eine Bridge arbeitet mit:

```text
MAC-Adressen
```

Die Bridge merkt sich:
- welche MAC-Adresse
- über welches Interface erreichbar ist

---

# Bridge anzeigen

```bash
bridge link
```

---

# Interfaces anzeigen

```bash
ip link
```

---

# Bridge löschen

```bash
ip link del br0
```

---

# Typischer Aufbau

```text
Container A ----\
                  \
                   Bridge ---- Host
                  /
Container B ----/
```

---

# Bridge vs Switch

## Bridge

Früher:
- Softwarelösung
- wenige Ports

Heute unter Linux oft:
- virtueller Switch

---

## Switch

- Hardwaregerät
- viele Ports
- schneller

---

# Bridge vs Hub

## Hub

```text
Sendet alles an alle Geräte
```

---

## Bridge/Switch

```text
Sendet Daten gezielt weiter
```

---

# Bridge und VLANs

Bridges können auch mit VLANs kombiniert werden.

Dadurch entstehen:
- virtuelle Switches
- getrennte Netzwerke
- komplexere Netzwerktopologien

---

# Typische Probleme

## Bridge nicht aktiviert

Dann funktioniert die Verbindung nicht.

---

## Interface nicht in Bridge

Dann gehört das Gerät nicht zum Netzwerk.

---

## Falsche IP-Konfiguration

Geräte können nicht kommunizieren.

---

# Linux-Befehle

## Bridge erstellen

```bash
ip link add br0 type bridge
```

---

## Bridge aktivieren

```bash
ip link set br0 up
```

---

## Interface in Bridge stecken

```bash
ip link set eth0 master br0
```

---

## Bridge anzeigen

```bash
bridge link
```

---

# Wichtige Merksätze

Eine Bridge verbindet Geräte im selben Netzwerk.

Eine Linux-Bridge arbeitet ähnlich wie ein Switch.

Bridges arbeiten auf Layer 2.

Bridges verwenden MAC-Adressen.

Linux-Bridges werden oft für Container und virtuelle Maschinen verwendet.

---

# Fragen

## Wofür wird eine Bridge verwendet?

> [!spoiler]- Lösung anzeigen
> Eine Bridge verbindet mehrere Netzwerkinterfaces innerhalb desselben Netzwerks.

---

## Auf welchem OSI-Layer arbeitet eine Bridge?

> [!spoiler]- Lösung anzeigen
> Eine Bridge arbeitet auf Layer 2.

---

## Wie erstellt man unter Linux eine Bridge?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip link add br0 type bridge
> ```