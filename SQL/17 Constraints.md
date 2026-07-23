## Was sind Constraints?

**Constraints** sind Regeln für Spalten und Tabellen.

Sie sorgen dafür, dass nur **gültige und sinnvolle Daten** in der Datenbank gespeichert werden können.

Beispiel:

Ein Pokémon-Level soll nur zwischen `1` und `100` liegen.

```sql
level INTEGER CHECK (level BETWEEN 1 AND 100)
```

Die Datenbank verhindert dadurch beispielsweise:

```text
Level -5   ❌
Level 200  ❌
```

---

# Warum brauchen wir Constraints?

Ohne Constraints könnte eine Datenbank unsinnige Daten enthalten.

Zum Beispiel:

```text
Kunde ohne Namen
doppelte Benutzer-ID
negative Preise
Pokémon Level -20
Rechnung für einen Kunden, der nicht existiert
```

Constraints helfen dabei, solche Fehler direkt auf Datenbankebene zu verhindern.

---

# Die wichtigsten Constraints

| Constraint | Aufgabe |
|---|---|
| `PRIMARY KEY` | Datensatz eindeutig identifizieren |
| `FOREIGN KEY` | Beziehung zwischen Tabellen absichern |
| `NOT NULL` | Wert muss vorhanden sein |
| `UNIQUE` | Wert darf nicht doppelt vorkommen |
| `CHECK` | Wert muss eine Bedingung erfüllen |
| `DEFAULT` | Standardwert festlegen |

---

# NOT NULL

`NOT NULL` bedeutet:

> Diese Spalte muss einen Wert enthalten.

Beispiel:

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);
```

Das ist erlaubt:

```sql
INSERT INTO Pokemon (pokemon_id, name)
VALUES (1, 'Pikachu');
```

Das nicht:

```sql
INSERT INTO Pokemon (pokemon_id, name)
VALUES (2, NULL);
```

❌ Der Name darf nicht fehlen.

---

# UNIQUE

`UNIQUE` verhindert doppelte Werte.

Beispiel:

```sql
CREATE TABLE Benutzer (
    benutzer_id INTEGER PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
```

Angenommen:

```text
max@example.com
```

existiert bereits.

Dann darf nicht noch einmal dieselbe E-Mail-Adresse gespeichert werden.

---

## Beispiel

```sql
INSERT INTO Benutzer (benutzer_id, email)
VALUES (1, 'max@example.com');
```

Danach:

```sql
INSERT INTO Benutzer (benutzer_id, email)
VALUES (2, 'max@example.com');
```

❌ `UNIQUE` verhindert den zweiten Eintrag.

---

# PRIMARY KEY

Der `PRIMARY KEY` identifiziert jeden Datensatz eindeutig.

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50)
);
```

Erlaubt:

```text
pokemon_id
----------
1
2
3
```

Nicht erlaubt:

```text
1
2
2  ❌
```

Ein Primary Key darf nicht doppelt vorkommen.

---

# PRIMARY KEY beinhaltet Eindeutigkeit

Ein Primary Key ist grundsätzlich:

```text
eindeutig
+
nicht NULL
```

Man muss deshalb nicht zusätzlich schreiben:

```sql
pokemon_id INTEGER PRIMARY KEY UNIQUE NOT NULL
```

Normalerweise reicht:

```sql
pokemon_id INTEGER PRIMARY KEY
```

---

# FOREIGN KEY

Ein `FOREIGN KEY` stellt sicher, dass eine Beziehung zu einem gültigen Datensatz besteht.

Beispiel:

```text
Trainer
   │
   │ 1:n
   ▼
Pokemon
```

```sql
CREATE TABLE Trainer (
    trainer_id INTEGER PRIMARY KEY,
    name VARCHAR(50)
);

CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    trainer_id INTEGER,

    FOREIGN KEY (trainer_id)
        REFERENCES Trainer(trainer_id)
);
```

---

## Was verhindert der Foreign Key?

Angenommen, es gibt nur:

```text
trainer_id
----------
1
2
3
```

Dann versuchen wir:

```sql
INSERT INTO Pokemon (
    pokemon_id,
    name,
    trainer_id
)
VALUES (
    1,
    'Pikachu',
    99
);
```

❌ Trainer `99` existiert nicht.

Der Foreign Key kann verhindern, dass diese ungültige Beziehung gespeichert wird.

---

# CHECK

Mit `CHECK` können wir eigene Bedingungen definieren.

Beispiel:

```sql
level INTEGER CHECK (level >= 1)
```

Damit darf das Level nicht kleiner als `1` sein.

---

## CHECK mit mehreren Bedingungen

```sql
level INTEGER
CHECK (level >= 1 AND level <= 100)
```

Oder:

```sql
level INTEGER
CHECK (level BETWEEN 1 AND 100)
```

Damit gilt:

```text
1   ✅
50  ✅
100 ✅

0   ❌
101 ❌
-5  ❌
```

---

# CHECK mit Text

`CHECK` funktioniert nicht nur mit Zahlen.

Beispiel:

```sql
status VARCHAR(20)
CHECK (status IN ('offen', 'bezahlt', 'storniert'))
```

Jetzt sind nur diese Werte erlaubt:

```text
offen
bezahlt
storniert
```

Das hier wäre nicht erlaubt:

```text
irgendwas
```

---

# CHECK mit mehreren Spalten

Ein `CHECK` kann auch mehrere Spalten miteinander vergleichen.

Beispiel:

```sql
CREATE TABLE Veranstaltung (
    id INTEGER PRIMARY KEY,
    startdatum DATE,
    enddatum DATE,

    CHECK (enddatum >= startdatum)
);
```

Damit verhindern wir beispielsweise:

```text
Start: 20.07.2026
Ende:  10.07.2026
```

❌ Die Veranstaltung kann nicht enden, bevor sie begonnen hat.

---

# DEFAULT

Mit `DEFAULT` legen wir einen Standardwert fest.

Beispiel:

```sql
level INTEGER DEFAULT 1
```

Wenn wir schreiben:

```sql
INSERT INTO Pokemon (pokemon_id, name)
VALUES (1, 'Pikachu');
```

wird automatisch verwendet:

```text
level = 1
```

---

## DEFAULT mit BOOLEAN

Beispiel:

```sql
aktiv BOOLEAN DEFAULT TRUE
```

Ein neuer Benutzer ist dadurch standardmäßig aktiv.

---

# Mehrere Constraints kombinieren

Eine Spalte kann mehrere Regeln besitzen.

```sql
name VARCHAR(50) NOT NULL
```

Oder:

```sql
email VARCHAR(100) NOT NULL UNIQUE
```

Oder:

```sql
level INTEGER
    NOT NULL
    DEFAULT 1
    CHECK (level BETWEEN 1 AND 100)
```

Damit gilt:

```text
level muss vorhanden sein
level ist standardmäßig 1
level muss zwischen 1 und 100 liegen
```

---

# Constraint direkt an der Spalte

Ein Constraint kann direkt bei der Spalte stehen:

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    level INTEGER CHECK (level BETWEEN 1 AND 100)
);
```

Das nennt man vereinfacht einen:

> **Spalten-Constraint**

---

# Constraint auf Tabellenebene

Constraints können auch separat innerhalb der Tabelle definiert werden.

Beispiel:

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER,
    name VARCHAR(50),

    PRIMARY KEY (pokemon_id)
);
```

