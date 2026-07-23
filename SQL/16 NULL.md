## Was bedeutet NULL?

`NULL` bedeutet in SQL:

> **Es ist kein Wert vorhanden.**

Beispiel:

| customer_id | first_name | phone |
|---|---|---|
| 1 | Max | 012345 |
| 2 | Anna | NULL |
| 3 | Peter | 098765 |

Bei Anna ist keine Telefonnummer gespeichert.

Das wird durch:

```text
NULL
```

dargestellt.

---

# NULL ist nicht 0

`NULL` und `0` sind nicht dasselbe.

```text
0
```

ist ein vorhandener Zahlenwert.

```text
NULL
```

bedeutet:

> Kein Wert vorhanden.

Beispiel:

```text
kontostand = 0
```

→ Wir kennen den Kontostand. Er beträgt 0 €.

```text
kontostand = NULL
```

→ Wir haben keinen Wert für den Kontostand.

---

# NULL ist kein leerer Text

Auch diese beiden Werte sind unterschiedlich:

```text
''
```

und:

```text
NULL
```

`''` ist ein vorhandener Text mit **0 Zeichen**.

`NULL` bedeutet:

> Es existiert kein Wert.

---

# NULL ist nicht 'NULL'

Auch das hier:

```sql
'NULL'
```

ist nicht dasselbe wie:

```sql
NULL
```

Durch die Anführungszeichen ist:

```sql
'NULL'
```

ein normaler Text.

Also:

```text
NULL    → kein Wert

'NULL'  → Text mit den Buchstaben N U L L
```

---

# IS NULL

Um nach `NULL` zu suchen, verwenden wir:

```sql
IS NULL
```

Beispiel:

```sql
SELECT *
FROM customer
WHERE phone IS NULL;
```

Damit finden wir:

> Alle Kunden ohne gespeicherte Telefonnummer.

---

# Nicht mit = vergleichen

Das hier ist falsch:

```sql
SELECT *
FROM customer
WHERE phone = NULL;
```

❌

Bei `NULL` verwenden wir nicht:

```sql
=
```

sondern:

```sql
IS NULL
```

Richtig:

```sql
SELECT *
FROM customer
WHERE phone IS NULL;
```

---

# IS NOT NULL

Wenn wir alle Datensätze suchen, die **einen Wert besitzen**, verwenden wir:

```sql
IS NOT NULL
```

Beispiel:

```sql
SELECT *
FROM customer
WHERE phone IS NOT NULL;
```

→ Alle Kunden mit gespeicherter Telefonnummer.

---

# Merksatz

```text
IS NULL
```

> Kein Wert vorhanden.

```text
IS NOT NULL
```

> Wert vorhanden.

---

# NULL beim INSERT

Beim Einfügen von Daten kann `NULL` angegeben werden:

```sql
INSERT INTO customer (
    first_name,
    last_name,
    phone
)
VALUES (
    'Max',
    'Müller',
    NULL
);
```

Damit wird keine Telefonnummer gespeichert.

Wichtig:

```sql
NULL
```

ohne Anführungszeichen.

---

# Spalte beim INSERT weglassen

Wenn eine Spalte `NULL` erlaubt und keinen anderen Standardwert besitzt, kann sie häufig auch weggelassen werden.

Statt:

```sql
INSERT INTO customer (
    first_name,
    last_name,
    phone
)
VALUES (
    'Max',
    'Müller',
    NULL
);
```

können wir beispielsweise schreiben:

```sql
INSERT INTO customer (
    first_name,
    last_name
)
VALUES (
    'Max',
    'Müller'
);
```

`phone` erhält dann entsprechend der Tabellendefinition keinen Wert.

---

# NULL beim UPDATE

Wir können einen vorhandenen Wert auf `NULL` setzen.

Angenommen:

```text
Max | 0123456789
```

Wir möchten die Telefonnummer entfernen:

```sql
UPDATE customer
SET phone = NULL
WHERE customer_id = 1;
```

Danach:

```text
Max | NULL
```

Der Kunde wurde **nicht gelöscht**.

