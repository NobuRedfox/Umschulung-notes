## Definition

Docker ist eine Plattform zum Erstellen, Verteilen und Ausführen von Containern.

Container enthalten Anwendungen mit allen benötigten Abhängigkeiten.

Dadurch laufen Programme auf verschiedenen Systemen identisch.

---

## Vorteile

- einfache Bereitstellung
- reproduzierbare Umgebungen
- schnelle Starts
- Isolation von Anwendungen
- geringer Ressourcenverbrauch

---

## Begriffe

### Image

Ein Image ist die Vorlage bzw. der Bauplan eines Containers.

Beispiele:

- nginx:alpine
- ubuntu:24.04
- python:3

---

### Container

Ein Container ist eine laufende Instanz eines Images.

Ein Image kann mehrere Container besitzen.

---

### Dockerfile

Beschreibt, wie ein Image gebaut wird.

---

### Docker Compose

Verwaltet und startet mehrere Container gleichzeitig.

Die Konfiguration erfolgt über eine `compose.yaml`.

---

## Beispiele

Docker Image:

- nginx:alpine

Docker Container:

- my-web

Docker Compose:

- OwnCloud + MariaDB + Redis

---

## Merksätze

- Image = Bauplan
- Container = laufende Instanz
- Dockerfile = Bauanleitung für Images
- Docker Compose = Verwaltung mehrerer Container