
> [!important]
> Gewichte bestimmen die Wichtigkeit von Eingaben, der Bias verschiebt die Entscheidung.

## Gewichte (Weights)
- multiplizieren die Eingaben
- bestimmen Einfluss

### Beispiel
**Wie wichtig ist ein Eingangssignal?**
Ein Neuron bekommt zwei Inputs:

```
x1 = 5   (z. B. „hat Fell“)
x2 = 2   (z. B. „hat Flügel“)
```

Gewichte:

```
w1 = 0.9
w2 = 0.1
```

--> Rechnung:

```
5 * 0.9 + 2 * 0.1 = 4.5 + 0.2 = 4.7
```

--> „Fell“ ist viel wichtiger als „Flügel“


## Bias

-->Bias ist ein **zusätzlicher Wert**, der immer dazugerechnet wird:
- also wird addiert
- verschiebt die Entscheidung

### Beispiel

```
Summe = 4.7Bias = -2
```

Ergebnis:

```
4.7 - 2 = 2.7
```

---

## Formel (ganz wichtig)

y = f(w₁x₁ + w₂x₂ + b)

Danach kommt noch die Aktivierungsfunktion `f(...)`

---

## Einfaches Bild im Kopf

- **Gewichte** → „Wie stark zählt etwas?“
- **Bias** → „Ab wann sage ich JA?“

---

## Vergleich aus dem Alltag

Stell dir vor, du entscheidest:

> „Ist das ein Hund?“

- Fell → wichtig (hohes Gewicht)
- Flügel → egal (kleines Gewicht)
- Bias → wie streng du bist

---

## Wichtigster Punkt

Beim Training werden genau diese Werte angepasst:

```
Gewichte + Bias = das, was die KI lernt
```

---

## Fazit

- Gewichte → Wichtigkeit
- Bias → Schwellenwert / Verschiebung
- zusammen → bestimmen das Verhalten des Netzwerks

---

## Verlinkungen

- [[Künstliches neuronales Netz]]