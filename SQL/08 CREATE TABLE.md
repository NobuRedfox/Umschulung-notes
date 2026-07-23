## Was macht CREATE TABLE?

Mit `CREATE TABLE` wird eine **neue Tabelle in einer Datenbank erstellt**.

Dabei legen wir fest:

- Name der Tabelle
- Spalten
- Datentypen
- Primärschlüssel
- Regeln für die Daten
- eventuell Fremdschlüssel

Grundaufbau:

```sql
CREATE TABLE tabellenname (
    spalte1 DATENTYP,
    spalte2 DATENTYP,
    spalte3 DATENTYP
);
```

---

# Einfache Tabelle erstellen

Beispiel:

```sql
CREATE TABLE Pokemon (
    id INTEGER,
    name VARCHAR(50),
    typ VARCHAR(30),
    level INTEGER
);
```

Dadurch entsteht eine Tabelle mit vier Spalten:

| Spalte | Datentyp |
|---|---|
| id | INTEGER |
| name | VARCHAR(50) |
| typ | VARCHAR(30) |
| level | INTEGER |

---

# Datentypen

Jede Spalte bekommt einen Datentyp.

Zum Beispiel:

```sql
id INTEGER
```

bedeutet:

> `id` soll eine Ganzzahl enthalten.

Oder:

```sql
name VARCHAR(50)
```

bedeutet:

> `name` enthält Text mit einer maximalen Länge von 50 Zeichen.

Häufige Datentypen sind:

| Datentyp | Bedeutung |
|---|---|
| `INTEGER` | Ganzzahl |
| `VARCHAR(n)` | Text mit maximaler Länge |
| `TEXT` | Text |
| `DECIMAL(p,s)` | Dezimalzahl |
| `DATE` | Datum |
| `BOOLEAN` | Wahr/Falsch |

Datentypen behandeln wir im nächsten Kapitel noch genauer.

---

# PRIMARY KEY

Ein `PRIMARY KEY` identifiziert jeden Datensatz **eindeutig**.

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    typ VARCHAR(30),
    level INTEGER
);
```

Die `id` darf dadurch nicht doppelt vorkommen.

Beispiel:

```text
id | name
---|--------
1  | Pikachu
2  | Glurak
3  | Bisasam
```

Nicht erlaubt wäre:

```text
1 | Pikachu
1 | Glurak
```

weil die ID `1` bereits existiert.

### Merksatz

> `PRIMARY KEY` = eindeutige Identifikation eines Datensatzes.

---

# NOT NULL

Mit `NOT NULL` legen wir fest:

> Diese Spalte muss einen Wert besitzen.

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    level INTEGER
);
```

Das wäre erlaubt:

```text
Pikachu
```

Aber kein fehlender Name:

```text
NULL
```

---

# UNIQUE

Mit `UNIQUE` darf ein Wert nicht mehrfach vorkommen.

Zum Beispiel:

```sql
CREATE TABLE Benutzer (
    id INTEGER PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
```

Eine E-Mail-Adresse darf dadurch nicht zweimal gespeichert werden.

---

# DEFAULT

Mit `DEFAULT` können wir einen Standardwert festlegen.

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    level INTEGER DEFAULT 1
);
```

Wenn wir beim Einfügen kein Level angeben:

```sql
INSERT INTO Pokemon (id, name)
VALUES (1, 'Pikachu');
```

bekommt Pikachu automatisch:

```text
level = 1
```

---

# CHECK

Mit `CHECK` können wir festlegen, welche Werte erlaubt sind.

Beispiel:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    level INTEGER CHECK (level >= 1)
);
```

Jetzt darf das Level nicht kleiner als `1` sein.

Erlaubt:

```text
level = 5
```

Nicht erlaubt:

```text
level = -10
```

---

## CHECK mit Bereich

Wir können auch mehrere Bedingungen verwenden:

```sql
level INTEGER CHECK (level >= 1 AND level <= 100)
```

Damit muss das Level zwischen `1` und `100` liegen.

Oder kürzer:

```sql
level INTEGER CHECK (level BETWEEN 1 AND 100)
```

---

# FOREIGN KEY

Mit einem `FOREIGN KEY` können Tabellen miteinander verbunden werden.

Beispiel:

```text
Trainer
   │
   │ 1:n
   ▼
Pokemon
```

Ein Trainer kann mehrere Pokémon besitzen.

Zuerst erstellen wir `Trainer`:

```sql
CREATE TABLE Trainer (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);
```

Danach `Pokemon`:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    trainer_id INTEGER,
    FOREIGN KEY (trainer_id)
        REFERENCES Trainer(id)
);
```

Die Spalte:

```text
trainer_id
```

enthält die ID eines Trainers.

---

# PRIMARY KEY und FOREIGN KEY

Das ist ein sehr wichtiges Prinzip:

```text
Trainer

