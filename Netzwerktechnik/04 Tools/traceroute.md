
> [!info]
> ## Bedeutung
> `traceroute`
>
> zeigt den Weg von Netzwerkpaketen durch verschiedene Router.

---

# Definition

`traceroute` zeigt,
über welche Router und Netzwerke Pakete ihr Ziel erreichen.

Dadurch kann man nachvollziehen:
- welchen Weg Pakete nehmen
- wo Netzwerkprobleme entstehen
- wie viele Router beteiligt sind

---

# Beispiel

```bash
traceroute google.com
```

---

# Beispielausgabe

```text
1  192.168.0.1
2  84.123.1.1
3  62.155.240.10
4  142.250.185.78
```

---

# Bedeutung

Jede Zeile zeigt:

```text
Einen Router auf dem Weg zum Ziel
```

Diese Zwischenstationen nennt man:

```text
Hops
```

---

# Hop

Ein Hop bedeutet:

```text
Ein Router-Schritt
```

---

# Beispielweg

```text
PC -> Router -> Provider -> Internet -> Zielserver
```

---

# TTL

`traceroute` arbeitet mit:

```text
TTL
```

---

# TTL

TTL bedeutet:

```text
Time To Live
```

TTL bestimmt,
wie viele Router ein Paket maximal passieren darf.

---

# Ablauf

`traceroute` sendet Pakete mit:
- TTL 1
- TTL 2
- TTL 3
- usw.

Jeder Router reduziert die TTL.

Wenn TTL:

```text
0
```

erreicht,
antwortet der Router.

Dadurch erkennt `traceroute` den Weg.

---

# Typische Einsatzgebiete

- Netzwerkprobleme finden
- langsame Verbindungen analysieren
- Routing prüfen
- Internetprobleme untersuchen

---

# Installation

## Debian/Ubuntu

```bash
sudo apt install traceroute
```

---

# Einfacher Test

```bash
traceroute google.com
```

---

# IPv4 verwenden

```bash
traceroute -4 google.com
```

---

# IPv6 verwenden

```bash
traceroute -6 google.com
```

---

# Numerische Ausgabe

```bash
traceroute -n google.com
```

---

# Bedeutung

```text
Keine DNS-Auflösung durchführen
```

Das macht die Ausgabe oft schneller.

---

# Unterschied zu ping

## ping

```text
Testet Erreichbarkeit
```

---

## traceroute

```text
Zeigt den Weg der Pakete
```

---

# Beispiel mit Containern

```bash
ip netns exec Apfel traceroute 8.8.8.8
```

---

# Typische Probleme

## * * *

Beispiel:

```text
* * *
```

Bedeutung:

```text
Router antwortet nicht
```

oder:
- Firewall blockiert Antwort
- ICMP deaktiviert

---

## Sehr viele Hops

Kann auf Routingprobleme hinweisen.

---

## Hohe Antwortzeiten

Kann auf:
- langsame Router
- Netzwerküberlastung
- schlechte Verbindung

hinweisen.

---

# traceroute und ICMP

Viele traceroute-Versionen verwenden:
- ICMP
- UDP
- manchmal TCP

---

# Linux-Befehle

## Einfacher traceroute

```bash
traceroute google.com
```

---

## IPv4 verwenden

```bash
traceroute -4 google.com
```

---

## IPv6 verwenden

```bash
traceroute -6 google.com
```

---

## Numerische Ausgabe

```bash
traceroute -n google.com
```

---

# traceroute vs tracepath

## traceroute

- umfangreicher
- mehr Optionen
- oft Root-Rechte nötig

---

## tracepath

- einfacher
- meist ohne sudo nutzbar

---

# Wichtige Merksätze

`traceroute` zeigt den Weg von Paketen durch Netzwerke.

Jeder Router auf dem Weg heißt Hop.

`traceroute` arbeitet mit TTL.

`traceroute` hilft bei der Fehlersuche in Netzwerken.

`traceroute` zeigt Routingwege und Zwischenrouter an.

---

# Fragen

## Wofür wird `traceroute` verwendet?

> [!spoiler]- Lösung anzeigen
> `traceroute` zeigt den Weg von Paketen durch verschiedene Router.

---

## Was ist ein Hop?

> [!spoiler]- Lösung anzeigen
> Ein Hop ist ein Router-Schritt auf dem Weg zum Ziel.

---

## Wofür steht TTL?

> [!spoiler]- Lösung anzeigen
> ```text
> Time To Live
> ```