## Definition

Ein Array ist eine Datenstruktur, die mehrere Werte desselben Datentyps unter einem gemeinsamen Namen speichert.

Jedes Element besitzt einen festen Platz, der über einen Index angesprochen wird.

---

## Eigenschaften

Arrays:

- speichern mehrere Werte
- enthalten nur einen Datentyp
- besitzen eine feste Größe
- sind über Indizes zugänglich
- beginnen bei Index 0

---

## Beispiel

Array mit fünf Zahlen:

```text
Index:   0   1   2   3   4
Wert:    4   8   2   9   1
```

---

## Warum verwendet man Arrays?

Statt viele einzelne Variablen anzulegen:

```java
int zahl1 = 4;
int zahl2 = 8;
int zahl3 = 2;
int zahl4 = 9;
int zahl5 = 1;
```

kann man alle Werte in einem Array speichern:

```java
int[] zahlen = {4, 8, 2, 9, 1};
```

---

## Array erstellen

### Mit Werten

```java
int[] zahlen = {4, 8, 2, 9, 1};
```

---

### Mit fester Größe

```java
int[] zahlen = new int[5];
```

Standardwerte:

```text
Index:   0   1   2   3   4
Wert:    0   0   0   0   0
```

---

## Auf Elemente zugreifen

```java
int[] zahlen = {4, 8, 2, 9, 1};

System.out.println(zahlen[0]);
```

Ausgabe:

```text
4
```

---

## Werte ändern

```java
int[] zahlen = {4, 8, 2, 9, 1};

zahlen[2] = 100;
```

Ergebnis:

```text
4, 8, 100, 9, 1
```

---

## Länge eines Arrays

```java
int[] zahlen = {4, 8, 2, 9, 1};

System.out.println(zahlen.length);
```

Ausgabe:

```text
5
```

---

## Durch ein Array laufen

```java
int[] zahlen = {4, 8, 2, 9, 1};

for (int i = 0; i < zahlen.length; i++) {
    System.out.println(zahlen[i]);
}
```

Ausgabe:

```text
4
8
2
9
1
```

---

## For-Each-Schleife

```java
int[] zahlen = {4, 8, 2, 9, 1};

for (int zahl : zahlen) {
    System.out.println(zahl);
}
```

Die For-Each-Schleife eignet sich, wenn alle Elemente nacheinander gelesen werden sollen.

---

## Typische Fehler

### Falscher Index

```java
int[] zahlen = {4, 8, 2};

System.out.println(zahlen[3]);
```

Fehler:

```text
ArrayIndexOutOfBoundsException
```

Gültige Indizes:

```text
0, 1, 2
```

---

## Zusammenhang mit Algorithmen

Viele Algorithmen arbeiten auf Arrays, zum Beispiel:

- Lineare Suche
- Binäre Suche
- Bubble Sort
- Selection Sort
- Insertion Sort

---

## Merksatz

> Ein Array speichert mehrere Werte desselben Datentyps unter einem gemeinsamen Namen.

---

# Fragen

## Was ist ein Array?

> [!spoiler]- Lösung anzeigen
> Eine Datenstruktur zum Speichern mehrerer Werte desselben Datentyps.

---

## Mit welchem Index beginnt ein Array?

> [!spoiler]- Lösung anzeigen
> Mit Index 0.

---

## Wie erhält man die Länge eines Arrays?

> [!spoiler]- Lösung anzeigen
> Mit `.length`.

---

## Können Arrays unterschiedliche Datentypen enthalten?

> [!spoiler]- Lösung anzeigen
> Nein, alle Elemente besitzen denselben Datentyp.

---

## Warum sind Arrays wichtig?

> [!spoiler]- Lösung anzeigen
> Viele Such- und Sortieralgorithmen arbeiten auf Arrays.

---

## Nächste Themen

- [[05 Lineare Suche]]
- [[06 Binäre Suche]]
- [[07 Bubble Sort]]