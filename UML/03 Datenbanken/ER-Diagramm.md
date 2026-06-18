# oder Entity-Relationship-Diagram

> [!info]
> Beschreibt die Struktur einer Datenbank mit Entitäten, Attributen und Beziehungen.

---
![[ER-Diagramm.png]]
# Definition

Ein ER-Diagramm (Entity-Relationship-Diagramm) wird verwendet, um Datenbanken zu modellieren.

Es zeigt:

- welche Daten gespeichert werden
- welche Entitäten existieren
- welche Attribute die Entitäten besitzen
- wie die Entitäten miteinander verbunden sind

---

# Bestandteile

## Entität (Entity)

Eine Entität entspricht meist einer Tabelle in der Datenbank.

Beispiele:

- Kunde
- Bestellung
- Film
- Benutzer
- Mitarbeiter
- Projekt

Darstellung:

```text
+-----------+
|   Kunde   |
+-----------+
```

---

## Attribut

Attribute beschreiben Eigenschaften einer Entität.

In ER-Diagrammen werden Attribute meist als Ellipsen dargestellt.

Beispiel:

```text
          Vorname
             |
ID ─ Mitarbeiter ─ Nachname
             |
     Personalnummer
```

---

## Primärschlüssel (PK)

Der Primärschlüssel identifiziert jeden Datensatz eindeutig.

Im ER-Diagramm wird er häufig unterstrichen dargestellt.

Beispiele:

- ID
- BenutzerID
- Kundennummer

---

## Beziehung (Relationship)

Beziehungen verbinden Entitäten miteinander.

In ER-Diagrammen werden Beziehungen als Raute dargestellt.

Beispiele:

```text
Mitarbeiter ── arbeitet_an ── Projekt

Mitarbeiter ── leitet ── Projekt

Ressort ── beschäftigt ── Mitarbeiter
```

---

# Kardinalitäten

Kardinalitäten geben an, wie viele Objekte an einer Beziehung beteiligt sind.

---

## 1 : 1

```mermaid
erDiagram

    PERSON ||--|| AUSWEIS : besitzt

    PERSON {
        int personID
    }

    AUSWEIS {
        int ausweisID
    }
``````

Eine Person besitzt genau einen Ausweis.

---

## 1 : n

```mermaid
erDiagram

    KUNDE ||--o{ BESTELLUNG : hat

    KUNDE {
        int kundenID
        string name
    }

    BESTELLUNG {
        int bestellID
        date datum
    }
``````

Ein Kunde kann mehrere Bestellungen haben.

Eine Bestellung gehört genau einem Kunden.

---

## n : m

```mermaid
erDiagram

    STUDENT }o--o{ KURS : besucht

    STUDENT {
        int studentID
    }

    KURS {
        int kursID
    }
``````

Ein Student kann mehrere Kurse besuchen.

Ein Kurs kann mehrere Studenten enthalten.

---

# Beispiel aus dem Unterricht

## Ressort

```mermaid
erDiagram

    RESSORT ||--o{ MITARBEITER : beschaeftigt
    MITARBEITER }o--o{ PROJEKT : arbeitet_an
    MITARBEITER ||--o{ PROJEKT : leitet

    RESSORT {
        int ID
        string Bezeichnung
    }

    MITARBEITER {
        int ID
        string Personalnummer
        string Vorname
        string Nachname
    }

    PROJEKT {
        int ID
        string Bezeichnung
        string Beschreibung
        date Beginn
        date Abschluss
    }
```
---

## Beziehungen

### beschäftigt

```text
Ressort 1 ── beschäftigt ── n Mitarbeiter
```

Bedeutung:

- Ein Ressort beschäftigt viele Mitarbeiter.
- Ein Mitarbeiter gehört genau einem Ressort.

---

### arbeitet_an

```text
Mitarbeiter n ── arbeitet_an ── m Projekt
```

Bedeutung:

- Ein Mitarbeiter kann an mehreren Projekten arbeiten.
- Ein Projekt kann mehrere Mitarbeiter haben.

---

### leitet

```text
Mitarbeiter 1 ── leitet ── n Projekt
```

Bedeutung:

- Ein Mitarbeiter kann mehrere Projekte leiten.
- Jedes Projekt hat genau einen Projektleiter.

---

# Vom ER-Diagramm zum Relationsmodell

ER-Diagramm:

```text
Ressort
    |
beschäftigt
    |
Mitarbeiter
    |
arbeitet_an
    |
Projekt
```

wird zu:

```text
Ressort
--------
ID (PK)
Bezeichnung

Mitarbeiter
------------
ID (PK)
Personalnummer
Vorname
Nachname
RessortID (FK)

Projekt
--------
ID (PK)
Bezeichnung
Beschreibung
Beginn
Abschluss
LeiterID (FK)

arbeitet_an
------------
MitarbeiterID (PK, FK)
ProjektID (PK, FK)
```

---

# Umwandlung von Beziehungen

## 1 : n Beziehung

Die Fremdschlüssel-Spalte kommt auf die n-Seite.

Beispiel:

```text
Ressort 1 ── n Mitarbeiter
```

Ergebnis:

```text
Mitarbeiter
------------
RessortID (FK)
```

---

## n : m Beziehung

Es wird eine zusätzliche Zwischentabelle benötigt.

Beispiel:

```text
Mitarbeiter n ── m Projekt
```

Ergebnis:

```text
arbeitet_an
------------
MitarbeiterID
ProjektID
```

---

# Unterschied zum Klassendiagramm

| Klassendiagramm | ER-Diagramm |
|-----------------|-------------|
| Klassen | Tabellen |
| Attribute | Spalten |
| Methoden vorhanden | Keine Methoden |
| Für Programme | Für Datenbanken |
| Java | SQL |

---

# Vorteile

- übersichtliche Datenmodellierung
- Grundlage für Datenbanken
- zeigt Beziehungen zwischen Daten
- hilft bei der Planung

---

# Merksatz

> Ein ER-Diagramm beschreibt die Struktur einer Datenbank mit Entitäten, Attributen und Beziehungen.

Es beantwortet die Frage:

**Welche Daten werden gespeichert und wie hängen sie zusammen?**

---

# Fragen

## Was beschreibt ein ER-Diagramm?

> [!spoiler]- Lösung anzeigen
> Die Struktur einer Datenbank mit Entitäten, Attributen und Beziehungen.

---

## Was ist eine Entität?

> [!spoiler]- Lösung anzeigen
> Eine Entität entspricht meist einer Tabelle in der Datenbank.

---

## Was ist ein Attribut?

> [!spoiler]- Lösung anzeigen
> Eine Eigenschaft einer Entität.

---

## Was ist eine Beziehung?

> [!spoiler]- Lösung anzeigen
> Eine Verbindung zwischen zwei oder mehreren Entitäten.

---

## Wofür steht PK?

> [!spoiler]- Lösung anzeigen
> Primärschlüssel.

---

## Wofür steht FK?

> [!spoiler]- Lösung anzeigen
> Fremdschlüssel.

---

## Wie wird eine 1:n-Beziehung in ein Relationsmodell umgewandelt?

> [!spoiler]- Lösung anzeigen
> Der Fremdschlüssel wird auf der n-Seite gespeichert.

---

## Wie wird eine n:m-Beziehung in ein Relationsmodell umgewandelt?

> [!spoiler]- Lösung anzeigen
> Durch eine zusätzliche Zwischentabelle.

---

## Wozu dient ein ER-Diagramm?

> [!spoiler]- Lösung anzeigen
> Zur Planung und Modellierung von Datenbanken.