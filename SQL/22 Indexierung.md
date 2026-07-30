Ein **Index** hilft einer Datenbank dabei, Datensätze schneller zu finden.

Man kann sich einen Index wie das **Stichwortverzeichnis eines Buches** vorstellen.

Ohne Stichwortverzeichnis müsste man möglicherweise jede Seite durchsuchen.

Mit einem Stichwortverzeichnis kann man direkt nachsehen, auf welcher Seite sich die gesuchte Information befindet.

---

# Ohne Index

Angenommen, unsere Tabelle `kunde` enthält sehr viele Datensätze:

|kunde_id|name|email|
|--:|---|---|
|1|Anna|[anna@example.com](mailto:anna@example.com)|
|2|Bob|[bob@example.com](mailto:bob@example.com)|
|3|Nobu|[nobu@example.com](mailto:nobu@example.com)|
|...|...|...|
|1.000.000|Max|[max@example.com](mailto:max@example.com)|

Wir suchen:

```sql
SELECT *
FROM kunde
WHERE name = 'Nobu';
```

Ohne passenden Index muss die Datenbank möglicherweise sehr viele Datensätze durchsuchen.

Vereinfacht:

```text
Anna → Nein
Bob  → Nein
Nobu → Treffer
...
```

Das nennt man häufig einen **Full Table Scan** bzw. **Table Scan**.

Bei kleinen Tabellen ist das normalerweise kein großes Problem.

Bei Tabellen mit Millionen Datensätzen kann es jedoch langsam werden.

---

# Mit Index

Wir können einen Index für die Spalte `name` erstellen:

```sql
CREATE INDEX idx_kunde_name
ON kunde(name);
```

Jetzt besitzt die Datenbank zusätzlich eine Datenstruktur, mit deren Hilfe sie schneller nach `name` suchen kann.

Vereinfacht:

```text
Index
  │
  ├── Anna → Datensatz 1
  ├── Bob  → Datensatz 2
  ├── Max  → Datensatz 1.000.000
  └── Nobu → Datensatz 3
                ↓
             Tabelle
```

Die Datenbank muss dadurch nicht unbedingt die komplette Tabelle durchsuchen.

---

# Syntax

Ein Index wird mit `CREATE INDEX` erstellt.

```sql
CREATE INDEX index_name
ON tabelle(spalte);
```

Beispiel:

```sql
CREATE INDEX idx_kunde_email
ON kunde(email);
```

Dabei ist:

```text
idx_kunde_email
        ↓
Name des Index

kunde
  ↓
Tabelle

email
  ↓
Spalte, die indexiert wird
```

---

# Warum verwendet man Indizes?

Indizes können Abfragen beschleunigen, bei denen häufig nach bestimmten Spalten gesucht wird.

Zum Beispiel:

```sql
SELECT *
FROM kunde
WHERE email = 'nobu@example.com';
```

Ein Index auf `email` kann diese Suche beschleunigen.

Auch bei anderen Operationen können Indizes hilfreich sein, zum Beispiel bei:

```sql
WHERE
JOIN
ORDER BY
```

---

# Beispiel mit JOIN

Wir haben zwei Tabellen:

```text
Kunde
-----
kunde_id PK
name


Bestellung
----------
bestellung_id PK
kunde_id FK
preis
```

Eine Abfrage könnte so aussehen:

```sql
SELECT kunde.name, bestellung.preis
FROM kunde
JOIN bestellung
ON kunde.kunde_id = bestellung.kunde_id;
```

Wenn sehr viele Bestellungen existieren, kann ein Index auf:

```text
bestellung.kunde_id
```

die Suche nach den passenden Bestellungen beschleunigen.

Zum Beispiel:

```sql
CREATE INDEX idx_bestellung_kunde
ON bestellung(kunde_id);
```

---

# Primary Key und Indizes

Bei vielen Datenbanksystemen wird für einen `PRIMARY KEY` automatisch ein Index angelegt.

Beispiel:

```sql
CREATE TABLE kunde (
    kunde_id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT
);
```

Dadurch kann die Datenbank sehr schnell nach einer bestimmten ID suchen:

```sql
SELECT *
FROM kunde
WHERE kunde_id = 42;
```

