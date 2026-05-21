
> [!info]
> ## Erklärung
>
> Flags sind Optionen für Befehle.
>
> Sie verändern das Verhalten eines Befehls.
>
> Meistens beginnen Flags mit `-`.

---

# Aufbau eines Befehls

Ein Shell-Befehl besteht meistens aus:

- Befehl → was tun
- Flag → wie ausführen

Beispiel:

```bash
ls -l
```

- `ls` → Dateien anzeigen
- `-l` → detaillierte Ausgabe

---

# Allgemein wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-r` | recursive → rekursiv arbeiten |
| `-f` | force → ohne Nachfrage |
| `-i` | interactive → nachfragen |
| `-v` | verbose → anzeigen was passiert |
| `-h` | human readable → lesbare Größen |
| `-a` | all → versteckte Dateien anzeigen |
| `-l` | long → detaillierte Ausgabe |
| `-t` | sort by time → nach Zeit sortieren |

---

# Flags kombinieren

Mehrere kurze Flags können kombiniert werden.

```bash
ls -lah
```

Das entspricht:

```bash
ls -l -a -h
```

---

# ls (list)

## Erklärung

`ls` zeigt Dateien und Ordner an.

---

## Beispiele

```bash
ls
ls -l
ls -a
ls -lah
ls -lt
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-l` | Details anzeigen |
| `-a` | versteckte Dateien anzeigen |
| `-h` | lesbare Größen |
| `-t` | nach Datum sortieren |

---

# rm (remove)

## Erklärung

`rm` löscht Dateien oder Ordner.

---

## Beispiele

```bash
rm datei.txt
rm -r ordner
rm -rf ordner
rm -ri ordner
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-r` | rekursiv löschen |
| `-f` | ohne Nachfrage |
| `-i` | Sicherheitsabfrage |

---

> [!warning]
> `rm -rf` löscht rekursiv und ohne Nachfrage.
>
> Dieser Befehl kann Daten dauerhaft löschen.

---

# cp (copy)

## Erklärung

`cp` kopiert Dateien oder Ordner.

---

## Beispiele

```bash
cp datei.txt copy.txt
cp -r ordner backup
cp -rv ordner backup
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-r` | Ordner kopieren |
| `-v` | Kopiervorgang anzeigen |

---

# mv (move)

## Erklärung

`mv` verschiebt oder benennt Dateien um.

---

## Beispiele

```bash
mv datei.txt neu.txt
mv datei.txt backup/
mv -v datei.txt backup/
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-v` | zeigt Verschieben an |
| `-i` | vor Überschreiben fragen |

---

# grep (search)

## Erklärung

`grep` sucht nach Text in Dateien.

---

## Beispiele

```bash
grep "text" datei.txt
grep -i "text" datei.txt
grep -r "text" ordner
grep -n "text" datei.txt
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-i` | Groß-/Kleinschreibung ignorieren |
| `-r` | rekursiv suchen |
| `-n` | Zeilennummer anzeigen |

---

# find

## Erklärung

`find` sucht Dateien und Ordner.

---

## Beispiele

```bash
find . -iname "*test*"
find . -type f
find . -type d
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-iname` | ohne Groß-/Kleinschreibung |
| `-type f` | nur Dateien |
| `-type d` | nur Ordner |

---

# tar

## Erklärung

`tar` erstellt oder entpackt Archive.

---

## Beispiele

```bash
tar -czf backup.tgz ordner
tar -xzf backup.tgz
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-c` | Archiv erstellen |
| `-x` | Archiv entpacken |
| `-z` | gzip verwenden |
| `-f` | Dateiname angeben |

---

# du (disk usage)

## Erklärung

`du` zeigt den Speicherverbrauch an.

---

## Beispiele

```bash
du -sh ordner
du -sm foo bar
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-s` | Gesamtsumme |
| `-h` | lesbare Größen |
| `-m` | Ausgabe in MiB |

---

# uname

## Erklärung

`uname` zeigt Systeminformationen an.

---

## Beispiele

```bash
uname -r
uname -a
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-r` | Kernel-Version |
| `-a` | alle Informationen |

---

# Git Flags

## Erklärung

Auch Git nutzt viele Flags.

---

## Beispiele

```bash
git commit -m "Nachricht"
git push -u origin main
git status -v
```

---

## Wichtige Flags

| Flag | Bedeutung |
|---|---|
| `-m` | Commit-Nachricht |
| `-u` | upstream setzen |
| `-a` | tracked Dateien automatisch stagen |
| `-v` | ausführliche Ausgabe |

---

# Verwandte Themen

- [[Linux]]
- [[Shell]]
- [[Terminal]]
- [[Bash]]
- [[Git]]

---

> [!important]
> ## Merksatz
>
> Flags verändern das Verhalten eines Befehls.

---

# Fragen

- Was ist ein Flag?

> [!spoiler]- Lösung anzeigen
> Ein Flag ist eine Option für einen Befehl.
>
> Es verändert das Verhalten des Befehls.

---

- Was macht das Flag `-r`?

> [!spoiler]- Lösung anzeigen
> `-r` bedeutet rekursiv.
>
> Der Befehl verarbeitet auch Unterordner und deren Inhalt.

---

- Warum ist `rm -rf` gefährlich?

> [!spoiler]- Lösung anzeigen
> Der Befehl löscht rekursiv und ohne Nachfrage.
>
> Dadurch können Daten dauerhaft gelöscht werden.

---

- Was bedeutet `-h`?

> [!spoiler]- Lösung anzeigen
> `-h` bedeutet human readable.
>
> Größen werden lesbar angezeigt, z. B. KB, MB oder GB.