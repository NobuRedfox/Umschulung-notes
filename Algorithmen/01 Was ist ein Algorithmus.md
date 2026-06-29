## Definition

Ein Algorithmus ist eine eindeutige Schritt-für-Schritt-Anleitung zur Lösung eines Problems.

Ein Algorithmus erhält Eingaben (Input), verarbeitet diese und liefert ein Ergebnis (Output).

---

## Eigenschaften

Ein Algorithmus sollte:

- Eindeutigkeit: Jeder Schritt ist klar beschrieben.  
- Endlichkeit: Der Algorithmus endet nach endlich vielen Schritten.  
- Ausführbarkeit: Jeder Schritt kann tatsächlich durchgeführt werden.  
- Ergebnisorientierung: Es wird ein Ergebnis erzeugt.

---

## Aufbau

```text
Input:  
4, 8, 2, 9, 1  
  
Verarbeitung:  
Vergleiche alle Zahlen miteinander.  
  
Output:  
9
```

---

## Beispiele aus dem Alltag

### Kochrezept

1. Wasser kochen
2. Nudeln ins Wasser geben
3. 10 Minuten warten
4. Nudeln abgießen

---

### Wegbeschreibung

1. Geradeaus gehen
2. Links abbiegen
3. Ziel erreichen

---

## Beispiel aus der Informatik

Aufgabe: Größte Zahl finden

Zahlen:

```text
4, 8, 2, 9, 1
```

Vorgehen:

1. Erste Zahl als größte merken
2. Jede weitere Zahl vergleichen
3. Falls größer → neue größte Zahl merken
4. Ergebnis ausgeben

Ergebnis:

```text
9
```

---

## Java-Beispiel

```java
int[] zahlen = {4, 8, 2, 9, 1};

int groesste = zahlen[0];

for (int i = 1; i < zahlen.length; i++) {
    if (zahlen[i] > groesste) {
        groesste = zahlen[i];
    }
}

System.out.println(groesste);
```

---

## Warum sind Algorithmen wichtig?

Algorithmen:

- lösen Probleme
- automatisieren Abläufe
- bilden die Grundlage jedes Programms
- bestimmen oft die Geschwindigkeit eines Programms

---

## Merksatz

>  Ein Algorithmus beschreibt einen Lösungsweg, nicht die Programmiersprache.

---

# Fragen

## Was ist ein Algorithmus?

> [!spoiler]- Lösung anzeigen
> Eine Schritt-für-Schritt-Anleitung zur Lösung eines Problems.

---

## Welche Eigenschaften sollte ein Algorithmus besitzen?

> [!spoiler]- Lösung anzeigen
> Eindeutig, endlich, ausführbar und mit Ergebnis.

---

## Was bedeutet Input?

> [!spoiler]- Lösung anzeigen
> Die Eingabedaten eines Algorithmus.

---

## Was bedeutet Output?

> [!spoiler]- Lösung anzeigen
> Das Ergebnis eines Algorithmus.

---

## Nenne drei Beispiele für Algorithmen.

> [!spoiler]- Lösung anzeigen
> Kochrezept, Wegbeschreibung, Suchalgorithmus.

---

## Warum sind Algorithmen wichtig?

> [!spoiler]- Lösung anzeigen
> Sie lösen Probleme und bilden die Grundlage von Programmen.

---

## Nächste Themen

- [[02 Pseudocode]]
- [[03 Struktogramme]]
- [[04 Arrays]]
- [[05 Lineare Suche]]
- [[06 Binäre Suche]]
- [[07 Bubble Sort]]
- [[08 Selection Sort]]
- [[09 Insertion Sort]]
- [[10 Rekursion]]
- [[11 Türme von Hanoi]]
- [[12 Komplexität]]
- [[13 Big-O-Notation]]