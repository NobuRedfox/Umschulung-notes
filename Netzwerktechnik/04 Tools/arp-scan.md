
> [!info]
> ## Bedeutung
> `arp-scan`
>
> durchsucht ein lokales Netzwerk nach Geräten.

---

# Definition

`arp-scan` sucht Geräte innerhalb eines lokalen Netzwerks.

Dabei verwendet das Programm:

```text
ARP
```

um:
- IP-Adressen
- MAC-Adressen
- Herstellerinformationen

zu finden.

---

# ARP

ARP bedeutet:

```text
Address Resolution Protocol
```

ARP verbindet:
- IP-Adressen
- MAC-Adressen

---

# Zweck von arp-scan

Mit `arp-scan` kann man:
- Geräte im Netzwerk finden
- aktive Hosts erkennen
- MAC-Adressen anzeigen
- Hersteller erkennen

---

# Beispiel

```bash
sudo arp-scan --localnet
```

---

# Bedeutung

```text
Durchsuche das lokale Netzwerk
```

---

# Beispielausgabe

```text
192.168.0.1    00:11:22:33:44:55    FritzBox
192.168.0.15   AA:BB:CC:DD:EE:FF    Intel
```

---

# Erklärung

## Erste Spalte

```text
IP-Adresse
```

---

## Zweite Spalte

```text
MAC-Adresse
```

---

## Dritte Spalte

```text
Hersteller
```

---

# Installation

## Debian/Ubuntu

```bash
sudo apt install arp-scan
```

---

# Netzwerkinterface auswählen

## Beispiel

```bash
sudo arp-scan --interface=eth0 --localnet
```

---

# Einzelne Netzwerke scannen

## Beispiel

```bash
sudo arp-scan 192.168.0.0/24
```

---

# Typischer Aufbau

```text
PC ---- Switch ---- Router
```

`arp-scan` findet Geräte im lokalen Netzwerksegment.

---

# Grenzen von arp-scan

`arp-scan` funktioniert normalerweise nur:
- im lokalen Netzwerk
- innerhalb desselben Broadcast-Domain

Nicht über das Internet.

---

# Unterschied zu ping

## ping

```text
Testet Erreichbarkeit eines einzelnen Geräts
```

---

## arp-scan

```text
Findet viele Geräte gleichzeitig
```

---

# arp-scan und MAC-Adressen

`arp-scan` arbeitet stark mit:
- ARP
- MAC-Adressen
- Layer 2

---

# OSI-Layer

ARP arbeitet hauptsächlich auf:

```text
Layer 2
```

---

# Typische Einsatzgebiete

- Netzwerkanalyse
- Gerätesuche
- Heimnetzwerk prüfen
- Container-Netzwerke testen
- Sicherheitsanalysen

---

# Beispiel mit virtuellen Netzwerken

```bash
ip netns exec Apfel arp-scan --localnet
```

---

# Typische Probleme

## Kein sudo

Dann funktioniert `arp-scan` oft nicht.

---

## Falsches Interface

Dann werden keine Geräte gefunden.

---

## Firewall blockiert ARP

Manche Geräte antworten nicht.

---

# Linux-Befehle

## Lokales Netzwerk scannen

```bash
sudo arp-scan --localnet
```

---

## Interface auswählen

```bash
sudo arp-scan --interface=eth0 --localnet
```

---

## Bestimmtes Netzwerk scannen

```bash
sudo arp-scan 192.168.0.0/24
```

---

# Unterschied zu nmap

## arp-scan

- schnell im LAN
- arbeitet mit ARP
- Layer 2

---

## nmap

- umfangreicher
- Portscanner
- Layer 3/4

---

# Wichtige Merksätze

`arp-scan` findet Geräte im lokalen Netzwerk.

`arp-scan` verwendet ARP und MAC-Adressen.

`arp-scan` funktioniert hauptsächlich im lokalen Netzwerk.

`arp-scan` benötigt oft Root-Rechte.

ARP arbeitet auf Layer 2.

---

# Fragen

## Wofür wird `arp-scan` verwendet?

> [!spoiler]- Lösung anzeigen
> `arp-scan` durchsucht lokale Netzwerke nach Geräten.

---

## Welche Informationen zeigt `arp-scan` an?

> [!spoiler]- Lösung anzeigen
> IP-Adressen, MAC-Adressen und oft Herstellerinformationen.

---

## Warum benötigt `arp-scan` häufig sudo?

> [!spoiler]- Lösung anzeigen
> Weil für ARP-Scans oft rohe Netzwerkpakete verwendet werden.