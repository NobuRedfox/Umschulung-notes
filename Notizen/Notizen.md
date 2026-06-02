speicherleck.de/pv
NewPipe
Virtualisierung (Typ 1,2 container, cloud und beispiele)


## Docker
Ordner erstellen:
mkdir -p src/container-image

Zum Ordner wechseln:
cd src/container-image

Python-Datei erstellen:
vim app.py

Inhalt:

print("Hallo World")

Dockerfile erstellen:
vim Dockerfile

Inhalt:

FROM python:3.12

COPY app.py /app.py

CMD ["python", "/app.py"]

Dateien prüfen:
ls -l

Image bauen:
docker build -t python-test .

Images anzeigen:
docker images

Container starten:
docker run python-test


docker exec ssh-container mkdir -p /home/tux/.ssh
docker cp ~/.ssh/id_ed25519.pub ssh-container:/home/tux/.ssh/authorized_keys
docker exec ssh-container chown -R tux:tux /home/tux/.ssh
docker exec ssh-container chmod 700 /home/tux/.ssh
docker exec ssh-container chmod 600 /home/tux/.ssh/authorized_keys

