## Definition

Der Laufzeitvergleich zeigt, wie effizient verschiedene Algorithmen arbeiten.

Dabei wird häufig die Big-O-Notation verwendet, um den Aufwand miteinander zu vergleichen.

Je kleiner die Big-O-Klasse, desto besser skaliert der Algorithmus bei großen Datenmengen.

---

# Suchalgorithmen

| Algorithmus | Voraussetzung | Best Case | Average Case | Worst Case |
|--------------|--------------|-----------|--------------|------------|
| Lineare Suche | Keine | O(1) | O(n) | O(n) |
| Binäre Suche | Sortiertes Array | O(1) | O(log n) | O(log n) |

---

## Vergleich

### Lineare Suche

✅ Vorteile

- funktioniert immer
- einfach zu programmieren
- benötigt kein sortiertes Array

❌ Nachteile

- langsam bei großen Datenmengen

---

### Binäre Suche

✅ Vorteile

- sehr schnell
- wenige Vergleiche

❌ Nachteile

- Array muss sortiert sein

---

# Sortieralgorithmen

| Algorithmus | Best Case | Average Case | Worst Case |
|--------------|-----------|--------------|------------|
| Bubble Sort | O(n)* | O(n²) | O(n²) |
| Selection Sort | O(n²) | O(n²) | O(n²) |
| Insertion Sort | O(n) | O(n²) | O(n²) |

\* mit Optimierung (Abbruch, wenn keine Vertauschung mehr stattfindet)

---

## Vergleich

### Bubble Sort

Arbeitsweise:

```text
Nachbarn vergleichen
↓

Bei Bedarf tauschen
↓

Größte Werte wandern nach rechts
```

---

### Selection Sort

Arbeitsweise:

```text
Kleinstes Element suchen
↓

Nach vorne tauschen
```

---

### Insertion Sort

Arbeitsweise:

```text
Element aufnehmen
↓

An richtiger Stelle einfügen
```

---

# Rekursion

| Algorithmus | Laufzeit |
|--------------|----------|
| Türme von Hanoi | O(2ⁿ) |

---

## Übersicht aller behandelten Algorithmen

| Algorithmus | Big-O | Besonderheit |
|-------------|--------|--------------|
| Array-Zugriff | O(1) | Direkter Zugriff |
| Lineare Suche | O(n) | Kein sortiertes Array nötig |
| Binäre Suche | O(log n) | Array muss sortiert sein |
| Bubble Sort | O(n²) | Vergleicht Nachbarn |
| Selection Sort | O(n²) | Sucht kleinstes Element |
| Insertion Sort | O(n²) | Fügt Elemente ein |
| Türme von Hanoi | O(2ⁿ) | Rekursiver Algorithmus |

---

# Reihenfolge der Laufzeiten

```text
Schnell
│
├── O(1)
│
├── O(log n)
│
├── O(n)
│
├── O(n²)
│
└── O(2ⁿ)
     ↓
Langsam
```

---

# Wann verwendet man welchen Algorithmus?

| Situation | Geeigneter Algorithmus |
|-----------|------------------------|
| Array ist unsortiert | Lineare Suche |
| Array ist sortiert | Binäre Suche |
| Kleine Datenmengen | Bubble Sort, Selection Sort oder Insertion Sort |
| Fast sortiertes Array | Insertion Sort |
| Rekursive Probleme | Rekursion (z. B. Türme von Hanoi) |

---

## Merksätze

> **O(1)** – immer gleich schnell.

> **O(log n)** – halbiert den Suchbereich.

> **O(n)** – arbeitet jedes Element einmal ab.

> **O(n²)** – viele Vergleiche zwischen den Elementen.

> **O(2ⁿ)** – wächst exponentiell und wird schnell sehr langsam.

---

# Fragen

## Welcher Suchalgorithmus ist schneller?

> [!spoiler]- Lösung anzeigen
> Die binäre Suche, wenn das Array sortiert ist.

---

## Welcher Sortieralgorithmus ist bei fast sortierten Arrays besonders gut?

> [!spoiler]- Lösung anzeigen
> Insertion Sort.

---

## Welcher Sortieralgorithmus sucht immer das kleinste Element?

> [!spoiler]- Lösung anzeigen
> Selection Sort.

---

## Welcher Sortieralgorithmus vergleicht benachbarte Elemente?

> [!spoiler]- Lösung anzeigen
> Bubble Sort.

---

## Welche Big-O-Klasse ist am effizientesten?

> [!spoiler]- Lösung anzeigen
> O(1)

---

## Welche Big-O-Klasse besitzt Türme von Hanoi?

> [!spoiler]- Lösung anzeigen
> O(2ⁿ)

---

## Zusammenfassung

```text
O(1)      → Array-Zugriff

O(log n)  → Binäre Suche

O(n)      → Lineare Suche

O(n²)     → Bubble Sort
             Selection Sort
             Insertion Sort

O(2ⁿ)     → Türme von Hanoi
```

---

## Nächste Themen

- [[15 Übungsaufgaben]]