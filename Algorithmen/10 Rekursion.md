# Rekursion

## Definition

Rekursion ist ein Verfahren, bei dem eine Methode sich selbst aufruft.

Dabei wird ein Problem in kleinere Teilprobleme zerlegt, bis ein einfach lösbarer Fall erreicht ist.

---

## Eigenschaften

Rekursion:

- eine Methode ruft sich selbst auf
- zerlegt Probleme in kleinere Teilprobleme
- benötigt eine Abbruchbedingung
- endet, wenn der Basisfall erreicht wird

---

## Bestandteile einer Rekursion

Jede Rekursion besteht aus zwei Teilen:

### Basisfall (Abbruchbedingung)

Beendet die Rekursion.

Beispiel:

```java
if (n == 1) {
    return;
}
```

---

### Rekursiver Aufruf

Die Methode ruft sich selbst mit einem kleineren Problem auf.

Beispiel:

```java
rekursion(n - 1);
```

---

## Beispiel

Aufgabe:

Die Zahlen von 5 bis 1 ausgeben.

```text
5
4
3
2
1
```

---

## Java-Beispiel

```java
public static void countdown(int n) {

    if (n == 0) {
        return;
    }

    System.out.println(n);

    countdown(n - 1);
}
```

Aufruf:

```java
countdown(5);
```

Ausgabe:

```text
5
4
3
2
1
```

---

## Ablauf

```text
countdown(5)

↓

countdown(4)

↓

countdown(3)

↓

countdown(2)

↓

countdown(1)

↓

countdown(0)

↓

Ende
```

---

## Warum braucht man eine Abbruchbedingung?

Ohne Basisfall ruft sich die Methode unendlich oft selbst auf.

Beispiel:

```java
public static void fehler() {

    fehler();
}
```

Ergebnis:

```text
StackOverflowError
```

---

## Beispiel: Fakultät

Die Fakultät einer Zahl wird so berechnet:

```text
5! = 5 × 4 × 3 × 2 × 1
```

Rekursiv:

```java
public static int fakultaet(int n) {

    if (n == 1) {
        return 1;
    }

    return n * fakultaet(n - 1);
}
```

Aufruf:

```java
System.out.println(fakultaet(5));
```

Ausgabe:

```text
120
```

---

## Vorteile

- übersichtlicher Code
- gut für Probleme, die sich in kleinere Teilprobleme zerlegen lassen
- oft einfacher als verschachtelte Schleifen

---

## Nachteile

- mehr Speicherverbrauch
- kann langsamer sein als Schleifen
- ohne Abbruchbedingung entsteht ein StackOverflowError

---

## Typische Anwendungsgebiete

- Türme von Hanoi
- Binäre Bäume
- Verzeichnisstrukturen
- Tiefensuche (DFS)
- Fakultät
- Fibonacci

---

## Merksatz

> Rekursion bedeutet, dass eine Methode sich selbst aufruft, bis eine Abbruchbedingung erreicht wird.

---

# Fragen

## Was ist Rekursion?

> [!spoiler]- Lösung anzeigen
> Eine Methode ruft sich selbst auf.

---

## Wozu dient die Abbruchbedingung?

> [!spoiler]- Lösung anzeigen
> Sie beendet die Rekursion.

---

## Was passiert ohne Abbruchbedingung?

> [!spoiler]- Lösung anzeigen
> Die Methode ruft sich unendlich oft selbst auf und verursacht einen StackOverflowError.

---

## Aus welchen zwei Bestandteilen besteht eine Rekursion?

> [!spoiler]- Lösung anzeigen
> Basisfall und rekursiver Aufruf.

---

## Nenne zwei Beispiele für Rekursion.

> [!spoiler]- Lösung anzeigen
> Türme von Hanoi und Fakultät.

---

## Nächste Themen

- [[11 Türme von Hanoi]]
- [[12 Komplexität]]
- [[13 Big-O-Notation]]