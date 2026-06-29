## Definition

Die lineare Suche ist ein Suchalgorithmus, der ein Array Element für Element durchsucht, bis der gesuchte Wert gefunden wird.

Dabei wird jedes Element nacheinander geprüft.

---

## Eigenschaften

Die lineare Suche:

- arbeitet von links nach rechts
- prüft Elemente nacheinander
- benötigt kein sortiertes Array
- ist einfach zu verstehen
- kann langsam werden bei großen Datenmengen

---

## Beispiel

Gesucht:

```text
9
```

Array:

```text
Index:   0   1   2   3   4
Wert:    4   8   2   9   1
```

Ablauf:

```text
4 → nicht gefunden
8 → nicht gefunden
2 → nicht gefunden
9 → gefunden
```

Ergebnis:

```text
Index 3
```

---

## Pseudocode

```text
für jedes Element im Array:

    wenn Element = gesucht:
        Ausgabe "Gefunden"
        Ende

Ausgabe "Nicht gefunden"
```

---

## Java-Beispiel

```java
int[] zahlen = {4, 8, 2, 9, 1};

int gesucht = 9;

for (int i = 0; i < zahlen.length; i++) {

    if (zahlen[i] == gesucht) {

        System.out.println("Gefunden an Index: " + i);
        break;
    }
}
```

Ausgabe:

```text
Gefunden an Index: 3
```

---

## Rückgabe des Index

Oft möchte man wissen, an welcher Position sich der Wert befindet.

```java
public static int lineareSuche(int[] array, int gesucht) {

    for (int i = 0; i < array.length; i++) {

        if (array[i] == gesucht) {
            return i;
        }
    }

    return -1;
}
```

Verwendung:

```java
int[] zahlen = {4, 8, 2, 9, 1};

int index = lineareSuche(zahlen, 9);

System.out.println(index);
```

Ausgabe:

```text
3
```

---

## Was bedeutet -1?

```java
return -1;
```

bedeutet:

```text
Wert nicht gefunden
```

Da Array-Indizes bei 0 beginnen, kann -1 niemals ein gültiger Index sein.

---

## Vor- und Nachteile

### Vorteile

- einfach zu programmieren
- leicht verständlich
- funktioniert mit unsortierten Arrays

### Nachteile

- langsam bei großen Datenmengen
- eventuell müssen alle Elemente geprüft werden

---

## Laufzeit

### Best Case

Der gesuchte Wert befindet sich direkt am Anfang.

```text
4, 8, 2, 9, 1
↑
```

Nur 1 Vergleich.

```text
O(1)
```

---

### Worst Case

Der gesuchte Wert befindet sich am Ende oder existiert nicht.

```text
4, 8, 2, 9, 1
            ↑
```

Alle Elemente müssen geprüft werden.

```text
O(n)
```

---

## Beispiel Schritt für Schritt

Gesucht:

```text
1
```

Array:

```text
4, 8, 2, 9, 1
```

Vergleiche:

```text
4 == 1 ? Nein
8 == 1 ? Nein
2 == 1 ? Nein
9 == 1 ? Nein
1 == 1 ? Ja
```

Gefunden.

---

## Merksatz

> Die lineare Suche durchsucht ein Array Element für Element, bis der gesuchte Wert gefunden wird.

---

# Fragen

## Was ist die lineare Suche?

> [!spoiler]- Lösung anzeigen
> Ein Suchalgorithmus, der Elemente nacheinander durchsucht.

---

## Muss das Array sortiert sein?

> [!spoiler]- Lösung anzeigen
> Nein.

---

## Was bedeutet der Rückgabewert -1?

> [!spoiler]- Lösung anzeigen
> Der gesuchte Wert wurde nicht gefunden.

---

## Wann ist die lineare Suche langsam?

> [!spoiler]- Lösung anzeigen
> Bei großen Datenmengen, da viele Elemente geprüft werden müssen.

---

## Wie lautet die Worst-Case-Laufzeit?

> [!spoiler]- Lösung anzeigen
> O(n)

---

## Nächste Themen

- [[06 Binäre Suche]]
- [[07 Bubble Sort]]
- [[12 Komplexität]]