
> [!info]
> ## Erklärung
>
> API steht für:
>
> ```text
> Application Programming Interface
> ```
>
> APIs ermöglichen die Kommunikation zwischen Programmen.
>
> Mit APIs kann man:
>
> - Daten senden
> - Daten empfangen
> - Dienste nutzen
> - Anwendungen verbinden

---

# Beispiel

## Erklärung

Eine App fragt Daten von einem Server an.

```text
App → API → Server → Antwort
```

---

# API im Alltag

## Beispiele

- Wetter-Apps
- Login mit Google
- GitHub API
- Discord Bots
- Zahlungsdienste
- Online-Shops

---

# HTTP

## Erklärung

Die meisten APIs verwenden HTTP oder HTTPS.

---

# HTTPS

## Erklärung

HTTPS ist die sichere Version von HTTP.

---

# URL

## Beispiel

```text
https://api.example.com/users
```

---

# Aufbau einer URL

| Teil | Bedeutung |
|---|---|
| `https://` | Protokoll |
| `api.example.com` | Domain |
| `/users` | Endpoint |

---

# Endpoints

## Erklärung

Endpoints sind bestimmte API-Adressen.

---

## Beispiele

```text
/users
/products
/messages
/login
```

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

`GET` lädt Daten.

### Beispiel

```http
GET /users
```

---

# POST Request

## Erklärung

`POST` sendet Daten.

### Beispiel

```http
POST /users
```

---

# JSON

## Erklärung

APIs verwenden häufig JSON.

---

# Beispiel

```json
{
    "name": "Max",
    "age": 25
}
```

---

# JSON Aufbau

| Zeichen | Bedeutung |
|---|---|
| `{}` | Objekt |
| `[]` | Liste |
| `:` | Zuweisung |
| `,` | Trenner |

---

# API Antwort

## Beispiel

```json
{
    "id": 1,
    "name": "Max"
}
```

---

# Statuscodes

| Code | Bedeutung |
|---|---|
| `200` | Erfolg |
| `201` | Erstellt |
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

# API testen mit curl

## GET

```bash
curl https://api.example.com/users
```

---

## POST

```bash
curl -X POST https://api.example.com/users
```

---

# JSON senden

## Beispiel

```bash
curl -X POST https://api.example.com/users \
-H "Content-Type: application/json" \
-d '{"name":"Max"}'
```

---

# API testen mit Postman

## Erklärung

Postman ist ein Tool zum Testen von APIs.

---

# REST API

## Erklärung

REST ist ein häufig verwendeter API-Stil.

REST verwendet:

- HTTP
- URLs
- JSON
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

# Parameter

## Erklärung

Parameter übergeben zusätzliche Daten.

---

# Query Parameter

## Beispiel

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

# Authentifizierung

## Erklärung

Viele APIs benötigen Anmeldung.

---

# API-Key

## Beispiel

```text
apikey=123456
```

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
> API-Keys und Tokens niemals öffentlich hochladen.

---

# `.env`

## Erklärung

API-Keys werden oft in `.env` Dateien gespeichert.

### Beispiel

```env
API_KEY=123456
```

---

# Pagination

## Erklärung

Große Datenmengen werden oft aufgeteilt.

---

# Beispiel

```text
/users?page=1
/users?page=2
```

---

# Rate Limit

## Erklärung

Viele APIs begrenzen Anfragen.

---

# Beispiel

```text
100 Requests pro Minute
```

---

# Häufige Datenformate

| Format | Verwendung |
|---|---|
| JSON | häufigste API-Struktur |
| XML | ältere APIs |
| CSV | Tabellen |
| HTML | Webseiten |

---

# API Dokumentation

## Erklärung

APIs besitzen oft Dokumentationen.

Typischer Inhalt:

- Endpoints
- Parameter
- Beispiele
- Statuscodes

---

# Bekannte APIs

| API | Verwendung |
|---|---|
| GitHub API | GitHub Daten |
| Discord API | Bots |
| OpenWeather API | Wetter |
| Spotify API | Musikdaten |

---

# APIs in Java

## Beispiel mit HttpClient

```java
HttpClient client = HttpClient.newHttpClient();
```

---

# APIs in Python

## Beispiel mit requests

```python
import requests

response = requests.get("https://api.example.com")
```

---

# Häufige Probleme

## 401 Unauthorized

### Ursache

Fehlender oder falscher Token.

---

## 404 Not Found

### Ursache

Falscher Endpoint.

---

## 500 Server Error

### Ursache

Fehler auf dem Server.

---

# Gute Praktiken

## Empfehlung

- Tokens geheim halten
- Statuscodes prüfen
- Fehler behandeln
- Dokumentation lesen
- Rate Limits beachten

---

# Verwandte Themen

- [[HTTP]]
- [[JSON]]
- [[REST]]
- [[curl]]
- [[Postman]]
- [[Backend]]

---

> [!important]
> ## Merksatz
>
> APIs ermöglichen die Kommunikation zwischen Programmen über standardisierte Schnittstellen.

---

# Fragen

## Was bedeutet API?

> [!spoiler]- Lösung anzeigen
> Application Programming Interface.

---

## Was macht ein `GET` Request?

> [!spoiler]- Lösung anzeigen
> Lädt Daten von einem Server.

---

## Wofür wird `POST` verwendet?

> [!spoiler]- Lösung anzeigen
> Zum Senden von Daten.

---

## Was ist JSON?

> [!spoiler]- Lösung anzeigen
> Ein häufig verwendetes Datenformat für APIs.

---

## Was bedeutet Statuscode `404`?

> [!spoiler]- Lösung anzeigen
> Die angeforderte Ressource wurde nicht gefunden.

---

## Warum sollte man API-Keys geheim halten?

> [!spoiler]- Lösung anzeigen
> Damit niemand unbefugt auf die API zugreifen kann.