# Datentypen
## Was macht SELECT?

Mit `SELECT` werden **Daten aus einer Datenbank abgefragt**.

Dabei werden die Daten nur gelesen und nicht verändert.

Grundaufbau:

```sql
SELECT spalte
FROM tabelle;
```

---

## Alle Spalten auswählen

Mit `*` werden **alle Spalten** einer Tabelle ausgegeben.

```sql
SELECT *
FROM customer;
```

`*` bedeutet:

> Alle Spalten auswählen.

---

## Eine bestimmte Spalte auswählen

Wenn wir nur eine bestimmte Spalte benötigen:

```sql
SELECT first_name
FROM customer;
```

Es wird nur die Spalte `first_name` ausgegeben.

---

## Mehrere Spalten auswählen

Mehrere Spalten werden mit einem Komma getrennt:

```sql
SELECT first_name, last_name
FROM customer;
```

Die Ausgabe enthält jetzt nur:

| first_name | last_name |
|---|---|
| Max | Müller |
| Anna | Schmidt |
| Peter | Meier |

---

## Reihenfolge der Spalten

Die Reihenfolge im `SELECT` bestimmt auch die Reihenfolge der Ausgabe.

```sql
SELECT last_name, first_name
FROM customer;
```

Ausgabe:

| last_name | first_name |
|---|---|
| Müller | Max |
| Schmidt | Anna |

---

## DISTINCT

Mit `DISTINCT` können doppelte Werte aus der Ausgabe entfernt werden.

Angenommen, unsere Tabelle enthält:

| id | city |
|---|---|
| 1 | Berlin |
| 2 | Augsburg |
| 3 | Berlin |
| 4 | Hamburg |

```sql
SELECT DISTINCT city
FROM customer;
```

Ausgabe:

```text
Berlin
Augsburg
Hamburg
```

`Berlin` wird nur einmal angezeigt.

### Merksatz

> `DISTINCT` entfernt doppelte Ergebnisse.

---

## Spalten umbenennen mit AS

Mit `AS` können wir einer Spalte für die Ausgabe einen anderen Namen geben.

```sql
SELECT first_name AS Vorname
FROM customer;
```

Oder mehrere:

```sql
SELECT
    first_name AS Vorname,
    last_name AS Nachname
FROM customer;
```

Die Datenbank selbst wird dadurch **nicht verändert**.

Nur die Ausgabe bekommt einen anderen Spaltennamen.

---

## Berechnungen mit SELECT

Mit `SELECT` können auch Berechnungen durchgeführt werden.

```sql
SELECT 10 + 5;
```

Ergebnis:

```text
15
```

Auch Werte aus Tabellen können verwendet werden:

```sql
SELECT unit_price * quantity
FROM invoice_line;
```

Hier wird für jede Zeile:

```text
Preis × Menge
```

berechnet.

---

## SELECT mit weiteren Befehlen

`SELECT` wird sehr häufig mit anderen SQL-Befehlen kombiniert.

Zum Beispiel:

```sql
SELECT *
FROM customer
WHERE country = 'Germany';
```

Oder:

```sql
SELECT first_name, last_name
FROM customer
ORDER BY last_name;
```

Diese Befehle behandeln wir in den nächsten Kapiteln genauer.

---

## Typischer Aufbau einer SELECT-Abfrage

Später können Abfragen zum Beispiel so aussehen:

```sql
SELECT first_name, last_name
FROM customer
WHERE country = 'Germany'
ORDER BY last_name
LIMIT 5;
```

Dabei bedeutet:

- `SELECT` → Was möchte ich sehen?
- `FROM` → Aus welcher Tabelle?
- `WHERE` → Welche Datensätze?
- `ORDER BY` → Wie sollen sie sortiert werden?
- `LIMIT` → Wie viele Ergebnisse?

---

## Wichtig zu merken

```sql
SELECT *
FROM customer;
```

→ Alle Spalten und alle Datensätze.

```sql
SELECT first_name
FROM customer;
```

→ Nur `first_name`.

```sql
SELECT first_name, last_name
FROM customer;
```

→ Mehrere ausgewählte Spalten.

```sql
SELECT DISTINCT country
FROM customer;
```

→ Doppelte Werte entfernen.

```sql
SELECT first_name AS Vorname
FROM customer;
```

→ Spalte in der Ausgabe umbenennen.

---

## Merksatz

> **SELECT = Was möchte ich sehen?**  
> **FROM = Woher sollen die Daten kommen?**

---

## Navigation

⬅️ [[01 SQL Grundlagen|Zurück zu Kapitel 01 – SQL Grundlagen]]

➡️ [[03 WHERE|Weiter zu Kapitel 03 – WHERE]]