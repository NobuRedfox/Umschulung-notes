
> [!info]
> ## Bedeutung
> DNS = Domain Name System

---

# Definition

DNS übersetzt Domainnamen in IP-Adressen.

Beispiel:

```text
google.com  ->  142.250.185.78
```

Menschen merken sich Namen leichter als IP-Adressen.

Darum benutzt das Internet DNS.

---

# Beispiel

Wenn du im Browser eingibst:

```text
google.com
```

kennt dein Computer zuerst die IP-Adresse nicht.

Darum fragt er einen DNS-Server:

```text
"Welche IP-Adresse gehört zu google.com?"
```

Der DNS-Server antwortet dann z.B.:

```text
142.250.185.78
```

Danach kann die Verbindung aufgebaut werden.

---

# Vergleich

## Ohne DNS

```text
142.250.185.78
```

Schwer zu merken.

---

## Mit DNS

```text
google.com
```

Einfach zu merken.

---

# Bekannte DNS-Server

## Google DNS

```text
8.8.8.8
8.8.4.4
```

---

## Cloudflare DNS

```text
1.1.1.1
1.0.0.1
```

---

## Quad9 DNS

```text
9.9.9.9
```

---

# Linux-Befehle

## DNS testen mit ping

```bash
ping google.com
```

Wenn DNS funktioniert,
wird der Name automatisch in eine IP-Adresse übersetzt.

---

## DNS direkt abfragen

```bash
nslookup google.com
```

---

## Alternativ mit dig

```bash
dig google.com
```

---

# DNS-Konfiguration unter Linux

## Datei anzeigen

```bash
cat /etc/resolv.conf
```

Beispiel:

```text
nameserver 8.8.8.8
```

Das bedeutet:

```text
Benutze 8.8.8.8 als DNS-Server.
```

---

# DNS in Containern

In virtuellen Containern oder Namespaces
muss oft manuell ein DNS-Server gesetzt werden.

Beispiel:

```bash
mkdir -p /etc/netns/Apfel

echo "nameserver 8.8.8.8" > /etc/netns/Apfel/resolv.conf
```

---

# Typische Fehler

## Internet funktioniert,
## aber Webseiten nicht

Symptom:

```bash
ping 8.8.8.8
```

funktioniert,

aber:

```bash
ping google.com
```

funktioniert nicht.

Dann ist meistens DNS kaputt.

---

# DNS-Auflösung

Der Vorgang heißt:

```text
Namensauflösung
```

oder:

```text
DNS-Auflösung
```

---

# Wichtige Merksätze

DNS übersetzt Domainnamen in IP-Adressen.

Ohne DNS müsste man IP-Adressen auswendig lernen.

DNS ist eine Art Telefonbuch des Internets.

DNS benutzt normalerweise Port 53.

DNS arbeitet auf Layer 7 des OSI-Modells.

---

# Fragen

## Wofür wird DNS verwendet?

> [!spoiler]- Lösung anzeigen
> DNS übersetzt Domainnamen in IP-Adressen.

---

## Woran erkennt man oft ein DNS-Problem?

> [!spoiler]- Lösung anzeigen
> Wenn `ping 8.8.8.8` funktioniert,
> aber `ping google.com` nicht funktioniert.

---

## Welche bekannten öffentlichen DNS-Server gibt es?

> [!spoiler]- Lösung anzeigen
> Beispiele:
>
> - Google DNS → `8.8.8.8`
> - Cloudflare DNS → `1.1.1.1`
> - Quad9 DNS → `9.9.9.9`