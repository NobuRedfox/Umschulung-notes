## Grundlagen

- [[IPv4]]
- [[Netzmaske]]
- [[CIDR]]
- [[Netzwerkadresse]]
- [[Broadcastadresse]]

---

## Subnetting

- [[Subnetting]]
- [[VLSM]]

---

## IPv6

- [[IPv6]]

---

## Formeln

- [[Hosts berechnen]]
- [[CIDR Übersicht]]

---

## Weitere Netzwerkthemen

- [[MAC-Adresse]]
- [[ARP]]
- [[DNS]]
- [[DHCP]]
- [[NAT]]
- [[TCP]]
- [[UDP]]
- [[Ports]]
- [[OSI-Modell]]
- [[Router]]
- [[Switch]]
- [[VLAN]]
- [[VPN]]

---

# Schnelle Übersicht

| Thema | Wichtig |
|---|---|
| IPv4 | 32 Bit |
| IPv6 | 128 Bit |
| Netzmaske | trennt Netzwerk und Host |
| CIDR | Anzahl der Netzwerkbits |
| Netzwerkadresse | erste Adresse |
| Broadcastadresse | letzte Adresse |
| Subnetting | Netzwerke aufteilen |
| VLSM | unterschiedlich große Subnetze |

---

# Wichtige Formeln

## Hostbits

```text
32 - CIDR
```

---

## Hosts

```text
2^Hostbits - 2
```

---

# Typische CIDR-Werte

| CIDR | Hosts |
|---|---|
| /30 | 2 |
| /29 | 6 |
| /28 | 14 |
| /27 | 30 |
| /26 | 62 |
| /25 | 126 |
| /24 | 254 |

---

# Merksätze

> [!important]
> Mehr Netzwerkbits
>
> → kleineres Netzwerk
>
> → weniger Hosts

---

> [!important]
> Netzwerkadresse:
>
> alle Hostbits = 0

---

> [!important]
> Broadcastadresse:
>
> alle Hostbits = 1