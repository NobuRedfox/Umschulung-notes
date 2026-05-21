
> [!info]
> ## Bedeutung
> gretap = GRE TAP Tunnel

---

# Definition

Ein gretap-Tunnel verbindet zwei entfernte Netzwerke virtuell miteinander.

Dabei entsteht ein virtuelles Ethernet-Kabel über ein bestehendes Netzwerk oder das Internet.

---

# Zweck

Mit gretap können:
- Switches
- Bridges
- VLANs
- Container-Netzwerke

über mehrere physische Computer hinweg verbunden werden.

---

# Beispiel

```text
PC A ================= PC B
        Internet
```

Zwischen beiden PCs entsteht ein virtuelles Netzwerkkabel.

---

# GRE

GRE bedeutet:

```text
Generic Routing Encapsulation
```

GRE kapselt Netzwerkpakete innerhalb anderer Pakete.

---

# TAP

TAP bedeutet:

```text
Layer-2 Ethernet-Tunnel
```

Dadurch können:
- MAC-Adressen
- Broadcasts
- VLANs

durch den Tunnel übertragen werden.

---

# Unterschied zu normalem GRE

## GRE

```text
Layer 3
IP-Pakete
```

---

## gretap

```text
Layer 2
Ethernet-Frames
```

---

# Typischer Aufbau

```text
Container --- Bridge --- gretap ==== gretap --- Bridge --- Container
```

Dadurch entsteht ein gemeinsames virtuelles LAN.

---

# gretap erstellen

## Beispiel

### PC A

```bash
ip link add gt0 type gretap local 192.168.0.10 remote 192.168.0.20
```

---

### PC B

```bash
ip link add gt0 type gretap local 192.168.0.20 remote 192.168.0.10
```

---

# Bedeutung

## local

```text
Eigene IP-Adresse
```

---

## remote

```text
IP-Adresse des anderen PCs
```

---

# Tunnel aktivieren

```bash
ip link set gt0 up
```

---

# IP-Adresse vergeben

```bash
ip addr add 172.16.0.10/24 dev gt0
```

---

# Beispielaufbau

```text
PC A                         PC B
172.16.0.10                 172.16.0.20
     \                       /
      \                     /
       ===== gretap =======
```

---

# gretap und Bridges

gretap wird oft mit Bridges kombiniert.

---

## Beispiel

```bash
ip link set gt0 master br0
```

Dadurch wird der Tunnel Teil des virtuellen Switches.

---

# Beispiel mit mehreren Rechnern

```text
Container --- Bridge --- gretap ==== gretap --- Bridge --- Container
```

Alle Geräte befinden sich danach im selben Layer-2-Netzwerk.

---

# Vorteile von gretap

- Layer-2-Tunnel
- Broadcastfähig
- VLAN-fähig
- Virtuelle LANs über große Entfernungen

---

# Nachteile

- Nicht verschlüsselt
- Zusätzlicher Netzwerk-Overhead
- Sicherheitsrisiko im Internet

---

# Verschlüsselung

gretap selbst verschlüsselt nicht.

Darum kombiniert man gretap oft mit:
- WireGuard
- VPN
- IPSec

---

# Linux-Befehle

## gretap erstellen

```bash
ip link add gt0 type gretap local 192.168.0.10 remote 192.168.0.20
```

---

## Tunnel aktivieren

```bash
ip link set gt0 up
```

---

## IP-Adresse vergeben

```bash
ip addr add 172.16.0.10/24 dev gt0
```

---

## In Bridge stecken

```bash
ip link set gt0 master br0
```

---

# Typische Probleme

## Tunnel nicht aktiv

Dann funktioniert die Verbindung nicht.

---

## Falsche local/remote-IP

Tunnel kann nicht aufgebaut werden.

---

## Firewall blockiert GRE

Dann funktioniert der Tunnel nicht.

---

## Keine Verschlüsselung

Daten können mitgelesen werden.

---

# gretap vs WireGuard

## gretap

```text
Layer 2
Nicht verschlüsselt
```

---

## WireGuard

```text
Layer 3
Verschlüsselt
VPN
```

---

# Wichtige Merksätze

gretap erstellt virtuelle Ethernet-Tunnel.

gretap arbeitet auf Layer 2.

gretap kann MAC-Adressen und Broadcasts übertragen.

gretap wird oft mit Bridges kombiniert.

gretap verschlüsselt Daten nicht.

---

# Fragen

## Wofür wird gretap verwendet?

> [!spoiler]- Lösung anzeigen
> gretap verbindet entfernte Netzwerke über virtuelle Ethernet-Tunnel.

---

## Auf welchem OSI-Layer arbeitet gretap?

> [!spoiler]- Lösung anzeigen
> gretap arbeitet auf Layer 2.

---

## Warum wird gretap oft mit WireGuard kombiniert?

> [!spoiler]- Lösung anzeigen
> Weil gretap selbst keine Verschlüsselung besitzt.