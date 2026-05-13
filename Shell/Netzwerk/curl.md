
> [!info]
> ## Erklärung
>
> `curl` ist ein Kommandozeilenprogramm für Datenübertragungen.
>
> Mit `curl` kann man:
>
> - Webseiten abrufen
> - APIs testen
> - Dateien herunterladen
> - Daten senden
> - HTTP-Requests ausführen

---

# Einfacher Request

## Erklärung

Ruft Inhalte einer Webseite oder API ab.

### Beispiel

```bash
curl https://example.com
```

---

# Datei herunterladen

## Erklärung

Lädt eine Datei herunter.

### Beispiel

```bash
curl -O https://example.com/bild.jpg
```

---

# Datei unter anderem Namen speichern

## Beispiel

```bash
curl -o bild.jpg https://example.com/image.png
```

---

# HTTP Methode festlegen

## Erklärung

Mit `-X` wird die HTTP-Methode angegeben.

### Beispiele

```bash
curl -X GET https://example.com

curl -X POST https://example.com
```

---

# Header senden

## Erklärung

Mit `-H` werden Header übertragen.

### Beispiel

```bash
curl -H "Content-Type: application/json" https://example.com
```

---

# JSON senden

## Erklärung

Mit `-d` werden Daten gesendet.

### Beispiel

```bash
curl -X POST https://example.com/users \
-H "Content-Type: application/json" \
-d '{"name":"Max"}'
```

---

# API testen

## GET Request

```bash
curl https://api.example.com/users
```

---

## POST Request

```bash
curl -X POST https://api.example.com/users \
-H "Content-Type: application/json" \
-d '{"name":"Max"}'
```

---

# Antwort-Header anzeigen

## Beispiel

```bash
curl -i https://example.com
```

---

# Nur Header anzeigen

## Beispiel

```bash
curl -I https://example.com
```

---

# Redirects folgen

## Erklärung

Mit `-L` folgt `curl` Weiterleitungen.

### Beispiel

```bash
curl -L https://example.com
```

---

# Stille Ausgabe

## Erklärung

`-s` unterdrückt Fortschrittsanzeigen.

### Beispiel

```bash
curl -s https://example.com
```

---

# Ausgabe speichern

## Beispiel

```bash
curl https://example.com > datei.html
```

---

# Authentifizierung

## Basic Auth

### Beispiel

```bash
curl -u user:pass https://example.com
```

---

# Bearer Token

## Beispiel

```bash
curl -H "Authorization: Bearer TOKEN" https://example.com
```

---

> [!warning]
> ## Wichtig
>
> Tokens und Passwörter niemals öffentlich teilen.

---

# Dateien hochladen

## Erklärung

Mit `-F` können Dateien gesendet werden.

### Beispiel

```bash
curl -F "file=@bild.jpg" https://example.com/upload
```

---

# JSON Antwort formatieren

## Mit jq

### Beispiel

```bash
curl https://api.example.com/users | jq
```

---

# User-Agent ändern

## Beispiel

```bash
curl -A "MeinBrowser" https://example.com
```

---

# Verbindung testen

## Erklärung

`curl` wird oft zum Testen von Webseiten und APIs verwendet.

### Beispiel

```bash
curl -I https://google.com
```

---

# HTTPS

## Erklärung

`curl` unterstützt HTTP und HTTPS.

---

# SSL ignorieren

## Erklärung

`-k` ignoriert SSL-Zertifikate.

### Beispiel

```bash
curl -k https://example.com
```

---

> [!warning]
> ## Vorsicht
>
> `-k` sollte nur zu Testzwecken verwendet werden.

---

# Download fortsetzen

## Beispiel

```bash
curl -C - -O https://example.com/file.zip
```

---

# Mehrere Dateien herunterladen

## Beispiel

```bash
curl -O https://example.com/a.txt \
-O https://example.com/b.txt
```

---

# Häufige Statuscodes

| Code | Bedeutung |
|---|---|
| `200` | Erfolg |
| `301` | Weiterleitung |
| `400` | Fehlerhafte Anfrage |
| `401` | Nicht autorisiert |
| `404` | Nicht gefunden |
| `500` | Serverfehler |

---

# Häufige Flags

| Flag | Bedeutung |
|---|---|
| `-X` | HTTP Methode |
| `-H` | Header |
| `-d` | Daten senden |
| `-O` | Originalname speichern |
| `-o` | Eigener Dateiname |
| `-I` | Nur Header |
| `-i` | Header anzeigen |
| `-L` | Redirects folgen |
| `-s` | Stille Ausgabe |
| `-k` | SSL ignorieren |

---

# Typischer API Request

## Beispiel

```bash
curl -X POST https://api.example.com/login \
-H "Content-Type: application/json" \
-d '{"user":"Max","password":"1234"}'
```

---

# Typischer Workflow

## API testen

```bash
curl https://api.example.com/users
```

---

## JSON senden

```bash
curl -X POST https://api.example.com/users \
-H "Content-Type: application/json" \
-d '{"name":"Max"}'
```

---

## Datei herunterladen

```bash
curl -O https://example.com/file.zip
```

---

# Verwandte Themen

- [[APIs]]
- [[HTTP]]
- [[JSON]]
- [[Shell]]
- [[Linux]]
- [[Postman]]

---

> [!important]
> ## Merksatz
>
> `curl` ermöglicht HTTP-Requests und Datenübertragungen direkt im Terminal.

---

# Fragen

## Was macht `curl`?

> [!spoiler]- Lösung anzeigen
> `curl` führt Datenübertragungen und HTTP-Requests aus.

---

## Was macht `-O`?

> [!spoiler]- Lösung anzeigen
> Speichert eine Datei unter ihrem Originalnamen.

---

## Was macht `-H`?

> [!spoiler]- Lösung anzeigen
> Sendet zusätzliche Header.

---

## Was macht `-X POST`?

> [!spoiler]- Lösung anzeigen
> Führt einen POST-Request aus.

---

## Was macht `-L`?

> [!spoiler]- Lösung anzeigen
> Folgt Weiterleitungen.

---

## Warum wird `curl` oft bei APIs verwendet?

> [!spoiler]- Lösung anzeigen
> Weil APIs häufig über HTTP angesprochen werden.