## Warum brauchen wir Schlüssel?

In einer relationalen Datenbank bestehen Informationen meistens aus mehreren Tabellen.

Zum Beispiel:

```text
customer
invoice
invoice_line
```

Damit die Datenbank weiß, **welche Datensätze zusammengehören**, verwendet man Schlüssel.

Die beiden wichtigsten sind:

```text
PRIMARY KEY
FOREIGN KEY
```

---

# PRIMARY KEY

Ein `PRIMARY KEY` (Primärschlüssel) identifiziert einen Datensatz **eindeutig**.

Beispiel:

| customer_id | first_name | last_name |
|---|---|---|
| 1 | Max | Müller |
| 2 | Anna | Schmidt |
| 3 | Max | Müller |

Obwohl zwei Kunden denselben Namen haben, können wir sie durch ihre ID unterscheiden.

```text
customer_id = 1
customer_id = 3
```

sind zwei verschiedene Kunden.

---

## PRIMARY KEY erstellen

```sql
CREATE TABLE customer (
    customer_id INTEGER PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
```

Hier ist:

```text
customer_id
```

der Primärschlüssel.

---

# Eigenschaften eines Primary Keys

Ein Primary Key muss:

- eindeutig sein
- einen Datensatz identifizieren
- darf nicht `NULL` sein

Das bedeutet:

```text
customer_id
-----------
1
2
3
4
```

ist erlaubt.

Aber:

```text
1
2
2
3
```

❌ Die `2` kommt doppelt vor.

---

# Warum nicht den Namen als Primary Key?

Man könnte auf die Idee kommen:

```sql
name VARCHAR(50) PRIMARY KEY
```

Das ist meistens keine gute Idee.

Mehrere Personen können beispielsweise heißen:

```text
Max Müller
```

Eine ID ist deshalb besser:

```text
1 → Max Müller
2 → Max Müller
```

Die Namen sind gleich, die IDs aber eindeutig.

---

# FOREIGN KEY

Ein `FOREIGN KEY` (Fremdschlüssel) stellt eine **Verbindung zu einer anderen Tabelle** her.

Beispiel:

Wir haben zwei Tabellen:

```text
customer
invoice
```

Ein Kunde kann mehrere Rechnungen besitzen.

Die Tabelle `customer`:

| customer_id | first_name |
|---|---|
| 1 | Max |
| 2 | Anna |

Die Tabelle `invoice`:

| invoice_id | customer_id | total |
|---|---|---|
| 100 | 1 | 25.99 |
| 101 | 1 | 15.50 |
| 102 | 2 | 40.00 |

In `invoice` ist:

```text
customer_id
```

ein Foreign Key.

---

# Verbindung zwischen den Tabellen

Die Verbindung sieht so aus:

```text
customer
----------------
customer_id (PK)
first_name
      │
      │
      │
      ▼
invoice
----------------
invoice_id  (PK)
customer_id (FK)
total
```

Der Foreign Key:

```text
invoice.customer_id
```

verweist auf:

```text
customer.customer_id
```

---

# FOREIGN KEY erstellen

```sql
CREATE TABLE customer (
    customer_id INTEGER PRIMARY KEY,
    first_name VARCHAR(50)
);
```

Danach:

```sql
CREATE TABLE invoice (
    invoice_id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    total DECIMAL(10,2),

    FOREIGN KEY (customer_id)
        REFERENCES customer(customer_id)
);
```

Der wichtige Teil ist:

```sql
FOREIGN KEY (customer_id)
REFERENCES customer(customer_id)
```

---

# Wie liest man einen Foreign Key?

Nehmen wir:

```sql
FOREIGN KEY (customer_id)
REFERENCES customer(customer_id)
```

Das kann man lesen als:

> Die Spalte `customer_id` dieser Tabelle verweist auf die Spalte `customer_id` der Tabelle `customer`.

Oder bildlich:

```text
invoice.customer_id
        │
        ▼
customer.customer_id
```

---

# PK und FK erkennen

Bei:

```text
customer
----------------
customer_id PK
first_name
last_name
```

ist:

```text
customer_id
```

der Primary Key.

Bei:

```text
invoice
----------------
invoice_id  PK
customer_id FK
total
```

ist:

```text
invoice_id
```

der Primary Key und:

```text
customer_id
```

der Foreign Key.

---

# Eine Tabelle kann mehrere Schlüssel besitzen

Eine Tabelle hat normalerweise einen Primary Key, kann aber mehrere Foreign Keys besitzen.

Beispiel:

```text
bestellung
----------------
bestellung_id PK
customer_id   FK
produkt_id    FK
```

Hier verweist:

```text
customer_id
```

auf einen Kunden und:

```text
produkt_id
```

auf ein Produkt.

---

# Foreign Key und 1:n

Primary Keys und Foreign Keys werden häufig für **1:n-Beziehungen** verwendet.

Beispiel:

```text
Trainer 1 ───── n Pokemon
```

Ein Trainer kann mehrere Pokémon besitzen.

Die Tabellen:

```text
Trainer
----------------
trainer_id PK
name
```

und:

```text
Pokemon
----------------
pokemon_id PK
name
trainer_id FK
```

Der Foreign Key liegt auf der **n-Seite**.

### Merksatz

> Bei einer 1:n-Beziehung liegt der Foreign Key normalerweise auf der n-Seite.

---

# Beispiel

Trainer:

