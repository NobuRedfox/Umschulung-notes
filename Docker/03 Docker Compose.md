## build

Image aus einem Dockerfile bauen.

```yaml
build: .
```

Beispiel:

```yaml
services:
  ssh:
    build: .
```

Docker baut das Image automatisch beim Start.

---

## volumes

Verzeichnisse einbinden.

```yaml
volumes:
  - ./data:/data
```

Bedeutung:

```text
Host-Verzeichnis
      ↓
Container-Verzeichnis
```

Daten bleiben erhalten, auch wenn der Container gelöscht wird.

Beispiele:

```yaml
volumes:
  - ./mysql:/var/lib/mysql
```

```yaml
volumes:
  - ./vw-data:/data
```

---

## environment

Umgebungsvariablen.

```yaml
environment:
  USERNAME=nobu
```

oder

```yaml
environment:
  - USERNAME=nobu
```

Mit .env-Datei:

```yaml
environment:
  - MYSQL_PASSWORD=${MYSQL_PASSWORD}
```

---

## .env

Speichert Konfigurationswerte und Passwörter getrennt von der Compose-Datei.

Beispiel:

```text
MYSQL_PASSWORD=geheim
MYSQL_USER=nobu
```

Compose liest die Werte automatisch ein.
