
> [!info]
> ## Bedeutung
> OSI = Open Systems Interconnection
>
> Das OSI-Modell beschreibt,
> wie Daten durch Netzwerke übertragen werden.

---

# Definition

Das OSI-Modell teilt Netzwerkkommunikation in:

```text
7 Schichten
```

Jede Schicht besitzt:
- eigene Aufgaben
- eigene Protokolle
- typische Geräte

Alle Schichten arbeiten zusammen.

---

# Übersicht

```text
7 Anwendung      / Application
6 Darstellung    / Presentation
5 Sitzung        / Session
4 Transport      
3 Vermittlung    / Network
2 Sicherung      / Data Link
1 Bitübertragung / Physical
```

---

# Layer 7 – Anwendung / Application

## Aufgabe

Diese Schicht ist der direkte Kontakt zu Programmen.

Hier greifen Anwendungen aufs Netzwerk zu.

---

## Protokolle

- HTTP      (Hypertext Transfer Protocol)
- HTTPS   (Hypertext Transfer Protocol Secure)
- DNS        (Domain Name System)
- DHCP     (Dynamic Host Configuration Protocol)
- FTP         (File Transfer Protocol)
- SMTP     (Simple Mail Transfer Protocol)

---

## Beispiele

- Browser öffnet Webseite
- DNS fragt IP-Adresse ab
- E-Mail senden

---

# Layer 6 – Darstellung / Presentation

## Aufgabe

Daten werden:
- formatiert
- übersetzt
- verschlüsselt

---

## Protokolle / Formate

- TLS / SSL
- UTF-8
- JPEG
- PNG

---

## Beispiele

- HTTPS verschlüsseln
- Bilddaten übertragen
- Text korrekt darstellen

---

# Layer 5 – Sitzung / Session

## Aufgabe

Verbindungen zwischen Geräten verwalten.

Zum Beispiel:
- starten
- offen halten
- beenden

---

## Protokolle

- NetBIOS
- RPC
- SMB-Sitzungen

---

## Beispiele

- Login-Sitzung
- Verbindung zu Dateiserver

---

# Layer 4 – Transport

## Aufgabe

Daten sicher oder schnell übertragen.

Hier wird geregelt:
- Reihenfolge
- Paketverlust
- Geschwindigkeit
- Ports

---

## Protokolle

- TCP
- UDP

---

## Beispiele

TCP:
- Webseiten
- SSH

UDP:
- DNS
- Gaming
- Streaming

---

# Layer 3 – Vermittlung / Network

## Aufgabe

Pakete zwischen Netzwerken weiterleiten.

Hier arbeitet Routing.

---

## Protokolle

- IPv4
- IPv6
- ICMP

---

## Beispiele

- Router entscheidet Weg
- ping
- Internetverbindung

---

# Layer 2 – Sicherung / Data Link

## Aufgabe

Übertragung von Daten im lokalen Netzwerk.

Hier arbeiten:

- MAC-Adressen
- Switches
- Bridges

---

## Protokolle

- Ethernet
- ARP
- VLAN

---

## Beispiele

- Switch verbindet mehrere PCs im LAN  
- ARP sucht zu einer IP-Adresse die passende MAC-Adresse  
- Bridge verbindet zwei Netzwerke oder Container  
- Daten werden als Ethernet-Frames übertragen

---

# Layer 1 – Bitübertragung / Physical

## Aufgabe

Physische Übertragung.

Bits werden über Kabel oder Funk übertragen.

---

## Protokolle / Standards

- LAN-Kabel
- Glasfaser
- WLAN-Funksignal
- Netzwerkkarten
- RJ45-Stecker

---

## Beispiele

- LAN-Kabel zwischen PC und Switch
- WLAN-Signal 
- Lichtsignal über Glasfaser

---

# Datenfluss

Beim Senden:

```text
7 → 1
```

Beim Empfangen:

```text
1 → 7
```

---

# Geräte im Vergleich

## Layer 1

- Kabel
- Repeater

---

## Layer 2

- Switch
- Bridge

---

## Layer 3

- Router

---

## Layer 7

- Browser
- DNS-Server

---

# Wichtige Merksätze

Layer 2 = MAC-Adresse

Layer 3 = IP-Adresse

Switch = Layer 2

Router = Layer 3

OSI besitzt 7 Schichten

---

# Fragen

## Wie viele Schichten besitzt das OSI-Modell?

> [!spoiler]- Lösung anzeigen
> Das OSI-Modell besitzt:
>
> ```text
> 7 Schichten
> ```

---

## Auf welchem Layer arbeitet ein Router?

> [!spoiler]- Lösung anzeigen
> Router arbeiten auf:
>
> ```text
> Layer 3
> ```

---

## Auf welchem Layer arbeitet ein Switch?

> [!spoiler]- Lösung anzeigen
> Switches arbeiten auf:
>
> ```text
> Layer 2
> ```