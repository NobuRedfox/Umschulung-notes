# Grundlagen

## Adressierung

- [[IPv4]]
- [[IPv6]]
- [[MAC-Adressen]]
- [[Netzmaske]]
- [[CIDR]]
- [[Broadcastadresse]]

---

## Netzwerkaufteilung

- [[Subnetting]]
- [[VLSM]]

---

## Netzwerkdienste

- [[DNS]]
- [[DHCP]]
- [[NAT]]

---

## Netzwerkgeräte

- [[Switch]]
- [[Router]]

---

## Netzwerkkommunikation

- [[Routing]]
- [[VLAN]]

---

# Linux-Netzwerk

## IP-Befehle

- [[ip-addr]]
- [[ip-link]]
- [[ip-route]]
- [[ip-netns]]
- [[sysctl-ip-forward]]

---

## Virtuelle Netzwerke

- [[bridge]]
- [[Namespaces]]
- [[veth-Direktverbindung]]
- [[routing-3-container]]
- [[Internet-Container]]

---

## Erweiterte Netzwerke

- [[gretap]]
- [[WireGuard VPN]]

---

# Netzwerktools

- [[ping]]
- [[nc]]
- [[socat]]
- [[traceroute]]
- [[wireshark]]
- [[arp-scan]]

---

# Übungen

- [[Subnetting-Uebungen]]
- [[VLSM-Uebungen]]
- [[IPv4-Uebungen]]
- [[Netzwerktechnik-Lernzielkontrolle]]

---

# Wichtige Reihenfolge zum Lernen

## Grundlagen

```text
IPv4
↓
Netzmaske
↓
CIDR
↓
Broadcastadresse
↓
Subnetting
↓
VLSM
```

---

## Routing & Netzwerke

```text
Switch
↓
Router
↓
Routing
↓
NAT
↓
VLAN
```

---

## Linux-Netzwerk

```text
ip addr
↓
ip link
↓
ip route
↓
ip netns
↓
veth
↓
bridge
↓
Routing-Labs
```

---

# Merksatz

```text
Theorie verstehen
↓
Befehle lernen
↓
Labs bauen
↓
Pakete analysieren
```