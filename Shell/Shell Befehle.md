## Erklärung
Shell-Befehle bestehen aus:
- Befehl → was tun
- Flag → wie tun

---

## 📁 Dateien & Ordner

### Anzeigen
```bash
ls  
ls -l
ls -a
ls -la
```

### Wechseln
```bash
cd ordner
cd ..
```

### Erstellen
```bash
mkdir test
mkdir -p a/b/c
```

### Löschen
```bash
rm datei.txt
rm -r ordner
rm -rf ordner
```

### Kopieren & Verschieben
```bash
cp datei.txt copy.txt
cp -r ordner neuerOrdner

mv datei.txt neu.txt
```

### Suchen
```bash
grep "text" datei.txt
grep -i "text" datei.txt
```

### Git Basics
```bash
git add .
git commit -m "Nachricht"  // -m = message
git push
```
