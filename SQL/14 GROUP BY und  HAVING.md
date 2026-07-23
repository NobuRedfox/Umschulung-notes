## Was macht GROUP BY?

Mit `GROUP BY` werden Datensätze mit gleichen Werten **zu Gruppen zusammengefasst**.

`GROUP BY` wird besonders häufig zusammen mit Aggregatfunktionen verwendet:

```text
COUNT()
SUM()
AVG()
MIN()
MAX()
```

Beispiel:

> Wie viele Kunden gibt es pro Land?

```sql
SELECT country, COUNT(*)
FROM customer
GROUP BY country;
```

---

# Warum brauchen wir GROUP BY?

Angenommen, unsere Tabelle enthält:

| customer_id | name | country |
|---|---|---|
| 1 | Max | Germany |
| 2 | Anna | Germany |
| 3 | John | USA |
| 4 | Lisa | Germany |
| 5 | Bob | USA |
| 6 | Yuki | Japan |

Wir möchten wissen:

> Wie viele Kunden gibt es in jedem Land?

`GROUP BY` bildet zuerst Gruppen:

```text
Germany
├── Max
├── Anna
└── Lisa

USA
├── John
└── Bob

Japan
└── Yuki
```

Anschließend kann `COUNT()` die Datensätze jeder Gruppe zählen.

Ergebnis:

| country | anzahl |
|---|---:|
| Germany | 3 |
| USA | 2 |
| Japan | 1 |

---

# GROUP BY mit COUNT()

```sql
SELECT country, COUNT(*) AS anzahl
FROM customer
GROUP BY country;
```

Das kann man lesen als:

```text
Gruppiere Kunden nach Land
        ↓
Zähle die Kunden jeder Gruppe
```

---

# GROUP BY mit SUM()

Angenommen, wir haben:

| invoice_id | billing_country | total |
|---|---|---:|
| 1 | Germany | 20.00 |
| 2 | Germany | 30.00 |
| 3 | USA | 15.00 |
| 4 | USA | 25.00 |

Wir möchten wissen:

> Wie hoch ist der Umsatz pro Land?

```sql
SELECT billing_country,
       SUM(total) AS umsatz
FROM invoice
GROUP BY billing_country;
```

Ergebnis:

| billing_country | umsatz |
|---|---:|
| Germany | 50.00 |
| USA | 40.00 |

---

# GROUP BY mit AVG()

Frage:

> Wie hoch ist der durchschnittliche Rechnungsbetrag pro Land?

```sql
SELECT billing_country,
       AVG(total) AS durchschnitt
FROM invoice
GROUP BY billing_country;
```

---

# GROUP BY mit MIN() und MAX()

Wir können auch mehrere Aggregatfunktionen verwenden:

```sql
SELECT billing_country,
       MIN(total) AS kleinste_rechnung,
       MAX(total) AS groesste_rechnung
FROM invoice
GROUP BY billing_country;
```

Damit bekommen wir für jedes Land:

```text
kleinste Rechnung
größte Rechnung
```

---

# Mehrere Aggregatfunktionen

```sql
SELECT billing_country,
       COUNT(*) AS anzahl,
       SUM(total) AS umsatz,
       AVG(total) AS durchschnitt,
       MIN(total) AS minimum,
       MAX(total) AS maximum
FROM invoice
GROUP BY billing_country;
```

Jetzt erhalten wir für **jedes Land** mehrere Statistiken.

---

# GROUP BY mit mehreren Spalten

Es kann auch nach mehreren Spalten gruppiert werden.

```sql
SELECT country,
       city,
       COUNT(*) AS anzahl
FROM customer
GROUP BY country, city;
```

Jetzt werden Gruppen aus der Kombination gebildet:

```text
Germany + Berlin
Germany + Augsburg
USA + New York
USA + Chicago
```

---

# WHERE mit GROUP BY

`WHERE` kann vor `GROUP BY` verwendet werden.

Beispiel:

> Wie viele Kunden gibt es pro Stadt, aber nur in Deutschland?

```sql
SELECT city,
       COUNT(*) AS anzahl
FROM customer
WHERE country = 'Germany'
GROUP BY city;
```

Die Reihenfolge ist:

```text
customer
   ↓
WHERE
   ↓
nur Germany
   ↓
GROUP BY city
   ↓
COUNT()
```

---

# HAVING

Mit `HAVING` können wir **Gruppen filtern**.

Das ist besonders wichtig bei Aggregatfunktionen.

Beispiel:

> Zeige nur Länder mit mehr als 5 Kunden.

```sql
SELECT country,
       COUNT(*) AS anzahl
FROM customer
GROUP BY country
HAVING COUNT(*) > 5;
```

---

# Warum nicht WHERE?

Man könnte auf die Idee kommen:

```sql
SELECT country,
       COUNT(*)
FROM customer
WHERE COUNT(*) > 5
GROUP BY country;
```

