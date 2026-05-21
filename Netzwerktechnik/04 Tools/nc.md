
> [!info]
> ## Bedeutung
> `nc` = Netcat
>
> Ein Netzwerkwerkzeug zum Senden und Empfangen von Daten.

---

# Definition

`nc` (Netcat) ist ein vielseitiges Netzwerktool.

Es kann:
- Verbindungen öffnen
- Daten senden
- Ports testen
- Server simulieren
- Clients simulieren

---

# Warum ist nc beliebt?

Netcat ist:
- sehr einfach
- extrem flexibel
- ideal für Netzwerktests

Darum nennt man es oft:

```text
Schweizer Taschenmesser für Netzwerke
```

---

# Typische Einsatzgebiete

- Ports testen
- einfache Chats
- Daten übertragen
- Debugging
- Server testen
- Reverse Shells
- Container-Netzwerke testen

---

# Verbindung testen

## Beispiel

```bash
nc google.com 80
```

Versucht,
eine TCP-Verbindung zu Port 80 aufzubauen.

---

# Einfacher Server

## Server starten

```bash
nc -l 1234
```

Bedeutung:

```text
Lausche auf Port 1234
```

---

# Client verbinden

## Auf anderem Terminal

```bash
nc 127.0.0.1 1234
```

Danach können beide Seiten Nachrichten senden.

---

# Einfacher Chat

```text
Terminal 1:
nc -l 1234

Terminal 2:
nc 127.0.0.1 1234
```

---

# Ports scannen

## Beispiel

```bash
nc -zv 192.168.0.1 22
```

---

# Bedeutung

## -z

```text
Nur Verbindung testen
```

---

## -v

```text
Ausführliche Ausgabe
```

---

# Mehrere Ports testen

```bash
nc -zv 192.168.0.1 20-30
```

---

# Datei senden

## Sender

```bash
nc -l 1234 < datei.txt
```

---

## Empfänger

```bash
nc 192.168.0.10 1234 > datei.txt
```

---

# HTTP testen

## Beispiel

```bash
nc google.com 80
```

Danach:

```text
GET / HTTP/1.1
Host: google.com
```

Mit leerer Zeile abschließen.

---

# UDP verwenden

Standardmäßig nutzt nc:

```text
TCP
```

---

## UDP

```bash
nc -u 192.168.0.1 1234
```

---

# Beispiel mit Containern

## Server

```bash
ip netns exec Apfel nc -l 1234
```

---

## Client

```bash
ip netns exec Banane nc 10.0.0.2 1234
```

---

# Installation

## Debian/Ubuntu

```bash
sudo apt install netcat-openbsd
```

---

# Typische Probleme

## Firewall blockiert Port

Dann funktioniert die Verbindung nicht.

---

## Falsche IP-Adresse

Client erreicht den Server nicht.

---

## Server läuft nicht

Dann schlägt die Verbindung fehl.

---

# nc vs ping

## ping

```text
Testet Erreichbarkeit über ICMP
```

---

## nc

```text
Testet echte TCP/UDP-Verbindungen
```

---

# nc vs socat

## nc

- einfacher
- schneller
- gut für Tests

---

## socat

- deutlich mächtiger
- komplexer
- mehr Funktionen

---

# Linux-Befehle

## Server starten

```bash
nc -l 1234
```

---

## Verbindung herstellen

```bash
nc 192.168.0.1 1234
```

---

## Port testen

```bash
nc -zv 192.168.0.1 22
```

---

## UDP verwenden

```bash
nc -u 192.168.0.1 1234
```

---

# Wichtige Merksätze

`nc` steht für Netcat.

Netcat kann Daten senden und empfangen.

`nc` wird häufig für Netzwerktests verwendet.

Mit `nc` kann man einfache Server und Clients erstellen.

`nc` unterstützt TCP und UDP.

---

# Fragen

## Wofür wird `nc` verwendet?

> [!spoiler]- Lösung anzeigen
> `nc` wird verwendet, um Netzwerkverbindungen zu testen sowie Daten zu senden und zu empfangen.

---

## Wie startet man einen einfachen Server mit `nc`?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> nc -l 1234
> ```

---

## Welche beiden Protokolle unterstützt `nc`?

> [!spoiler]- Lösung anzeigen
> ```text
> TCP und UDP
> ```