Nur der Wert in `phone` wurde entfernt.

---

# DELETE oder NULL?

Das ist ein wichtiger Unterschied.

```sql
DELETE FROM customer
WHERE customer_id = 1;
```

→ Der komplette Kunde wird gelöscht.

Dagegen:

```sql
UPDATE customer
SET phone = NULL
WHERE customer_id = 1;
```

→ Nur die Telefonnummer wird entfernt.

Der Kunde bleibt bestehen.

---

# NOT NULL

Beim Erstellen einer Tabelle können wir verhindern, dass eine Spalte `NULL` enthält.

Dafür gibt es:

```sql
NOT NULL
```

Beispiel:

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    level INTEGER
);
```

Jetzt muss jedes Pokémon einen Namen besitzen.

Das wäre nicht erlaubt:

```sql
INSERT INTO Pokemon (pokemon_id, name)
VALUES (1, NULL);
```

❌ `name` darf nicht `NULL` sein.

---

# NULL und DEFAULT

Angenommen:

```sql
level INTEGER DEFAULT 1
```

Wenn wir `level` beim `INSERT` weglassen:

```sql
INSERT INTO Pokemon (name)
VALUES ('Pikachu');
```

wird der Standardwert verwendet:

```text
level = 1
```

Das ist etwas anderes als ausdrücklich:

```sql
INSERT INTO Pokemon (name, level)
VALUES ('Pikachu', NULL);
```

Dann versuchen wir:

```text
level = NULL
```

zu speichern.

### Merksatz

> `DEFAULT` und `NULL` sind nicht dasselbe.

---

# NULL bei Aggregatfunktionen

Viele Aggregatfunktionen ignorieren `NULL`.

Angenommen:

| level |
|---:|
| 10 |
| 20 |
| NULL |
| 30 |

Dann:

```sql
SELECT AVG(level)
FROM Pokemon;
```

berechnet:

```text
(10 + 20 + 30) / 3
```

und nicht:

```text
(10 + 20 + 0 + 30) / 4
```

`NULL` wird also nicht automatisch als `0` behandelt.

---

# COUNT und NULL

Hier gibt es einen wichtigen Unterschied.

```sql
SELECT COUNT(*)
FROM customer;
```

zählt:

> Alle Datensätze.

Dagegen:

```sql
SELECT COUNT(phone)
FROM customer;
```

zählt:

> Nur Datensätze, bei denen `phone` nicht `NULL` ist.

Beispiel:

| customer | phone |
|---|---|
| Max | 12345 |
| Anna | NULL |
| Peter | 67890 |

Dann:

```sql
COUNT(*)
```

ergibt:

```text
3
```

aber:

```sql
COUNT(phone)
```

ergibt:

```text
2
```

---

# NULL bei LEFT JOIN

`NULL` ist auch bei `LEFT JOIN` sehr wichtig.

Angenommen:

```text
customer
   │
   ▼
invoice
```

Wir möchten alle Kunden anzeigen:

```sql
SELECT c.first_name,
       i.invoice_id
FROM customer c
LEFT JOIN invoice i
    ON c.customer_id = i.customer_id;
```

Ein Kunde ohne Rechnung könnte so erscheinen:

```text
Peter | NULL
```

Der `LEFT JOIN` behält Peter, obwohl keine passende Rechnung existiert.

Für die Spalten aus `invoice` erhalten wir dann `NULL`.

---

# Kunden ohne Rechnung finden

Das können wir ausnutzen:

```sql
SELECT c.first_name,
       c.last_name
FROM customer c
LEFT JOIN invoice i
    ON c.customer_id = i.customer_id
