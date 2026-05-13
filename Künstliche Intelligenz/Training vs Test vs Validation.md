
> [!important]
> Daten werden aufgeteilt, um die echte Leistung eines Modells zu messen.

## Warum überhaupt aufteilen?

Wenn du alles zum Trainieren nutzt:

- Modell sieht ALLE Daten  
- Ergebnis sieht super aus  
- aber:
```
es kann trotzdem schlecht auf neue Daten reagieren
```
-> = **Overfitting**

---
## Die 3 Datensätze
### 1. Trainingsdaten (Training Set)

-> Damit lernt das Modell
- Gewichte werden angepasst
- [[Gradientenabstieg]] + [[Backpropagation]] laufen hier

### 2. Validierungsdaten (Validation Set)

-> Wird **während des Trainings** genutzt
- hilft beim Einstellen von:
    - Lernrate
    - Anzahl [[Epoch & Batch]]
- entscheidet: „wird es besser oder schlechter?“

### 3. Testdaten (Test Set)

-> Damit prüfst du das Modell **am Ende**
- Modell hat diese Daten **noch nie gesehen**
- zeigt echte Leistung
### Bild im Kopf

```
Training → lernen
Validation → einstellen
Test → prüfen
```

---
## Ziel

Overfitting vermeiden und Generalisierung prüfen
(Generalisierung bedeutet, dass ein Modell **auch bei neuen, unbekannten Daten gut funktioniert**)