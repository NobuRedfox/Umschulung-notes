
> [!info]
> ## Bedeutung
> Wireshark ist ein Netzwerk-Analyseprogramm.
>
> Damit können Netzwerkpakete mitgelesen und analysiert werden.

---

# Definition

Wireshark zeichnet Netzwerkverkehr auf
und zeigt einzelne Pakete detailliert an.

Dadurch kann man sehen:
- welche Geräte kommunizieren
- welche Protokolle verwendet werden
- welche Daten übertragen werden

---

# Zweck

Wireshark wird verwendet für:
- Netzwerkfehler finden
- Protokolle analysieren
- Sicherheitstests
- Debugging
- Lernen von Netzwerken

---

# Beispiel

```text
PC ---- Switch ---- Router ---- Internet
```

Wireshark kann die Pakete zwischen den Geräten analysieren.

---

# Paketmitschnitt

Wireshark erstellt einen:

```text
Packet Capture
```

also einen Mitschnitt von Netzwerkpaketen.

---

# Typische Protokolle

Wireshark kann viele Protokolle analysieren:

- Ethernet
- ARP
- IPv4
- IPv6
- TCP
- UDP
- ICMP
- DNS
- HTTP
- HTTPS
- DHCP

---

# Beispiel

## DNS-Anfrage

```text
google.com -> Welche IP-Adresse?
```

Wireshark zeigt:
- Anfrage
- Antwort
- Zielserver
- IP-Adresse

---

# Installation

## Debian/Ubuntu

```bash
sudo apt install wireshark
```

---

# Starten

## GUI starten

```bash
wireshark
```

---

# Interfaces auswählen

Beim Start zeigt Wireshark:
- Ethernet
- WLAN
- virtuelle Interfaces
- Bridges
- veth-Interfaces

an.

---

# Capture starten

Einfach:
- Interface auswählen
- Doppelklick
- Mitschnitt beginnt

---

# Capture stoppen

Mit dem roten Stop-Button.

---

# Filter

Wireshark unterstützt sehr mächtige Filter.

---

# Beispiele

## Nur ICMP

```text
icmp
```

---

## Nur DNS

```text
dns
```

---

## Nur TCP

```text
tcp
```

---

## Bestimmte IP

```text
ip.addr == 192.168.0.15
```

---

## Bestimmter Port

```text
tcp.port == 80
```

---

# Paketaufbau

Wireshark zeigt Pakete schichtweise an.

---

# Beispiel

```text
Ethernet
IPv4
TCP
HTTP
```

---

# OSI-Modell

Wireshark eignet sich hervorragend,
um das OSI-Modell praktisch zu verstehen.

---

# Farben

Wireshark markiert Protokolle farbig.

Beispiel:
- TCP
- DNS
- ICMP
- Fehler

---

# Beispiel mit ping

## Terminal

```bash
ping google.com
```

---

## Wireshark-Filter

```text
icmp
```

Dann sieht man:
- Echo Request
- Echo Reply

---

# Beispiel mit DNS

## Terminal

```bash
ping google.com
```

---

## Filter

```text
dns
```

Dann sieht man:
- DNS-Anfrage
- DNS-Antwort

---

# Beispiel mit HTTP

## Filter

```text
http
```

Dann sieht man:
- Webseitenanfragen
- Header
- Antworten

---

# Beispiel mit Containern

Wireshark kann auch:
- Bridges
- veth
- virtuelle Interfaces
- Docker-Netzwerke

analysieren.

---

# tshark

Wireshark besitzt auch eine CLI-Version:

```text
tshark
```

---

# Beispiel

```bash
sudo tshark
```

---

# Typische Einsatzgebiete

- Netzwerkdebugging
- Sicherheitsanalyse
- Protokollanalyse
- Container-Netzwerke
- Fehlersuche

---

# Typische Probleme

## Kein Netzwerkverkehr sichtbar

Oft:
- falsches Interface gewählt
- Capture nicht gestartet

---

## Keine Berechtigung

Dann benötigt man oft:

```bash
sudo wireshark
```

oder Gruppenrechte.

---

## Zu viele Pakete

Dann helfen Filter.

---

# Wireshark vs tcpdump

## Wireshark

- grafisch
- übersichtlich
- einfach analysierbar

---

## tcpdump

- Terminal
- leichtgewichtig
- gut für Server

---

# Linux-Befehle

## Wireshark starten

```bash
wireshark
```

---

## tshark starten

```bash
sudo tshark
```

---

# Wichtige Merksätze

Wireshark analysiert Netzwerkpakete.

Wireshark zeigt Netzwerkverkehr detailliert an.

Wireshark eignet sich hervorragend für Fehlersuche.

Mit Filtern kann Netzwerkverkehr gezielt analysiert werden.

Wireshark unterstützt viele Netzwerkprotokolle.

---

# Fragen

## Wofür wird Wireshark verwendet?

> [!spoiler]- Lösung anzeigen
> Wireshark wird verwendet, um Netzwerkpakete mitzulesen und zu analysieren.

---

## Wie heißt die Terminal-Version von Wireshark?

> [!spoiler]- Lösung anzeigen
> ```text
> tshark
> ```

---

## Welcher Filter zeigt nur ICMP-Pakete an?

> [!spoiler]- Lösung anzeigen
> ```text
> icmp
> ```