id (PK)
│
│
└──────────────┐
               │
               ▼
Pokemon

id (PK)
trainer_id (FK)
```

`Trainer.id` ist der:

```text
PRIMARY KEY
```

`Pokemon.trainer_id` ist der:

```text
FOREIGN KEY
```

Der Foreign Key verweist auf den Primary Key der anderen Tabelle.

---

# Tabelle mit mehreren Regeln

Die Regeln können miteinander kombiniert werden.

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    typ VARCHAR(30),
    level INTEGER DEFAULT 1 CHECK (level BETWEEN 1 AND 100),
    trainer_id INTEGER,
    
    FOREIGN KEY (trainer_id)
        REFERENCES Trainer(id)
);
```

Hier haben wir bereits:

```text
PRIMARY KEY
NOT NULL
DEFAULT
CHECK
FOREIGN KEY
```

---

# CONSTRAINT

Regeln wie `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE` und `CHECK` bezeichnet man allgemein als:

> **Constraints**

Constraints sind Regeln, die bestimmen, welche Daten in einer Tabelle erlaubt sind.

Beispiele:

```text
PRIMARY KEY
FOREIGN KEY
NOT NULL
UNIQUE
CHECK
DEFAULT
```

Constraints behandeln wir später noch einmal ausführlicher.

---

# CREATE TABLE IF NOT EXISTS

Je nach Datenbanksystem kann man schreiben:

```sql
CREATE TABLE IF NOT EXISTS Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50)
);
```

Das bedeutet:

> Erstelle die Tabelle nur, wenn sie noch nicht existiert.

Dadurch wird ein Fehler vermieden, wenn die Tabelle bereits vorhanden ist.

---

# Tabelle wieder löschen

Eine komplette Tabelle wird mit `DROP TABLE` gelöscht:

```sql
DROP TABLE Pokemon;
```

⚠️ Dabei werden die Tabelle **und ihre Daten** gelöscht.

Nicht verwechseln:

```sql
DELETE FROM Pokemon;
```

→ löscht die Datensätze

```sql
DROP TABLE Pokemon;
```

→ löscht die komplette Tabelle

---

# Reihenfolge bei verbundenen Tabellen

Wenn Tabellen über Foreign Keys verbunden sind, müssen wir auf die Reihenfolge achten.

Wenn `Pokemon` einen Foreign Key auf `Trainer` besitzt:

```text
Trainer
   ↑
   │
Pokemon
```

sollten wir zuerst erstellen:

```text
1. Trainer
2. Pokemon
```

Denn `Pokemon` verweist auf `Trainer`.

### Merksatz

> Erst die Tabelle erstellen, **auf die verwiesen wird**.

---

# Typische Fehler

## Komma vergessen

Falsch:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY
    name VARCHAR(50)
);
```

❌ Zwischen den Spalten fehlt ein Komma.

Richtig:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50)
);
```

---

## Komma nach letzter Zeile

Das hier kann je nach Datenbanksystem Probleme verursachen:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
);
```

Besser:

```sql
CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50)
);
```

---

## Foreign Key auf falsche Spalte

```sql
FOREIGN KEY (trainer_id)
REFERENCES Trainer(id)
```

Dabei gilt:

```text
trainer_id
     ↓
Spalte in der aktuellen Tabelle

Trainer
     ↓
andere Tabelle

id
     ↓
Spalte der anderen Tabelle
```

---

# Komplettes Beispiel

```sql
CREATE TABLE Trainer (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE
);

CREATE TABLE Pokemon (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    typ VARCHAR(30),
    level INTEGER DEFAULT 1 CHECK (level BETWEEN 1 AND 100),
    trainer_id INTEGER,

    FOREIGN KEY (trainer_id)
        REFERENCES Trainer(id)
);
```

Damit haben wir zwei miteinander verbundene Tabellen.

---

# Merksätze

> `CREATE TABLE` = neue Tabelle erstellen

> Jede Spalte braucht einen Namen und normalerweise einen Datentyp.

> `PRIMARY KEY` = Datensatz eindeutig identifizieren

> `FOREIGN KEY` = Verbindung zu einer anderen Tabelle

> `NOT NULL` = Wert darf nicht fehlen

> `UNIQUE` = Wert darf nicht doppelt vorkommen

> `DEFAULT` = Standardwert

> `CHECK` = zusätzliche Bedingung für erlaubte Werte

Und ganz wichtig bei Beziehungen:

> **Der Foreign Key verweist normalerweise auf den Primary Key einer anderen Tabelle.**

---

## Navigation

⬅️ [[07 DELETE|Zurück zu Kapitel 07 – DELETE]]

➡️ [[09 Datentypen|Weiter zu Kapitel 09 – Datentypen]]