## Was ist eine Unterabfrage?

Eine **Unterabfrage** ist eine SQL-Abfrage innerhalb einer anderen SQL-Abfrage.

Sie wird auch genannt:

> **Subquery**

Beispiel:

```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT customer_id
    FROM invoice
    WHERE invoice_id = 10
);
```

Hier haben wir tatsächlich:

```text
SELECT
    ↓
    SELECT
```

Der innere `SELECT` liefert ein Ergebnis, das vom äußeren `SELECT` weiterverwendet wird.

---

# Von innen nach außen lesen

Das ist die wichtigste Regel bei Unterabfragen:

> **Zuerst die innere Abfrage verstehen.**

Beispiel:

```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT customer_id
    FROM invoice
    WHERE invoice_id = 10
);
```

Zuerst betrachten wir:

```sql
SELECT customer_id
FROM invoice
WHERE invoice_id = 10;
```

Angenommen, das Ergebnis ist:

```text
customer_id
-----------
5
```

Dann können wir uns vorstellen, SQL ersetzt die Unterabfrage durch:

```text
5
```

Die äußere Abfrage wird also praktisch zu:

```sql
SELECT *
FROM customer
WHERE customer_id = 5;
```

Jetzt wird Kunde 5 gefunden.

---

# Bildlich vorgestellt

```text
SELECT customer_id
FROM invoice
WHERE invoice_id = 10

        ↓

        5

        ↓

SELECT *
FROM customer
WHERE customer_id = 5
```

### Merksatz

> **Innere Abfrage ausführen → Ergebnis einsetzen → äußere Abfrage ausführen**

---

# Unterabfrage mit =

Wenn die Unterabfrage **genau einen Wert** zurückgibt, können wir häufig `=` verwenden.

```sql
SELECT *
FROM customer
WHERE customer_id = (
    SELECT customer_id
    FROM invoice
    WHERE invoice_id = 10
);
```

Die innere Abfrage liefert beispielsweise:

```text
5
```

Dann funktioniert:

```sql
customer_id = 5
```

---

# Unterabfrage mit IN

Was passiert aber, wenn die Unterabfrage mehrere Werte zurückgibt?

Beispiel:

```sql
SELECT customer_id
FROM invoice
WHERE total > 20;
```

Das könnte liefern:

```text
1
3
5
8
```

Dann können wir nicht sinnvoll schreiben:

```sql
customer_id = (1, 3, 5, 8)
```

Stattdessen verwenden wir:

```sql
IN
```

```sql
SELECT *
FROM customer
WHERE customer_id IN (
    SELECT customer_id
    FROM invoice
    WHERE total > 20
);
```

Das entspricht gedanklich:

```sql
SELECT *
FROM customer
WHERE customer_id IN (1, 3, 5, 8);
```

---

# = oder IN?

Eine wichtige Faustregel:

## Ein Wert

Wenn die Unterabfrage genau **einen Wert** liefert:

```sql
=
```

Beispiel:

```sql
WHERE customer_id = (
    SELECT customer_id
    FROM invoice
    WHERE invoice_id = 10
);
```

---

## Mehrere Werte

Wenn mehrere Werte möglich sind:

```sql
IN
```

Beispiel:

```sql
WHERE customer_id IN (
    SELECT customer_id
    FROM invoice
    WHERE total > 20
);
```

### Merksatz

> Ein Ergebnis → `=`

> Mehrere mögliche Ergebnisse → `IN`

---

# Unterabfrage mit MAX()

Unterabfragen sind praktisch, wenn wir erst einen Wert berechnen und anschließend den dazugehörigen Datensatz suchen möchten.

Frage:

> Welche Rechnung hat den höchsten Rechnungsbetrag?

Zuerst können wir herausfinden:

```sql
SELECT MAX(total)
FROM invoice;
```

Angenommen:

```text
25.86
```

Jetzt suchen wir die Rechnung:

```sql
SELECT *
FROM invoice
WHERE total = (
    SELECT MAX(total)
    FROM invoice
);
```

---

# Was passiert?

Innere Abfrage:

```sql
SELECT MAX(total)
FROM invoice;
```

Ergebnis:

```text
25.86
```

Dann:

```sql
SELECT *
FROM invoice
WHERE total = 25.86;
```

Damit erhalten wir den kompletten Datensatz.

---

# Unterschied zu ORDER BY

Das gleiche Problem könnten wir teilweise auch lösen mit:

```sql
SELECT *
FROM invoice
ORDER BY total DESC
LIMIT 1;
```

Aber es gibt einen Unterschied.

Wenn mehrere Rechnungen exakt denselben höchsten Wert besitzen:

```text
25.86
25.86
```

liefert:

```sql
LIMIT 1
```

nur eine davon.

Die Unterabfrage:

```sql
WHERE total = (
    SELECT MAX(total)
    FROM invoice
);
```

kann **alle Rechnungen mit diesem Höchstwert** liefern.

---

# Unterabfrage mit AVG()

Frage:

