## Was macht DELETE?

Mit `DELETE` werden **vorhandene Datensätze aus einer Tabelle gelöscht**.

Grundaufbau:

```sql
DELETE FROM tabelle
WHERE bedingung;
```

Beispiel:

```sql
DELETE FROM customer
WHERE customer_id = 5;
```

Dadurch wird der Kunde mit der ID `5` gelöscht.

---

# DELETE FROM

Bei `DELETE` schreiben wir:

```sql
DELETE FROM customer
```

Damit bestimmen wir:

> Aus welcher Tabelle sollen Datensätze gelöscht werden?

Anschließend bestimmt `WHERE`, welche Datensätze betroffen sind:

```sql
WHERE customer_id = 5;
```

Komplett:

```sql
DELETE FROM customer
WHERE customer_id = 5;
```

---

# WHERE bei DELETE

`WHERE` ist bei `DELETE` besonders wichtig.

```sql
DELETE FROM customer
WHERE country = 'Germany';
```

Dadurch werden **alle Kunden aus Deutschland** gelöscht.

Es muss also nicht immer nur ein Datensatz betroffen sein.

---

# ⚠️ DELETE ohne WHERE

Dieser Befehl ist gefährlich:

```sql
DELETE FROM customer;
```

Er bedeutet:

> Lösche ALLE Datensätze aus `customer`.

Die Tabelle selbst bleibt bestehen, aber sie ist danach leer.

---

# Erst SELECT, dann DELETE

Wie bei `UPDATE` ist es sinnvoll, vor dem Löschen mit `SELECT` zu prüfen, welche Datensätze betroffen sind.

Angenommen, wir möchten alle Kunden aus Deutschland löschen.

Zuerst:

```sql
SELECT *
FROM customer
WHERE country = 'Germany';
```

Jetzt sehen wir genau, welche Datensätze betroffen wären.

Danach:

```sql
DELETE FROM customer
WHERE country = 'Germany';
```

### Merksatz

> Vor einem wichtigen `DELETE` zuerst dasselbe `WHERE` mit `SELECT` testen.

---

# DELETE mit mehreren Bedingungen

Wir können `AND` verwenden:

```sql
DELETE FROM Pokemon
WHERE typ = 'Feuer'
AND level < 10;
```

Gelöscht werden nur Pokémon, die:

```text
Typ = Feuer
UND
Level < 10
```

erfüllen.

---

# DELETE mit OR

Auch `OR` funktioniert:

```sql
DELETE FROM Pokemon
WHERE typ = 'Feuer'
OR typ = 'Pflanze';
```

→ Feuer- oder Pflanzen-Pokémon werden gelöscht.

---

# DELETE mit IN

Das gleiche lässt sich übersichtlicher mit `IN` schreiben:

```sql
DELETE FROM Pokemon
WHERE typ IN ('Feuer', 'Pflanze');
```

---

# DELETE mit NULL

Wir können auch Datensätze löschen, bei denen ein Wert `NULL` ist.

```sql
DELETE FROM customer
WHERE phone IS NULL;
```

Wichtig:

```sql
IS NULL
```

und nicht:

```sql
= NULL
```

---

# DELETE und Foreign Keys

Beim Löschen können **Beziehungen zwischen Tabellen** wichtig werden.

Beispiel:

```text
customer
   │
   │ 1:n
   ▼
invoice
```

Ein Kunde kann mehrere Rechnungen besitzen.

Wenn wir versuchen:

```sql
DELETE FROM customer
WHERE customer_id = 5;
```

kann die Datenbank das Löschen verhindern, wenn noch Rechnungen zu diesem Kunden existieren.

Der Grund ist der **Foreign Key**.

---

# Abhängige Datensätze zuerst löschen

Angenommen:

```text
customer
    ↓
invoice
    ↓
invoice_line
```

Dann kann es notwendig sein, von **unten nach oben** zu löschen:

```text
1. invoice_line
2. invoice
3. customer
```

Also zuerst die Datensätze, die von anderen Datensätzen abhängig sind.

Genau solche Aufgaben hatten wir bereits.

---

## Beispiel

Angenommen, Rechnung `5` soll gelöscht werden und besitzt noch Einträge in `invoice_line`.

Zuerst:

```sql
DELETE FROM invoice_line
WHERE invoice_id = 5;
```

Danach:

```sql
DELETE FROM invoice
WHERE invoice_id = 5;
```

Jetzt existieren keine abhängigen `invoice_line`-Datensätze mehr.

---

# DELETE mit Unterabfrage

Wir können `DELETE` auch mit einem `SELECT` kombinieren.

Beispiel:

```sql
DELETE FROM invoice_line
WHERE invoice_id IN (
    SELECT invoice_id
    FROM invoice
    WHERE customer_id = 5
);
```

Das bedeutet:

```text
Finde alle Rechnungen
von Kunde 5
        ↓
SELECT invoice_id
        ↓
Lösche die dazugehörigen
invoice_line-Einträge
```

Unterabfragen behandeln wir später noch ausführlicher.

---

# DELETE ist nicht DROP

Diese beiden Befehle dürfen nicht verwechselt werden.

## DELETE

```sql
DELETE FROM customer;
```

→ Löscht die **Datensätze**.

Die Tabelle `customer` existiert weiterhin.

---

## DROP

```sql
DROP TABLE customer;
```

→ Löscht die **komplette Tabelle**.

Also:

```text
DELETE → Inhalt löschen

DROP   → Tabelle löschen
```

---

# DELETE ist nicht UPDATE

Wenn wir nur einen Wert entfernen möchten, brauchen wir eventuell gar kein `DELETE`.

Beispiel:

Wir wollen die Telefonnummer eines Kunden entfernen.

Nicht:

```sql
DELETE FROM customer
WHERE customer_id = 5;
```

❌ Das würde den kompletten Kunden löschen.

Sondern:

```sql
UPDATE customer
SET phone = NULL
WHERE customer_id = 5;
```

→ Der Kunde bleibt erhalten, nur die Telefonnummer wird entfernt.

---

# Typische Fehler

## WHERE vergessen

```sql
DELETE FROM Pokemon;
```

❌ Alle Pokémon werden gelöscht.

Wenn nur Pikachu gelöscht werden soll:

```sql
DELETE FROM Pokemon
WHERE name = 'Pikachu';
```

---

## Spalten hinter DELETE schreiben

Falsch:

```sql
DELETE name
FROM Pokemon
WHERE id = 1;
```

❌ Mit `DELETE` löschen wir keine einzelne Spalte.

`DELETE` löscht immer **ganze Datensätze / Zeilen**.

Richtig:

```sql
DELETE FROM Pokemon
WHERE id = 1;
```

---

# Merksätze

> `DELETE` = Datensätze löschen

> `FROM` = Aus welcher Tabelle?

> `WHERE` = Welche Datensätze?

Besonders wichtig:

> ⚠️ **DELETE ohne WHERE löscht alle Datensätze der Tabelle.**

Bei Beziehungen:

> **Erst die abhängigen Datensätze löschen.**

Und:

```text
DELETE → Datensätze löschen
DROP   → komplette Tabelle löschen
UPDATE → vorhandene Werte verändern
```

Im Zweifel zuerst:

```sql
SELECT *
FROM tabelle
WHERE bedingung;
```

und erst danach:

```sql
DELETE FROM tabelle
WHERE bedingung;
```

---

## Navigation

⬅️ [[06 UPDATE|Zurück zu Kapitel 06 – UPDATE]]

➡️ [[08 CREATE TABLE|Weiter zu Kapitel 08 – CREATE TABLE]]