❌ Das funktioniert so nicht.

Warum?

`WHERE` wird ausgeführt, **bevor die Gruppen gebildet wurden**.

Zu diesem Zeitpunkt existiert:

```sql
COUNT(*)
```

für die Gruppen noch gar nicht.

Deshalb brauchen wir:

```sql
HAVING COUNT(*) > 5
```

---

# WHERE vs HAVING

Das ist der wichtigste Unterschied dieses Kapitels.

## WHERE

Filtert:

> einzelne Datensätze

Beispiel:

```sql
WHERE country = 'Germany'
```

---

## HAVING

Filtert:

> Gruppen / Ergebnisse von Aggregatfunktionen

Beispiel:

```sql
HAVING COUNT(*) > 5
```

---

# Beispiel

Wir möchten wissen:

> Welche Städte in Deutschland haben mehr als 10 Kunden?

```sql
SELECT city,
       COUNT(*) AS anzahl
FROM customer
WHERE country = 'Germany'
GROUP BY city
HAVING COUNT(*) > 10;
```

Schritt für Schritt:

```text
customer
   ↓
WHERE country = 'Germany'
   ↓
nur deutsche Kunden
   ↓
GROUP BY city
   ↓
Kunden nach Stadt gruppieren
   ↓
COUNT(*)
   ↓
Anzahl pro Stadt
   ↓
HAVING COUNT(*) > 10
   ↓
nur Städte mit mehr als 10 Kunden
```

---

# HAVING mit SUM()

Frage:

> Welche Länder haben mehr als 1000 € Umsatz?

```sql
SELECT billing_country,
       SUM(total) AS umsatz
FROM invoice
GROUP BY billing_country
HAVING SUM(total) > 1000;
```

---

# HAVING mit AVG()

Frage:

> Welche Länder haben einen durchschnittlichen Rechnungsbetrag über 20 €?

```sql
SELECT billing_country,
       AVG(total) AS durchschnitt
FROM invoice
GROUP BY billing_country
HAVING AVG(total) > 20;
```

---

# GROUP BY mit JOIN

`GROUP BY` wird sehr häufig mit `JOIN` kombiniert.

Frage:

> Wie viele Rechnungen hat jeder Kunde?

Wir benötigen:

```text
customer
   ↓
invoice
```

Die Tabellen sind über `customer_id` verbunden.

```sql
SELECT c.customer_id,
       c.first_name,
       c.last_name,
       COUNT(i.invoice_id) AS anzahl_rechnungen
FROM customer c
INNER JOIN invoice i
    ON c.customer_id = i.customer_id
GROUP BY c.customer_id,
         c.first_name,
         c.last_name;
```

---

# Was passiert hier?

Zuerst verbindet der JOIN:

```text
customer
+
invoice
```

Dann gruppieren wir nach Kunde:

```text
Max
├── Rechnung 1
├── Rechnung 2
└── Rechnung 3

Anna
├── Rechnung 4
└── Rechnung 5
```

Danach:

```sql
COUNT(i.invoice_id)
```

Ergebnis:

```text
Max  → 3 Rechnungen
Anna → 2 Rechnungen
```

---

# LEFT JOIN mit GROUP BY

Angenommen, wir möchten **alle Kunden** sehen, auch Kunden ohne Rechnung.

Dann verwenden wir:

```sql
SELECT c.customer_id,
       c.first_name,
       c.last_name,
       COUNT(i.invoice_id) AS anzahl_rechnungen
FROM customer c
LEFT JOIN invoice i
    ON c.customer_id = i.customer_id
GROUP BY c.customer_id,
         c.first_name,
         c.last_name;
```

Ein Kunde ohne Rechnung bekommt:

```text
anzahl_rechnungen = 0
```

---

# Warum COUNT(i.invoice_id) und nicht COUNT(*)?

Das ist bei `LEFT JOIN` wichtig.

Bei:

```sql
COUNT(i.invoice_id)
```

werden `NULL`-Werte ignoriert.

Ein Kunde ohne Rechnung bekommt deshalb:

```text
0
```

Bei `COUNT(*)` würde die durch den `LEFT JOIN` erzeugte Zeile trotzdem gezählt.

### Merksatz

> Bei `LEFT JOIN` genau überlegen, **was** du zählen möchtest.

---

# GROUP BY mit ORDER BY

Natürlich können wir das Ergebnis anschließend sortieren.

```sql
SELECT country,
       COUNT(*) AS anzahl
FROM customer
GROUP BY country
ORDER BY anzahl DESC;
```

Damit steht das Land mit den meisten Kunden oben.

---

# GROUP BY + HAVING + ORDER BY

Alles zusammen:

```sql
SELECT country,
       COUNT(*) AS anzahl
FROM customer
GROUP BY country
HAVING COUNT(*) >= 5
ORDER BY anzahl DESC;
```

