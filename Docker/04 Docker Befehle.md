# Häufig genutzte Docker-Befehle

## Images anzeigen

```bash
docker images
```

## Container anzeigen

```bash
docker ps
docker ps -a
```

## Image herunterladen

```bash
docker pull nginx
```

## Image bauen

```bash
docker build -t image-name .
```

## Container starten

```bash
docker run image-name
```

## Container im Hintergrund starten

```bash
docker run -d image-name
```

## Container benennen

```bash
docker run --name my-container image-name
```

## Port weiterleiten

```bash
docker run -p 8080:80 nginx
```

## Volume einbinden

```bash
docker run -v $(pwd):/workdir image-name
```

## Container stoppen

```bash
docker stop container-name
```

## Container starten

```bash
docker start container-name
```

## Container neu starten

```bash
docker restart container-name
```

## Container löschen

```bash
docker rm container-name
```

## Container erzwingen löschen

```bash
docker rm -f container-name
```

## Image löschen

```bash
docker rmi image-name
```

## In Container wechseln

```bash
docker exec -it container-name bash
```

oder

```bash
docker exec -it container-name sh
```

## Dateien in Container kopieren

```bash
docker cp datei.txt container-name:/pfad/
```

## Logs anzeigen

```bash
docker logs container-name
```

## Logs live verfolgen

```bash
docker logs -f container-name
```

## Alle gestoppten Container löschen

```bash
docker container prune
```

## Speicherverbrauch anzeigen

```bash
docker system df
```

## Docker Informationen

```bash
docker info
```

## Docker Version

```bash
docker version
```

---

# Docker Compose

## Container starten

```bash
docker compose up -d
```

## Container stoppen

```bash
docker compose down
```

## Neu bauen

```bash
docker compose up -d --build
```

## Logs anzeigen

```bash
docker compose logs -f
```

## Container anzeigen

```bash
docker compose ps
```

## Konfiguration prüfen

```bash
docker compose config
```

---  
  
## Merksätze  
  
- Image = Bauplan  
- Container = laufende Instanz  
- Dockerfile = Bauanleitung für Images  
- Docker Compose = Verwaltung mehrerer Container  
- Ports verbinden Host und Container  
- Volumes speichern Daten dauerhaft  
- Environment übergibt Konfigurationswerte  
- Container entstehen aus Images  
- Ein Image kann mehrere Container besitzen