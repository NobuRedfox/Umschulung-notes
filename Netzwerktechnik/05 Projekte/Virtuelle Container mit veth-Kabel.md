> [!info]
> ## Ziel
>
Zwei virtuelle Container sollen direkt über ein virtuelles Netzwerkkabel (`veth`) verbunden werden.

```text
goblin -------- ork
```

---

# Erklärung

## Network Namespace

```bash
ip netns add goblin
```

Erstellt einen virtuellen Container mit eigenem Netzwerkstack.

Jeder Namespace besitzt:
- eigene Netzwerkschnittstellen
- eigene Routingtabellen
- eigene IP-Adressen

---

## Loopback aktivieren

```bash
ip netns exec goblin ip link set lo up
```

Aktiviert das interne Netzwerkinterface (`localhost`).

---

## Virtuelles Kabel erstellen

```bash
ip link add kabel-goblin type veth peer name kabel-ork
```

Erstellt ein virtuelles Ethernet-Kabel.

Es entstehen zwei Enden:
- kabel-goblin
- kabel-ork

Wenn ein Paket an einem Ende hineingeht,
kommt es am anderen Ende heraus.

---

## Kabel in Container verschieben

```bash
ip link set kabel-goblin netns goblin
ip link set kabel-ork netns ork
```

Steckt die Kabelenden in die jeweiligen Container.

---

## Interfaces aktivieren

```bash
ip netns exec goblin ip link set kabel-goblin up
```

Aktiviert das Netzwerkinterface.

---

## IP-Adressen vergeben

```bash
ip netns exec goblin ip addr add 172.100.0.3/24 dev kabel-goblin
```

Vergibt IP-Adressen innerhalb desselben Netzwerks.

---

## Verbindung testen

```bash
ip netns exec goblin ping -c1 172.100.0.4
```

Testet die Verbindung.

---

# Komplettes Script

```bash
set -ex

# Alte Container löschen
ip netns del goblin 2>/dev/null || true
ip netns del ork 2>/dev/null || true

# Alte Kabel löschen
ip link del kabel-goblin 2>/dev/null || true

# Container erstellen
ip netns add goblin
ip netns add ork

# Loopback aktivieren
ip netns exec goblin ip link set lo up
ip netns exec ork ip link set lo up

# Virtuelles Kabel erstellen
ip link add kabel-goblin type veth peer name kabel-ork

# Kabel in Container verschieben
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

# Zwei Shells öffnen
screenrc="$(mktemp)"

cat <<EOF > "$screenrc"
screen -t "goblin" ip netns exec goblin bash
split
focus
screen -t "ork" ip netns exec ork bash
focus
EOF

STY= exec screen -c "$screenrc"
```

---

# Nützliche Befehle

## Container betreten

```bash
ip netns exec goblin bash
```

---

## IP-Adressen anzeigen

```bash
ip netns exec goblin ip addr
```

---

## Routing anzeigen

```bash
ip netns exec goblin ip route
```

---

## Container löschen

```bash
ip netns del goblin
ip netns del ork
```