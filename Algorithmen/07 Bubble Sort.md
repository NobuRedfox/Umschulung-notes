# Bubble Sort

## Definition

Bubble Sort ist ein einfacher Sortieralgorithmus.

Dabei werden immer zwei benachbarte Elemente miteinander verglichen.

Ist das linke Element größer als das rechte, werden die beiden Werte vertauscht.

Die größten Werte "steigen" dabei Schritt für Schritt nach rechts auf – ähnlich wie Luftblasen im Wasser.

---

## Eigenschaften

Bubble Sort:

- sortiert durch Vergleichen und Tauschen
- arbeitet direkt im Array
- ist leicht zu verstehen
- eignet sich eher für kleine Datenmengen
- wird bei großen Arrays schnell langsam

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

Vergleich:

```text
4 und 8
```

```text
4 < 8
```

Keine Änderung.

---

Vergleich:

```text
8 und 2
```

```text
8 > 2
```

Tauschen:

```text
4, 2, 8, 9, 1
```

---

Vergleich:

```text
8 und 9
```

```text
8 < 9
```

Keine Änderung.

---

Vergleich:

```text
9 und 1
```

```text
9 > 1
```

Tauschen:

```text
4, 2, 8, 1, 9
```

Die größte Zahl steht jetzt ganz rechts.

---

## Zweiter Durchlauf

```text
4, 2, 8, 1, 9
```

Vergleich:

```text
4 und 2
```

Tauschen:

```text
2, 4, 8, 1, 9
```

---

Vergleich:

```text
8 und 1
```

Tauschen:

```text
2, 4, 1, 8, 9
```

---

## Weitere Durchläufe

```text
2, 4, 1, 8, 9
↓
2, 1, 4, 8, 9
↓
1, 2, 4, 8, 9
```

Fertig sortiert.

---

## Pseudocode

```text
wiederhole:

    für alle Nachbarpaare:

        wenn links > rechts:
            tauschen

bis keine Vertauschung mehr nötig ist
```

---

## Java-Beispiel

```java
int[] zahlen = {4, 8, 2, 9, 1};

for (int i = 0; i < zahlen.length - 1; i++) {

    for (int j = 0; j < zahlen.length - 1 - i; j++) {

        if (zahlen[j] > zahlen[j + 1]) {

            int temp = zahlen[j];
            zahlen[j] = zahlen[j + 1];
            zahlen[j + 1] = temp;
        }
    }
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

Bestimmt, wie oft das Array durchlaufen wird.

---

### Innere Schleife

```java
for (int j = 0; j < zahlen.length - 1 - i; j++)
```

Vergleicht benachbarte Elemente.

---

### Tauschen

```java
int temp = zahlen[j];
zahlen[j] = zahlen[j + 1];
zahlen[j + 1] = temp;
```

Vertauscht die beiden Werte.

---

## Visualisierung

```text
4, 8, 2, 9, 1

4, 2, 8, 9, 1
4, 2, 8, 1, 9

2, 4, 8, 1, 9
2, 4, 1, 8, 9

2, 1, 4, 8, 9

1, 2, 4, 8, 9
```

---

## Vor- und Nachteile

### Vorteile

- einfach zu verstehen
- einfach zu programmieren

### Nachteile

- viele Vergleiche
- viele Vertauschungen
- bei großen Datenmengen langsam

---

## Laufzeit

### Best Case

Array bereits sortiert:

```text
O(n)
```

(mit Optimierung)

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

---

## Merksatz

> Bubble Sort vergleicht benachbarte Elemente und tauscht sie, bis das Array vollständig sortiert ist.

---

# Fragen

## Wie arbeitet Bubble Sort?

> [!spoiler]- Lösung anzeigen
> Durch Vergleichen und Tauschen benachbarter Elemente.

---

## Warum heißt der Algorithmus Bubble Sort?

> [!spoiler]- Lösung anzeigen
> Weil die größten Werte wie Luftblasen nach oben bzw. nach rechts steigen.

---

## Welche Laufzeit besitzt Bubble Sort im Worst Case?

> [!spoiler]- Lösung anzeigen
> O(n²)

---

## Welche Elemente werden miteinander verglichen?

> [!spoiler]- Lösung anzeigen
> Immer benachbarte Elemente.

---

## Ist Bubble Sort für große Datenmengen geeignet?

> [!spoiler]- Lösung anzeigen
> Nein, er wird dann sehr langsam.

---

## Nächste Themen

- [[08 Selection Sort]]
- [[09 Insertion Sort]]
- [[14 Laufzeitvergleich]]