> [!important]  
> Primärschlüssel sind besonders gut für schnelle und eindeutige Zugriffe auf Datensätze geeignet.

---

# UNIQUE und Indizes

Auch ein `UNIQUE`-Constraint wird von vielen Datenbanksystemen mithilfe eines eindeutigen Index umgesetzt.

Beispiel:

```sql
CREATE TABLE kunde (
    kunde_id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT UNIQUE
);
```

Die Datenbank muss schnell überprüfen können, ob eine E-Mail bereits vorhanden ist.

---

# Index über mehrere Spalten

Ein Index kann auch mehrere Spalten enthalten.

Beispiel:

```sql
CREATE INDEX idx_kunde_name_ort
ON kunde(name, ort);
```

Das nennt man einen **zusammengesetzten Index** oder **Composite Index**.

Er kann beispielsweise bei einer Abfrage helfen wie:

```sql
SELECT *
FROM kunde
WHERE name = 'Nobu'
AND ort = 'Augsburg';
```

⚠️ Bei zusammengesetzten Indizes spielt die **Reihenfolge der Spalten** eine wichtige Rolle.

Ein Index auf:

```text
(name, ort)
```

ist nicht automatisch dasselbe wie:

```text
(ort, name)
```

---

# Index löschen

Ein nicht mehr benötigter Index kann gelöscht werden.

```sql
DROP INDEX idx_kunde_name;
```

Die genaue Syntax kann sich je nach Datenbanksystem etwas unterscheiden.

---

# Nachteile von Indizes

Indizes machen nicht automatisch alles schneller.

Sie benötigen zusätzlichen:

```text
Speicherplatz
```

Außerdem müssen Indizes aktualisiert werden, wenn Daten verändert werden.

Zum Beispiel bei:

```sql
INSERT
UPDATE
DELETE
```

Beispiel:

```sql
INSERT INTO kunde
VALUES (4, 'Lisa', 'lisa@example.com');
```

Die Datenbank muss:

```text
Datensatz speichern
        +
Index aktualisieren
```

Dadurch können Schreiboperationen langsamer werden.

---

# Zu viele Indizes

Man sollte deshalb nicht einfach jede Spalte indexieren.

```text
Mehr Indizes
    ↓
schnellere bestimmte Lesezugriffe
    ↓
aber
    ↓
mehr Speicherplatz
+
langsamere Schreibzugriffe
```

Die Kunst besteht darin, hauptsächlich die Spalten zu indexieren, die häufig für Abfragen benötigt werden.

---

# Wann ist ein Index sinnvoll?

Ein Index kann besonders sinnvoll sein, wenn:

- eine Tabelle sehr viele Datensätze enthält
    
- häufig nach einer bestimmten Spalte gesucht wird
    
- eine Spalte häufig in `WHERE` verwendet wird
    
- Spalten häufig für `JOIN` verwendet werden
    
- Daten häufig sortiert werden
    
- Werte möglichst eindeutig gefunden werden sollen
    

Weniger sinnvoll kann ein zusätzlicher Index sein, wenn:

- die Tabelle sehr klein ist
    
- eine Spalte kaum abgefragt wird
    
- sehr viele Schreiboperationen stattfinden
    
- bereits ein geeigneter Index existiert
    

---

# Einfaches Beispiel

Wir haben:

```text
1.000.000 Kunden
```

und suchen regelmäßig über:

Ein **Index** hilft einer Datenbank dabei, Datensätze schneller zu finden.

Man kann sich einen Index wie das **Stichwortverzeichnis eines Buches** vorstellen.

Ohne Stichwortverzeichnis müsste man möglicherweise jede Seite durchsuchen.

Mit einem Stichwortverzeichnis kann man direkt nachsehen, auf welcher Seite sich die gesuchte Information befindet.

---

# Ohne Index

Angenommen, unsere Tabelle `kunde` enthält sehr viele Datensätze:

|kunde_id|name|email|
|--:|---|---|
|1|Anna|[anna@example.com](mailto:anna@example.com)|
|2|Bob|[bob@example.com](mailto:bob@example.com)|
|3|Nobu|[nobu@example.com](mailto:nobu@example.com)|
|...|...|...|
|1.000.000|Max|[max@example.com](mailto:max@example.com)|