Hier steht `PRIMARY KEY` nicht direkt hinter der Spalte.

---

# Zusammengesetzter PRIMARY KEY

Das brauchen wir besonders bei n:m-Beziehungen.

Beispiel:

```text
Student
   ↓
Student_Kurs
   ↑
Kurs
```

Die Zwischentabelle:

```sql
CREATE TABLE Student_Kurs (
    student_id INTEGER,
    kurs_id INTEGER,

    PRIMARY KEY (student_id, kurs_id),

    FOREIGN KEY (student_id)
        REFERENCES Student(student_id),

    FOREIGN KEY (kurs_id)
        REFERENCES Kurs(kurs_id)
);
```

Der Primary Key besteht hier aus:

```text
student_id
+
kurs_id
```

Die Kombination muss eindeutig sein.

---

# Benannte Constraints

Constraints können auch einen eigenen Namen bekommen.

Dafür gibt es das Schlüsselwort:

```sql
CONSTRAINT
```

Beispiel:

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    level INTEGER,

    CONSTRAINT chk_pokemon_level
        CHECK (level BETWEEN 1 AND 100)
);
```

Der Name:

```text
chk_pokemon_level
```

hilft dabei, die Regel später leichter zu erkennen.

---

# Beispiel mit FOREIGN KEY

Auch Foreign Keys können benannt werden:

```sql
CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    trainer_id INTEGER,

    CONSTRAINT fk_pokemon_trainer
        FOREIGN KEY (trainer_id)
        REFERENCES Trainer(trainer_id)
);
```

Hier bedeutet:

```text
fk
↓
Foreign Key

