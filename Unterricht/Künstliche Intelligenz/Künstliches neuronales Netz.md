>[!Important]
Ein künstliches neuronales Netz besteht aus **Neuronen (Knoten)**, die in **Schichten** organisiert sind und durch **Gewichte** miteinander verbunden sind.

## Die 4 wichtigsten Bestandteile
### 1. Neuronen (Nodes)
- kleine Recheneinheiten
- bekommen Eingaben und berechnen einen Output
-> wie "Mini-Entscheider“

### 2. Gewichte (Weights)
- jede Verbindung hat ein Gewicht
- bestimmt, **wie wichtig ein Signal ist
-> zb.:
- großes Gewicht -> wichtig
- kleines Gewicht -> weniger wichtig

### 3. Aktivierungsfunktion
- entscheidet, ob ein Neuron "feuert"
-> Beispiel:
- ReLU
- Sigmoid

### 4. Schichten (Layers)
Ein Netz ist ein Schichten aufgebaut:
- **Input Layer** -> nimmt Daten auf
- **Hidden Layer(s) -> verarbeitet Informationen
- **Output Layer** -> gibt Ergebnis aus

### Einfaches Bild im Kopf

```
Input → Verarbeitung → Ergebnis
```

oder:

```
Daten → Neuronen → Entscheidung
```

### Beispiel
Du gibst ein Bild rein:

- Input: Pixel
- Hidden Layer: erkennt Muster (Kanten, Formen)
- Output: „Das ist eine Katze“


## Verlinkungen

- [[Aktivierungsfunktion]]
- [[Gewichte]]