Wir suchen:

```sql
SELECT *
FROM kunde
WHERE name = 'Nobu';
```

Ohne passenden Index muss die Datenbank möglicherweise sehr viele Datensätze durchsuchen.

Vereinfacht:

```text
Anna → Nein
Bob  → Nein
Nobu → Treffer
...
```

Das nennt man häufig einen **Full Table Scan** bzw. **Table Scan**.

Bei kleinen Tabellen ist das normalerweise kein großes Problem.

Bei Tabellen mit Millionen Datensätzen kann es jedoch langsam werden.

---

# Mit Index

Wir können einen Index für die Spalte `name` erstellen:

```sql
CREATE INDEX idx_kunde_name
ON kunde(name);
```

Jetzt besitzt die Datenbank zusätzlich eine Datenstruktur, mit deren Hilfe sie schneller nach `name` suchen kann.

Vereinfacht:

```text
Index
  │
  ├── Anna → Datensatz 1
  ├── Bob  → Datensatz 2
  ├── Max  → Datensatz 1.000.000
  └── Nobu → Datensatz 3
                ↓
             Tabelle
```

Die Datenbank muss dadurch nicht unbedingt die komplette Tabelle durchsuchen.

---

# Syntax

Ein Index wird mit `CREATE INDEX` erstellt.

```sql
CREATE INDEX index_name
ON tabelle(spalte);
```

Beispiel:

```sql
CREATE INDEX idx_kunde_email
ON kunde(email);
```

Dabei ist:

```text
idx_kunde_email
        ↓
Name des Index

kunde
  ↓
Tabelle

email
  ↓
Spalte, die indexiert wird
```

---

# Warum verwendet man Indizes?

Indizes können Abfragen beschleunigen, bei denen häufig nach bestimmten Spalten gesucht wird.

Zum Beispiel:

```sql
SELECT *
FROM kunde
WHERE email = 'nobu@example.com';
```

Ein Index auf `email` kann diese Suche beschleunigen.

Auch bei anderen Operationen können Indizes hilfreich sein, zum Beispiel bei:

```sql
WHERE
JOIN
ORDER BY
```

---

# Beispiel mit JOIN

Wir haben zwei Tabellen:

```text
Kunde
-----
kunde_id PK
name


Bestellung
----------
bestellung_id PK
kunde_id FK
preis
```

Eine Abfrage könnte so aussehen:

```sql
SELECT kunde.name, bestellung.preis
FROM kunde
JOIN bestellung
ON kunde.kunde_id = bestellung.kunde_id;
```

Wenn sehr viele Bestellungen existieren, kann ein Index auf:

```text
bestellung.kunde_id
```

die Suche nach den passenden Bestellungen beschleunigen.

Zum Beispiel:

```sql
CREATE INDEX idx_bestellung_kunde
ON bestellung(kunde_id);
```

---

# Primary Key und Indizes

Bei vielen Datenbanksystemen wird für einen `PRIMARY KEY` automatisch ein Index angelegt.

Beispiel:

```sql
CREATE TABLE kunde (
    kunde_id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT
);
```

Dadurch kann die Datenbank sehr schnell nach einer bestimmten ID suchen:

```sql
SELECT *
FROM kunde
WHERE kunde_id = 42;
```

> [!important]  
> Primärschlüssel sind besonders gut für schnelle und eindeutige Zugriffe auf Datensätze geeignet.

---

# UNIQUE und Indizes

Auch ein `UNIQUE`-Constraint wird von vielen Datenbanksystemen mithilfe eines eindeutigen Index umgesetzt.

Beispiel:

```sql
CREATE TABLE kunde (
    kunde_id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT UNIQUE
);
```

Die Datenbank muss schnell überprüfen können, ob eine E-Mail bereits vorhanden ist.

---

# Index über mehrere Spalten

Ein Index kann auch mehrere Spalten enthalten.

Beispiel:

```sql
CREATE INDEX idx_kunde_name_ort
ON kunde(name, ort);
```

Das nennt man einen **zusammengesetzten Index** oder **Composite Index**.

Er kann beispielsweise bei einer Abfrage helfen wie:

```sql
SELECT *
FROM kunde
WHERE name = 'Nobu'
AND ort = 'Augsburg';
```

