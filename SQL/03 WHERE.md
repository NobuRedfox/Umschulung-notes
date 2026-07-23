## Was macht WHERE?

Mit `WHERE` können Datensätze **gefiltert** werden.

Ohne `WHERE`:

```sql
SELECT *
FROM customer;
```

→ Alle Kunden werden ausgegeben.

Mit `WHERE`:

```sql
SELECT *
FROM customer
WHERE country = 'Germany';
```

→ Nur Kunden aus Deutschland werden ausgegeben.

---

## Grundaufbau

```sql
SELECT spalte
FROM tabelle
WHERE bedingung;
```

Beispiel:

```sql
SELECT first_name, last_name
FROM customer
WHERE country = 'Germany';
```

---

## Vergleichsoperatoren

In einer `WHERE`-Bedingung können verschiedene Vergleichsoperatoren verwendet werden.

| Operator | Bedeutung |
|---|---|
| `=` | gleich |
| `!=` | ungleich |
| `<>` | ungleich |
| `>` | größer als |
| `<` | kleiner als |
| `>=` | größer oder gleich |
| `<=` | kleiner oder gleich |

---

## = Gleich

```sql
SELECT *
FROM customer
WHERE country = 'Germany';
```

Nur Datensätze mit:

```text
country = Germany
```

werden ausgegeben.

---

## != Ungleich

```sql
SELECT *
FROM customer
WHERE country != 'Germany';
```

→ Alle Kunden, die **nicht** aus Deutschland kommen.

Alternativ funktioniert häufig auch:

```sql
WHERE country <> 'Germany'
```

---

## Größer und kleiner

Bei Zahlen können wir beispielsweise schreiben:

```sql
SELECT *
FROM Pokemon
WHERE level > 20;
```

→ Alle Pokémon über Level 20.

Oder:

```sql
SELECT *
FROM Filme
WHERE bewertung >= 8.8;
```

→ Alle Filme mit einer Bewertung von mindestens `8.8`.

---

# Mehrere Bedingungen

## AND

Mit `AND` müssen **beide Bedingungen erfüllt** sein.

```sql
SELECT *
FROM Pokemon
WHERE typ = 'Elektro'
AND level > 20;
```

Das Pokémon muss:

1. vom Typ Elektro sein
2. UND über Level 20 sein

### Merksatz

> `AND` = Alles muss stimmen.

---

## OR

Bei `OR` muss **mindestens eine Bedingung erfüllt** sein.

```sql
SELECT *
FROM Pokemon
WHERE typ = 'Feuer'
OR typ = 'Pflanze';
```

→ Feuer- **oder** Pflanzen-Pokémon.

### Merksatz

> `OR` = Mindestens eine Bedingung muss stimmen.

---

## AND und OR kombinieren

Hier muss man aufpassen.

```sql
SELECT *
FROM Pokemon
WHERE level > 20
AND (typ = 'Feuer' OR typ = 'Pflanze');
```

Gesucht werden Pokémon:

```text
Level > 20
UND
Typ Feuer ODER Pflanze
```

Die Klammern machen deutlich, welche Bedingungen zusammengehören.

---

## NOT

Mit `NOT` wird eine Bedingung umgekehrt.

```sql
SELECT *
FROM customer
WHERE NOT country = 'Germany';
```

→ Alle Kunden, die nicht aus Deutschland kommen.

---

# IN

Wenn mehrere mögliche Werte erlaubt sind, ist `IN` oft übersichtlicher als mehrere `OR`.

Statt:

```sql
SELECT *
FROM Pokemon
WHERE typ = 'Feuer'
OR typ = 'Pflanze'
OR typ = 'Elektro';
```

können wir schreiben:

```sql
SELECT *
FROM Pokemon
WHERE typ IN ('Feuer', 'Pflanze', 'Elektro');
```

### Merksatz

> `IN` = Der Wert darf einer aus dieser Liste sein.

---

## NOT IN

`IN` kann auch umgedreht werden:

```sql
SELECT *
FROM Pokemon
WHERE typ NOT IN ('Feuer', 'Pflanze');
```

→ Alle Pokémon außer Feuer- und Pflanzen-Pokémon.

---

# BETWEEN

Mit `BETWEEN` kann ein Bereich angegeben werden.

```sql
SELECT *
FROM Pokemon
WHERE level BETWEEN 10 AND 30;
```

Das entspricht ungefähr:

```sql
WHERE level >= 10
AND level <= 30;
```

Die Grenzen `10` und `30` gehören also dazu.

---

## BETWEEN bei anderen Werten

Zum Beispiel bei Preisen:

```sql
SELECT *
FROM Spiele
WHERE preis BETWEEN 20 AND 60;
```

→ Spiele zwischen 20 € und 60 €.

---

# Textwerte

Text wird in SQL normalerweise in einfache Anführungszeichen geschrieben:

```sql
WHERE country = 'Germany'
```

```sql
WHERE first_name = 'Nobu'
```

Zahlen benötigen keine Anführungszeichen:

```sql
WHERE level = 20
```

---

# Wichtig: NULL

Bei `NULL` funktioniert:

```sql
WHERE spalte = NULL
```

**nicht richtig.**

Dafür verwendet SQL:

```sql
WHERE spalte IS NULL;
```

oder:

```sql
WHERE spalte IS NOT NULL;
```

`NULL` behandeln wir ausführlicher in Kapitel 16.

---

# Typische Beispiele

## Bestimmten Kunden suchen

```sql
SELECT *
FROM customer
WHERE first_name = 'Max';
```

## Pokémon über Level 20

```sql
SELECT *
FROM Pokemon
WHERE level > 20;
```

## Elektro-Pokémon über Level 20

```sql
SELECT name
FROM Pokemon
WHERE typ = 'Elektro'
AND level > 20;
```

## Feuer oder Pflanze

```sql
SELECT *
FROM Pokemon
WHERE typ IN ('Feuer', 'Pflanze');
```

## Filme ab Bewertung 8.8

```sql
SELECT *
FROM Filme
WHERE bewertung >= 8.8;
```

---

# Merksätze

> **WHERE = Welche Datensätze möchte ich haben?**

> `AND` → alle Bedingungen müssen stimmen

> `OR` → mindestens eine Bedingung muss stimmen

> `IN` → einer von mehreren Werten

> `BETWEEN` → Wert liegt in einem Bereich

> `IS NULL` → Wert ist nicht vorhanden

---

## Navigation

⬅️ [[02 SELECT|Zurück zu Kapitel 02 – SELECT]]

➡️ [[04 ORDER BY und LIMIT|Weiter zu Kapitel 04 – ORDER BY und LIMIT]]