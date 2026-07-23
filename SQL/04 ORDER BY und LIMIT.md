## Was macht ORDER BY?

Mit `ORDER BY` werden Ergebnisse einer Abfrage **sortiert**.

Grundaufbau:

```sql
SELECT spalte
FROM tabelle
ORDER BY spalte;
```

Beispiel:

```sql
SELECT *
FROM customer
ORDER BY last_name;
```

Die Kunden werden nach ihrem Nachnamen sortiert.

---

## ASC – Aufsteigend sortieren

`ASC` steht für **Ascending** = aufsteigend.

```sql
SELECT *
FROM customer
ORDER BY last_name ASC;
```

Bei Text bedeutet das:

```text
A → Z
```

Bei Zahlen:

```text
1 → 2 → 3 → 4 ...
```

`ASC` ist die Standardeinstellung.

Deshalb sind diese beiden Abfragen gleich:

```sql
SELECT *
FROM customer
ORDER BY last_name;
```

```sql
SELECT *
FROM customer
ORDER BY last_name ASC;
```

### Merksatz

> `ASC` = klein nach groß / A nach Z

---

## DESC – Absteigend sortieren

`DESC` steht für **Descending** = absteigend.

```sql
SELECT *
FROM customer
ORDER BY last_name DESC;
```

Bei Text:

```text
Z → A
```

Bei Zahlen:

```text
100 → 99 → 98 ...
```

### Beispiel mit Pokémon

```sql
SELECT name, level
FROM Pokemon
ORDER BY level DESC;
```

Das Pokémon mit dem höchsten Level steht ganz oben.

### Merksatz

> `DESC` = groß nach klein / Z nach A

---

# Nach mehreren Spalten sortieren

Es kann auch nach mehreren Spalten sortiert werden.

```sql
SELECT first_name, last_name, country
FROM customer
ORDER BY country, last_name;
```

SQL sortiert zuerst nach:

```text
country
```

und bei gleichen Ländern zusätzlich nach:

```text
last_name
```

---

## ASC und DESC kombinieren

Auch unterschiedliche Sortierrichtungen sind möglich:

```sql
SELECT *
FROM customer
ORDER BY country ASC, last_name DESC;
```

Hier wird:

1. `country` aufsteigend sortiert
2. `last_name` innerhalb des Landes absteigend sortiert

---

# LIMIT

Mit `LIMIT` wird festgelegt, **wie viele Datensätze ausgegeben werden**.

```sql
SELECT *
FROM customer
LIMIT 5;
```

→ Es werden maximal **5 Datensätze** ausgegeben.

---

## ORDER BY und LIMIT kombinieren

Besonders nützlich wird `LIMIT` zusammen mit `ORDER BY`.

Beispiel:

```sql
SELECT *
FROM Spiele
ORDER BY preis DESC
LIMIT 1;
```

Was passiert?

```text
1. Alle Spiele werden betrachtet
2. Nach Preis absteigend sortieren
3. Nur das erste Ergebnis anzeigen
```

Damit bekommen wir:

> Das teuerste Spiel.

---

## Höchsten Wert finden

Zum Beispiel das Pokémon mit dem höchsten Level:

```sql
SELECT name, level
FROM Pokemon
ORDER BY level DESC
LIMIT 1;
```

---

## Niedrigsten Wert finden

Dafür drehen wir die Sortierung um:

```sql
SELECT name, level
FROM Pokemon
ORDER BY level ASC
LIMIT 1;
```

→ Pokémon mit dem niedrigsten Level.

---

## Top 3 anzeigen

Wir können natürlich auch mehrere Ergebnisse anzeigen:

```sql
SELECT name, level
FROM Pokemon
ORDER BY level DESC
LIMIT 3;
```

→ Die drei Pokémon mit dem höchsten Level.

---

# WHERE + ORDER BY + LIMIT

Die Befehle können miteinander kombiniert werden.

```sql
SELECT *
FROM Filme
WHERE bewertung >= 8
ORDER BY bewertung DESC
LIMIT 3;
```

Bedeutung:

```text
Filme mit Bewertung >= 8
        ↓
nach Bewertung sortieren
        ↓
höchste Bewertung zuerst
        ↓
nur die ersten 3
```

---

# Reihenfolge der SQL-Befehle

Beim Schreiben einer Abfrage ist die Reihenfolge wichtig:

```sql
SELECT
FROM
WHERE
ORDER BY
LIMIT
```

Beispiel:

```sql
SELECT titel, bewertung
FROM Filme
WHERE bewertung >= 8
ORDER BY bewertung DESC
LIMIT 3;
```

Nicht:

```sql
SELECT titel, bewertung
FROM Filme
LIMIT 3
WHERE bewertung >= 8;
```

❌ Das wäre eine falsche Reihenfolge.

---

# Typische Beispiele

## Namen alphabetisch sortieren

```sql
SELECT first_name, last_name
FROM customer
ORDER BY last_name ASC;
```

## Höchstes Pokémon-Level

```sql
SELECT name, level
FROM Pokemon
ORDER BY level DESC
LIMIT 1;
```

## Teuerstes Spiel

```sql
SELECT titel, preis
FROM Spiele
ORDER BY preis DESC
LIMIT 1;
```

## Drei bestbewertete Filme

```sql
SELECT titel, bewertung
FROM Filme
ORDER BY bewertung DESC
LIMIT 3;
```

---

# Merksätze

> `ORDER BY` = Ergebnisse sortieren

> `ASC` = aufsteigend ↑

> `DESC` = absteigend ↓

> `LIMIT` = Anzahl der Ergebnisse begrenzen

Besonders wichtig:

```sql
ORDER BY wert DESC
LIMIT 1;
```

→ **Höchsten Wert finden**

```sql
ORDER BY wert ASC
LIMIT 1;
```

→ **Niedrigsten Wert finden**

---

## Navigation

⬅️ [[03 WHERE|Zurück zu Kapitel 03 – WHERE]]

➡️ [[05 INSERT|Weiter zu Kapitel 05 – INSERT]]