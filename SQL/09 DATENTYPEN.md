## Was sind Datentypen?

Ein **Datentyp** legt fest, welche Art von Daten in einer Spalte gespeichert werden kann.

Beispiele:

```text
Alter       → Ganzzahl
Name        → Text
Preis       → Dezimalzahl
Geburtstag  → Datum
```

Beim Erstellen einer Tabelle geben wir deshalb für jede Spalte einen Datentyp an:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    level INTEGER
);
```

Hier gilt:

```text
id     → INTEGER
name   → VARCHAR(50)
level  → INTEGER
```

---

# INTEGER

`INTEGER` wird für **Ganzzahlen** verwendet.

Beispiele:

```text
1
15
100
-20
```

SQL:

```sql
level INTEGER
```

Typische Anwendungen:

```text
IDs
Alter
Anzahl
Level
Menge
```

Beispiel:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    level INTEGER
);
```

---

# VARCHAR

`VARCHAR` wird für **Text mit einer bestimmten maximalen Länge** verwendet.

```sql
name VARCHAR(50)
```

Die `50` bedeutet:

> Der Text darf maximal 50 Zeichen lang sein.

Beispiele:

```text
Pikachu
Max
Deutschland
Monster Hunter Wilds
```

Typische Anwendungen:

```text
Name
E-Mail
Adresse
Stadt
Titel
```

Beispiel:

```sql
first_name VARCHAR(50)
```

---

# TEXT

`TEXT` wird ebenfalls für Text verwendet.

```sql
beschreibung TEXT
```

`TEXT` eignet sich besonders für längere Texte.

Zum Beispiel:

```text
Beschreibung
Kommentar
Nachricht
Notiz
```

Beispiel:

```sql
CREATE TABLE Filme (
    id INTEGER PRIMARY KEY,
    titel VARCHAR(100),
    beschreibung TEXT
);
```

---

# VARCHAR oder TEXT?

Beide speichern Text.

```sql
name VARCHAR(50)
```

ist sinnvoll, wenn die Länge begrenzt werden soll.

```sql
beschreibung TEXT
```

ist sinnvoll für längere Texte.

### Merksatz

> `VARCHAR` → eher kurze Texte

> `TEXT` → längere Texte

Die genaue Behandlung von `VARCHAR` und `TEXT` kann sich je nach Datenbanksystem unterscheiden.

---

# DECIMAL

`DECIMAL` wird für Dezimalzahlen verwendet, bei denen eine **genaue Speicherung wichtig ist**.

Besonders typisch:

> Geldbeträge

Beispiel:

```sql
preis DECIMAL(10,2)
```

Die beiden Zahlen bedeuten:

```text
DECIMAL(10,2)
         │  │
         │  └── 2 Nachkommastellen
         │
         └───── insgesamt maximal 10 Stellen
```

Zum Beispiel:

```text
69.99
1250.50
9.95
```

---

## Beispiel mit Preis

```sql
CREATE TABLE Spiele (
    id INTEGER PRIMARY KEY,
    titel VARCHAR(100),
    preis DECIMAL(10,2)
);
```

Einfügen:

```sql
INSERT INTO Spiele (id, titel, preis)
VALUES (1, 'Monster Hunter Wilds', 69.99);
```

---

# FLOAT und REAL

Je nach Datenbanksystem gibt es außerdem Datentypen wie:

```text
FLOAT
REAL
DOUBLE
```

Sie speichern **Gleitkommazahlen**.

Zum Beispiel:

```sql
temperatur REAL
```

Sie können jedoch Rundungsungenauigkeiten besitzen.

Deshalb sollte man für Geldbeträge normalerweise eher:

```sql
DECIMAL
```

verwenden.

### Merksatz

> Geld → `DECIMAL`

---

# DATE

`DATE` speichert ein **Datum**.

```sql
geburtsdatum DATE
```

Ein Datum wird häufig so dargestellt:

```text
2026-07-23
```

Also:

```text
Jahr-Monat-Tag
```

Beispiel:

```sql
CREATE TABLE Kunde (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    geburtsdatum DATE
);
```

---

# TIME

`TIME` wird für eine Uhrzeit verwendet.

```sql
startzeit TIME
```

Beispiel:

```text
14:30:00
```

---

# DATETIME / TIMESTAMP

Wenn Datum **und** Uhrzeit gespeichert werden sollen, gibt es je nach Datenbanksystem:

```text
DATETIME
```

oder:

```text
TIMESTAMP
```

Beispiel:

```text
2026-07-23 14:30:00
```

Typische Anwendung:

```text
Bestellung erstellt
Benutzer registriert
Nachricht gesendet
Rechnung erstellt
```

Zum Beispiel:

```sql
erstellt_am TIMESTAMP
```

---

# BOOLEAN

`BOOLEAN` steht für einen Wahrheitswert:

```text
TRUE
FALSE
```

Beispiel:

```sql
aktiv BOOLEAN
```

Oder:

```sql
bezahlt BOOLEAN
```

