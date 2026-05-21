
> [!info]
> ## Bedeutung
> `ping`
>
> testet die Erreichbarkeit eines anderen Geräts im Netzwerk.

---

# Definition

`ping` sendet Netzwerkpakete an ein Zielgerät
und wartet auf eine Antwort.

Dadurch kann geprüft werden:
- ob ein Gerät erreichbar ist
- wie schnell die Verbindung ist
- ob Paketverlust existiert

---

# ICMP

`ping` verwendet das Protokoll:

```text
ICMP
```

---

# Zweck von ping

Mit `ping` kann man:
- Netzwerkverbindungen testen
- Router prüfen
- Internet testen
- DNS prüfen
- Paketverlust erkennen

---

# Einfaches Beispiel

```bash
ping google.com
```

---

# Beispielausgabe

```text
64 bytes from 142.250.185.78:
icmp_seq=1 ttl=117 time=15.2 ms
```

---

# Erklärung

## icmp_seq

```text
Nummer des Pakets
```

---

## ttl

```text
Time To Live
```

Wie viele Router ein Paket maximal durchlaufen darf.

---

## time

```text
Antwortzeit
```

Meist in Millisekunden.

---

# Verbindung testen

## Router testen

```bash
ping 192.168.0.1
```

---

## Internet testen

```bash
ping 8.8.8.8
```

---

## DNS testen

```bash
ping google.com
```

---

# Unterschied

## ping 8.8.8.8

```text
Testet Netzwerkverbindung
```

---

## ping google.com

```text
Testet zusätzlich DNS
```

---

# Anzahl der Pakete begrenzen

```bash
ping -c 4 google.com
```

---

# Bedeutung

```text
Sende nur 4 Pakete
```

---

# Dauerping stoppen

```text
Strg + C
```

---

# Paketverlust

Am Ende zeigt `ping` oft:

```text
packet loss
```

---

# Beispiel

```text
0% packet loss
```

Bedeutung:

```text
Alle Pakete angekommen
```

---

# Hoher Ping

Ein hoher Ping bedeutet:
- langsame Verbindung
- hohe Latenz

---

# Beispielwerte

## Sehr gut

```text
< 10 ms
```

---

## Gut

```text
10 - 30 ms
```

---

## Langsam

```text
> 100 ms
```

---

# IPv6-Ping

```bash
ping6 google.com
```

oder:

```bash
ping -6 google.com
```

---

# Beispiel mit Containern

```bash
ip netns exec Apfel ping 10.0.0.2
```

---

# Typische Einsatzgebiete

- Netzwerkfehler finden
- Internet testen
- Router prüfen
- Container testen
- Paketverlust prüfen

---

# Typische Probleme

## Host unreachable

```text
Ziel nicht erreichbar
```

---

## Unknown host

```text
DNS funktioniert nicht
```

---

## 100% packet loss

```text
Keine Verbindung
```

---

# ping vs nc

## ping

```text
ICMP
Erreichbarkeit testen
```

---

## nc

```text
TCP/UDP
Ports testen
```

---

# Linux-Befehle

## Einfacher Ping

```bash
ping google.com
```

---

## Nur 4 Pakete senden

```bash
ping -c 4 google.com
```

---

## IPv6 verwenden

```bash
ping -6 google.com
```

---

# Wichtige Merksätze

`ping` testet die Erreichbarkeit von Geräten.

`ping` verwendet ICMP.

Mit `ping` kann man Latenz und Paketverlust messen.

`ping 8.8.8.8` testet Netzwerkverbindung.

`ping google.com` testet zusätzlich DNS.

---

# Fragen

## Wofür wird `ping` verwendet?

> [!spoiler]- Lösung anzeigen
> `ping` testet die Erreichbarkeit eines anderen Geräts im Netzwerk.

---

## Welches Protokoll verwendet `ping`?

> [!spoiler]- Lösung anzeigen
> ```text
> ICMP
> ```

---

## Wofür steht die Zeitangabe bei `ping`?

> [!spoiler]- Lösung anzeigen
> Die Zeit zeigt die Antwortdauer des Zielgeräts in Millisekunden an.