Bedeutung:

```text
Kunden nach Land gruppieren
        ↓
Kunden pro Land zählen
        ↓
nur Länder mit mindestens 5 Kunden
        ↓
höchste Anzahl zuerst
```

---

# Komplette Abfrage

Eine größere SQL-Abfrage könnte so aussehen:

```sql
SELECT c.country,
       COUNT(i.invoice_id) AS anzahl_rechnungen,
       SUM(i.total) AS umsatz
FROM customer c
INNER JOIN invoice i
    ON c.customer_id = i.customer_id
WHERE i.total > 5
GROUP BY c.country
HAVING SUM(i.total) > 100
ORDER BY umsatz DESC
LIMIT 5;
```

---

# Reihenfolge beim Schreiben

Die Reihenfolge der Befehle ist wichtig:

```text
SELECT
FROM
JOIN
ON
WHERE
GROUP BY
HAVING
ORDER BY
LIMIT
```

Als SQL:

```sql
SELECT ...
FROM ...
JOIN ...
    ON ...
WHERE ...
GROUP BY ...
HAVING ...
ORDER BY ...
LIMIT ...;
```

---

# Logisch denken

Eine vereinfachte Vorstellung:

```text
FROM / JOIN
      ↓
Tabellen holen und verbinden

WHERE
      ↓
einzelne Datensätze filtern

GROUP BY
      ↓
Gruppen bilden

Aggregatfunktionen
      ↓
COUNT / SUM / AVG ...

HAVING
      ↓
Gruppen filtern

ORDER BY
      ↓
Ergebnis sortieren

LIMIT
      ↓
Anzahl begrenzen
```

---

# Typische Aufgaben erkennen

Wenn eine Aufgabe sagt:

> Wie viele Kunden gibt es **pro Land**?

Das Wort:

```text
pro
```

ist ein sehr guter Hinweis auf:

```sql
GROUP BY
```

---

## Beispiel

> Umsatz **pro Kunde**

```sql
GROUP BY customer_id
```

> Anzahl der Kunden **pro Land**

```sql
GROUP BY country
```

> Durchschnittlicher Preis **pro Kategorie**

```sql
GROUP BY category
```

### Merksatz

> Wenn du in der Aufgabe **„pro ...“** liest, solltest du sofort an `GROUP BY` denken.

---

# Wann brauche ich HAVING?

Wenn die Aufgabe anschließend eine Bedingung für die Gruppe enthält.

Beispiel:

> Zeige Länder mit **mehr als 10 Kunden**.

```sql
GROUP BY country
HAVING COUNT(*) > 10;
```

Oder:

> Zeige Kunden mit **mehr als 5 Rechnungen**.

```sql
GROUP BY customer_id
HAVING COUNT(*) > 5;
```

---

# WHERE oder HAVING?

Stell dir die Frage:

> Filtere ich einzelne Datensätze oder ein berechnetes Gruppenergebnis?

Einzelne Datensätze:

```sql
WHERE
```

Gruppenergebnis:

```sql
HAVING
```

---

# Beispiel zum Unterschied

> Nur Rechnungen über 10 € berücksichtigen.

```sql
WHERE total > 10
```

Hier filtern wir **einzelne Rechnungen**.

---

> Nur Länder mit einem Gesamtumsatz über 1000 € anzeigen.

```sql
HAVING SUM(total) > 1000
```

Hier filtern wir das **Ergebnis einer Gruppe**.

---

# Übersicht

| Befehl | Aufgabe |
|---|---|
| `WHERE` | einzelne Zeilen filtern |
| `GROUP BY` | Zeilen gruppieren |
| `COUNT()` | Gruppe zählen |
| `SUM()` | Gruppe summieren |
| `AVG()` | Durchschnitt der Gruppe |
| `HAVING` | Gruppen filtern |
| `ORDER BY` | Ergebnis sortieren |

---

# Merksätze

> `GROUP BY` = gleiche Werte zu Gruppen zusammenfassen.

> **„pro ...“** in einer Aufgabe ist oft ein Hinweis auf `GROUP BY`.

> `WHERE` = einzelne Datensätze filtern.

> `HAVING` = Gruppen filtern.

Besonders wichtig:

```text
WHERE → VOR der Gruppierung

HAVING → NACH der Gruppierung
```

Beispiel:

```sql
SELECT country, COUNT(*)
FROM customer
WHERE city IS NOT NULL
GROUP BY country
HAVING COUNT(*) > 5;
```

Also:

> **WHERE filtert Zeilen – HAVING filtert Gruppen.**

---

## Navigation

⬅️ [[13 Aggregatfunktionen|Zurück zu Kapitel 13 – Aggregatfunktionen]]

➡️ [[15 Unterabfragen|Weiter zu Kapitel 15 – Unterabfragen]]