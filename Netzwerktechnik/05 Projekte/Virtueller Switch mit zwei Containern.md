> [!info]
>## Ziel
>
Zwei virtuelle Container sollen nicht direkt,
sondern über einen virtuellen Switch verbunden werden.

```text
goblin --- Switch --- kobold
```

Der virtuelle Switch heißt in diesem Beispiel:

```text
br0
```

---

# Erklärung

## Network Namespace

```bash
ip netns add goblin
```

Erstellt einen virtuellen Container mit eigenem Netzwerkbereich.

---

## Bridge

```bash
ip link add br0 type bridge
```

Erstellt einen virtuellen Switch.

Eine Bridge verbindet mehrere Netzwerkinterfaces miteinander,
ähnlich wie ein echter Switch.

---

## veth-Kabel

```bash
ip link add kabel1-A type veth peer name kabel1-B
```

Erstellt ein virtuelles Kabel mit zwei Enden.

Ein Ende bleibt beim Switch,
das andere Ende kommt in den Container.

---

## Interface in den Switch stecken

```bash
ip link set kabel1-A master br0
```

Steckt das Kabelende in den virtuellen Switch.

---

# Aufbau

```text
goblin
  |
kabel1-B
  |
kabel1-A
  |
br0
  |
kabel2-A
  |
kabel2-B
  |
kobold
```

---

# IP-Adressen

```text
goblin  = 172.100.0.33/24
kobold  = 172.100.0.44/24
```

Beide Container liegen im selben Netzwerk:

```text
172.100.0.0/24
```

---

# Komplettes Script

```bash
set -ex

# Alte Container löschen
ip netns del goblin 2>/dev/null || true
ip netns del kobold 2>/dev/null || true

# Alte Bridge löschen
ip link del br0 2>/dev/null || true

# Alte Kabel löschen
ip link del kabel1-A 2>/dev/null || true
ip link del kabel2-A 2>/dev/null || true

# Container erstellen
ip netns add goblin
ip netns add kobold

# Loopback aktivieren
ip netns exec goblin ip link set lo up
ip netns exec kobold ip link set lo up

# Virtuellen Switch erstellen
ip link add br0 type bridge
ip link set br0 up

# Kabel zwischen Switch und goblin erstellen
ip link add kabel1-A type veth peer name kabel1-B

# Ein Kabelende in goblin stecken
ip link set kabel1-B netns goblin

# Anderes Kabelende in Switch stecken
ip link set kabel1-A master br0

# Kabel aktivieren
ip link set kabel1-A up
ip netns exec goblin ip link set kabel1-B up

# Kabel zwischen Switch und kobold erstellen
ip link add kabel2-A type veth peer name kabel2-B

# Ein Kabelende in kobold stecken
ip link set kabel2-B netns kobold

# Anderes Kabelende in Switch stecken
ip link set kabel2-A master br0

# Kabel aktivieren
ip link set kabel2-A up
ip netns exec kobold ip link set kabel2-B up

# IP-Adressen vergeben
ip netns exec goblin ip addr add 172.100.0.33/24 dev kabel1-B
ip netns exec kobold ip addr add 172.100.0.44/24 dev kabel2-B

# Verbindung testen
ip netns exec goblin ping -c1 172.100.0.44

# Zwei Shells öffnen
screenrc="$(mktemp)"

cat <<EOF > "$screenrc"
screen -t "goblin" ip netns exec goblin bash
split
focus
screen -t "kobold" ip netns exec kobold bash
focus
EOF

STY= exec screen -c "$screenrc"
```

---

# Testbefehle

## Von goblin zu kobold pingen

```bash
ip netns exec goblin ping 172.100.0.44
```

---

## Von kobold zu goblin pingen

```bash
ip netns exec kobold ping 172.100.0.33
```

---

## Bridge anzeigen

```bash
ip link show br0
```

---

## Eingesteckte Interfaces anzeigen

```bash
bridge link
```

---

## IP-Adressen anzeigen

```bash
ip netns exec goblin ip addr
ip netns exec kobold ip addr
```

---

# Wichtige Merksätze

Eine Bridge ist ein virtueller Switch.

Ein Switch verbindet Geräte im selben Netzwerk.

Hier brauchen wir kein Routing,
weil beide Container im selben Netz sind:

```text
172.100.0.0/24
```

Routing braucht man erst,
wenn verschiedene Netzwerke verbunden werden sollen.