## Definition

Die Türme von Hanoi sind ein klassisches Beispiel für Rekursion.

Es gibt drei Stäbe und mehrere Scheiben.  
Alle Scheiben sollen von einem Startstab auf einen Zielstab bewegt werden.

---

## Regeln

- Es darf immer nur eine Scheibe bewegt werden.
- Eine größere Scheibe darf niemals auf einer kleineren Scheibe liegen.
- Es gibt einen Startstab, einen Hilfsstab und einen Zielstab.

---

## Aufbau

```text
Startstab        Hilfsstab        Zielstab
   A                B                C
```

Beispiel mit 3 Scheiben:

```text
A: 3 2 1
B:
C:
```

Ziel:

```text
A:
B:
C: 3 2 1
```

---

## Grundidee

Um `n` Scheiben von A nach C zu bewegen:

1. Bewege `n - 1` Scheiben von A nach B
2. Bewege die größte Scheibe von A nach C
3. Bewege `n - 1` Scheiben von B nach C

---

## Pseudocode

```text
hanoi(n, von, hilfe, nach):

    wenn n == 1:
        Ausgabe von -> nach
        Ende

    hanoi(n - 1, von, nach, hilfe)

    Ausgabe von -> nach

    hanoi(n - 1, hilfe, von, nach)
```

---

## Java-Beispiel

```java
public class Main {

    public static void main(String[] args) {
        hanoi(3, "A", "B", "C");
    }

    public static void hanoi(int n, String von, String hilfe, String nach) {

        if (n == 1) {
            System.out.println(von + " -> " + nach);
            return;
        }

        hanoi(n - 1, von, nach, hilfe);

        System.out.println(von + " -> " + nach);

        hanoi(n - 1, hilfe, von, nach);
    }
}
```

---

## Ausgabe bei 3 Scheiben

```text
A -> C
A -> B
C -> B
A -> C
B -> A
B -> C
A -> C
```

---

## Erklärung der Parameter

```java
hanoi(n, von, hilfe, nach)
```

| Parameter | Bedeutung |
|---|---|
| `n` | Anzahl der Scheiben |
| `von` | Startstab |
| `hilfe` | Hilfsstab |
| `nach` | Zielstab |

---

## Ablauf bei 3 Scheiben

Aufruf:

```java
hanoi(3, "A", "B", "C");
```

Bedeutung:

```text
Bewege 3 Scheiben von A nach C mit Hilfe von B.
```

---

### Schritt 1

```java
hanoi(2, "A", "C", "B");
```

Bewege 2 Scheiben von A nach B.

---

### Schritt 2

```text
A -> C
```

Bewege die größte Scheibe von A nach C.

---

### Schritt 3

```java
hanoi(2, "B", "A", "C");
```

Bewege 2 Scheiben von B nach C.

---

## Wichtiges Muster

```java
hanoi(n - 1, von, nach, hilfe);
```

Bedeutet:

```text
Lege die kleineren Scheiben erstmal auf den Hilfsstab.
```

---

```java
System.out.println(von + " -> " + nach);
```

Bedeutet:

```text
Bewege die größte Scheibe zum Zielstab.
```

---

```java
hanoi(n - 1, hilfe, von, nach);
```

Bedeutet:

```text
Lege die kleineren Scheiben vom Hilfsstab auf den Zielstab.
```

---

## Anzahl der Züge

Die Anzahl der nötigen Züge lautet:

```text
2^n - 1
```

Beispiele:

| Scheiben | Züge |
|---|---:|
| 1 | 1 |
| 2 | 3 |
| 3 | 7 |
| 4 | 15 |
| 5 | 31 |

---

## Laufzeit

Die Laufzeit wächst sehr schnell.

```text
O(2^n)
```

Bei jeder zusätzlichen Scheibe verdoppelt sich die Arbeit ungefähr.

---

## Merksatz

> Bei den Türmen von Hanoi wird das Problem immer in kleinere Teilprobleme zerlegt: erst kleinere Scheiben weglegen, dann große Scheibe bewegen, dann kleinere Scheiben wieder darauflegen.

---

# Fragen

## Was zeigen die Türme von Hanoi besonders gut?

> [!spoiler]- Lösung anzeigen
> Rekursion.

---

## Welche drei Stäbe gibt es?

> [!spoiler]- Lösung anzeigen
> Startstab, Hilfsstab und Zielstab.

---

## Was ist die wichtigste Regel?

> [!spoiler]- Lösung anzeigen
> Eine größere Scheibe darf niemals auf einer kleineren Scheibe liegen.

---

## Was bedeutet `n`?

> [!spoiler]- Lösung anzeigen
> Die Anzahl der Scheiben.

---

## Wie viele Züge braucht man bei 3 Scheiben?

> [!spoiler]- Lösung anzeigen
> 7 Züge.

---

## Wie lautet die Formel für die Anzahl der Züge?

> [!spoiler]- Lösung anzeigen
> 2^n - 1

---

## Nächste Themen

- [[12 Komplexität]]
- [[13 Big-O-Notation]]
- [[14 Laufzeitvergleich]]