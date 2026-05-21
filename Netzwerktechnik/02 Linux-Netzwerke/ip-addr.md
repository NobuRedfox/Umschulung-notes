
> [!info]
> ## Bedeutung
> `ip addr`
>
> zeigt die IP-Adressen und Netzwerkschnittstellen eines Systems an.

---

# Definition

Der Befehl:

```bash
ip addr
```

zeigt:
- Netzwerkinterfaces
- IPv4-Adressen
- IPv6-Adressen
- MAC-Adressen
- Status der Interfaces

an.

---

# Kurzform

```bash
ip a
```

---

# Beispiel

```bash
ip addr
```

---

# Beispielausgabe

```text
2: enp2s0:
    inet 192.168.0.15/24
    inet6 fe80::1234/64
    link/ether 00:1a:2b:3c:4d:5e
```

---

# Erklärung der Ausgabe

## inet

```text
IPv4-Adresse
```

Beispiel:

```text
192.168.0.15/24
```

---

## inet6

```text
IPv6-Adresse
```

Beispiel:

```text
fe80::1234/64
```

---

## link/ether

```text
MAC-Adresse
```

Beispiel:

```text
00:1a:2b:3c:4d:5e
```

---

# Netzwerkinterfaces

Beispiele für Interfaces:

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

# Interface-Status

## UP

```text
Interface aktiv
```

---

## DOWN

```text
Interface deaktiviert
```

---

# IPv4-Adresse hinzufügen

```bash
ip addr add 192.168.0.10/24 dev eth0
```

Bedeutung:

```text
Füge eth0 die IP-Adresse 192.168.0.10 hinzu.
```

---

# IPv4-Adresse entfernen

```bash
ip addr del 192.168.0.10/24 dev eth0
```

---

# Nur IPv4 anzeigen

```bash
ip -4 addr
```

---

# Nur IPv6 anzeigen

```bash
ip -6 addr
```

---

# Interface aktivieren

```bash
ip link set eth0 up
```

---

# Interface deaktivieren

```bash
ip link set eth0 down
```

---

# Beispiel in virtuellen Netzwerken

```bash
ip netns exec Apfel ip addr
```

Zeigt die IP-Adressen innerhalb des Containers `Apfel`.

---

# Typische Einsatzgebiete

- Netzwerkfehler finden
- IP-Adressen prüfen
- MAC-Adressen anzeigen
- Container-Netzwerke prüfen
- Interfaces aktivieren

---

# Typische Probleme

## Keine IP-Adresse

Dann funktioniert oft:
- DHCP nicht
- Netzwerk nicht
- Internet nicht

---

## Interface DOWN

Dann ist das Netzwerkinterface deaktiviert.

---

## Falsche IP-Adresse

Geräte können nicht kommunizieren.

---

# Unterschied zu ifconfig

Früher wurde oft verwendet:

```bash
ifconfig
```

Heute nutzt man meistens:

```bash
ip addr
```

---

# Linux-Befehle

## IP-Adressen anzeigen

```bash
ip addr
```

---

## Kurzform

```bash
ip a
```

---

## IPv4-Adresse hinzufügen

```bash
ip addr add 192.168.0.10/24 dev eth0
```

---

## IPv4-Adresse entfernen

```bash
ip addr del 192.168.0.10/24 dev eth0
```

---

# Wichtige Merksätze

`ip addr` zeigt Netzwerkinterfaces und IP-Adressen an.

`inet` bedeutet IPv4-Adresse.

`inet6` bedeutet IPv6-Adresse.

`link/ether` zeigt die MAC-Adresse an.

`ip a` ist die Kurzform von `ip addr`.

---

# Fragen

## Wofür wird `ip addr` verwendet?

> [!spoiler]- Lösung anzeigen
> `ip addr` zeigt Netzwerkinterfaces und IP-Adressen an.

---

## Was bedeutet `inet` in der Ausgabe?

> [!spoiler]- Lösung anzeigen
> `inet` zeigt die IPv4-Adresse an.

---

## Wie lautet die Kurzform von `ip addr`?

> [!spoiler]- Lösung anzeigen
> ```bash
> ip a
> ```