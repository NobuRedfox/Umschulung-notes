
> [!info]
> ## Bedeutung
> DHCP = Dynamic Host Configuration Protocol

---

# Definition

DHCP verteilt automatisch Netzwerkeinstellungen an Geräte.

Zum Beispiel:
- IP-Adresse
- Subnetzmaske
- Gateway
- DNS-Server

Ohne DHCP müsste alles manuell eingestellt werden.

---

# Beispiel

Wenn du dich zuhause mit dem WLAN verbindest,
bekommt dein Gerät meistens automatisch:

```text
IP-Adresse
Gateway
DNS-Server
```

Diese Daten kommen normalerweise vom Router per DHCP.

---

# Typische DHCP-Daten

## Beispiel

```text
IP-Adresse:   192.168.0.23
Gateway:      192.168.0.1
DNS-Server:   192.168.0.1
```

---

# DHCP-Server

Der DHCP-Server verteilt die Netzwerkeinstellungen.

Oft ist der Router gleichzeitig:
- Router
- Switch
- WLAN-Access-Point
- DHCP-Server

---

# DHCP-Client

Der DHCP-Client fordert eine IP-Adresse an.

Zum Beispiel:
- Laptop
- Smartphone
- Container
- Drucker

---

# DHCP-Ablauf

Der grundlegende Ablauf:

```text
1. Discover
2. Offer
3. Request
4. Acknowledge
```

Kurz erklärt:

```text
Client:
"Hat jemand eine IP-Adresse für mich?"

Server:
"Ja, nimm diese hier."

Client:
"Okay, die möchte ich."

Server:
"Alles klar, gehört jetzt dir."
```

---

# Linux-Befehle

## IP-Adresse anzeigen

```bash
ip addr
```

---

## Routing anzeigen

```bash
ip route
```

---

## DHCP-Adresse anfordern

```bash
dhclient eth0
```

---

# Statische IP vs DHCP

## DHCP

```text
IP-Adresse automatisch
```

Vorteile:
- Einfach
- Schnell
- Weniger Fehler

---

## Statische IP

```text
IP-Adresse manuell festgelegt
```

Vorteile:
- Immer dieselbe Adresse
- Gut für Server

---

# Typische Probleme

## Keine IP-Adresse erhalten

Dann funktioniert oft DHCP nicht.

Symptom:

```text
Keine Internetverbindung
```

oder:

```text
169.254.x.x
```

Diese Adresse bedeutet oft:

```text
Kein DHCP-Server erreichbar
```

---

# DHCP und Router

Der Router verteilt meistens:
- IP-Adresse
- DNS-Server
- Gateway

an alle Geräte im Netzwerk.

---

# Wichtige Merksätze

DHCP verteilt automatisch Netzwerkeinstellungen.

DHCP spart manuelle Konfiguration.

Ohne DHCP müsste jedes Gerät manuell eingerichtet werden.

DHCP benutzt normalerweise:
- UDP Port 67
- UDP Port 68

DHCP arbeitet auf Layer 7 des OSI-Modells.

---

# Fragen

## Wofür wird DHCP verwendet?

> [!spoiler]- Lösung anzeigen
> DHCP verteilt automatisch Netzwerkeinstellungen wie IP-Adresse, Gateway und DNS-Server.

---

## Was ist der Unterschied zwischen DHCP und statischer IP?

> [!spoiler]- Lösung anzeigen
> DHCP vergibt IP-Adressen automatisch.
>
> Eine statische IP wird manuell festgelegt.

---

## Woran erkennt man oft ein DHCP-Problem?

> [!spoiler]- Lösung anzeigen
> Geräte bekommen oft eine Adresse wie:
>
> `169.254.x.x`
>
> oder haben keine Internetverbindung.