
> [!info]
> ## Erklärung
>
> `.gitignore` legt fest, welche Dateien oder Ordner von Git ignoriert werden.
>
> Dadurch werden z. B.:
>
> - temporäre Dateien
> - Build-Dateien
> - IDE-Dateien
> - Logs
> - Cache-Dateien
>
> nicht in Git gespeichert.

---

# Warum `.gitignore` wichtig ist

## Erklärung

Viele Dateien gehören nicht ins Repository.

Beispiele:

- IntelliJ Einstellungen
- Build-Ordner
- Cache-Dateien
- Passwörter
- Logs

Ohne `.gitignore` wird das Repository schnell unübersichtlich.

---

# Datei erstellen

## Beispiel

```bash
touch .gitignore
```

---

# Einfaches Beispiel

## Inhalt

```gitignore
.idea/
*.iml
out/
```

---

# Kommentare

## Erklärung

Kommentare beginnen mit `#`.

### Beispiel

```gitignore
# IntelliJ Dateien
.idea/
```

---

# Ordner ignorieren

## Beispiel

```gitignore
node_modules/

build/

out/
```

---

# Dateitypen ignorieren

## Beispiele

```gitignore
*.log

*.tmp

*.class
```

---

# Einzelne Datei ignorieren

## Beispiel

```gitignore
geheim.txt
```

---

# Python Beispiele

## Beispiel

```gitignore
__pycache__/

*.pyc

venv/
```

---

# Java Beispiele

## Beispiel

```gitignore
out/

target/

*.class
```

---

# IntelliJ Beispiele

## Beispiel

```gitignore
.idea/

*.iml
```

---

# VS Code Beispiele

## Beispiel

```gitignore
.vscode/
```

---

# Betriebssystem-Dateien

## Beispiel

```gitignore
.DS_Store

Thumbs.db
```

---

# Rekursiv ignorieren

## Beispiel

```gitignore
logs/
```

Ignoriert alle `logs`-Ordner.

---

# Ausnahme definieren

## Erklärung

Mit `!` können Dateien wieder erlaubt werden.

### Beispiel

```gitignore
*.log

!important.log
```

---

# Bereits getrackte Dateien

## Erklärung

`.gitignore` wirkt nur bei neuen Dateien.

Bereits getrackte Dateien bleiben weiterhin in Git.

---

# Datei aus Git entfernen

## Beispiel

```bash
git rm --cached datei.txt
```

---

## Ordner aus Git entfernen

```bash
git rm -r --cached ordner/
```

---

> [!warning]
> ## Wichtig
>
> Danach:
>
> ```bash
> git commit -m "Remove tracked files"
> ```
>
> sonst bleibt die Änderung lokal.

---

# Typischer Workflow

## Beispiel

```bash
touch .gitignore

git add .gitignore

git commit -m "Add .gitignore"
```

---

# Häufige `.gitignore` Beispiele

## Java + IntelliJ

```gitignore
.idea/
*.iml
out/
target/
```

---

## Python

```gitignore
__pycache__/
*.pyc
venv/
```

---

## Node.js

```gitignore
node_modules/
.env
```

---

# `.env` Dateien

## Erklärung

`.env` Dateien enthalten oft:

- Passwörter
- API-Keys
- Zugangsdaten

Diese sollten fast nie hochgeladen werden.

---

# GitHub Templates

## Erklärung

GitHub bietet fertige `.gitignore` Vorlagen.

Beispiele:

- Java
- Python
- Node.js
- Visual Studio
- IntelliJ

---

# Gute Regeln

## Empfehlung

Ignorieren:

- Build-Dateien
- IDE-Dateien
- Logs
- temporäre Dateien
- Cache-Dateien

Nicht ignorieren:

- Quellcode
- wichtige Konfigurationen
- Dokumentation

---

# Häufige Fehler

## `.gitignore` funktioniert nicht

### Ursache

Datei wurde bereits getrackt.

### Lösung

```bash
git rm --cached datei.txt
```

---

## Zu viele Dateien ignoriert

### Problem

Wichtige Dateien fehlen im Repository.

---

# Nützliche Befehle

## Status prüfen

```bash
git status
```

---

## Getrackte Dateien anzeigen

```bash
git ls-files
```

---

# Beispielprojekt

## Struktur

```text
projekt/
├── src/
├── out/
├── .idea/
├── README.md
└── .gitignore
```

---

## `.gitignore`

```gitignore
.idea/
out/
*.iml
```

---

# Verwandte Themen

- [[Git]]
- [[GitHub]]
- [[Git Branches]]
- [[Shell]]
- [[IntelliJ]]

---

> [!important]
> ## Merksatz
>
> `.gitignore` verhindert, dass unnötige Dateien in Git gespeichert werden.

---

# Fragen

## Was macht `.gitignore`?

> [!spoiler]- Lösung anzeigen
> `.gitignore` legt fest, welche Dateien Git ignorieren soll.

---

## Werden bereits getrackte Dateien ignoriert?

> [!spoiler]- Lösung anzeigen
> Nein.
>
> Bereits getrackte Dateien müssen zuerst entfernt werden.

---

## Was macht `git rm --cached`?

> [!spoiler]- Lösung anzeigen
> Entfernt Dateien aus Git, aber nicht vom Computer.

---

## Warum sollte man `.env` ignorieren?

> [!spoiler]- Lösung anzeigen
> Weil dort oft Zugangsdaten gespeichert werden.

---

## Was bedeutet `*.log`?

> [!spoiler]- Lösung anzeigen
> Alle Dateien mit der Endung `.log` werden ignoriert.