Ein Datensatz könnte also enthalten:

```text
bezahlt = TRUE
```

oder:

```text
bezahlt = FALSE
```

Je nach Datenbanksystem werden Boolean-Werte intern auch als Zahlen gespeichert:

```text
1 → TRUE
0 → FALSE
```

---

# CHAR

`CHAR` speichert Text mit einer **festen Länge**.

Beispiel:

```sql
land_code CHAR(2)
```

Mögliche Werte:

```text
DE
US
JP
FR
```

Das eignet sich gut, wenn ein Wert immer dieselbe Länge besitzt.

---

# NULL ist kein Datentyp

Wichtig:

```text
NULL
```

ist **kein Datentyp**.

`NULL` bedeutet:

> Es ist kein Wert vorhanden.

Beispiel:

| id | name | phone |
|---|---|---|
| 1 | Max | NULL |

Das bedeutet nicht:

```text
phone = 0
```

und auch nicht:

```text
phone = ''
```

sondern:

> Für `phone` ist kein Wert vorhanden.

---

# Telefonnummern sind kein INTEGER

Eine Telefonnummer besteht zwar aus Zahlen, sollte aber normalerweise als **Text** gespeichert werden.

Also eher:

```sql
phone VARCHAR(30)
```

und nicht:

```sql
phone INTEGER
```

Warum?

Telefonnummern können zum Beispiel enthalten:

```text
+49 821 123456
```

Außerdem wollen wir mit Telefonnummern normalerweise **nicht rechnen**.

### Gute Faustregel

> Nur weil etwas aus Ziffern besteht, muss es keine Zahl sein.

---

# Postleitzahlen sind ebenfalls Text

Eine deutsche Postleitzahl:

```text
01234
```

würde als Zahl möglicherweise zu:

```text
1234
```

werden.

Die führende `0` wäre verloren.

Deshalb:

```sql
postal_code VARCHAR(10)
```

statt:

```sql
postal_code INTEGER
```

---

# IDs

IDs werden sehr häufig als Ganzzahlen gespeichert:

```sql
customer_id INTEGER PRIMARY KEY
```

Beispiel:

```text
1
2
3
4
5
```

Mit diesen Zahlen wird aber normalerweise nicht gerechnet.

Sie dienen hauptsächlich dazu:

> Datensätze eindeutig zu identifizieren.

---

# Welchen Datentyp nehme ich?

| Daten | Typischer Datentyp |
|---|---|
| ID | `INTEGER` |
| Name | `VARCHAR` |
| Titel | `VARCHAR` |
| Beschreibung | `TEXT` |
| Alter | `INTEGER` |
| Level | `INTEGER` |
| Anzahl | `INTEGER` |
| Preis | `DECIMAL` |
| Datum | `DATE` |
| Uhrzeit | `TIME` |
| Datum + Uhrzeit | `TIMESTAMP` |
| Ja / Nein | `BOOLEAN` |
| Telefonnummer | `VARCHAR` |
| Postleitzahl | `VARCHAR` |
| Ländercode | `CHAR` |

---

# Beispiel einer Tabelle

```sql
CREATE TABLE Produkt (
    id INTEGER PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    beschreibung TEXT,
    preis DECIMAL(10,2),
    lagerbestand INTEGER,
    verfuegbar BOOLEAN,
    erstellt_am TIMESTAMP
);
```

Damit haben wir verschiedene Datentypen:

```text
id             → INTEGER
name           → VARCHAR
beschreibung   → TEXT
preis          → DECIMAL
lagerbestand   → INTEGER
verfuegbar     → BOOLEAN
erstellt_am    → TIMESTAMP
```

---

# Wichtig: Datenbanksysteme unterscheiden sich

Nicht jedes Datenbanksystem besitzt exakt dieselben Datentypen oder behandelt sie gleich.

Zum Beispiel unterscheiden sich:

```text
SQLite
MySQL
PostgreSQL
SQL Server
```

teilweise voneinander.

Die grundlegende Idee bleibt aber gleich:

> Jede Spalte bekommt einen Datentyp, der zu den gespeicherten Daten passt.

---

# Merksätze

> `INTEGER` → Ganzzahlen

> `VARCHAR` → kürzere Texte

> `TEXT` → längere Texte

> `DECIMAL` → genaue Dezimalzahlen, besonders Geld

> `DATE` → Datum

> `TIME` → Uhrzeit

> `TIMESTAMP` → Datum + Uhrzeit

> `BOOLEAN` → Wahr / Falsch

Und besonders wichtig:

> **Nicht alles, was aus Ziffern besteht, sollte als Zahl gespeichert werden.**

Telefonnummern und Postleitzahlen sind gute Beispiele dafür.

---

## Navigation

⬅️ [[08 CREATE TABLE|Zurück zu Kapitel 08 – CREATE TABLE]]

➡️ [[10 Primary Key und Foreign Key|Weiter zu Kapitel 10 – Primary Key und Foreign Key]]