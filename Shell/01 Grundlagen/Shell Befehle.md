
> [!info]
> ## Erklärung
>
> Shell-Befehle werden im Terminal ausgeführt.
>
> Mit ihnen kann man:
>
> - Dateien verwalten
> - Ordner erstellen
> - Programme starten
> - Daten suchen
> - Systeme verwalten

---

# Aufbau eines Befehls

Ein Shell-Befehl besteht meistens aus:

- **Befehl** → was tun
- **Flag** → wie ausführen
- **Argument** → worauf anwenden

## Beispiel

```bash
ls -l ordner
```

- `ls` → Befehl
- `-l` → Flag
- `ordner` → Argument

---

# Dateien & Ordner

## Anzeigen

### Erklärung

`ls` zeigt Dateien und Ordner an.

### Beispiele

```bash
ls
ls -l
ls -a
ls -lah
```

---

## Wechseln

### Erklärung

`cd` wechselt den aktuellen Ordner.

### Beispiele

```bash
cd ordner
cd ..
cd ~
```

---

## Erstellen

### Erklärung

- `mkdir` erstellt Ordner
- `touch` erstellt Dateien

### Beispiele

```bash
mkdir test
mkdir -p a/b/c

touch datei.txt
```

---

## Löschen

### Erklärung

`rm` löscht Dateien oder Ordner.

### Beispiele

```bash
rm datei.txt
rm -r ordner
rm -rf ordner
```

---

> [!warning]
> ## Vorsicht bei `rm -rf`
>
> `rm -rf` löscht rekursiv und ohne Nachfrage.
>
> Dadurch können Dateien dauerhaft gelöscht werden.

---

## Kopieren & Verschieben

### Erklärung

- `cp` kopiert Dateien oder Ordner
- `mv` verschiebt oder benennt Dateien um

### Beispiele

```bash
cp datei.txt copy.txt
cp -r ordner neuerOrdner

mv datei.txt neu.txt
mv datei.txt backup/
```

---

# Dateien anzeigen

## cat

### Erklärung

`cat` zeigt den Inhalt einer Datei an.

### Beispiele

```bash
cat datei.txt
```

---

## head

### Erklärung

`head` zeigt die ersten Zeilen einer Datei.

### Beispiele

```bash
head datei.txt
head -5 datei.txt
```

---

## tail

### Erklärung

`tail` zeigt die letzten Zeilen einer Datei.

### Beispiele

```bash
tail datei.txt
tail -5 datei.txt
```

---

# Suchen

## grep

### Erklärung

`grep` sucht nach Text in Dateien.

### Beispiele

```bash
grep "text" datei.txt
grep -i "text" datei.txt
grep -r "text" ordner
```

### Mit Pipes

```bash
ls | grep test
```

---

## find

### Erklärung

`find` sucht Dateien und Ordner.

### Beispiele

```bash
find . -iname "*test*"
find . -name "*.txt"

find . -type f
find . -type d
```

---

# Pipes

## Erklärung

Mit `|` wird die Ausgabe eines Befehls an den nächsten Befehl weitergegeben.

### Beispiele

```bash
ls | grep test

grep "Hallo" datei.txt | sort
```

---

# Redirects

## Erklärung

Mit Redirects wird Ausgabe in Dateien geschrieben.

---

## Ausgabe überschreiben

```bash
ls > datei.txt
```

---

## Ausgabe anhängen

```bash
echo "Hallo" >> datei.txt
```

---

# Textbearbeitung

## cut

### Erklärung

`cut` schneidet Teile aus Texten heraus.

### Beispiele

```bash
echo "Max,Muster" | cut -d',' -f1
```

---

## tr

### Erklärung

`tr` ersetzt Zeichen.

### Beispiele

```bash
echo "hallo" | tr a-z A-Z
```

---

## sort

### Erklärung

`sort` sortiert Zeilen.

### Beispiele

```bash
sort datei.txt
```

---

## uniq

### Erklärung

`uniq` entfernt doppelte Zeilen, wenn sie direkt nacheinander stehen.

### Beispiele

```bash
uniq datei.txt

sort datei.txt | uniq
```

---

# Archive

## tar

### Erklärung

`tar` erstellt oder entpackt Archive.

### Beispiele

```bash
tar -czf backup.tgz ordner
tar -xzf backup.tgz
```

---

# Systeminformationen

## uname

### Erklärung

`uname` zeigt Systeminformationen an.

### Beispiele

```bash
uname -r
uname -a
```

---

## du

### Erklärung

`du` zeigt den Speicherverbrauch an.

### Beispiele

```bash
du -sh ordner
du -sm foo bar
```

---

## kill

### Erklärung

`kill` beendet Prozesse.

### Beispiele

```bash
kill 1234
kill -9 1234
```

---

# Rechte

## chmod

### Erklärung

`chmod` ändert Dateirechte.

### Beispiele

```bash
chmod +x script.sh
chmod 755 script.sh
```

---

## chown

### Erklärung

`chown` ändert den Besitzer einer Datei.

### Beispiele

```bash
chown user datei.txt
chown user:user datei.txt
```

---

# Netzwerk

## curl

### Erklärung

`curl` lädt Inhalte aus dem Internet herunter oder zeigt sie an.

### Beispiele

```bash
curl https://example.com

curl -O https://example.com/bild.jpg

curl -s https://example.com
```

---

# Git Basics

## Erklärung

Git verwaltet Versionen von Projekten.

### Beispiele

```bash
git init

git status

git add .

git commit -m "Nachricht"

git push
git pull
```

---

# Verwandte Themen

- [[Linux]]
- [[Shell]]
- [[Terminal]]
- [[Bash]]
- [[Git]]
- [[Shell Flags]]

---

> [!important]
> ## Merksatz
>
> Shell-Befehle ermöglichen die Steuerung eines Linux-Systems über das Terminal.

---

# Fragen

## Was macht der Befehl `ls`?

> [!spoiler]- Lösung anzeigen
> `ls` zeigt Dateien und Ordner an.

---

## Wofür wird `grep` verwendet?

> [!spoiler]- Lösung anzeigen
> `grep` sucht nach Text in Dateien.

---

## Was macht die Pipe `|`?

> [!spoiler]- Lösung anzeigen
> Die Ausgabe eines Befehls wird an den nächsten Befehl weitergegeben.

---

## Warum ist `rm -rf` gefährlich?

> [!spoiler]- Lösung anzeigen
> Der Befehl löscht rekursiv und ohne Nachfrage.
>
> Dadurch können Daten dauerhaft gelöscht werden.

---

## Was macht `curl`?

> [!spoiler]- Lösung anzeigen
> `curl` lädt Inhalte aus dem Internet herunter oder zeigt sie an.