| trainer_id | name |
|---|---|
| 1 | Ash |
| 2 | Misty |

Pokémon:

| pokemon_id | name | trainer_id |
|---|---|---|
| 1 | Pikachu | 1 |
| 2 | Glurak | 1 |
| 3 | Starmie | 2 |

Wir sehen:

```text
Ash
trainer_id = 1
```

kommt bei mehreren Pokémon vor.

```text
Pikachu → trainer_id 1
Glurak  → trainer_id 1
```

Damit gehören beide Pokémon zu Ash.

---

# Primary Key darf nicht doppelt sein

In `Trainer`:

```text
trainer_id
----------
1
2
3
```

Jede ID ist eindeutig.

Der Primary Key darf nicht doppelt vorkommen.

---

# Foreign Key darf mehrfach vorkommen

In `Pokemon`:

```text
trainer_id
----------
1
1
1
2
2
```

Das ist völlig in Ordnung.

Warum?

Weil ein Trainer mehrere Pokémon besitzen kann.

### Wichtig

> Primary Key → eindeutig

> Foreign Key → darf mehrfach vorkommen

---

# Foreign Key und ungültige Werte

Angenommen, unsere Trainer sind:

```text
trainer_id
----------
1
2
3
```

Dann versuchen wir:

```sql
INSERT INTO Pokemon (pokemon_id, name, trainer_id)
VALUES (1, 'Pikachu', 99);
```

Wenn der Foreign Key korrekt eingerichtet und geprüft wird, kann die Datenbank das verhindern.

Warum?

Es gibt keinen Trainer:

```text
trainer_id = 99
```

Der Foreign Key schützt damit die **Datenintegrität**.

---

# Foreign Keys und DELETE

Foreign Keys werden besonders wichtig, wenn Daten gelöscht werden.

Wir haben:

```text
customer
   │
   ▼
invoice
   │
   ▼
invoice_line
```

Eine `invoice_line` gehört zu einer `invoice`.

Eine `invoice` gehört zu einem `customer`.

---

## Beispiel

```text
customer
customer_id = 5
      │
      ▼
invoice
invoice_id = 10
      │
      ▼
invoice_line
invoice_id = 10
```

Wenn wir direkt versuchen:

```sql
DELETE FROM customer
WHERE customer_id = 5;
```

kann die Datenbank das Löschen verhindern.

Denn es existiert noch eine Rechnung, die auf diesen Kunden verweist.

---

# Richtige Löschreihenfolge

Bei solchen Beziehungen müssen wir häufig **von unten nach oben** löschen.

```text
customer
   ↓
invoice
   ↓
invoice_line
```

Löschreihenfolge:

```text
1. invoice_line
2. invoice
3. customer
```

Also zuerst die Datensätze, die am stärksten abhängig sind.

---

# ON DELETE CASCADE

Es gibt auch die Möglichkeit:

```sql
ON DELETE CASCADE
```

Beispiel:

```sql
FOREIGN KEY (customer_id)
REFERENCES customer(customer_id)
ON DELETE CASCADE
```

Damit kann die Datenbank abhängige Datensätze automatisch mitlöschen.

⚠️ Das sollte bewusst eingesetzt werden, da dadurch mehrere Datensätze automatisch gelöscht werden können.

---

# PRIMARY KEY vs FOREIGN KEY

| PRIMARY KEY | FOREIGN KEY |
|---|---|
| Primärschlüssel | Fremdschlüssel |
| Identifiziert Datensatz | Verbindet Tabellen |
| Eindeutig | Darf mehrfach vorkommen |
| Nicht `NULL` | Kann je nach Definition `NULL` sein |
| Gehört zur eigenen Tabelle | Verweist auf andere Tabelle |

---

# Komplettes Beispiel

```sql
CREATE TABLE Trainer (
    trainer_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL
);

CREATE TABLE Pokemon (
    pokemon_id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    trainer_id INTEGER,

    FOREIGN KEY (trainer_id)
        REFERENCES Trainer(trainer_id)
);
```

Die Beziehung:

```text
Trainer
----------------
trainer_id PK
name
     │
     │ 1
     │
     │
     │ n
     ▼
Pokemon
----------------
pokemon_id PK
name
trainer_id FK
```

---

# So kannst du es dir merken

Der **Primary Key** sagt:

> Wer bin ich?

```text
Pokemon.pokemon_id
```

Der **Foreign Key** sagt:

> Zu wem gehöre ich?

```text
Pokemon.trainer_id
```

Beispiel:

```text
pokemon_id = 7
```

→ Ich bin Pokémon Nummer 7.

```text
trainer_id = 2
```

→ Ich gehöre Trainer Nummer 2.

---

# Merksätze

> **PRIMARY KEY = eindeutige ID eines Datensatzes**

> **FOREIGN KEY = Verbindung zu einer anderen Tabelle**

> Der Foreign Key verweist normalerweise auf den Primary Key einer anderen Tabelle.

Bei einer 1:n-Beziehung:

> **Der Foreign Key kommt auf die n-Seite.**

Und beim Löschen abhängiger Datensätze:

> **Von unten nach oben löschen.**

---

## Navigation

⬅️ [[09 Datentypen|Zurück zu Kapitel 09 – Datentypen]]

➡️ [[11 BEZIEHUNGEN|Weiter zu Kapitel 11 – Beziehungen 1 zu n und n zu m]]