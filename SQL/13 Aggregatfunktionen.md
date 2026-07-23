## Was sind Aggregatfunktionen?

Aggregatfunktionen führen Berechnungen über **mehrere Datensätze** durch und liefern daraus ein Ergebnis.

Die wichtigsten Aggregatfunktionen sind:

| Funktion | Bedeutung |
|---|---|
| `COUNT()` | Anzahl zählen |
| `SUM()` | Werte addieren |
| `AVG()` | Durchschnitt berechnen |
| `MIN()` | kleinsten Wert finden |
| `MAX()` | größten Wert finden |

---

# COUNT()

Mit `COUNT()` können Datensätze gezählt werden.

Beispiel:

```sql
SELECT COUNT(*)
FROM customer;
```

Das bedeutet:

> Wie viele Datensätze gibt es in `customer`?

Angenommen, die Tabelle enthält 59 Kunden:

```text
COUNT(*)
--------
59
```

---

## COUNT(*) vs COUNT(spalte)

Es gibt einen wichtigen Unterschied.

```sql
SELECT COUNT(*)
FROM customer;
```

`COUNT(*)` zählt **alle Datensätze**.

Bei:

```sql
SELECT COUNT(phone)
FROM customer;
```

werden nur Datensätze gezählt, bei denen `phone` **nicht NULL** ist.

Beispiel:

| customer_id | phone |
|---|---|
| 1 | 12345 |
| 2 | NULL |
| 3 | 67890 |

Dann ergibt:

```sql
SELECT COUNT(*)
FROM customer;
```

```text
3
```

Aber:

```sql
SELECT COUNT(phone)
FROM customer;
```

ergibt:

```text
2
```

### Merksatz

> `COUNT(*)` zählt Zeilen.

> `COUNT(spalte)` ignoriert `NULL`.

---

# COUNT mit WHERE

Aggregatfunktionen können mit `WHERE` kombiniert werden.

```sql
SELECT COUNT(*)
FROM customer
WHERE country = 'Germany';
```

Damit zählen wir:

> Wie viele Kunden kommen aus Deutschland?

---

# COUNT DISTINCT

Wir können auch nur unterschiedliche Werte zählen.

```sql
SELECT COUNT(DISTINCT country)
FROM customer;
```

Das bedeutet:

> Wie viele unterschiedliche Länder gibt es?

Angenommen:

```text
Germany
Germany
France
Japan
Japan
```

Dann ist:

```sql
COUNT(DISTINCT country)
```

gleich:

```text
3
```

---

# SUM()

Mit `SUM()` werden Zahlenwerte **addiert**.

Beispiel:

```sql
SELECT SUM(total)
FROM invoice;
```

Damit berechnen wir:

> Summe aller Rechnungsbeträge.

Angenommen:

```text
29.99
15.50
42.00
```

Dann ergibt:

```text
87.49
```

---

## SUM mit WHERE

```sql
SELECT SUM(total)
FROM invoice
WHERE billing_country = 'Germany';
```

Damit berechnen wir nur die Summe der Rechnungen aus Deutschland.

---

# AVG()

`AVG()` steht für:

> Average = Durchschnitt

Beispiel:

```sql
SELECT AVG(total)
FROM invoice;
```

Damit berechnen wir den durchschnittlichen Rechnungsbetrag.

Angenommen:

```text
10
20
30
```

Dann:

```text
(10 + 20 + 30) / 3
```

ergibt:

```text
20
```

---

## Beispiel mit Pokémon

```sql
SELECT AVG(level)
FROM Pokemon;
```

→ Durchschnittliches Level aller Pokémon.

---

# MIN()

Mit `MIN()` wird der **kleinste Wert** gefunden.

```sql
SELECT MIN(total)
FROM invoice;
```

→ Kleinster Rechnungsbetrag.

Beispiel:

```text
10.99
25.50
5.99
100.00
```

Ergebnis:

```text
5.99
```

---

# MAX()

Mit `MAX()` wird der **größte Wert** gefunden.

```sql
SELECT MAX(total)
FROM invoice;
```

→ Größter Rechnungsbetrag.

Beispiel:

```text
10.99
25.50
5.99
100.00
```

Ergebnis:

```text
100.00
```

---

# MIN und MAX statt ORDER BY?

Wir haben bereits gelernt:

```sql
SELECT *
FROM Spiele
ORDER BY preis DESC
LIMIT 1;
```

Damit finden wir das teuerste Spiel.

Mit:

```sql
SELECT MAX(preis)
FROM Spiele;
```

bekommen wir ebenfalls den höchsten Preis.

Aber es gibt einen Unterschied.

---

## MAX()

```sql
SELECT MAX(preis)
FROM Spiele;
```

liefert beispielsweise:

```text
69.99
```

Wir bekommen nur den **höchsten Wert**.

---

## ORDER BY + LIMIT

```sql
SELECT titel, preis
FROM Spiele
ORDER BY preis DESC
LIMIT 1;
```

liefert:

```text
Monster Hunter Wilds | 69.99
```

Hier bekommen wir den **kompletten gewünschten Datensatz bzw. weitere Spalten dazu**.

### Merksatz

> `MAX()` → höchsten Wert berechnen

> `ORDER BY ... DESC LIMIT 1` → Datensatz mit dem höchsten Wert finden

---

# Mehrere Aggregatfunktionen gleichzeitig

Wir können mehrere Funktionen in einem `SELECT` verwenden.

```sql
SELECT
    COUNT(*) AS anzahl,
    MIN(total) AS kleinste_rechnung,
    MAX(total) AS groesste_rechnung,
    AVG(total) AS durchschnitt,
    SUM(total) AS gesamt
FROM invoice;
```

Das könnte beispielsweise ergeben:

| anzahl | kleinste_rechnung | groesste_rechnung | durchschnitt | gesamt |
|---:|---:|---:|---:|---:|
| 100 | 1.99 | 99.99 | 25.42 | 2542.00 |

---

# Alias mit AS

Bei Aggregatfunktionen ist `AS` besonders praktisch.

Ohne Alias:

```sql
SELECT COUNT(*)
FROM customer;
```

Die Spalte könnte heißen:

```text
COUNT(*)
```

Mit Alias:

```sql
SELECT COUNT(*) AS anzahl_kunden
FROM customer;
```

Die Ausgabe heißt dann:

```text
anzahl_kunden
```

Das ist deutlich verständlicher.

---

# Aggregatfunktionen mit JOIN

Aggregatfunktionen können auch mit JOINs kombiniert werden.

Beispiel:

> Wie viele Rechnungen gibt es von Kunde 5?

```sql
SELECT COUNT(*) AS anzahl_rechnungen
FROM customer c
INNER JOIN invoice i
    ON c.customer_id = i.customer_id
WHERE c.customer_id = 5;
```

---

# SUM mit JOIN

Wir können auch berechnen, wie viel ein bestimmter Kunde insgesamt ausgegeben hat:

```sql
SELECT SUM(i.total) AS gesamt
FROM customer c
INNER JOIN invoice i
    ON c.customer_id = i.customer_id
WHERE c.customer_id = 5;
```

---

# Berechnungen innerhalb von SUM()

Aggregatfunktionen können auch Berechnungen enthalten.

Angenommen `invoice_line` besitzt:

```text
unit_price
quantity
```

Dann können wir berechnen:

```sql
SELECT SUM(unit_price * quantity)
FROM invoice_line;
```

Für jede Zeile wird zuerst gerechnet:

```text
unit_price × quantity
```

Danach werden alle Ergebnisse addiert.

---

# NULL bei Aggregatfunktionen

Die meisten Aggregatfunktionen ignorieren `NULL`.

Zum Beispiel:

```text
level
-----
10
20
NULL
30
```

Bei:

```sql
SELECT AVG(level)
FROM Pokemon;
```

wird `NULL` nicht als `0` gerechnet.

Berechnet wird:

```text
(10 + 20 + 30) / 3
```

nicht:

```text
(10 + 20 + 0 + 30) / 4
```

---

# Aggregatfunktion vs normale Funktion

Aggregatfunktionen betrachten mehrere Datensätze gemeinsam.

Zum Beispiel:

```sql
SELECT MAX(total)
FROM invoice;
```

Aus:

```text
10
20
30
40
```

wird:

```text
40
```

Viele Zeilen werden also zu **einem Ergebnis zusammengefasst**.

```text
10 ─┐
20 ─┤
30 ─┼── MAX() ──> 40
40 ─┘
```

Daher kommt auch der Name:

> **Aggregatfunktion**

---

# Das Problem mit normalen Spalten

Diese Abfrage ist problematisch:

```sql
SELECT country, COUNT(*)
FROM customer;
```

Wir wollen vermutlich wissen:

> Wie viele Kunden gibt es pro Land?

Dafür müssen die Datensätze zuerst nach `country` gruppiert werden.

Das machen wir mit:

```sql
GROUP BY
```

Also:

```sql
SELECT country, COUNT(*)
FROM customer
GROUP BY country;
```

Genau darum geht es im nächsten Kapitel.

---

# Die fünf wichtigsten Funktionen

## COUNT

```sql
COUNT(*)
```

> Wie viele?

---

## SUM

```sql
SUM(preis)
```

> Wie viel insgesamt?

---

## AVG

```sql
AVG(preis)
```

> Wie hoch ist der Durchschnitt?

---

## MIN

```sql
MIN(preis)
```

> Was ist der kleinste Wert?

---

## MAX

```sql
MAX(preis)
```

> Was ist der größte Wert?

---

# Typische Aufgaben erkennen

Wenn in einer Aufgabe steht:

> Wie viele Kunden gibt es?

Denke an:

```sql
COUNT()
```

---

Wenn dort steht:

> Wie hoch ist der Gesamtumsatz?

Denke an:

```sql
SUM()
```

---

Wenn dort steht:

> Wie hoch ist der durchschnittliche Preis?

Denke an:

```sql
AVG()
```

---

Wenn dort steht:

> Was ist der niedrigste Preis?

Denke an:

```sql
MIN()
```

---

Wenn dort steht:

> Was ist der höchste Preis?

Denke an:

```sql
MAX()
```

---

# Übersicht

| Frage | Funktion |
|---|---|
| Wie viele? | `COUNT()` |
| Wie viel insgesamt? | `SUM()` |
| Wie hoch im Durchschnitt? | `AVG()` |
| Kleinster Wert? | `MIN()` |
| Größter Wert? | `MAX()` |

---

# Merksatz

Die fünf wichtigsten Aggregatfunktionen:

```text
COUNT → zählen
SUM   → addieren
AVG   → Durchschnitt
MIN   → kleinster Wert
MAX   → größter Wert
```

Und wichtig:

> Aggregatfunktionen machen aus **vielen Datensätzen ein zusammengefasstes Ergebnis**.

Sobald die Aufgabe allerdings fragt:

> **Wie viele / wie viel / welcher Durchschnitt PRO ...?**

zum Beispiel:

> Wie viele Kunden **pro Land**?

dann brauchen wir zusätzlich:

```sql
GROUP BY
```

---

## Navigation

⬅️ [[12 JOIN|Zurück zu Kapitel 12 – JOIN]]

➡️ [[14 GROUP BY und HAVING|Weiter zu Kapitel 14 – GROUP BY und HAVING]]