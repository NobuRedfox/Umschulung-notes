## Definition

Die Big-O-Notation beschreibt, wie stark die Laufzeit eines Algorithmus mit zunehmender Eingabegröße wächst.

Dabei interessiert nicht die genaue Ausführungszeit in Sekunden, sondern das Verhalten bei immer größeren Datenmengen.

---

## Warum verwendet man Big-O?

Computer sind unterschiedlich schnell.

Ein Algorithmus sollte deshalb unabhängig von der Hardware bewertet werden.

Big-O beschreibt nur das Wachstum der Laufzeit.

---

## Eingabegröße

In der Big-O-Notation steht

```text
n
```

für die Größe der Eingabe.

Beispiele:

```text
10 Elemente
100 Elemente
1000 Elemente
1000000 Elemente
```

Je größer **n**, desto wichtiger wird die Laufzeit.

---

## Die wichtigsten Big-O-Klassen

### O(1) – Konstant

Die Laufzeit bleibt immer gleich.

Beispiel:

```java
System.out.println(array[3]);
```

Egal ob das Array 10 oder 1.000.000 Elemente besitzt – der Zugriff dauert gleich lange.

---

### O(log n) – Logarithmisch

Die Datenmenge wird bei jedem Schritt halbiert.

Beispiel:

- Binäre Suche

```text
1000
↓
500
↓
250
↓
125
↓
...
```

Sehr schnell.

---

### O(n) – Linear

Jedes Element wird genau einmal betrachtet.

Beispiel:

- Lineare Suche

```text
1
2
3
4
5
...
```

Verdoppelt sich die Datenmenge, verdoppelt sich ungefähr auch die Laufzeit.

---

### O(n²) – Quadratisch

Jedes Element wird mit vielen anderen Elementen verglichen.

Beispiele:

- Bubble Sort
- Selection Sort
- Insertion Sort (Average/Worst Case)

```text
□□□□□

□ □ □ □ □
□ □ □ □ □
□ □ □ □ □
□ □ □ □ □
□ □ □ □ □
```

Die Laufzeit wächst sehr schnell.

---

### O(2ⁿ) – Exponentiell

Mit jedem zusätzlichen Element verdoppelt sich ungefähr die Arbeit.

Beispiel:

- Türme von Hanoi

```text
n = 1 → 1

n = 2 → 2

n = 3 → 4

n = 4 → 8

...
```

Sehr langsam.

---

## Vergleich

| Big-O | Beschreibung | Beispiel |
|-------|--------------|-----------|
| O(1) | konstant | Array-Zugriff |
| O(log n) | logarithmisch | Binäre Suche |
| O(n) | linear | Lineare Suche |
| O(n²) | quadratisch | Bubble Sort |
| O(2ⁿ) | exponentiell | Türme von Hanoi |

---

## Von schnell nach langsam

```text
O(1)
↓

O(log n)
↓

O(n)
↓

O(n²)
↓

O(2ⁿ)
```

Je weiter unten, desto langsamer wird der Algorithmus bei großen Datenmengen.

---

## Beispiele aus euren Algorithmen

| Algorithmus | Big-O |
|-------------|--------|
| Array-Zugriff | O(1) |
| Lineare Suche | O(n) |
| Binäre Suche | O(log n) |
| Bubble Sort | O(n²) |
| Selection Sort | O(n²) |
| Insertion Sort | O(n²) |
| Türme von Hanoi | O(2ⁿ) |

---

## Was Big-O nicht beschreibt

Big-O beschreibt **nicht**:

- die Laufzeit in Sekunden
- die Geschwindigkeit eines bestimmten Computers
- kleine Unterschiede zwischen Programmen

Big-O beschreibt nur, wie die Laufzeit wächst, wenn die Eingabe größer wird.

---

## Merksatz

> Die Big-O-Notation beschreibt, wie stark die Laufzeit eines Algorithmus mit wachsender Eingabegröße zunimmt.

---

# Fragen

## Was beschreibt die Big-O-Notation?

> [!spoiler]- Lösung anzeigen
> Das Wachstum der Laufzeit eines Algorithmus.

---

## Wofür steht n?

> [!spoiler]- Lösung anzeigen
> Für die Größe der Eingabe.

---

## Welche Big-O-Klasse besitzt die lineare Suche?

> [!spoiler]- Lösung anzeigen
> O(n)

---

## Welche Big-O-Klasse besitzt die binäre Suche?

> [!spoiler]- Lösung anzeigen
> O(log n)

---

## Welche Big-O-Klasse besitzen Bubble Sort und Selection Sort?

> [!spoiler]- Lösung anzeigen
> O(n²)

---

## Welche Big-O-Klasse besitzt der Array-Zugriff?

> [!spoiler]- Lösung anzeigen
> O(1)

---

## Welche Big-O-Klasse besitzt Türme von Hanoi?

> [!spoiler]- Lösung anzeigen
> O(2ⁿ)

---

## Nächste Themen

- [[14 Laufzeitvergleich]]
- [[15 Übungsaufgaben]]