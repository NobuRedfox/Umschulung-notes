
> [!info]
> ## Erklärung
>
> Bash ist eine Shell unter Linux.
>
> Mit Bash kann man:
>
> - Befehle ausführen
> - Programme starten
> - Dateien verwalten
> - Skripte schreiben
> - Aufgaben automatisieren

---

# Shell vs Bash

| Begriff | Bedeutung |
|---|---|
| Shell | Allgemeine Kommandozeile |
| Bash | Eine bestimmte Shell unter Linux |

---

# Bash-Skript erstellen

## Erklärung

Bash-Skripte sind Dateien mit mehreren Befehlen.

---

## Beispiel

```bash
touch script.sh
```

---

# Shebang

## Erklärung

Die Shebang legt fest, welche Shell verwendet wird.

### Beispiel

```bash
#!/bin/bash
```

---

# Skript ausführbar machen

## Erklärung

Mit `chmod +x` wird ein Skript ausführbar.

### Beispiel

```bash
chmod +x script.sh
```

---

# Skript starten

## Beispiele

```bash
./script.sh

bash script.sh
```

---

# Kommentare

## Erklärung

Kommentare beginnen mit `#`.

### Beispiele

```bash
# Das ist ein Kommentar

echo "Hallo"
```

---

# Variablen

## Erklärung

Variablen speichern Werte.

### Beispiele

```bash
NAME="Max"

echo $NAME
```

---

> [!important]
> Beim Zuweisen darf kein Leerzeichen verwendet werden.

```bash
NAME="Max"
```

Falsch:

```bash
NAME = "Max"
```

---

# Benutzereingaben

## read

### Erklärung

`read` liest Eingaben vom Benutzer.

### Beispiel

```bash
read NAME

echo $NAME
```

---

## Mit Text

```bash
read -p "Name: " NAME

echo "Hallo $NAME"
```

---

# Ausgabe

## echo

### Erklärung

`echo` gibt Text aus.

### Beispiele

```bash
echo "Hallo"

echo $HOME
```

---

# Bedingungen

## if

### Erklärung

`if` führt Code nur unter bestimmten Bedingungen aus.

### Beispiel

```bash
if [ $ZAHL -eq 5 ]
then
    echo "Zahl ist 5"
fi
```

---

# Vergleichsoperatoren

| Operator | Bedeutung |
|---|---|
| `-eq` | gleich |
| `-ne` | ungleich |
| `-lt` | kleiner |
| `-gt` | größer |
| `-le` | kleiner oder gleich |
| `-ge` | größer oder gleich |

---

# Stringvergleich

## Beispiele

```bash
if [ "$NAME" = "Max" ]
then
    echo "Hallo Max"
fi
```

---

# Schleifen

## for

### Erklärung

`for` wiederholt Befehle mehrfach.

### Beispiel

```bash
for i in 1 2 3
do
    echo $i
done
```

---

## while

### Erklärung

`while` wiederholt Befehle solange eine Bedingung wahr ist.

### Beispiel

```bash
COUNT=1

while [ $COUNT -le 5 ]
do
    echo $COUNT
    COUNT=$((COUNT + 1))
done
```

---

# Funktionen

## Erklärung

Funktionen gruppieren Befehle.

### Beispiel

```bash
hallo() {
    echo "Hallo Welt"
}

hallo
```

---

# Argumente

## Erklärung

Bash-Skripte können Argumente erhalten.

### Beispiel

```bash
echo $1
echo $2
```

---

## Skript starten

```bash
./script.sh Max 25
```

---

# Wichtige Spezialvariablen

| Variable | Bedeutung |
|---|---|
| `$0` | Skriptname |
| `$1` | Erstes Argument |
| `$2` | Zweites Argument |
| `$#` | Anzahl der Argumente |
| `$@` | Alle Argumente |

---

# Dateiprüfungen

## Beispiele

```bash
if [ -f datei.txt ]
then
    echo "Datei existiert"
fi
```

---

# Häufige Prüfungen

| Prüfung | Bedeutung |
|---|---|
| `-f` | Datei existiert |
| `-d` | Ordner existiert |
| `-e` | Datei oder Ordner existiert |
| `-x` | Datei ist ausführbar |

---

# Mathematische Berechnungen

## Beispiele

```bash
ZAHL=$((5 + 3))

echo $ZAHL
```

---

# Exit Codes

## Erklärung

Programme geben einen Exit Code zurück.

| Code | Bedeutung |
|---|---|
| `0` | Erfolg |
| `1` | Fehler |

---

# Exit Code prüfen

## Beispiel

```bash
echo $?
```

---

# Pipes & Redirects

## Beispiele

```bash
ls | grep test

echo "Hallo" > datei.txt

echo "Welt" >> datei.txt
```

---

# Wichtige Umgebungsvariablen

| Variable | Bedeutung |
|---|---|
| `$HOME` | Home-Verzeichnis |
| `$PATH` | Suchpfade für Programme |
| `$USER` | Benutzername |
| `$PWD` | Aktueller Ordner |

---

# Nützliche Befehle

## history

### Erklärung

Zeigt alte Befehle an.

### Beispiel

```bash
history
```

---

## clear

### Erklärung

Leert das Terminal.

### Beispiel

```bash
clear
```

---

## alias

### Erklärung

`alias` erstellt Kurzbefehle.

### Beispiel

```bash
alias ll="ls -lah"
```

---

# Fehlerbehandlung

## Erklärung

Mit `exit` kann ein Skript beendet werden.

### Beispiel

```bash
exit 1
```

---

# Beispielskript

## Hallo-Welt-Skript

```bash
#!/bin/bash

read -p "Wie heißt du? " NAME

echo "Hallo $NAME"
```

---

# Verwandte Themen

- [[Linux]]
- [[Shell]]
- [[Shell Befehle]]
- [[Shell Flags]]
- [[Terminal]]
- [[Scripting]]

---

> [!important]
> ## Merksatz
>
> Bash ermöglicht die Automatisierung von Aufgaben unter Linux.

---

# Fragen

## Was ist Bash?

> [!spoiler]- Lösung anzeigen
> Bash ist eine Shell unter Linux.

---

## Was macht `chmod +x`?

> [!spoiler]- Lösung anzeigen
> Macht eine Datei ausführbar.

---

## Wofür wird `read` verwendet?

> [!spoiler]- Lösung anzeigen
> `read` liest Benutzereingaben ein.

---

## Was macht `$1`?

> [!spoiler]- Lösung anzeigen
> `$1` enthält das erste Argument eines Skripts.

---

## Was bedeutet Exit Code `0`?

> [!spoiler]- Lösung anzeigen
> Exit Code `0` bedeutet Erfolg.

---

## Was macht `alias`?

> [!spoiler]- Lösung anzeigen
> `alias` erstellt Kurzbefehle.