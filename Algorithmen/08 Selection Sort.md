## Definition

Selection Sort ist ein einfacher Sortieralgorithmus.

Dabei wird in jedem Durchlauf das kleinste Element im noch unsortierten Teil des Arrays gesucht und an die richtige Position getauscht.

Nach jedem Durchlauf ist ein weiteres Element dauerhaft an der richtigen Stelle.

---

## Eigenschaften

Selection Sort:

- sucht immer das kleinste Element
- tauscht nur einmal pro Durchlauf
- arbeitet direkt im Array
- ist leicht zu verstehen
- eignet sich eher für kleine Datenmengen

---

## Beispiel

Unsortiertes Array:

```text
4, 8, 2, 9, 1
```

Ziel:

```text
1, 2, 4, 8, 9
```

---

## Erster Durchlauf

Kleinstes Element suchen:

```text
4, 8, 2, 9, 1
            ↑
```

Das kleinste Element ist:

```text
1
```

Tauschen mit der ersten Position:

```text
1, 8, 2, 9, 4
```

---

## Zweiter Durchlauf

Nur der unsortierte Teil wird betrachtet:

```text
8, 2, 9, 4
```

Kleinstes Element:

```text
2
```

Tauschen:

```text
1, 2, 8, 9, 4
```

---

## Dritter Durchlauf

```text
8, 9, 4
```

Kleinstes Element:

```text
4
```

Tauschen:

```text
1, 2, 4, 9, 8
```

---

## Vierter Durchlauf

```text
9, 8
```

Kleinstes Element:

```text
8
```

Tauschen:

```text
1, 2, 4, 8, 9
```

Fertig sortiert.

---

## Visualisierung

```text
4, 8, 2, 9, 1
↓
1, 8, 2, 9, 4
↓
1, 2, 8, 9, 4
↓
1, 2, 4, 9, 8
↓
1, 2, 4, 8, 9
```

---

## Pseudocode

```text
für jede Position im Array:

    kleinstes Element suchen

    mit aktueller Position tauschen
```

---

## Java-Beispiel

```java
int[] zahlen = {4, 8, 2, 9, 1};

for (int i = 0; i < zahlen.length - 1; i++) {

    int minIndex = i;

    for (int j = i + 1; j < zahlen.length; j++) {

        if (zahlen[j] < zahlen[minIndex]) {
            minIndex = j;
        }
    }

    int temp = zahlen[i];
    zahlen[i] = zahlen[minIndex];
    zahlen[minIndex] = temp;
}

for (int zahl : zahlen) {
    System.out.print(zahl + " ");
}
```

Ausgabe:

```text
1 2 4 8 9
```

---

## Erklärung des Codes

### Äußere Schleife

```java
for (int i = 0; i < zahlen.length - 1; i++)
```

Bestimmt die Position, an der das nächste kleinste Element abgelegt wird.

---

### Innere Schleife

```java
for (int j = i + 1; j < zahlen.length; j++)
```

Durchsucht den noch unsortierten Teil des Arrays nach dem kleinsten Element.

---

### Kleinsten Index merken

```java
int minIndex = i;
```

Speichert die Position des aktuell kleinsten Elements.

---

### Tauschen

```java
int temp = zahlen[i];
zahlen[i] = zahlen[minIndex];
zahlen[minIndex] = temp;
```

Das kleinste gefundene Element wird an seine endgültige Position gesetzt.

---

## Vor- und Nachteile

### Vorteile

- einfach zu verstehen
- nur ein Tausch pro Durchlauf
- übersichtlicher Algorithmus

### Nachteile

- viele Vergleiche notwendig
- bei großen Datenmengen langsam

---

## Laufzeit

### Best Case

```text
O(n²)
```

---

### Average Case

```text
O(n²)
```

---

### Worst Case

```text
O(n²)
```

Selection Sort durchsucht immer den gesamten unsortierten Bereich – auch wenn das Array bereits sortiert ist.

---

## Vergleich zu Bubble Sort

| Bubble Sort | Selection Sort |
|--------------|----------------|
| Vergleicht benachbarte Elemente | Sucht das kleinste Element |
| Viele Vertauschungen | Nur ein Tausch pro Durchlauf |
| Größte Werte wandern nach rechts | Kleinste Werte wandern nach links |

---

## Merksatz

> Selection Sort sucht in jedem Durchlauf das kleinste Element und legt es an die richtige Position.

---

# Fragen

## Wie arbeitet Selection Sort?

> [!spoiler]- Lösung anzeigen
> Er sucht das kleinste Element im unsortierten Bereich und tauscht es an die richtige Position.

---

## Was passiert nach jedem Durchlauf?

> [!spoiler]- Lösung anzeigen
> Ein weiteres Element steht dauerhaft an der richtigen Stelle.

---

## Wie viele Tauschvorgänge gibt es pro Durchlauf?

> [!spoiler]- Lösung anzeigen
> Genau einen.

---

## Welche Laufzeit besitzt Selection Sort?

> [!spoiler]- Lösung anzeigen
> O(n²)

---

## Worin unterscheidet sich Selection Sort von Bubble Sort?

> [!spoiler]- Lösung anzeigen
> Bubble Sort vergleicht benachbarte Elemente und tauscht häufig. Selection Sort sucht das kleinste Element und tauscht nur einmal pro Durchlauf.

---

## Nächste Themen

- [[09 Insertion Sort]]
- [[14 Laufzeitvergleich]]