## Was macht INSERT?

Mit `INSERT` werden **neue Datensätze in eine Tabelle eingefügt**.

Grundaufbau:

```sql
INSERT INTO tabelle (spalte1, spalte2)
VALUES (wert1, wert2);
```

Beispiel:

```sql
INSERT INTO customer (first_name, last_name)
VALUES ('Max', 'Müller');
```

Dadurch wird ein neuer Datensatz in `customer` angelegt.

---

# INSERT INTO

Nach `INSERT INTO` geben wir an, **in welche Tabelle** die Daten eingefügt werden sollen.

```sql
INSERT INTO customer
```

Danach geben wir die Spalten an:

```sql
(first_name, last_name)
```

Und anschließend die Werte:

```sql
VALUES ('Max', 'Müller');
```

Komplett:

```sql
INSERT INTO customer (first_name, last_name)
VALUES ('Max', 'Müller');
```

---

# Reihenfolge beachten

Die Werte müssen zu den angegebenen Spalten passen.

```sql
INSERT INTO customer (first_name, last_name)
VALUES ('Max', 'Müller');
```

Hier gilt:

```text
first_name → Max
last_name  → Müller
```

Wenn wir die Reihenfolge ändern:

```sql
INSERT INTO customer (last_name, first_name)
VALUES ('Müller', 'Max');
```

funktioniert es ebenfalls.

Wichtig ist nur:

> Die Reihenfolge der Werte muss zur Reihenfolge der Spalten passen.

---

# Zahlen und Text

Text wird in einfache Anführungszeichen geschrieben:

```sql
'Pikachu'
```

Zahlen benötigen keine Anführungszeichen:

```sql
15
```

Beispiel:

```sql
INSERT INTO Pokemon (name, typ, level, kp)
VALUES ('Pikachu', 'Elektro', 15, 42);
```

---

# ID automatisch vergeben

Wenn eine ID automatisch erzeugt wird, müssen wir sie beim `INSERT` nicht angeben.

Zum Beispiel:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name TEXT,
    typ TEXT,
    level INTEGER
);
```

Dann reicht:

```sql
INSERT INTO Pokemon (name, typ, level)
VALUES ('Pikachu', 'Elektro', 15);
```

Die `id` wird von der Datenbank vergeben, wenn die Tabelle entsprechend eingerichtet ist.

---

# Mehrere Datensätze einfügen

Mit einem `INSERT` können auch mehrere Datensätze eingefügt werden.

```sql
INSERT INTO Pokemon (name, typ, level)
VALUES
    ('Pikachu', 'Elektro', 15),
    ('Glurak', 'Feuer', 55),
    ('Bisasam', 'Pflanze', 10);
```

Dadurch werden drei Datensätze eingefügt.

---

# INSERT mit allen Spalten

Es ist auch möglich, die Spaltennamen wegzulassen:

```sql
INSERT INTO Pokemon
VALUES (1, 'Pikachu', 'Elektro', 15);
```

Das ist allerdings fehleranfälliger.

Man muss dann:

- jeden benötigten Wert angeben
- die genaue Reihenfolge der Tabellenspalten kennen

Besser:

```sql
INSERT INTO Pokemon (name, typ, level)
VALUES ('Pikachu', 'Elektro', 15);
```

### Merksatz

> Spaltennamen beim `INSERT` mit anzugeben ist übersichtlicher und sicherer.

---

# NULL einfügen

Wenn ein Wert nicht vorhanden ist, kann unter bestimmten Voraussetzungen `NULL` verwendet werden.

```sql
INSERT INTO customer (first_name, last_name, phone)
VALUES ('Max', 'Müller', NULL);
```

Das funktioniert allerdings nur, wenn die Spalte `NULL` erlaubt.

---

# INSERT INTO ... SELECT

Jetzt kommt eine wichtige Variante, die wir auch schon in den Aufgaben hatten.

Wir können Daten aus einer anderen Tabelle mit einem `SELECT` holen und direkt einfügen.

Grundaufbau:

```sql
INSERT INTO ziel_tabelle (spalte1, spalte2)
SELECT spalte1, spalte2
FROM quell_tabelle;
```

Hier brauchen wir **kein `VALUES`**.

---

## Beispiel

Angenommen, wir haben:

```text
customer
```

und wollen bestimmte Kundendaten in eine andere Tabelle kopieren.

```sql
INSERT INTO kunden_backup (first_name, last_name)
SELECT first_name, last_name
FROM customer;
```

Das bedeutet:

```text
customer
   ↓
SELECT
   ↓
Daten werden ausgelesen
   ↓
INSERT INTO
   ↓
kunden_backup
```

---

# INSERT INTO ... SELECT mit WHERE

Natürlich können wir das auch mit `WHERE` kombinieren.

```sql
INSERT INTO kunden_backup (first_name, last_name)
SELECT first_name, last_name
FROM customer
WHERE country = 'Germany';
```

Jetzt werden nur Kunden aus Deutschland eingefügt.

---

# VALUES oder SELECT?

Es gibt zwei wichtige Varianten.

## Neue Werte selbst angeben

```sql
INSERT INTO customer (first_name, last_name)
VALUES ('Max', 'Müller');
```

Hier geben **wir selbst** die Werte an.

---

## Werte aus einer Tabelle holen

```sql
INSERT INTO kunden_backup (first_name, last_name)
SELECT first_name, last_name
FROM customer;
```

Hier kommen die Werte aus einem `SELECT`.

### Wichtig

Normalerweise verwenden wir entweder:

```sql
INSERT INTO ...
VALUES ...
```

oder:

```sql
INSERT INTO ...
SELECT ...
```

---

# Typische Fehler

## Spalten und Werte passen nicht zusammen

Falsch:

```sql
INSERT INTO Pokemon (name, level)
VALUES ('Pikachu');
```

❌ Zwei Spalten, aber nur ein Wert.

Richtig:

```sql
INSERT INTO Pokemon (name, level)
VALUES ('Pikachu', 15);
```

---

## Text ohne Anführungszeichen

Falsch:

```sql
VALUES (Pikachu, Elektro);
```

Richtig:

```sql
VALUES ('Pikachu', 'Elektro');
```

---

## VALUES bei INSERT ... SELECT

Falsch:

```sql
INSERT INTO kunden_backup (first_name, last_name)
VALUES
SELECT first_name, last_name
FROM customer;
```

Richtig:

```sql
INSERT INTO kunden_backup (first_name, last_name)
SELECT first_name, last_name
FROM customer;
```

---

# Merksätze

> `INSERT INTO` = Wo sollen die neuen Daten hin?

> `VALUES` = Welche neuen Werte möchte ich selbst einfügen?

Einzelner Datensatz:

```sql
INSERT INTO tabelle (spalten)
VALUES (werte);
```

Mehrere Datensätze:

```sql
INSERT INTO tabelle (spalten)
VALUES
    (werte),
    (werte),
    (werte);
```

Daten aus einer anderen Tabelle:

```sql
INSERT INTO ziel_tabelle (spalten)
SELECT spalten
FROM quell_tabelle;
```

---

## Navigation

⬅️ [[04 ORDER BY und LIMIT|Zurück zu Kapitel 04 – ORDER BY und LIMIT]]

➡️ [[06 UPDATE|Weiter zu Kapitel 06 – UPDATE]]