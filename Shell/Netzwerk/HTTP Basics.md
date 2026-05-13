
> [!info]
> ## Erklärung
>
> HTTP steht für:
>
> ```text
> HyperText Transfer Protocol
> ```
>
> HTTP ermöglicht die Kommunikation zwischen:
>
> - Browsern
> - Webseiten
> - APIs
> - Servern
>
> über das Internet.

---

# Grundprinzip

## Erklärung

Ein Client sendet eine Anfrage an einen Server.

```text
Client → Request → Server
Client ← Response ← Server
```

---

# Beispiele für Clients

- Browser
- Apps
- Spiele
- curl
- Postman

---

# HTTPS

## Erklärung

HTTPS ist die sichere Version von HTTP.

---

# Unterschied

| HTTP | HTTPS |
|---|---|
| unverschlüsselt | verschlüsselt |
| unsicher | sicher |
| Port 80 | Port 443 |

---

# URL Aufbau

## Beispiel

```text
https://example.com/users
```

---

# Bestandteile

| Teil | Bedeutung |
|---|---|
| `https://` | Protokoll |
| `example.com` | Domain |
| `/users` | Pfad / Endpoint |

---

# Requests

## Erklärung

Ein Request ist eine Anfrage an einen Server.

---

# Bestandteile eines Requests

- Methode
- URL
- Header
- Body

---

# HTTP Methoden

| Methode | Bedeutung |
|---|---|
| `GET` | Daten abrufen |
| `POST` | Daten senden |
| `PUT` | Daten ersetzen |
| `PATCH` | Daten teilweise ändern |
| `DELETE` | Daten löschen |

---

# GET Request

## Erklärung

Fordert Daten an.

### Beispiel

```http
GET /users
```

---

# POST Request

## Erklärung

Sendet Daten an den Server.

### Beispiel

```http
POST /users
```

---

# Responses

## Erklärung

Der Server antwortet mit einer Response.

---

# Bestandteile einer Response

- Statuscode
- Header
- Daten (Body)

---

# Statuscodes

| Code | Bedeutung |
|---|---|
| `200` | Erfolg |
| `201` | Erstellt |
| `301` | Weiterleitung |
| `400` | Fehlerhafte Anfrage |
| `401` | Nicht autorisiert |
| `403` | Verboten |
| `404` | Nicht gefunden |
| `500` | Serverfehler |

---

# Wichtige Statuscodes

## Beispiele

```text
200 OK
404 Not Found
500 Internal Server Error
```

---

# Header

## Erklärung

Header enthalten zusätzliche Informationen.

---

# Beispiele

```http
Content-Type: application/json

Authorization: Bearer TOKEN
```

---

# Content-Type

## Erklärung

Beschreibt das Datenformat.

---

# Beispiele

| Content-Type | Bedeutung |
|---|---|
| `text/html` | HTML |
| `application/json` | JSON |
| `text/plain` | einfacher Text |

---

# Body

## Erklärung

Der Body enthält die eigentlichen Daten.

---

# JSON Beispiel

```json
{
    "name": "Max",
    "age": 25
}
```

---

# Cookies

## Erklärung

Cookies speichern Informationen im Browser.

Beispiele:

- Login
- Sprache
- Einstellungen

---

# Sessions

## Erklärung

Sessions speichern Benutzerinformationen auf dem Server.

---

# Authentifizierung

## Erklärung

Viele Webseiten und APIs benötigen Anmeldung.

---

# Beispiele

- Passwort
- Session Cookie
- API-Key
- Bearer Token

---

# Bearer Token

## Beispiel

```http
Authorization: Bearer TOKEN
```

---

> [!warning]
> ## Wichtig
>
> Tokens niemals öffentlich teilen.

---

# Query Parameter

## Erklärung

Zusätzliche Informationen in der URL.

### Beispiel

```text
/users?page=2
```

---

# Path Parameter

## Beispiel

```text
/users/5
```

---

# Redirects

## Erklärung

Der Server leitet auf eine andere URL weiter.

### Beispiel

```text
301 Moved Permanently
```

---

# DNS

## Erklärung

DNS übersetzt Domains in IP-Adressen.

---

# Beispiel

```text
google.com → 142.250.x.x
```

---

# Ports

| Port | Verwendung |
|---|---|
| `80` | HTTP |
| `443` | HTTPS |
| `22` | SSH |

---

# REST

## Erklärung

REST ist ein häufiger Stil für APIs.

REST verwendet:

- HTTP
- JSON
- URLs
- Statuscodes

---

# Typische REST Endpoints

| Aktion | Endpoint |
|---|---|
| Benutzer anzeigen | `GET /users` |
| Benutzer erstellen | `POST /users` |
| Benutzer ändern | `PUT /users/1` |
| Benutzer löschen | `DELETE /users/1` |

---

# HTTP mit curl

## GET Request

```bash
curl https://example.com
```

---

## POST Request

```bash
curl -X POST https://example.com
```

---

# HTTP mit Browser

## Erklärung

Browser senden automatisch HTTP-Requests.

---

# Typischer Ablauf

```text
Browser → Request → Server
Browser ← HTML ← Server
```

---

# Häufige Probleme

## 404 Not Found

### Ursache

Die Seite existiert nicht.

---

## 401 Unauthorized

### Ursache

Nicht eingeloggt oder Token fehlt.

---

## 500 Internal Server Error

### Ursache

Fehler auf dem Server.

---

# Gute Praktiken

## Empfehlung

- HTTPS verwenden
- Tokens geheim halten
- Statuscodes prüfen
- Fehler behandeln

---

# Verwandte Themen

- [[APIs]]
- [[REST]]
- [[JSON]]
- [[curl]]
- [[Netzwerk]]
- [[Backend]]

---

> [!important]
> ## Merksatz
>
> HTTP ermöglicht die Kommunikation zwischen Clients und Servern im Internet.

---

# Fragen

## Was bedeutet HTTP?

> [!spoiler]- Lösung anzeigen
> HyperText Transfer Protocol.

---

## Unterschied zwischen HTTP und HTTPS?

> [!spoiler]- Lösung anzeigen
> HTTPS ist verschlüsselt und sicherer.

---

## Was macht ein `GET` Request?

> [!spoiler]- Lösung anzeigen
> Ruft Daten vom Server ab.

---

## Was bedeutet Statuscode `404`?

> [!spoiler]- Lösung anzeigen
> Die angeforderte Ressource wurde nicht gefunden.

---

## Wofür werden Header verwendet?

> [!spoiler]- Lösung anzeigen
> Für zusätzliche Informationen bei Requests und Responses.

---

## Was ist ein Bearer Token?

> [!spoiler]- Lösung anzeigen
> Ein Token zur Authentifizierung.