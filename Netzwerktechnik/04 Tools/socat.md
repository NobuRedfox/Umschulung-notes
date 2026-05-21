
> [!info]
> ## Bedeutung
> `socat` = SOcket CAT
>
> Ein sehr mächtiges Netzwerk- und Datenweiterleitungstool.

---

# Definition

`socat` verbindet zwei Datenströme miteinander.

Es kann:
- Netzwerkverbindungen erstellen
- Daten weiterleiten
- Ports verbinden
- Pipes verwenden
- Dateien verbinden
- Terminals verbinden

---

# Zweck

`socat` wird verwendet für:
- Netzwerktests
- Portweiterleitungen
- Tunnel
- Debugging
- virtuelle Verbindungen
- Container-Netzwerke

---

# Unterschied zu nc

## nc

```text
Einfacher
Weniger Funktionen
```

---

## socat

```text
Deutlich mächtiger
Sehr flexibel
```

---

# Einfaches Beispiel

## Server

```bash
socat TCP-LISTEN:1234 STDOUT
```

Bedeutung:

```text
Lausche auf TCP-Port 1234
und gib Daten auf dem Terminal aus.
```

---

# Client

```bash
echo "Hallo" | socat - TCP:127.0.0.1:1234
```

---

# Einfacher Chat

## Server

```bash
socat TCP-LISTEN:1234 STDIO
```

---

## Client

```bash
socat STDIO TCP:127.0.0.1:1234
```

---

# Portweiterleitung

## Beispiel

```bash
socat TCP-LISTEN:8080,fork TCP:google.com:80
```

---

# Bedeutung

```text
Leite Port 8080 an google.com:80 weiter.
```

---

# fork

```text
Erlaube mehrere Verbindungen gleichzeitig
```

---

# UDP verwenden

## Beispiel

```bash
socat UDP-LISTEN:1234 STDOUT
```

---

# Datei übertragen

## Sender

```bash
socat -u FILE:datei.txt TCP:192.168.0.10:1234
```

---

## Empfänger

```bash
socat TCP-LISTEN:1234 OPEN:datei.txt,creat
```

---

# Serielle Schnittstellen

`socat` kann auch:
- serielle Ports
- virtuelle Terminals
- Pipes

verbinden.

---

# Virtuelles Terminal erstellen

```bash
socat -d -d PTY,raw,echo=0 PTY,raw,echo=0
```

---

# Beispiel mit Containern

## Server

```bash
ip netns exec Apfel socat TCP-LISTEN:1234 STDOUT
```

---

## Client

```bash
ip netns exec Banane socat - TCP:10.0.0.2:1234
```

---

# Installation

## Debian/Ubuntu

```bash
sudo apt install socat
```

---

# Typische Einsatzgebiete

- Netzwerktests
- Portweiterleitung
- Reverse Proxys
- Container-Kommunikation
- Debugging
- Tunneling

---

# Typische Probleme

## Port bereits belegt

Dann startet der Listener nicht.

---

## Firewall blockiert Port

Verbindung funktioniert nicht.

---

## Falsche Zieladresse

Pakete erreichen das Ziel nicht.

---

# socat vs nc

## nc

- einfacher
- schneller zu benutzen
- gut für kleine Tests

---

## socat

- viel flexibler
- komplexer
- unterstützt viele Datentypen

---

# Linux-Befehle

## TCP-Server starten

```bash
socat TCP-LISTEN:1234 STDOUT
```

---

## Verbindung herstellen

```bash
socat - TCP:127.0.0.1:1234
```

---

## Portweiterleitung

```bash
socat TCP-LISTEN:8080,fork TCP:google.com:80
```

---

## UDP verwenden

```bash
socat UDP-LISTEN:1234 STDOUT
```

---

# Wichtige Merksätze

`socat` verbindet Datenströme miteinander.

`socat` ist deutlich mächtiger als `nc`.

`socat` unterstützt TCP, UDP, Dateien und Terminals.

`socat` wird häufig für Debugging und Netzwerktests verwendet.

`socat` kann Ports und Verbindungen weiterleiten.

---

# Fragen

## Wofür wird `socat` verwendet?

> [!spoiler]- Lösung anzeigen
> `socat` verbindet Datenströme und wird für Netzwerktests sowie Datenweiterleitung verwendet.

---

## Was bedeutet `TCP-LISTEN:1234`?

> [!spoiler]- Lösung anzeigen
> Lausche auf TCP-Port 1234.

---

## Was ist der Unterschied zwischen `nc` und `socat`?

> [!spoiler]- Lösung anzeigen
> `socat` ist deutlich flexibler und unterstützt mehr Funktionen als `nc`.