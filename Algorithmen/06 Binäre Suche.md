## Definition

Die binäre Suche ist ein Suchalgorithmus für sortierte Arrays.

Statt jedes Element einzeln zu prüfen, wird das Array immer wieder in zwei Hälften geteilt.

Dadurch findet die binäre Suche gesuchte Werte deutlich schneller als die lineare Suche.

---

## Voraussetzung

Das Array muss sortiert sein.

Beispiel:

```text
1, 2, 4, 8, 9
```

Nicht geeignet:

```text
4, 8, 2, 9, 1
```

---

## Funktionsweise

Gesucht:

```text
8
```

Array:

```text
Index:   0   1   2   3   4
Wert:    1   2   4   8   9
```

---

### Schritt 1

Mittleres Element bestimmen:

```text
4
```

Vergleich:

```text
8 > 4
```

Der gesuchte Wert muss rechts liegen.

Linke Hälfte wird verworfen.

---

### Schritt 2

Verbleibender Bereich:

```text
8, 9
```

Mittleres Element:

```text
8
```

Gefunden.

---

## Visualisierung

```text
1  2  4  8  9
      ↑

8 > 4

      X
1  2  4 | 8  9

          ↑

Gefunden
```

---

## Pseudocode

```text
links = 0
rechts = letztes Element

solange links <= rechts:

    mitte berechnen

    wenn Wert an mitte = gesucht:
        gefunden

    wenn gesucht < Wert an mitte:
        rechts verschieben

    sonst:
        links verschieben
```

---

## Java-Beispiel

```java
public static int binaereSuche(int[] array, int gesucht) {

    int links = 0;
    int rechts = array.length - 1;

    while (links <= rechts) {

        int mitte = (links + rechts) / 2;

        if (array[mitte] == gesucht) {
            return mitte;
        }

        if (gesucht < array[mitte]) {
            rechts = mitte - 1;
        } else {
            links = mitte + 1;
        }
    }

    return -1;
}
```

---

## Verwendung

```java
int[] zahlen = {1, 2, 4, 8, 9};

int index = binaereSuche(zahlen, 8);

System.out.println(index);
```

Ausgabe:

```text
3
```

---

## Beispiel Schritt für Schritt

Gesucht:

```text
13
```

Array:

```text
1, 3, 5, 7, 9, 11, 13, 15
```

---

### Vergleich 1

```text
Mitte = 7
```

```text
13 > 7
```

Links wird verworfen.

---

### Vergleich 2

```text
11
```

```text
13 > 11
```

Links wird erneut verworfen.

---

### Vergleich 3

```text
13
```

Gefunden.

---

## Warum ist die binäre Suche schneller?

Lineare Suche:

```text
1
2
3
4
5
6
7
8
...
```

Element für Element.

---

Binäre Suche:

```text
1000 Elemente
↓
500
↓
250
↓
125
↓
62
↓
31
↓
15
↓
7
↓
3
↓
1
```

Die Datenmenge wird bei jedem Schritt halbiert.

---

## Vor- und Nachteile

### Vorteile

- sehr schnell
- wenige Vergleiche notwendig
- gut für große Datenmengen

### Nachteile

- Array muss sortiert sein
- etwas schwieriger zu verstehen als die lineare Suche

---

## Laufzeit

### Best Case

Gesuchter Wert befindet sich direkt in der Mitte.

```text
O(1)
```

---

### Average Case

```text
O(log n)
```

---

### Worst Case

```text
O(log n)
```

---

## Vergleich zur linearen Suche

| Eigenschaft | Lineare Suche | Binäre Suche |
|------------|------------|------------|
| Sortiertes Array nötig | Nein | Ja |
| Einfachheit | Sehr einfach | Etwas komplexer |
| Worst Case | O(n) | O(log n) |
| Geschwindigkeit | Langsamer | Schneller |

---

## Merksatz

> Die binäre Suche halbiert den Suchbereich bei jedem Schritt und benötigt deshalb deutlich weniger Vergleiche als die lineare Suche.

---

# Fragen

## Wann kann die binäre Suche verwendet werden?

> [!spoiler]- Lösung anzeigen
> Nur bei sortierten Arrays.

---

## Was passiert bei jedem Schritt?

> [!spoiler]- Lösung anzeigen
> Der Suchbereich wird halbiert.

---

## Warum ist die binäre Suche schneller als die lineare Suche?

> [!spoiler]- Lösung anzeigen
> Weil nicht jedes Element geprüft werden muss.

---

## Wie lautet die Worst-Case-Laufzeit?

> [!spoiler]- Lösung anzeigen
> O(log n)

---

## Was bedeutet der Rückgabewert -1?

> [!spoiler]- Lösung anzeigen
> Der Wert wurde nicht gefunden.

---

## Nächste Themen

- [[07 Bubble Sort]]
- [[12 Komplexität]]
- [[13 Big-O-Notation]]