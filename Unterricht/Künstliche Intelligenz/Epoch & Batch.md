## Epoch & Batch

> [!important]
>  - Eine Epoch ist ein kompletter Durchlauf durch alle Trainingsdaten.
>  - Ein Batch ist eine Teilmenge dieser Daten.

---
## Batch (Datenportion)
- kleine Datenportion
- Training erfolgt schrittweise

### Beispiel

Du hast:
```
1000 Trainingsdaten
```
Batch Size = 100
bedeutet:
```
1000 / 100 = 10 Batches
```

---
## Epoch (Durchlauf)
- kompletter Durchlauf aller Daten

### Beispiel

```
1000 Daten → 1 Epoch = alle einmal gesehen
```

---

## Zusammenhang
1 Epoch = mehrere Batches

```
1000 Daten
Batch Size = 100

→ 10 Batches = 1 Epoch
```

---
## Training läuft so ab

```
Epoch 1:  
Batch 1 → lernen  
Batch 2 → lernen  
...  
Batch 10 → lernen
Epoch 2:  
wieder von vorne
```

Das wird oft wiederholt (z. B. 10–100 Epochs)
## Wichtig
Gradientenabstieg und Backpropagation passieren pro Batch

---
## Verbindungen

- [[Gradientenabstieg]] → passiert **pro Batch**
- [[Loss-Funktion]] → wird ständig berechnet
- [[Backpropagation]] → läuft bei jedem Batch