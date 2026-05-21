
> [!info]
> ## Erklärung
>
> GitHub ist eine Plattform für Git-Repositories.
>
> Mit GitHub kann man:
>
> - Code speichern
> - Projekte verwalten
> - im Team arbeiten
> - Pull Requests erstellen
> - Open Source Projekte veröffentlichen

---

# Git vs GitHub

| Begriff | Bedeutung |
|---|---|
| Git | Versionsverwaltungssystem |
| GitHub | Plattform für Git-Repositories |

---

# Repository erstellen

## Erklärung

Ein Repository ist ein Projekt auf GitHub.

### Möglichkeiten

- öffentlich (`public`)
- privat (`private`)

---

# Repository klonen

## git clone

### Erklärung

Lädt ein Repository herunter.

### Beispiel

```bash
git clone https://github.com/user/repo.git
```

---

# Mit Repository verbinden

## git remote add origin

### Erklärung

Verbindet lokales Projekt mit GitHub.

### Beispiel

```bash
git remote add origin https://github.com/user/repo.git
```

---

# Änderungen hochladen

## git push

### Erklärung

Lädt Commits zu GitHub hoch.

### Beispiele

```bash
git push

git push origin main
```

---

# Änderungen herunterladen

## git pull

### Erklärung

Lädt Änderungen von GitHub herunter.

### Beispiel

```bash
git pull
```

---

# Branches auf GitHub

## Erklärung

Branches können separat hochgeladen werden.

### Beispiel

```bash
git push origin feature-login
```

---

# Pull Requests

## Erklärung

Pull Requests dienen dazu:

- Änderungen zu prüfen
- Code zu diskutieren
- Branches zu mergen

---

# Typischer Pull-Request Workflow

## Ablauf

1. Branch erstellen
2. Änderungen committen
3. Branch pushen
4. Pull Request öffnen
5. Review durchführen
6. Merge durchführen

---

# Forks

## Erklärung

Ein Fork ist eine Kopie eines fremden Repositories.

Forks werden oft bei Open Source Projekten verwendet.

---

# Issues

## Erklärung

Issues werden für:

- Bugs
- Aufgaben
- Ideen
- Diskussionen

verwendet.

---

# README.md

## Erklärung

`README.md` beschreibt das Projekt.

Typischer Inhalt:

- Projektbeschreibung
- Installation
- Nutzung
- Screenshots
- Befehle

---

# .gitignore

## Erklärung

`.gitignore` verhindert das Tracken bestimmter Dateien.

### Beispiel

```gitignore
.idea/
*.iml
out/
__pycache__/
```

---

# Public vs Private

| Typ | Sichtbarkeit |
|---|---|
| Public | Jeder kann das Repository sehen |
| Private | Nur eingeladene Personen |

---

# Mitarbeiter hinzufügen

## Erklärung

Bei privaten Repositories müssen Benutzer eingeladen werden.

---

## Ablauf

1. Repository öffnen
2. Settings
3. Collaborators
4. Benutzer hinzufügen

---

# SSH vs HTTPS

## HTTPS

### Beispiel

```bash
https://github.com/user/repo.git
```

### Vorteile

- einfacher Einstieg
- kein SSH-Key nötig

---

## SSH

### Beispiel

```bash
git@github.com:user/repo.git
```

### Vorteile

- komfortabler
- kein Passwort nötig
- häufig von Entwicklern genutzt

---

# SSH-Key erstellen

## Beispiel

```bash
ssh-keygen -t ed25519 -C "mail@example.com"
```

---

# SSH testen

## Beispiel

```bash
ssh -T git@github.com
```

---

# Repository Status prüfen

## git remote -v

### Erklärung

Zeigt verbundene GitHub-Repositories an.

### Beispiel

```bash
git remote -v
```

---

# Häufige Befehle

## Täglicher Workflow

```bash
git status

git add .

git commit -m "Änderung"

git push
```

---

# Markdown

## Erklärung

GitHub verwendet Markdown für Dokumentation.

### Beispiele

```markdown
# Überschrift

## Unterüberschrift

- Liste
```

---

# GitHub Profile

## Erklärung

GitHub-Profile zeigen:

- Projekte
- Beiträge
- Commits
- Open Source Aktivitäten

---

# Gute Repository-Struktur

## Beispiel

```text
projekt/
├── src/
├── docs/
├── README.md
├── .gitignore
└── LICENSE
```

---

# Häufige Probleme

## Merge-Konflikte

Entstehen bei widersprüchlichen Änderungen.

---

## Push rejected

### Ursache

Remote-Repository enthält neuere Änderungen.

### Lösung

```bash
git pull
```

---

## Authentication failed

### Ursache

Falsche Zugangsdaten oder fehlender SSH-Key.

---

# Open Source

## Erklärung

Viele Projekte auf GitHub sind Open Source.

Dadurch kann man:

- Code lernen
- beitragen
- Pull Requests erstellen
- Projekte analysieren

---

# GitHub Actions

## Erklärung

GitHub Actions automatisieren Prozesse.

Beispiele:

- Tests
- Builds
- Deployments

---

# GitHub Desktop

## Erklärung

GitHub Desktop ist eine grafische Oberfläche für Git und GitHub.

---

# Verwandte Themen

- [[Git]]
- [[Git Branches]]
- [[Shell]]
- [[SSH]]
- [[Markdown]]
- [[.gitignore]]

---

> [!important]
> ## Merksatz
>
> GitHub ermöglicht Zusammenarbeit und Versionsverwaltung für Softwareprojekte.

---

# Fragen

## Was ist GitHub?

> [!spoiler]- Lösung anzeigen
> GitHub ist eine Plattform für Git-Repositories.

---

## Unterschied zwischen Git und GitHub?

> [!spoiler]- Lösung anzeigen
> Git ist das Versionsverwaltungssystem.
>
> GitHub ist die Online-Plattform dafür.

---

## Was ist ein Pull Request?

> [!spoiler]- Lösung anzeigen
> Ein Pull Request dient zum Prüfen und Mergen von Änderungen.

---

## Was macht `git clone`?

> [!spoiler]- Lösung anzeigen
> Lädt ein Repository herunter.

---

## Warum verwendet man `.gitignore`?

> [!spoiler]- Lösung anzeigen
> Um bestimmte Dateien von Git auszuschließen.

---

## Unterschied zwischen Public und Private Repository?

> [!spoiler]- Lösung anzeigen
> Public ist öffentlich sichtbar.
>
> Private nur für eingeladene Benutzer.