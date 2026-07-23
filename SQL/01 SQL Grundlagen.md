## Was ist SQL?

**SQL** steht für **Structured Query Language**.

SQL wird verwendet, um mit relationalen Datenbanken zu arbeiten.

Mit SQL können wir:

- Daten speichern
- Daten auslesen
- Daten verändern
- Daten löschen
- Tabellen erstellen
- Beziehungen zwischen Tabellen herstellen

---

## Datenbank und Tabelle

Eine **Datenbank** besteht normalerweise aus mehreren Tabellen.

Beispiel:

### Tabelle `customer`

| id | first_name | last_name |
|---|---|---|
| 1 | Max | Müller |
| 2 | Anna | Schmidt |
| 3 | Peter | Meier |

Eine Tabelle besteht aus:

- **Spalten** → Eigenschaften / Attribute
- **Zeilen** → einzelne Datensätze

Bei `customer` wären:

`id`, `first_name` und `last_name` die **Spalten**.

Eine komplette Zeile wie:

```text
1 | Max | Müller
```

ist ein **Datensatz**.

---

## Die wichtigsten SQL-Befehle

### SELECT

Daten auslesen:

```sql
SELECT * FROM customer;
```

`*` bedeutet:

> Alle Spalten auswählen.

---

### INSERT

Neue Daten hinzufügen:

```sql
INSERT INTO customer (first_name, last_name)
VALUES ('Max', 'Müller');
```

---

### UPDATE

Vorhandene Daten verändern:

```sql
UPDATE customer
SET first_name = 'Peter'
WHERE id = 1;
```

---

### DELETE

Daten löschen:

```sql
DELETE FROM customer
WHERE id = 1;
```

---

### CREATE TABLE

Eine neue Tabelle erstellen:

```sql
CREATE TABLE customer (
    id INTEGER PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
```

---

## SQL-Befehlsgruppen

SQL-Befehle werden in verschiedene Gruppen eingeteilt.

### DQL – Data Query Language

Daten abfragen:

```sql
SELECT
```

### DML – Data Manipulation Language

Daten verändern:

```text
INSERT
UPDATE
DELETE
```

### DDL – Data Definition Language

Struktur der Datenbank verändern:

```text
CREATE
ALTER
DROP
```

---

## Wichtig

SQL-Schlüsselwörter müssen normalerweise nicht großgeschrieben werden.

Das funktioniert:

```sql
select * from customer;
```

Üblicher und besser lesbar ist:

```sql
SELECT * FROM customer;
```

SQL-Befehle werden normalerweise mit einem Semikolon `;` beendet.

---

## Merksatz

> **SELECT** → lesen  
> **INSERT** → hinzufügen  
> **UPDATE** → ändern  
> **DELETE** → löschen  
> **CREATE** → erstellen  
> **DROP** → entfernen

---
---

## Weiter

[[02 SELECT|Weiter zu Kapitel 02 – SELECT →]]