pokemon_trainer
↓
beschreibt die Beziehung
```

---

# ON DELETE

Bei Foreign Keys können Regeln dafür festgelegt werden, was beim Löschen passiert.

Beispiel:

```sql
FOREIGN KEY (trainer_id)
REFERENCES Trainer(trainer_id)
ON DELETE CASCADE
```

---

# ON DELETE CASCADE

`CASCADE` bedeutet vereinfacht:

> Wird der übergeordnete Datensatz gelöscht, werden abhängige Datensätze automatisch mitgelöscht.

Beispiel:

```text
Trainer Ash
├── Pikachu
├── Glurak
└── Bisasam
```

Wenn Ash gelöscht wird, könnten durch:

```sql
ON DELETE CASCADE
```

auch seine zugehörigen Pokémon-Datensätze automatisch gelöscht werden.

⚠️ Deshalb sollte `CASCADE` bewusst eingesetzt werden.

---

# ON DELETE SET NULL

Eine andere Möglichkeit ist:

```sql
ON DELETE SET NULL
```

Beispiel:

```sql
FOREIGN KEY (trainer_id)
REFERENCES Trainer(trainer_id)
ON DELETE SET NULL
```

Wird der Trainer gelöscht, bleiben die Pokémon bestehen.

Aus:

```text
Pikachu → trainer_id = 1
```

wird:

```text
Pikachu → trainer_id = NULL
```

Dafür muss die Spalte natürlich `NULL` erlauben.

---

# ON DELETE RESTRICT

Je nach Datenbanksystem gibt es auch:

```sql
ON DELETE RESTRICT
```

Das bedeutet:

> Der übergeordnete Datensatz darf nicht gelöscht werden, solange abhängige Datensätze existieren.

Beispiel:

```text
customer
   ↓
invoice
```

Solange Rechnungen vorhanden sind, kann das Löschen des Kunden verhindert werden.

---

# Komplettes Beispiel

```sql
CREATE TABLE Trainer (
    trainer_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);

CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,

    name VARCHAR(50)
        NOT NULL,

    level INTEGER
        NOT NULL
        DEFAULT 1
        CHECK (level BETWEEN 1 AND 100),

    trainer_id INTEGER,

    FOREIGN KEY (trainer_id)
        REFERENCES Trainer(trainer_id)
        ON DELETE SET NULL
);
```

Damit haben wir:

```text
PRIMARY KEY
NOT NULL
UNIQUE
DEFAULT
CHECK
FOREIGN KEY
```

in einem Beispiel.

---

# Constraints und Datenintegrität

Das eigentliche Ziel von Constraints ist:

> **Datenintegrität**

Das bedeutet vereinfacht:

> Die Datenbank soll nur Daten enthalten, die ihren festgelegten Regeln entsprechen.

Beispiele:

```text
Keine doppelte ID
Keine ungültige Beziehung
Kein fehlender Pflichtwert
Kein Level -20
Keine doppelte E-Mail-Adresse
```

Die Datenbank selbst schützt dadurch ihre Daten.

---

# Typische Aufgaben erkennen

Steht in einer Aufgabe:

> darf nicht leer sein

denke an:

```sql
NOT NULL
```

---

> darf nur einmal vorkommen

```sql
UNIQUE
```

---

> eindeutig identifizieren

```sql
PRIMARY KEY
```

---

> verweist auf eine andere Tabelle

```sql
FOREIGN KEY
```

---

> muss zwischen X und Y liegen

```sql
CHECK
```

---

> soll standardmäßig den Wert X besitzen

```sql
DEFAULT
```

---

# Übersicht

| Anforderung | Constraint |
|---|---|
| Pflichtfeld | `NOT NULL` |
| Eindeutiger Wert | `UNIQUE` |
| Eindeutige ID | `PRIMARY KEY` |
| Tabellen verbinden | `FOREIGN KEY` |
| Bedingung prüfen | `CHECK` |
| Standardwert | `DEFAULT` |

---

# Merksätze

> **Constraints = Regeln für unsere Daten.**

Die wichtigsten:

```text
PRIMARY KEY → eindeutige Identifikation

FOREIGN KEY → gültige Beziehung

NOT NULL    → Wert muss vorhanden sein

UNIQUE      → keine doppelten Werte

CHECK       → Wert muss Bedingung erfüllen

DEFAULT     → Standardwert
```

Und der Sinn dahinter:

> **Nicht erst im Programm hoffen, dass richtige Daten gespeichert werden – die Datenbank selbst kann Regeln durchsetzen.**

---

## Navigation

⬅️ [[16 NULL|Zurück zu Kapitel 16 – NULL]]

➡️ [[18 Normalformen|Weiter zu Kapitel 18 – Normalformen]]