# oder Class Diagram

> [!info]
> Beschreibt die Struktur eines Programms mit Klassen, Attributen, Methoden und deren Beziehungen.

---
![[Klassendiagramm.png]]

# Definition

Ein Klassendiagramm zeigt:

- welche Klassen existieren
- welche Attribute sie besitzen
- welche Methoden sie enthalten
- wie die Klassen miteinander verbunden sind

Es ist der Bauplan eines objektorientierten Programms.

---

# Aufbau einer Klasse

Eine Klasse besteht aus drei Bereichen:

```mermaid
classDiagram

class Auto {
    marke : String
    baujahr : int

    fahren() : void
    bremsen() : void
}
```

---

## Klassenname

Der obere Bereich enthält den Namen der Klasse.

Beispiel:

```text
Auto
```

---

## Attribute

Der mittlere Bereich enthält die Eigenschaften der Klasse.

```text
marke : String
baujahr : int
```

Java:

```java
private String marke;
private int baujahr;
```

---

## Methoden

Der untere Bereich enthält die Funktionen der Klasse.

```text
fahren() : void
bremsen() : void
```

Java:

```java
public void fahren() {

}

public void bremsen() {

}
```

---

# Sichtbarkeiten

| Symbol | Bedeutung |
|----------|----------|
| + | public |
| - | private |
| # | protected |

Beispiel:

```mermaid
classDiagram

class Auto {
    - marke : String
    - baujahr : int

    + fahren() : void
    + bremsen() : void
}
```

---

# Beziehungen

## Assoziation

Eine Klasse kennt eine andere Klasse.

```mermaid
classDiagram

class Fahrer
class Auto

Fahrer --> Auto : fährt
```

Java:

```java
class Auto {
    Fahrer fahrer;
}
```

---

## Vererbung

Eine Klasse erbt von einer anderen.

```mermaid
classDiagram

class Fahrzeug
class Auto

Fahrzeug <|-- Auto
```

Java:

```java
class Fahrzeug {

}

class Auto extends Fahrzeug {

}
```

---

## Aggregation

Schwache "Hat-ein"-Beziehung.

Ein Team hat Spieler.

```mermaid
classDiagram

class Team
class Spieler

Team o-- Spieler
```

Die Spieler können auch ohne Team existieren.

---

## Komposition

Starke "Hat-eine"-Beziehung.

Ein Haus hat Räume.

```mermaid
classDiagram

class Haus
class Raum

Haus *-- Raum
```

Wird das Haus gelöscht, existieren die Räume nicht mehr.

---

# Multiplizitäten

Zeigen an, wie viele Objekte beteiligt sind.

---

## Eins zu Eins

```mermaid
classDiagram

class Person
class Ausweis

Person "1" -- "1" Ausweis
```

Eine Person besitzt genau einen Ausweis.

---

## Eins zu Viele

```mermaid
classDiagram

class Kunde
class Bestellung

Kunde "1" -- "*" Bestellung
```

Ein Kunde kann mehrere Bestellungen haben.

---

## Viele zu Viele

```mermaid
classDiagram

class Student
class Kurs

Student "*" -- "*" Kurs
```

Ein Student kann mehrere Kurse besuchen.

Ein Kurs kann mehrere Studenten enthalten.

---

# Beispiel: Immobilie

```mermaid
classDiagram

class Immobilie {
    - adresse : String
    - wohnflaeche : double
    - preis : double

    + anzeigen() : void
    + preisProQM() : double
}
```

---

# Beispiel: Vererbung

```mermaid
classDiagram

class Immobilie
class Haus
class Wohnung

Immobilie <|-- Haus
Immobilie <|-- Wohnung
```

Java:

```java
class Immobilie {

}

class Haus extends Immobilie {

}

class Wohnung extends Immobilie {

}
```

---

# Beispiel: Eigentümer und Immobilie

```mermaid
classDiagram

class Eigentuemer {
    - name : String
    - telefon : String
}

class Immobilie {
    - adresse : String
    - preis : double
}

Eigentuemer "1" -- "*" Immobilie : besitzt
```

Bedeutung:

- Ein Eigentümer kann mehrere Immobilien besitzen.
- Eine Immobilie gehört genau einem Eigentümer.

---

# Vorteile

- Übersicht über die Programmstruktur
- Grundlage für die Implementierung
- Hilft bei Planung und Dokumentation
- Zeigt Beziehungen zwischen Klassen

---

# Merksatz

> Das Klassendiagramm beschreibt die Struktur eines Programms mit Klassen, Attributen, Methoden und Beziehungen.

Es beantwortet die Frage:

**Welche Klassen gibt es und wie hängen sie zusammen?**

---

# Fragen

## Was beschreibt ein Klassendiagramm?

> [!spoiler]- Lösung anzeigen
> Die Struktur eines Programms mit Klassen, Attributen, Methoden und Beziehungen.

---

## Welche drei Bereiche besitzt eine Klasse?

> [!spoiler]- Lösung anzeigen
> Klassenname, Attribute und Methoden.

---

## Wofür steht das Symbol "+"?

> [!spoiler]- Lösung anzeigen
> public

---

## Was bedeutet Vererbung?

> [!spoiler]- Lösung anzeigen
> Eine Klasse übernimmt Eigenschaften und Methoden einer anderen Klasse.

---

## Was ist eine Assoziation?

> [!spoiler]- Lösung anzeigen
> Eine Klasse kennt oder verwendet eine andere Klasse.

---

## Was ist der Unterschied zwischen Aggregation und Komposition?

> [!spoiler]- Lösung anzeigen
> Bei der Aggregation können Objekte unabhängig existieren, bei der Komposition nicht.

---

## Was bedeutet die Multiplizität "1..*"?

> [!spoiler]- Lösung anzeigen
> Ein Objekt ist mit mindestens einem oder mehreren anderen Objekten verbunden.