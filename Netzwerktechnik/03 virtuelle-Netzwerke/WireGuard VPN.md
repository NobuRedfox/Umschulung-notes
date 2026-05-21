
> [!info]
> ## Bedeutung
> WireGuard = modernes VPN-Protokoll

---

# Definition

WireGuard ist ein modernes VPN-System.

Ein VPN erstellt einen verschlüsselten Tunnel zwischen mehreren Geräten.

Dadurch können Geräte sicher über das Internet kommunizieren.

---

# Zweck

WireGuard wird verwendet für:
- sichere Verbindungen
- Remote-Zugriff
- Standortvernetzung
- verschlüsselte Tunnel
- private Netzwerke

---

# Beispiel

```text
PC A ===== Internet ===== PC B
```

Zwischen beiden Geräten entsteht ein verschlüsselter Tunnel.

---

# VPN

VPN bedeutet:

```text
Virtual Private Network
```

---

# Vorteile von WireGuard

- Sehr schnell
- Einfach konfigurierbar
- Moderne Verschlüsselung
- Wenig Overhead
- Kleiner Codeumfang

---

# Vergleich mit älteren VPNs

## OpenVPN

- älter
- komplexer
- langsamer

---

## IPSec

- sehr komplex
- viele Einstellungen

---

## WireGuard

- modern
- einfach
- schnell

---

# Aufbau

```text
Client ===== WireGuard ===== Server
```

---

# Verschlüsselung

WireGuard verschlüsselt:
- Datenverkehr
- IP-Pakete
- Netzwerkverbindungen

Dadurch können Daten nicht einfach mitgelesen werden.

---

# WireGuard arbeitet auf

```text
Layer 3
```

Es transportiert hauptsächlich:
- IP-Pakete

---

# Installation

## Debian/Ubuntu

```bash
sudo apt install wireguard
```

---

# Schlüssel erzeugen

## Private Key

```bash
wg genkey
```

---

## Public Key erzeugen

```bash
wg pubkey
```

---

# Beispielkonfiguration

## Server

```text
[Interface]
Address = 10.10.0.1/24
ListenPort = 51820
PrivateKey = SERVER_PRIVATE_KEY
```

---

## Client

```text
[Interface]
Address = 10.10.0.2/24
PrivateKey = CLIENT_PRIVATE_KEY
```

---

# Peer

Ein Peer ist ein anderes WireGuard-Gerät.

---

## Beispiel

```text
[Peer]
PublicKey = CLIENT_PUBLIC_KEY
AllowedIPs = 10.10.0.2/32
```

---

# AllowedIPs

Bestimmt:
- welche Netzwerke erreichbar sind
- welche Pakete durch den Tunnel gehen

---

# Interface starten

```bash
wg-quick up wg0
```

---

# Interface stoppen

```bash
wg-quick down wg0
```

---

# Status anzeigen

```bash
wg
```

---

# Beispielaufbau

```text
Laptop ===== Internet ===== Homeserver
```

Der Laptop kann danach sicher auf das Heimnetz zugreifen.

---

# WireGuard und Container

WireGuard kann verwendet werden für:
- Container
- virtuelle Netzwerke
- gretap-Verschlüsselung
- Kubernetes
- Docker

---

# WireGuard + gretap

Oft verwendet:

```text
gretap über WireGuard
```

Dadurch erhält man:
- Layer-2-Tunnel
- plus Verschlüsselung

---

# Linux-Befehle

## Interface starten

```bash
wg-quick up wg0
```

---

## Interface stoppen

```bash
wg-quick down wg0
```

---

## Status anzeigen

```bash
wg
```

---

## Interfaces anzeigen

```bash
ip addr
```

---

# Typische Probleme

## Port blockiert

Standardport:

```text
51820/UDP
```

Firewall muss den Port erlauben.

---

## Falscher Public Key

Tunnel kann nicht aufgebaut werden.

---

## Falsche AllowedIPs

Pakete gehen nicht durch den Tunnel.

---

## Kein IP-Forwarding

Routing funktioniert nicht.

---

# WireGuard vs gretap

## WireGuard

```text
Layer 3
Verschlüsselt
VPN
```

---

## gretap

```text
Layer 2
Nicht verschlüsselt
Ethernet-Tunnel
```

---

# Wichtige Merksätze

WireGuard ist ein modernes VPN-Protokoll.

WireGuard verschlüsselt Netzwerkverkehr.

WireGuard arbeitet auf Layer 3.

WireGuard ist schneller und einfacher als viele ältere VPN-Systeme.

WireGuard verwendet Public-Key-Kryptografie.

---

# Fragen

## Wofür wird WireGuard verwendet?

> [!spoiler]- Lösung anzeigen
> WireGuard erstellt verschlüsselte VPN-Tunnel zwischen Geräten.

---

## Auf welchem OSI-Layer arbeitet WireGuard?

> [!spoiler]- Lösung anzeigen
> WireGuard arbeitet auf Layer 3.

---

## Welcher Standardport wird von WireGuard verwendet?

> [!spoiler]- Lösung anzeigen
> ```text
> UDP Port 51820
> ```