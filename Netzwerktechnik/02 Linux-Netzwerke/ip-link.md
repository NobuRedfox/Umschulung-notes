
> [!info]
> ## Bedeutung
> `ip link`
>
> zeigt und verwaltet Netzwerkinterfaces unter Linux.

---

# Definition

Der Befehl:

```bash
ip link
```

zeigt Informationen über Netzwerkinterfaces an.

Zum Beispiel:
- Interface-Namen
- MAC-Adressen
- Status
- virtuelle Interfaces

---

# Kurzform

```bash
ip l
```

---

# Beispiel

```bash
ip link
```

---

# Beispielausgabe

```text
2: enp2s0:
    link/ether 00:1a:2b:3c:4d:5e
```

---

# Erklärung

## enp2s0

Name des Netzwerkinterfaces.

---

## link/ether

Zeigt die MAC-Adresse an.

Beispiel:

```text
00:1a:2b:3c:4d:5e
```

---

# Netzwerkinterfaces

Typische Interfaces:

```text
eth0
enp2s0
wlan0
lo
veth0
br0
```

---

# Loopback-Interface

```text
lo
```

Das interne Netzwerkinterface des eigenen Computers.

---

# Interface aktivieren

```bash
ip link set eth0 up
```

Bedeutung:

```text
Netzwerkinterface aktivieren
```

---

# Interface deaktivieren

```bash
ip link set eth0 down
```

---

# Interface löschen

```bash
ip link del veth0
```

---

# Virtuelles Kabel erstellen

```bash
ip link add veth-A type veth peer name veth-B
```

Erstellt ein virtuelles Ethernet-Kabel.

---

# Bridge erstellen

```bash
ip link add br0 type bridge
```

Erstellt einen virtuellen Switch.

---

# Interface in Bridge stecken

```bash
ip link set eth0 master br0
```

---

# Interface in Namespace verschieben

```bash
ip link set veth0 netns Apfel
```

Das Interface gehört danach zum Container `Apfel`.

---

# Interface umbenennen

```bash
ip link set eth0 name lan0
```

---

# MTU anzeigen

`ip link` zeigt auch die:

```text
MTU
```

---

# MTU

Bedeutung:

```text
Maximale Paketgröße
```

Beispiel:

```text
1500
```

---

# Beispiel mit Containern

```bash
ip link add veth-A type veth peer name veth-B
```

---

## Danach

```text
veth-A <----> veth-B
```

Pakete,
die an einem Ende hineingehen,
kommen am anderen Ende heraus.

---

# Typische Einsatzgebiete

- Netzwerkinterfaces anzeigen
- Interfaces aktivieren
- virtuelle Netzwerke bauen
- Bridges erstellen
- Container vernetzen

---

# Typische Probleme

## Interface DOWN

Dann funktioniert das Netzwerk nicht.

---

## Interface gelöscht

Dann existiert die Verbindung nicht mehr.

---

## Falscher Interface-Name

Der Befehl funktioniert nicht.

---

# Unterschied zwischen ip addr und ip link

## ip addr

```text
IP-Adressen anzeigen
```

---

## ip link

```text
Netzwerkinterfaces verwalten
```

---

# Linux-Befehle

## Interfaces anzeigen

```bash
ip link
```

---

## Kurzform

```bash
ip l
```

---

## Interface aktivieren

```bash
ip link set eth0 up
```

---

## Interface deaktivieren

```bash
ip link set eth0 down
```

---

## Interface löschen

```bash
ip link del eth0
```

---

# Wichtige Merksätze

`ip link` verwaltet Netzwerkinterfaces.

`ip link` zeigt MAC-Adressen und Interface-Status an.

Mit `ip link` können virtuelle Netzwerke erstellt werden.

`ip l` ist die Kurzform von `ip link`.

`ip link` arbeitet hauptsächlich auf Layer 2.

---

# Fragen

## Wofür wird `ip link` verwendet?

> [!spoiler]- Lösung anzeigen
> `ip link` zeigt und verwaltet Netzwerkinterfaces.

---

## Wie aktiviert man ein Netzwerkinterface?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip link set eth0 up
> ```

---

## Wie lautet die Kurzform von `ip link`?

> [!spoiler]- Lösung anzeigen
> ```bash
> ip l
> ```