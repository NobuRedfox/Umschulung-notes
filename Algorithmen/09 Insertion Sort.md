## Definition

Insertion Sort ist ein einfacher Sortieralgorithmus.

Dabei wird jedes Element nacheinander an die richtige Position im bereits sortierten Teil des Arrays eingefügt.

Das Vorgehen ähnelt dem Sortieren von Spielkarten auf der Hand.

---

## Eigenschaften

Insertion Sort:

- fügt Elemente an der richtigen Stelle ein
- arbeitet direkt im Array
- ist leicht zu verstehen
- eignet sich gut für kleine oder fast sortierte Arrays
- ist bei großen, unsortierten Arrays langsam

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

Sortierter Bereich:

```text
4
```

Nächstes Element:

```text
8
```

Da

```text
8 > 4
```

bleibt alles unverändert.

```text
4, 8, 2, 9, 1
```

---

## Zweiter Durchlauf

Element:

```text
2
```

Vergleich:

```text
2 < 8
```

8 wird nach rechts verschoben.

```text
4, 8, 8, 9, 1
```

Vergleich:

```text
2 < 4
```

4 wird ebenfalls verschoben.

```text
4, 4, 8, 9, 1
```

Jetzt wird die 2 eingefügt.

```text
2, 4, 8, 9, 1
```

---

## Dritter Durchlauf

Element:

```text
9
```

Da

```text
9 > 8
```

bleibt alles unverändert.

```text
2, 4, 8, 9, 1
```

---

## Vierter Durchlauf

Element:

```text
1
```

Alle größeren Werte werden nach rechts verschoben.

```text
2, 4, 8, 9, 9
↓
2, 4, 8, 8, 9
↓
2, 4, 4, 8, 9
↓
2, 2, 4, 8, 9
↓
1, 2, 4, 8, 9
```

Fertig sortiert.

---

## Visualisierung

```text
4, 8, 2, 9, 1
↓
4, 8, 2, 9, 1
↓
2, 4, 8, 9, 1
↓
2, 4, 8, 9, 1
↓
1, 2, 4, 8, 9
```

---

## Pseudocode

```text
für jedes Element ab dem zweiten:

    Element merken

    solange vorheriges Element größer ist:

        Element nach rechts verschieben

    gemerktes Element einsetzen
```

---

## Java-Beispiel

```java
int[] zahlen = {4, 8, 2, 9, 1};

for (int i = 1; i < zahlen.length; i++) {

    int aktuell = zahlen[i];
    int j = i - 1;

    while (j >= 0 && zahlen[j] > aktuell) {

        zahlen[j + 1] = zahlen[j];
        j--;
    }

    zahlen[j + 1] = aktuell;
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
for (int i = 1; i < zahlen.length; i++)
```

Geht jedes Element ab dem zweiten Element durch.

---

### Aktuelles Element merken

```java
int aktuell = zahlen[i];
```

Das Element wird zwischengespeichert.

---

### Größere Elemente verschieben

```java
while (j >= 0 && zahlen[j] > aktuell)
```

Alle größeren Werte werden um eine Position nach rechts verschoben.

---

### Element einsetzen

```java
zahlen[j + 1] = aktuell;
```

Das gemerkte Element wird an der richtigen Stelle eingefügt.

---

## Vor- und Nachteile

### Vorteile

- einfach zu verstehen
- gut für kleine Arrays
- sehr schnell bei fast sortierten Arrays

### Nachteile

- bei großen, unsortierten Arrays langsam
- viele Verschiebungen möglich

---

## Laufzeit

### Best Case

Array bereits sortiert:

```text
O(n)
```

---

### Average Case

```text
O(n²)
```

---

### Worst Case

Array vollständig rückwärts sortiert:

```text
O(n²)
```

---

## Vergleich mit den anderen Sortieralgorithmen

| Bubble Sort | Selection Sort | Insertion Sort |
|--------------|----------------|----------------|
| Tauscht Nachbarn | Sucht das kleinste Element | Fügt Elemente an der richtigen Stelle ein |
| Viele Tauschvorgänge | Ein Tausch pro Durchlauf | Viele Verschiebungen |
| Einfach | Einfach | Einfach |

---

## Merksatz

> Insertion Sort fügt jedes neue Element an der richtigen Stelle im bereits sortierten Bereich ein.

---

# Fragen

## Wie arbeitet Insertion Sort?

> [!spoiler]- Lösung anzeigen
> Jedes Element wird an der richtigen Position im bereits sortierten Bereich eingefügt.

---

## Woran erinnert Insertion Sort?

> [!spoiler]- Lösung anzeigen
> An das Sortieren von Spielkarten auf der Hand.

---

## Welche Laufzeit besitzt Insertion Sort im Best Case?

> [!spoiler]- Lösung anzeigen
> O(n)

---

## Welche Laufzeit besitzt Insertion Sort im Worst Case?

> [!spoiler]- Lösung anzeigen
> O(n²)

---

## Wann eignet sich Insertion Sort besonders gut?

> [!spoiler]- Lösung anzeigen
> Für kleine oder bereits fast sortierte Arrays.

---

## Nächste Themen

- [[10 Rekursion]]
- [[12 Komplexität]]
- [[14 Laufzeitvergleich]]