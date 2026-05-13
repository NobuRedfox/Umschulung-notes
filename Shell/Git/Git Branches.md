
> [!info]
> ## Erklärung
>
> Branches sind separate Entwicklungszweige in Git.
>
> Mit Branches kann man:
>
> - neue Features entwickeln
> - Fehler beheben
> - experimentieren
> - sicher im Team arbeiten
>
> ohne direkt `main` zu verändern.

---

# Warum Branches?

## Erklärung

Branches ermöglichen parallele Entwicklung.

Beispiel:

```text
main
 ├── stabile Version
 │
 └── feature-login
      └── neues Login-System
```

Dadurch bleibt `main` stabil.

---

# Branch anzeigen

## git branch

### Erklärung

Zeigt vorhandene Branches an.

### Beispiel

```bash
git branch
```

---

> [!important]
> Der aktuelle Branch wird mit `*` markiert.

---

# Branch erstellen

## Erklärung

Erstellt einen neuen Branch.

### Beispiel

```bash
git branch feature-login
```

---

# Branch wechseln

## git switch

### Erklärung

Wechselt den aktuellen Branch.

### Beispiele

```bash
git switch main

git switch feature-login
```

---

## Branch erstellen + wechseln

### Beispiel

```bash
git switch -c feature-login
```

---

# Änderungen committen

## Erklärung

Commits gehören immer zum aktuellen Branch.

### Beispiel

```bash
git add .

git commit -m "Login hinzugefügt"
```

---

# Branch zusammenführen

## git merge

### Erklärung

`git merge` kombiniert zwei Branches.

### Beispiel

```bash
git switch main

git merge feature-login
```

---

# Merge löschen

## Branch löschen

### Erklärung

Löscht einen Branch.

### Beispiel

```bash
git branch -d feature-login
```

---

> [!warning]
> ## Vorsicht
>
> `-d` löscht nur gemergte Branches.
>
> Mit `-D` kann ein Branch erzwungen gelöscht werden.

---

# Remote Branches

## Erklärung

Branches können auf GitHub hochgeladen werden.

### Beispiel

```bash
git push origin feature-login
```

---

# Remote Branch herunterladen

## Beispiel

```bash
git pull
```

---

# Alle Branches anzeigen

## Beispiele

```bash
git branch

git branch -r

git branch -a
```

---

# Bedeutungen

| Befehl | Bedeutung |
|---|---|
| `git branch` | lokale Branches |
| `git branch -r` | Remote-Branches |
| `git branch -a` | alle Branches |

---

# Typischer Workflow

## Feature Branch Workflow

```bash
git switch main

git pull

git switch -c feature-login

git add .

git commit -m "Login erstellt"

git push origin feature-login
```

---

# Merge Workflow

## Beispiel

```bash
git switch main

git pull

git merge feature-login
```

---

# Merge-Konflikte

## Erklärung

Merge-Konflikte entstehen, wenn dieselbe Datei mehrfach geändert wurde.

---

## Beispiel

```text
<<<<<<< HEAD
Hallo Welt
=======
Hallo Max
>>>>>>> feature-login
```

---

# Konflikte lösen

## Erklärung

1. Datei bearbeiten
2. Konfliktmarker entfernen
3. Datei speichern
4. Commit erstellen

---

# Detached HEAD

## Erklärung

Detached HEAD bedeutet, dass man sich nicht auf einem normalen Branch befindet.

---

## Beispiel

```bash
git checkout COMMIT_ID
```

---

> [!warning]
> Änderungen können verloren gehen, wenn kein neuer Branch erstellt wird.

---

# Branch umbenennen

## Beispiel

```bash
git branch -m neuer-name
```

---

# Branch verfolgen

## Erklärung

Lokaler Branch mit Remote-Branch verbinden.

### Beispiel

```bash
git push -u origin feature-login
```

---

> [!important]
> Danach reicht oft einfach:
>
> ```bash
> git push
> ```

---

# Rebase

## Erklärung

`rebase` verschiebt Commits auf eine andere Basis.

### Beispiel

```bash
git rebase main
```

---

> [!warning]
> Rebase verändert die Commit-Historie.
>
> Vorsicht bei Teamprojekten.

---

# Häufige Branch-Namen

| Name | Verwendung |
|---|---|
| `main` | stabile Hauptversion |
| `develop` | Entwicklungsbranch |
| `feature-*` | neue Features |
| `bugfix-*` | Fehlerbehebung |
| `hotfix-*` | dringende Fehler |

---

# GitHub Pull Requests

## Erklärung

Pull Requests werden verwendet, um Änderungen zu prüfen und zu mergen.

Typischer Ablauf:

1. Branch erstellen
2. Änderungen committen
3. Branch pushen
4. Pull Request öffnen
5. Merge durchführen

---

# Nützliche Befehle

## Aktuellen Branch anzeigen

```bash
git branch --show-current
```

---

## Branch-Graph anzeigen

```bash
git log --oneline --graph --all
```

---

# Verwandte Themen

- [[Git]]
- [[GitHub]]
- [[Shell]]
- [[Merge Konflikte]]
- [[.gitignore]]

---

> [!important]
> ## Merksatz
>
> Branches ermöglichen parallele Entwicklung ohne die Hauptversion zu gefährden.

---

# Fragen

## Was ist ein Branch?

> [!spoiler]- Lösung anzeigen
> Ein Branch ist ein separater Entwicklungszweig.

---

## Was macht `git switch`?

> [!spoiler]- Lösung anzeigen
> Wechselt den aktuellen Branch.

---

## Was macht `git merge`?

> [!spoiler]- Lösung anzeigen
> Führt Branches zusammen.

---

## Warum sind Branches wichtig?

> [!spoiler]- Lösung anzeigen
> Sie ermöglichen sichere parallele Entwicklung.

---

## Was ist ein Merge-Konflikt?

> [!spoiler]- Lösung anzeigen
> Ein Konflikt entsteht, wenn dieselbe Datei mehrfach geändert wurde.

---

## Was macht `git push -u origin branch`?

> [!spoiler]- Lösung anzeigen
> Verbindet lokalen und Remote-Branch.