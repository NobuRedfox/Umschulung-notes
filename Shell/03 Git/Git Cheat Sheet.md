
> [!info]
> ## Erklärung
>
> Git ist ein Versionsverwaltungssystem.
>
> Mit Git kann man:
>
> - Änderungen speichern
> - Projekte versionieren
> - mit anderen zusammenarbeiten
> - alte Versionen wiederherstellen
> - Code auf Plattformen wie GitHub hochladen

---

# Grundkonzept

Git arbeitet meistens mit diesen Bereichen:

```text
Arbeitsordner
↓
Staging Area
↓
Commit-Historie
↓
Remote Repository (GitHub)
```

---

# Repository erstellen

## git init

### Erklärung

`git init` erstellt ein neues Git-Repository.

### Beispiel

```bash
git init
```

---

## git clone

### Erklärung

`git clone` lädt ein bestehendes Repository herunter.

### Beispiel

```bash
git clone https://github.com/user/repo.git
```

---

# Status prüfen

## git status

### Erklärung

`git status` zeigt den aktuellen Zustand des Repositories an.

### Beispiel

```bash
git status
```

---

# Dateien hinzufügen

## git add

### Erklärung

`git add` fügt Änderungen zur Staging Area hinzu.

### Beispiele

```bash
git add datei.txt

git add .
```

---

> [!important]
> `git add .` fügt alle Änderungen im aktuellen Ordner hinzu.

---

# Änderungen speichern

## git commit

### Erklärung

`git commit` speichert Änderungen dauerhaft in der Git-Historie.

### Beispiele

```bash
git commit -m "Erster Commit"

git commit -m "Bug behoben"
```

---

# Mit GitHub verbinden

## git remote add origin

### Erklärung

Verbindet das lokale Repository mit GitHub.

### Beispiel

```bash
git remote add origin https://github.com/user/repo.git
```

---

# Änderungen hochladen

## git push

### Erklärung

`git push` lädt Commits auf GitHub hoch.

### Beispiele

```bash
git push

git push origin main
```

---

# Änderungen herunterladen

## git pull

### Erklärung

`git pull` lädt neue Änderungen herunter und merged sie automatisch.

### Beispiel

```bash
git pull
```

---

## git fetch

### Erklärung

`git fetch` lädt Änderungen herunter, merged sie aber noch nicht.

### Beispiel

```bash
git fetch
```

---

> [!important]
> ## Unterschied
>
> - `fetch` → nur herunterladen
> - `pull` → herunterladen + zusammenführen

---

# Branches

## git branch

### Erklärung

`git branch` zeigt oder erstellt Branches.

### Beispiele

```bash
git branch

git branch feature-login
```

---

## git switch

### Erklärung

`git switch` wechselt den Branch.

### Beispiele

```bash
git switch main

git switch feature-login
```

---

## Branch erstellen und wechseln

```bash
git switch -c feature-login
```

---

# Branches zusammenführen

## git merge

### Erklärung

`git merge` kombiniert Branches.

### Beispiel

```bash
git merge feature-login
```

---

# Änderungen ansehen

## git diff

### Erklärung

`git diff` zeigt Änderungen an Dateien.

### Beispiele

```bash
git diff

git diff datei.txt
```

---

# Commit-Historie

## git log

### Erklärung

`git log` zeigt die Commit-Historie an.

### Beispiele

```bash
git log

git log --oneline
```

---

# Dateien ignorieren

## .gitignore

### Erklärung

`.gitignore` verhindert, dass bestimmte Dateien von Git verfolgt werden.

### Beispiel

```gitignore
.idea/
*.iml
__pycache__/
out/
```

---

> [!warning]
> Dateien, die bereits getrackt wurden, ignoriert `.gitignore` nicht automatisch.

---

# Änderungen rückgängig machen

## git restore

### Erklärung

`git restore` verwirft Änderungen an Dateien.

### Beispiel

```bash
git restore datei.txt
```

---

## git reset

### Erklärung

`git reset` entfernt Änderungen aus der Staging Area.

### Beispiele

```bash
git reset

git reset datei.txt
```

---

## git revert

### Erklärung

`git revert` erstellt einen neuen Commit, der Änderungen rückgängig macht.

### Beispiel

```bash
git revert COMMIT_ID
```

---

# Temporär speichern

## git stash

### Erklärung

`git stash` speichert unfertige Änderungen temporär.

### Beispiele

```bash
git stash

git stash pop
```

---

# Tags

## Erklärung

Tags markieren wichtige Versionen.

### Beispiele

```bash
git tag v1.0

git tag
```

---

# Häufige Befehle

## Täglicher Workflow

```bash
git status

git add .

git commit -m "Beschreibung"

git push
```

---

# Typische Probleme

## Merge-Konflikte

### Erklärung

Ein Merge-Konflikt entsteht, wenn zwei Personen dieselbe Datei ändern.

---

## Detached HEAD

### Erklärung

Detached HEAD bedeutet, dass man sich nicht auf einem normalen Branch befindet.

---

# Nützliche Befehle

## git rm

### Erklärung

Entfernt Dateien aus Git.

### Beispiele

```bash
git rm datei.txt

git rm --cached datei.txt
```

---

## git mv

### Erklärung

Verschiebt oder benennt Dateien um.

### Beispiel

```bash
git mv alt.txt neu.txt
```

---

# GitHub

## Erklärung

GitHub ist eine Plattform für Git-Repositories.

Mit GitHub kann man:

- Code speichern
- Projekte teilen
- Pull Requests erstellen
- im Team arbeiten

---

# Wichtige Begriffe

| Begriff | Bedeutung |
|---|---|
| Repository | Git-Projekt |
| Commit | Gespeicherte Änderung |
| Branch | Entwicklungszweig |
| Merge | Branches zusammenführen |
| Remote | Externes Repository |
| Clone | Repository herunterladen |
| Push | Änderungen hochladen |
| Pull | Änderungen herunterladen |

---

# Verwandte Themen

- [[GitHub]]
- [[Linux]]
- [[Shell]]
- [[Terminal]]
- [[Git Branches]]
- [[.gitignore]]

---

> [!important]
> ## Merksatz
>
> Git speichert Änderungen an Projekten und ermöglicht Zusammenarbeit im Team.

---

# Fragen

## Was macht `git status`?

> [!spoiler]- Lösung anzeigen
> `git status` zeigt den aktuellen Zustand des Repositories an.

---

## Was macht `git add`?

> [!spoiler]- Lösung anzeigen
> `git add` fügt Änderungen zur Staging Area hinzu.

---

## Was macht `git commit`?

> [!spoiler]- Lösung anzeigen
> `git commit` speichert Änderungen dauerhaft in der Git-Historie.

---

## Unterschied zwischen `git fetch` und `git pull`?

> [!spoiler]- Lösung anzeigen
> `fetch` lädt Änderungen nur herunter.
>
> `pull` lädt Änderungen herunter und merged sie automatisch.

---

## Was ist ein Branch?

> [!spoiler]- Lösung anzeigen
> Ein Branch ist ein separater Entwicklungszweig.

---

## Wofür wird `.gitignore` verwendet?

> [!spoiler]- Lösung anzeigen
> `.gitignore` verhindert, dass bestimmte Dateien von Git verfolgt werden.