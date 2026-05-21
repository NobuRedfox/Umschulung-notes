> [! info]
> ## Ziel
> 
> Drei virtuelle Container sollen verbunden werden.
> Der mittlere Container soll als Router arbeiten.

```text
Apfel ----- Banane ----- Erdbeere
```

---

# Aufbau

Banane verbindet zwei verschiedene Netzwerke.

## Linkes Netzwerk

```text
10.0.1.0/24
```

```text
Apfel   = 10.0.1.1
Banane  = 10.0.1.254
```

---

## Rechtes Netzwerk

```text
10.0.2.0/24
```

```text
Banane    = 10.0.2.254
Erdbeere  = 10.0.2.1
```

---

# Erklärung

## Network Namespace

```bash
ip netns add Apfel
```

Erstellt einen virtuellen Container mit eigenem Netzwerkbereich.

---

## veth-Kabel

```bash
ip link add veth-Apfel type veth peer name veth-Bananea
```

Erstellt ein virtuelles Netzwerkkabel mit zwei Enden.

---

## Router

Ein Router verbindet verschiedene Netzwerke miteinander.

Banane ist hier der Router, weil Banane in beiden Netzwerken eine IP-Adresse hat:

```text
10.0.1.254
10.0.2.254
```

---

## Default Route

```bash
ip route add default via 10.0.1.254
```

Bedeutung:

```text
Wenn du ein Ziel nicht direkt kennst,
schicke das Paket an 10.0.1.254.
```

---

## IP-Forwarding

```bash
sysctl -w net.ipv4.ip_forward=1
```

Erlaubt Banane, Pakete zwischen den beiden Netzwerken weiterzuleiten.

Ohne IP-Forwarding empfängt Banane zwar Pakete,
leitet sie aber nicht weiter.

---

# Komplettes Script

```bash
set -ex

# Alte Container löschen
ip netns del Apfel 2>/dev/null || true
ip netns del Banane 2>/dev/null || true
ip netns del Erdbeere 2>/dev/null || true

# Alte Kabel löschen
ip link del veth-Apfel 2>/dev/null || true
ip link del veth-Bananeb 2>/dev/null || true

# Container erstellen
ip netns add Apfel
ip netns add Banane
ip netns add Erdbeere

# veth-Kabel erstellen
ip link add veth-Apfel type veth peer name veth-Bananea
ip link add veth-Bananeb type veth peer name veth-Erdbeere

# Kabel in Container verschieben
ip link set veth-Apfel netns Apfel
ip link set veth-Bananea netns Banane

ip link set veth-Bananeb netns Banane
ip link set veth-Erdbeere netns Erdbeere

# IP-Adressen vergeben
ip netns exec Apfel ip addr add 10.0.1.1/24 dev veth-Apfel
ip netns exec Banane ip addr add 10.0.1.254/24 dev veth-Bananea

ip netns exec Banane ip addr add 10.0.2.254/24 dev veth-Bananeb
ip netns exec Erdbeere ip addr add 10.0.2.1/24 dev veth-Erdbeere

# Interfaces aktivieren
ip netns exec Apfel ip link set lo up
ip netns exec Apfel ip link set veth-Apfel up

ip netns exec Banane ip link set lo up
ip netns exec Banane ip link set veth-Bananea up
ip netns exec Banane ip link set veth-Bananeb up

ip netns exec Erdbeere ip link set lo up
ip netns exec Erdbeere ip link set veth-Erdbeere up

# Routing setzen
ip netns exec Apfel ip route add default via 10.0.1.254
ip netns exec Erdbeere ip route add default via 10.0.2.254

# Router-Funktion in Banane aktivieren
ip netns exec Banane sysctl -w net.ipv4.ip_forward=1

# Verbindung testen
ip netns exec Apfel ping -c1 10.0.2.1

# Drei Shells öffnen
screenrc="$(mktemp)"

cat <<EOF > "$screenrc"
screen -t "Apfel" ip netns exec Apfel bash
split
focus
screen -t "Banane" ip netns exec Banane bash
split
focus
screen -t "Erdbeere" ip netns exec Erdbeere bash
focus
EOF

STY= exec screen -c "$screenrc"
```

---

# Testbefehle

## Von Apfel zu Erdbeere pingen

```bash
ip netns exec Apfel ping 10.0.2.1
```

---

## Von Erdbeere zu Apfel pingen

```bash
ip netns exec Erdbeere ping 10.0.1.1
```

---

## Routingtabelle von Apfel anzeigen

```bash
ip netns exec Apfel ip route
```

---

## Routingtabelle von Erdbeere anzeigen

```bash
ip netns exec Erdbeere ip route
```

---

## IP-Adressen von Banane anzeigen

```bash
ip netns exec Banane ip addr
```

---

# Erwartete Routingtabellen

## Apfel

```text
default via 10.0.1.254 dev veth-Apfel
10.0.1.0/24 dev veth-Apfel proto kernel scope link src 10.0.1.1
```

---

## Erdbeere

```text
default via 10.0.2.254 dev veth-Erdbeere
10.0.2.0/24 dev veth-Erdbeere proto kernel scope link src 10.0.2.1
```

---

# Wichtige Merksätze

Ein Switch verbindet Geräte im selben Netzwerk.

Ein Router verbindet verschiedene Netzwerke.

Banane ist hier der Router.

Banane braucht zwei IP-Adressen,
weil Banane in zwei Netzwerken steht.

Ohne Default Route wissen Apfel und Erdbeere nicht,
wohin sie fremde Netzwerke schicken sollen.

Ohne IP-Forwarding leitet Banane keine Pakete weiter.