WHERE i.invoice_id IS NULL;
```

Damit finden wir:

> Kunden, für die keine Rechnung existiert.

Das Muster:

```sql
LEFT JOIN ...
WHERE rechte_tabelle.id IS NULL
```

ist deshalb sehr nützlich.

---

# NULL bei Berechnungen

Mit `NULL` muss man bei Berechnungen aufpassen.

Beispiel:

```sql
SELECT 10 + NULL;
```

Das Ergebnis ist normalerweise:

```text
NULL
```

Warum?

Wenn ein Teil der Berechnung unbekannt ist, ist auch das Ergebnis unbekannt.

Also:

```text
10 + NULL → NULL
```

---

# COALESCE()

Mit `COALESCE()` können wir einen Ersatzwert für `NULL` festlegen.

Beispiel:

```sql
SELECT first_name,
       COALESCE(phone, 'Keine Telefonnummer')
FROM customer;
```

Wenn `phone` vorhanden ist:

```text
Max | 0123456789
```

Wenn `phone` `NULL` ist:

```text
Anna | Keine Telefonnummer
```

Die Daten in der Tabelle werden dadurch nicht verändert.

Nur die Ausgabe verwendet einen Ersatzwert.

---

# COALESCE bei Zahlen

Auch bei Berechnungen ist das praktisch.

Angenommen:

```text
rabatt = NULL
```

Dann könnten wir schreiben:

```sql
SELECT preis - COALESCE(rabatt, 0)
FROM produkt;
```

`COALESCE` bedeutet hier:

> Wenn `rabatt` NULL ist, verwende stattdessen 0.

---

# Wie funktioniert COALESCE?

```sql
COALESCE(wert1, wert2, wert3)
```

liefert den **ersten Wert, der nicht NULL ist**.

Beispiel:

```sql
COALESCE(NULL, NULL, 'Hallo')
```

Ergebnis:

```text
Hallo
```

---

# Dreiwertige Logik

SQL kennt bei Vergleichen nicht nur:

```text
TRUE
FALSE
```

sondern auch:

```text
UNKNOWN
```

Das hängt mit `NULL` zusammen.

Wenn wir beispielsweise fragen:

```text
Ist NULL = 5?
```

können wir nicht sagen:

```text
TRUE
```

Aber streng genommen auch nicht:

```text
FALSE
```

Denn `NULL` bedeutet:

> Wir kennen den Wert nicht.

Das Ergebnis ist deshalb:

```text
UNKNOWN
```

Das ist auch der Grund, warum wir nicht schreiben:

```sql
WHERE phone = NULL
```

sondern:

```sql
WHERE phone IS NULL
```

---

# Typische Fehler

## Fehler 1

```sql
WHERE phone = NULL
```

❌

Richtig:

```sql
WHERE phone IS NULL
```

---

## Fehler 2

```sql
WHERE phone != NULL
```

❌

Richtig:

```sql
WHERE phone IS NOT NULL
```

---

## Fehler 3

```sql
SET phone = 'NULL'
```

❌ Dadurch wird der Text `NULL` gespeichert.

Richtig:

```sql
SET phone = NULL
```

---

## Fehler 4

Annehmen:

```text
NULL = 0
```

❌

`0` ist ein Wert.

`NULL` bedeutet:

```text
kein Wert vorhanden
```

---

# Übersicht

| Wert | Bedeutung |
|---|---|
| `NULL` | kein Wert vorhanden |
| `0` | Zahl Null |
| `''` | leerer Text |
| `'NULL'` | Text „NULL“ |

Suchen nach fehlendem Wert:

```sql
IS NULL
```

Suchen nach vorhandenem Wert:

```sql
IS NOT NULL
```

---

# Merksätze

> **NULL bedeutet: Kein Wert vorhanden.**

Nicht verwechseln:

```text
NULL ≠ 0
NULL ≠ ''
NULL ≠ 'NULL'
```

Bei Abfragen:

```sql
IS NULL
```

und:

```sql
IS NOT NULL
```

Nicht:

```sql
= NULL
```

Und besonders wichtig:

> `COUNT(*)` zählt alle Zeilen.

> `COUNT(spalte)` zählt nur Werte, die nicht `NULL` sind.

---

## Navigation

⬅️ [[15 Unterabfragen|Zurück zu Kapitel 15 – Unterabfragen]]

➡️ [[17 Constraints|Weiter zu Kapitel 17 – Constraints]]