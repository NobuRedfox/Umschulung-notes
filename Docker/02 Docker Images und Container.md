## Image

Ein Image ist die Vorlage bzw. der Bauplan eines Containers.

Ein Image enthält:
- Anwendung
- Bibliotheken
- Abhängigkeiten
- Konfigurationen

Beispiele:

- ubuntu
- nginx
- mariadb
- redis

---

## Container

Ein Container ist eine laufende Instanz eines Images.

Ein Image kann mehrere Container besitzen.

Beispiel:

Image:

```text
nginx:alpine
```

Container:

```text
my-web
```

---

## Unterschiede

Image:

- Vorlage
- unveränderlich
- wird gebaut oder heruntergeladen

Container:

- laufende Instanz
- kann gestartet oder gestoppt werden
- besitzt eigenen Prozess

---

## Image herunterladen

```bash
docker pull nginx
```

---

## Image erstellen

```bash
docker build -t python-test .
```

Bedeutung:

```text
-t           → Name vergeben
python-test  → Image-Name
.            → aktueller Ordner
```

---

## Container starten

```bash
docker run python-test
```

---

## Container im Hintergrund starten

```bash
docker run -d python-test
```

---

## Container anzeigen

Laufende Container:

```bash
docker ps
```

Alle Container:

```bash
docker ps -a
```

---

## Container stoppen

```bash
docker stop container-name
```

---

## Container löschen

```bash
docker rm container-name
```

---

## Image löschen

```bash
docker rmi image-name
```

---

## Merksätze

- Image = Bauplan
- Container = laufende Instanz
- Ein Image kann mehrere Container besitzen
- Container entstehen aus Images