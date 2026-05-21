# Interfaces anzeigen

```bash
ip link
```

Kurzform:

```bash
ip l
```

---

# IP-Adressen anzeigen

```bash
ip addr
```

Kurzform:

```bash
ip a
```

---

# Routingtabelle anzeigen

```bash
ip route
```

Kurzform:

```bash
ip r
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

# IP-Adresse hinzufügen

```bash
ip addr add 192.168.0.10/24 dev eth0
```

---

# Route hinzufügen

```bash
ip route add default via 192.168.0.1
```

---

# Namespace erstellen

```bash
ip netns add Apfel
```

---

# Namespaces anzeigen

```bash
ip netns list
```

---

# Befehl im Namespace ausführen

```bash
ip netns exec Apfel bash
```

---

# veth-Kabel erstellen

```bash
ip link add veth-A type veth peer name veth-B
```

---

# Interface in Namespace verschieben

```bash
ip link set veth-A netns Apfel
```

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

# Interface in Bridge stecken

```bash
ip link set veth0 master br0
```

---

# IP-Forwarding aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

# NAT aktivieren

```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

# Ping

```bash
ping google.com
```

---

# traceroute

```bash
traceroute google.com
```

---

# Ports testen

```bash
nc -zv 192.168.0.1 22
```

---

# Einfacher TCP-Server

```bash
nc -l 1234
```

---

# Geräte im Netzwerk suchen

```bash
sudo arp-scan --localnet
```

---

# Wireshark starten

```bash
wireshark
```

---

# WireGuard starten

```bash
wg-quick up wg0
```

---

# Wichtige Dateien

## DNS

```bash
/etc/resolv.conf
```

---

# Wichtige Netzwerke

## Localhost

```text
127.0.0.1
```

---

## Broadcast

```text
255.255.255.255
```

---

## Private Netzwerke

### Klasse A

```text
10.0.0.0/8
```

---

### Klasse B

```text
172.16.0.0/12
```

---

### Klasse C

```text
192.168.0.0/16
```

---

# Wichtige Ports

## DNS

```text
53
```

---

## HTTP

```text
80
```

---

## HTTPS

```text
443
```

---

## SSH

```text
22
```

---

## WireGuard

```text
51820/UDP
```

---

# Wichtige Merksätze

```text
Switch = Layer 2
Router = Layer 3
```

---

```text
MAC-Adresse = Layer 2
IP-Adresse = Layer 3
```

---

```text
Bridge = virtueller Switch
```

---

```text
veth = virtuelles Netzwerkkabel
```

---

```text
NAT übersetzt private in öffentliche IP-Adressen
```