⚠️ Bei zusammengesetzten Indizes spielt die **Reihenfolge der Spalten** eine wichtige Rolle.

Ein Index auf:

```text
(name, ort)
```

ist nicht automatisch dasselbe wie:

```text
(ort, name)
```

---

# Index löschen

Ein nicht mehr benötigter Index kann gelöscht werden.

```sql
DROP INDEX idx_kunde_name;
```

Die genaue Syntax kann sich je nach Datenbanksystem etwas unterscheiden.

---

# Nachteile von Indizes

Indizes machen nicht automatisch alles schneller.

Sie benötigen zusätzlichen:

```text
Speicherplatz
```

Außerdem müssen Indizes aktualisiert werden, wenn Daten verändert werden.

Zum Beispiel bei:

```sql
INSERT
UPDATE
DELETE
```

Beispiel:

```sql
INSERT INTO kunde
VALUES (4, 'Lisa', 'lisa@example.com');
```

Die Datenbank muss:

```text
Datensatz speichern
        +
Index aktualisieren
```

Dadurch können Schreiboperationen langsamer werden.

---

# Zu viele Indizes

Man sollte deshalb nicht einfach jede Spalte indexieren.

```text
Mehr Indizes
    ↓
schnellere bestimmte Lesezugriffe
    ↓
aber
    ↓
mehr Speicherplatz
+
langsamere Schreibzugriffe
```

Die Kunst besteht darin, hauptsächlich die Spalten zu indexieren, die häufig für Abfragen benötigt werden.

---

# Wann ist ein Index sinnvoll?

Ein Index kann besonders sinnvoll sein, wenn:

- eine Tabelle sehr viele Datensätze enthält
    
- häufig nach einer bestimmten Spalte gesucht wird
    
- eine Spalte häufig in `WHERE` verwendet wird
    
- Spalten häufig für `JOIN` verwendet werden
    
- Daten häufig sortiert werden
    
- Werte möglichst eindeutig gefunden werden sollen
    

Weniger sinnvoll kann ein zusätzlicher Index sein, wenn:

- die Tabelle sehr klein ist
    
- eine Spalte kaum abgefragt wird
    
- sehr viele Schreiboperationen stattfinden
    
- bereits ein geeigneter Index existiert
    

---

# Einfaches Beispiel

Wir haben:

```text
1.000.000 Kunden
```

und suchen regelmäßig über:

```sql
WHERE email = ?
```

Dann kann ein Index sinnvoll sein:

```sql
CREATE INDEX idx_kunde_email
ON kunde(email);
```

Wenn wir dagegen eine Tabelle mit nur zehn Kunden haben, bringt ein zusätzlicher Index kaum einen praktischen Vorteil.

---

# Merksatz

> Ein Index macht das **Suchen schneller**, benötigt aber zusätzlichen Speicher und kann das **Schreiben langsamer** machen.

Vereinfacht:

```text
                INDEX
                  │
        ┌─────────┴─────────┐
        ↓                   ↓
   SELECT schneller    INSERT / UPDATE /
                      DELETE ggf. langsamer
```

Deshalb gilt:

> [!important]  
> **Nicht jede Spalte indexieren – sondern die Spalten, nach denen häufig gesucht oder über die Tabellen verbunden werden.**

---

WHERE email = ?
```

Dann kann ein Index sinnvoll sein:

```sql
CREATE INDEX idx_kunde_email
ON kunde(email);
```

Wenn wir dagegen eine Tabelle mit nur zehn Kunden haben, bringt ein zusätzlicher Index kaum einen praktischen Vorteil.

---

# Merksatz

> Ein Index macht das **Suchen schneller**, benötigt aber zusätzlichen Speicher und kann das **Schreiben langsamer** machen.

Vereinfacht:

```text
                INDEX
                  │
        ┌─────────┴─────────┐
        ↓                   ↓
   SELECT schneller    INSERT / UPDATE /
                      DELETE ggf. langsamer
```

Deshalb gilt:

> [!important]  
> **Nicht jede Spalte indexieren – sondern die Spalten, nach denen häufig gesucht oder über die Tabellen verbunden werden.**

---

## Navigation

← [[21 ER-Modell & Datenmodelle]] | [[23 NoSQL]] →