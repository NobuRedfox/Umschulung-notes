## Definition

Die Komplexität beschreibt, wie viel Aufwand ein Algorithmus benötigt.

Dabei betrachtet man hauptsächlich:

- die Laufzeit (Zeitkomplexität)
- den Speicherverbrauch (Speicherkomplexität)

Je geringer die Komplexität, desto effizienter arbeitet ein Algorithmus.

---

## Warum ist Komplexität wichtig?

Nicht nur das Ergebnis eines Algorithmus ist wichtig, sondern auch, wie schnell und wie effizient dieses Ergebnis erreicht wird.

Zwei Algorithmen können dieselbe Aufgabe lösen, aber unterschiedlich viel Zeit benötigen.

---

## Arten der Komplexität

### Zeitkomplexität

Beschreibt, wie viele Arbeitsschritte ein Algorithmus benötigt.

Beispiel:

```text
10 Elemente  → 10 Vergleiche
100 Elemente → 100 Vergleiche
1000 Elemente → 1000 Vergleiche
```

---

### Speicherkomplexität

Beschreibt, wie viel zusätzlicher Speicher ein Algorithmus benötigt.

Beispiel:

- zusätzliche Variablen
- Hilfsarrays
- rekursive Aufrufe

---

## Einfluss der Eingabegröße

Je größer die Datenmenge wird, desto wichtiger wird die Komplexität.

Beispiel:

```text
10 Zahlen
↓

100 Zahlen
↓

1.000 Zahlen
↓

1.000.000 Zahlen
```

Ein ineffizienter Algorithmus wird mit großen Datenmengen schnell sehr langsam.

---

## Beispiel

Lineare Suche:

```text
1 2 3 4 5 6 7 8 9
```

Im schlimmsten Fall muss jedes Element überprüft werden.

---

Binäre Suche:

```text
1 2 3 4 5 6 7 8 9
        ↑
```

Der Suchbereich wird bei jedem Schritt halbiert.

Dadurch benötigt die binäre Suche deutlich weniger Vergleiche.

---

## Vergleich

| Algorithmus | Aufwand |
|-------------|---------|
| Lineare Suche | hoch |
| Binäre Suche | gering |
| Bubble Sort | hoch |
| Selection Sort | hoch |
| Insertion Sort | mittel |

---

## Zusammenhang mit Big-O

Die Komplexität wird häufig mit der Big-O-Notation beschrieben.

Beispiele:

```text
O(1)
O(log n)
O(n)
O(n²)
O(2ⁿ)
```

Die genaue Bedeutung dieser Schreibweise wird im nächsten Kapitel erklärt.

---

## Merksatz

> Die Komplexität beschreibt den Aufwand eines Algorithmus hinsichtlich Zeit und Speicher.

---

# Fragen

## Was beschreibt die Komplexität?

> [!spoiler]- Lösung anzeigen
> Den Aufwand eines Algorithmus.

---

## Welche zwei Arten der Komplexität gibt es?

> [!spoiler]- Lösung anzeigen
> Zeitkomplexität und Speicherkomplexität.

---

## Warum ist Komplexität wichtig?

> [!spoiler]- Lösung anzeigen
> Sie zeigt, wie effizient ein Algorithmus arbeitet.

---

## Welche Komplexität betrachtet man am häufigsten?

> [!spoiler]- Lösung anzeigen
> Die Zeitkomplexität.

---

## Womit wird die Komplexität häufig beschrieben?

> [!spoiler]- Lösung anzeigen
> Mit der Big-O-Notation.

---

## Nächste Themen

- [[13 Big-O-Notation]]
- [[14 Laufzeitvergleich]]
- [[15 Übungsaufgaben]]