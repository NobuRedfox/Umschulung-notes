
> [!important]
> Aktivierungsfunktionen bestimmen, wie ein Neuron auf Eingaben reagiert.

## 1. ReLU (Rectified Linear Unit)

--> Bedeutung:
- Wenn Wert **negativ** → wird zu **0**
- Wenn Wert **positiv** → bleibt gleich
### Beispiel

- Input: -3 → Output: 0
- Input: 5 → Output: 5

--> super einfach & schnell → deshalb sehr beliebt
- negative Werte → 0
- positive Werte → unverändert

## 2. Sigmoid

![[sigmoid.svg]]
Bedeutung:

- wandelt alles in einen Wert zwischen **0 und 1** um
### Beispiel

- Input: -10 → ≈ 0
- Input: 0 → 0.5
- Input: 10 → ≈ 1
-> oft für **Wahrscheinlichkeiten** genutzt

---

##  Unterschied einfach erklärt

|Funktion|Verhalten|Einsatz|
|---|---|---|
|ReLU|schneidet alles < 0 ab|Standard in Hidden Layers|
|Sigmoid|macht Werte zwischen 0 und 1|Output / Wahrscheinlichkeit|
### Bild im Kopf
- **ReLu** -> alles Negative ignorieren
- **Sigmoid** -> in Wahrscheinlichkeit umwandeln

---
## Fazit

-> Ohne Aktivierungsfunktion wäre ein neuronales Netz nur „lineare Mathematik“  
-> Mit ihnen kann es **komplexe Muster lernen**

---

### Verbindungen

- [[Aktivierungsfunktion]]