> Welche Rechnungen liegen über dem Durchschnitt?

Zuerst:

```sql
SELECT AVG(total)
FROM invoice;
```

Angenommen:

```text
Durchschnitt = 10.50
```

Dann:

```sql
SELECT *
FROM invoice
WHERE total > (
    SELECT AVG(total)
    FROM invoice
);
```

Gedanklich:

```sql
WHERE total > 10.50
```

---

# Unterabfrage mit INSERT

Unterabfragen können auch beim Einfügen von Daten verwendet werden.

Zum Beispiel:

```sql
INSERT INTO kunden_backup (first_name, last_name)
SELECT first_name, last_name
FROM customer
WHERE country = 'Germany';
```

Hier liefert der `SELECT` die Daten, die anschließend eingefügt werden.

Wichtig:

Bei:

```sql
INSERT INTO ... SELECT
```

benötigen wir kein `VALUES`.

---

# Unterabfrage in VALUES

Je nach Aufgabe und Datenbanksystem kann eine Unterabfrage auch einen einzelnen Wert für ein `INSERT` liefern.

Beispiel:

```sql
INSERT INTO invoice (
    customer_id,
    total
)
VALUES (
    (
        SELECT customer_id
        FROM customer
        WHERE email = 'max@example.com'
    ),
    29.99
);
```

Das sieht am Anfang etwas wild aus.

Deshalb wieder:

> Von innen nach außen lesen.

---

## Schritt 1

```sql
SELECT customer_id
FROM customer
WHERE email = 'max@example.com';
```

Ergebnis:

```text
5
```

---

## Schritt 2

Dann wird daraus gedanklich:

```sql
INSERT INTO invoice (
    customer_id,
    total
)
VALUES (
    5,
    29.99
);
```

Jetzt ist viel klarer, was passiert.

---

# Mehrere Unterabfragen in VALUES

Es können sogar mehrere Werte durch Unterabfragen ermittelt werden.

Zum Beispiel:

```sql
INSERT INTO neue_tabelle (
    customer_id,
    invoice_id
)
VALUES (
    (
        SELECT customer_id
        FROM customer
        WHERE email = 'max@example.com'
    ),
    (
        SELECT invoice_id
        FROM invoice
        WHERE customer_id = 5
        LIMIT 1
    )
);
```

Deshalb kann man in manchen Musterlösungen plötzlich mehrere `SELECT` innerhalb eines `VALUES` sehen.

Jeder innere `SELECT` liefert dabei einen Wert für die jeweilige Spalte.

---

# Unterabfrage mit DELETE

Unterabfragen sind auch beim Löschen sehr praktisch.

Wir haben:

```text
customer
    ↓
invoice
    ↓
invoice_line
```

Frage:

> Lösche alle Rechnungspositionen von Kunde 5.

`invoice_line` besitzt aber vielleicht gar keine:

```text
customer_id
```

sondern nur:

```text
invoice_id
```

Wir müssen deshalb zuerst herausfinden:

> Welche Rechnungen gehören Kunde 5?

```sql
SELECT invoice_id
FROM invoice
WHERE customer_id = 5;
```

Angenommen:

```text
10
11
15
```

Dann:

```sql
DELETE FROM invoice_line
WHERE invoice_id IN (10, 11, 15);
```

Beides zusammen:

```sql
DELETE FROM invoice_line
WHERE invoice_id IN (
    SELECT invoice_id
    FROM invoice
    WHERE customer_id = 5
);
```

---

# Warum ist das praktisch?

Unsere Tabellen sind verbunden:

```text
customer
customer_id
     │
     ▼
invoice
customer_id
invoice_id
     │
     ▼
invoice_line
invoice_id
```

`invoice_line` kennt den Kunden nicht direkt.

Aber:

```text
invoice_line
     ↓
invoice
     ↓
customer
```

Über die Unterabfrage können wir die benötigten IDs ermitteln.

---

# Unterabfrage mit UPDATE

Auch bei `UPDATE` können Unterabfragen verwendet werden.

Beispiel:

```sql
UPDATE Pokemon
SET level = level + 1
WHERE trainer_id = (
    SELECT trainer_id
    FROM Trainer
    WHERE name = 'Ash'
);
```

Zuerst:

```sql
SELECT trainer_id
FROM Trainer
WHERE name = 'Ash';
```

Ergebnis:

```text
1
```

Dann:

```sql
UPDATE Pokemon
SET level = level + 1
WHERE trainer_id = 1;
```

Alle Pokémon von Ash bekommen ein Level dazu.

---

# EXISTS

Eine weitere Möglichkeit ist:

```sql
EXISTS
```

Damit prüfen wir:

> Existiert mindestens ein passender Datensatz?

Beispiel:

```sql
SELECT *
FROM customer c
WHERE EXISTS (
    SELECT 1
    FROM invoice i
    WHERE i.customer_id = c.customer_id
);
```

Damit finden wir Kunden, die mindestens eine Rechnung besitzen.

Für den Anfang ist aber wichtiger, dass du sicher mit:

```text
=
IN
```

und normalen Unterabfragen umgehen kannst.

---

# NOT IN

Natürlich können wir auch nach Datensätzen suchen, deren Wert **nicht** in der Unterabfrage vorkommt.

```sql
SELECT *
FROM customer
WHERE customer_id NOT IN (
    SELECT customer_id
    FROM invoice
    WHERE customer_id IS NOT NULL
);
```

Damit suchen wir Kunden, deren ID nicht in den Rechnungen vorkommt.

Also vereinfacht:

> Kunden ohne Rechnung.

Bei `NOT IN` muss man mit `NULL` aufpassen, weshalb `NOT EXISTS` in der Praxis oft robuster ist.

---

# Unterabfrage oder JOIN?

Viele Aufgaben können sowohl mit einem `JOIN` als auch mit einer Unterabfrage gelöst werden.

Beispiel:

> Welche Kunden besitzen eine Rechnung?

Mit Unterabfrage:

```sql
SELECT *
FROM customer
WHERE customer_id IN (
    SELECT customer_id
    FROM invoice
);
```

Mit JOIN:

```sql
SELECT DISTINCT c.*
FROM customer c
INNER JOIN invoice i
    ON c.customer_id = i.customer_id;
```

Beide Wege können sinnvoll sein.

---

# Wann denke ich an eine Unterabfrage?

Eine Unterabfrage ist besonders naheliegend, wenn du denkst:

> **Ich muss zuerst etwas herausfinden, damit ich die eigentliche Abfrage machen kann.**

Beispiel:

> Welche Rechnungen sind teurer als der Durchschnitt?

Zuerst muss ich wissen:

```text
Wie hoch ist der Durchschnitt?
```

Also:

```sql
SELECT AVG(total)
FROM invoice;
```

Danach:

```text
Welche Rechnungen liegen darüber?
```

Also:

```sql
SELECT *
FROM invoice
WHERE total > (...);
```

Zusammen:

```sql
SELECT *
FROM invoice
WHERE total > (
    SELECT AVG(total)
    FROM invoice
);
```

---

# So löst du Unterabfragen

Wenn du eine komplizierte Aufgabe bekommst:

## 1. Frage dich

> Was muss ich zuerst herausfinden?

Schreibe dafür einen normalen `SELECT`.

---

## 2. Teste diesen SELECT

Zum Beispiel:

```sql
SELECT AVG(total)
FROM invoice;
```

---

## 3. Überlege, was das Ergebnis wäre

Zum Beispiel:

```text
10.50
```

---

## 4. Schreibe die äußere Abfrage

```sql
SELECT *
FROM invoice
WHERE total > 10.50;
```

---

## 5. Ersetze den festen Wert durch die Unterabfrage

```sql
SELECT *
FROM invoice
WHERE total > (
    SELECT AVG(total)
    FROM invoice
);
```

Fertig.

---

# Wichtigster Denk-Trick

Wenn dich so etwas verwirrt:

```sql
SELECT *
FROM invoice
WHERE total > (
    SELECT AVG(total)
    FROM invoice
);
```

decke gedanklich die äußere Abfrage ab.

Betrachte nur:

```sql
SELECT AVG(total)
FROM invoice;
```

Angenommen:

```text
12
```

Dann ersetzt du die Klammer gedanklich:

```sql
SELECT *
FROM invoice
WHERE total > 12;
```

Jetzt ist die Abfrage wieder ganz normal.

---

# Übersicht

| Situation | Häufige Lösung |
|---|---|
| Unterabfrage liefert einen Wert | `=` `>` `<` usw. |
| Unterabfrage liefert mehrere Werte | `IN` |
| Prüfen, ob etwas existiert | `EXISTS` |
| Höchsten Wert finden und Datensatz anzeigen | `MAX()` als Unterabfrage |
| Über Durchschnitt suchen | `AVG()` als Unterabfrage |
| IDs aus anderer Tabelle benötigen | Unterabfrage mit `SELECT id` |

---

# Merksätze

> **Unterabfrage = Abfrage innerhalb einer Abfrage.**

> **Immer von innen nach außen lesen.**

Wenn innen:

```sql
SELECT ...
```

steht, stell dir vor, dieser Teil wird zuerst durch sein Ergebnis ersetzt.

Zum Beispiel:

```sql
WHERE customer_id = (
    SELECT customer_id ...
);
```

wird gedanklich zu:

```sql
WHERE customer_id = 5;
```

Und:

> Ein Wert → meistens `=`

> Mehrere Werte → meistens `IN`

Der wichtigste Hinweis in einer Aufgabe ist oft:

> **„Ich muss zuerst X herausfinden, bevor ich Y suchen kann.“**

Dann solltest du an eine **Unterabfrage** denken.

---

## Navigation

⬅️ [[14 GROUP BY und HAVING|Zurück zu Kapitel 14 – GROUP BY und HAVING]]

➡️ [[16 NULL|Weiter zu Kapitel 16 – NULL]]