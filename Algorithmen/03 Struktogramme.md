## Definition

Ein Struktogramm ist eine grafische Darstellung eines Algorithmus.

Es zeigt die Reihenfolge von Anweisungen, Bedingungen und Schleifen in einer übersichtlichen Form.

Struktogramme helfen dabei, einen Algorithmus zu planen und zu verstehen, bevor er programmiert wird.

---

## Eigenschaften

Struktogramme:

- stellen Algorithmen grafisch dar
- sind unabhängig von Programmiersprachen
- zeigen die Programmstruktur
- helfen bei der Planung von Programmen
- sind leicht lesbar

---

## Grundelemente

### Anweisung

Eine einfache Aktion.

```text
+------------------+
| Zahl ausgeben    |
+------------------+
```

---

### Bedingung

Eine Entscheidung mit zwei möglichen Wegen.

```text
+------------------+
| Alter >= 18 ?    |
+--------+---------+
| Ja     | Nein    |
+--------+---------+
```

---

### Schleife

Anweisungen werden mehrfach wiederholt.

```text
+------------------+
| solange i < 10   |
+------------------+
| i = i + 1        |
+------------------+
```

---

## Beispiel: Größte Zahl finden

Aufgabe:

```text
4, 8, 2, 9, 1
```

Struktogramm:

```text
+--------------------------------+
| größte = erste Zahl            |
+--------------------------------+
| Für jede weitere Zahl          |
|                                |
|  Ist Zahl > größte ?           |
|                                |
|  Ja -> größte = Zahl           |
+--------------------------------+
| Ausgabe größte                 |
+--------------------------------+
```

Ergebnis:

```text
9
```

---

## Beispiel: Volljährigkeit prüfen

Pseudocode:

```text
wenn Alter >= 18:
    Ausgabe "Volljährig"
sonst:
    Ausgabe "Minderjährig"
```

Struktogramm:

```text
+------------------------------+
| Alter eingeben               |
+--------------+---------------+
| Alter >= 18? |               |
+------+-------+---------------+
| Ja   | Nein                  |
+------+-----------------------+
| Volljährig                   |
| Minderjährig                 |
+------------------------------+
```

---

## Vorteile

- übersichtliche Darstellung
- Fehler werden früh erkannt
- unabhängig von Java oder anderen Sprachen
- erleichtert die Planung von Programmen

---

## Unterschied zu Pseudocode

### Pseudocode

```text
wenn Alter >= 18:
    Ausgabe "Volljährig"
sonst:
    Ausgabe "Minderjährig"
```

### Struktogramm

```text
+--------------+
| Alter >= 18? |
+------+-------+
| Ja   | Nein  |
+------+-------+
```

Pseudocode beschreibt den Ablauf als Text.

Struktogramme stellen denselben Ablauf grafisch dar.

---

## Merksatz

> Ein Struktogramm zeigt die Struktur eines Algorithmus in grafischer Form.

---

# Fragen

## Was ist ein Struktogramm?

> [!spoiler]- Lösung anzeigen
> Eine grafische Darstellung eines Algorithmus.

---

## Warum verwendet man Struktogramme?

> [!spoiler]- Lösung anzeigen
> Um Algorithmen übersichtlich darzustellen und zu planen.

---

## Welche Grundelemente gibt es?

> [!spoiler]- Lösung anzeigen
> Anweisungen, Bedingungen und Schleifen.

---

## Sind Struktogramme an eine Programmiersprache gebunden?

> [!spoiler]- Lösung anzeigen
> Nein.

---

## Was ist der Unterschied zwischen Pseudocode und Struktogramm?

> [!spoiler]- Lösung anzeigen
> Pseudocode beschreibt einen Algorithmus als Text, ein Struktogramm stellt ihn grafisch dar.

---

## Nächste Themen

- [[04 Arrays]]
- [[05 Lineare Suche]]
- [[06 Binäre Suche]]