
> [!important]
> Ein Modell kann zu wenig oder zu viel lernen.

## Underfitting
Modell ist zu "dumm“

- erkennt Muster nicht
- macht viele Fehler
- auch bei Trainingsdaten schlecht
### Bild:
```
zu einfach → versteht nichts
```

---
## Overfitting
Modell ist zu "schlau“ (aber falsch)

- merkt sich Trainingsdaten auswendig
- funktioniert schlecht bei neuen Daten
### Bild:
```
auswendig gelernt → kein echtes Verständnis
```

---
## Verhalten

| Zustand      | Training | Neue Daten |
| ------------ | -------- | ---------- |
| Underfitting | schlecht | schlecht   |
| Overfitting  | sehr gut | schlecht   |
| Optimal      | gut      | gut        |

---
## Ziel
Gute Balance zwischen beiden finden

---

## Verbindungen

- [[Epoch & Batch]] → zu viele Epochs → Overfitting
- [[Loss-Funktion]] → Training Loss vs Test Loss
- [[Gradientenabstieg]] → optimiert nur Trainingsdaten