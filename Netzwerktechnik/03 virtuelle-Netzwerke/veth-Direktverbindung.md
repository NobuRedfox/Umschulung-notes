
> [!info]
> ## Bedeutung
> `veth` = Virtual Ethernet
>
> Ein veth-Paar funktioniert wie ein virtuelles Netzwerkkabel.

---

# Definition

Eine veth-Direktverbindung verbindet zwei Netzwerkinterfaces direkt miteinander.

Pakete,
die an einem Ende hineingehen,
kommen am anderen Ende wieder heraus.

---

# Zweck

veth-Verbindungen werden oft verwendet für:
- Container
- Docker
- Namespaces
- virtuelle Netzwerke
- Netzwerklabore

---

# Beispiel

```text
goblin -------- ork
```

Zwischen beiden Containern besteht ein virtuelles Ethernet-Kabel.

---

# veth-Paar erstellen

```bash
ip link add veth-A type veth peer name veth-B
```

---

# Bedeutung

## veth-A

Erstes Kabelende.

---

## veth-B

Zweites Kabelende.

---

# Eigenschaften

Ein veth-Paar funktioniert wie:
- ein Netzwerkkabel
- mit zwei Steckern

---

# Aufbau

```text
veth-A <----> veth-B
```

Pakete werden direkt weitergeleitet.

---

# Beispiel mit Namespaces

```text
Namespace A ---- veth ---- Namespace B
```

---

# Interfaces in Namespaces verschieben

## Beispiel

```bash
ip link set veth-A netns goblin
ip link set veth-B netns ork
```

---

# Interfaces aktivieren

```bash
ip netns exec goblin ip link set veth-A up
```

---

# IP-Adressen vergeben

```bash
ip netns exec goblin ip addr add 172.100.0.3/24 dev veth-A
```

---

# Komplettes Beispiel

```bash
set -ex

# Alte Namespaces löschen
ip netns del goblin 2>/dev/null || true
ip netns del ork 2>/dev/null || true

# Altes Kabel löschen
ip link del kabel-goblin 2>/dev/null || true

# Namespaces erstellen
ip netns add goblin
ip netns add ork

# Loopback aktivieren
ip netns exec goblin ip link set lo up
ip netns exec ork ip link set lo up

# Virtuelles Kabel erstellen
ip link add kabel-goblin type veth peer name kabel-ork

# Kabelenden verschieben
ip link set kabel-goblin netns goblin
ip link set kabel-ork netns ork

# Interfaces aktivieren
ip netns exec goblin ip link set kabel-goblin up
ip netns exec ork ip link set kabel-ork up

# IP-Adressen vergeben
ip netns exec goblin ip addr add 172.100.0.3/24 dev kabel-goblin
ip netns exec ork ip addr add 172.100.0.4/24 dev kabel-ork

# Verbindung testen
ip netns exec goblin ping -c1 172.100.0.4
```

---

# Verbindung testen

## Ping

```bash
ip netns exec goblin ping 172.100.0.4
```

---

# Interfaces anzeigen

```bash
ip link
```

---

# IP-Adressen anzeigen

```bash
ip netns exec goblin ip addr
```

---

# Namespaces anzeigen

```bash
ip netns list
```

---

# Typische Einsatzgebiete

- Container-Netzwerke
- Docker
- Routing-Labs
- virtuelle Switches
- Bridges

---

# Typische Probleme

## Interface DOWN

Dann funktioniert die Verbindung nicht.

---

## Keine IP-Adresse

Dann können Geräte nicht kommunizieren.

---

## Interface nicht im richtigen Namespace

Dann existiert die Verbindung nicht korrekt.

---

# Unterschied zu Bridge

## veth-Direktverbindung

```text
Direktes Kabel zwischen zwei Geräten
```

---

## Bridge

```text
Virtueller Switch für mehrere Geräte
```

---

# Unterschied zu Routing

## veth

```text
Direkte Layer-2-Verbindung
```

---

## Router

```text
Verbindung verschiedener Netzwerke
```

---

# Linux-Befehle

## veth-Paar erstellen

```bash
ip link add veth-A type veth peer name veth-B
```

---

## Interface aktivieren

```bash
ip link set veth-A up
```

---

## Interface verschieben

```bash
ip link set veth-A netns goblin
```

---

## Interface löschen

```bash
ip link del veth-A
```

---

# Wichtige Merksätze

Ein veth-Paar funktioniert wie ein virtuelles Netzwerkkabel.

veth wird häufig für Container verwendet.

Pakete werden direkt zwischen beiden Enden weitergeleitet.

veth arbeitet auf Layer 2.

veth-Verbindungen werden oft mit Namespaces kombiniert.

---

# Fragen

## Wofür wird ein veth-Paar verwendet?

> [!spoiler]- Lösung anzeigen
> Ein veth-Paar verbindet zwei Netzwerkinterfaces direkt miteinander.

---

## Wie erstellt man ein veth-Paar?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip link add veth-A type veth peer name veth-B
> ```

---

## Auf welchem OSI-Layer arbeitet veth?

> [!spoiler]- Lösung anzeigen
> veth arbeitet auf Layer 2.