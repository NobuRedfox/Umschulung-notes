## Was macht UPDATE?

Mit `UPDATE` werden **bereits vorhandene Datensätze verändert**.

Grundaufbau:

```sql
UPDATE tabelle
SET spalte = neuer_wert
WHERE bedingung;
```

Beispiel:

```sql
UPDATE customer
SET first_name = 'Max'
WHERE customer_id = 1;
```

Dadurch wird der Vorname des Kunden mit der ID `1` geändert.

---

# UPDATE und SET

Mit `UPDATE` bestimmen wir zunächst die Tabelle:

```sql
UPDATE customer
```

Mit `SET` bestimmen wir anschließend:

> Welche Spalte soll welchen neuen Wert bekommen?

```sql
SET first_name = 'Max'
```

Zusammen:

```sql
UPDATE customer
SET first_name = 'Max';
```

⚠️ Hier fehlt allerdings noch `WHERE`!

---

# WHERE bei UPDATE

Mit `WHERE` bestimmen wir, **welche Datensätze geändert werden sollen**.

```sql
UPDATE customer
SET first_name = 'Max'
WHERE customer_id = 1;
```

Nur der Kunde mit:

```text
customer_id = 1
```

wird verändert.

---

# ⚠️ UPDATE ohne WHERE

Bei `UPDATE` muss man besonders aufpassen.

```sql
UPDATE customer
SET country = 'Germany';
```

Das bedeutet:

> Setze bei **ALLEN Kunden** das Land auf Germany.

Die komplette Spalte wird verändert.

Deshalb vor einem `UPDATE` immer überlegen:

> Brauche ich ein `WHERE`?

---

# Erst SELECT, dann UPDATE

Bei wichtigen Änderungen kann man zuerst mit `SELECT` prüfen, welche Datensätze betroffen wären.

Zum Beispiel möchten wir:

```sql
UPDATE customer
SET country = 'Germany'
WHERE city = 'Berlin';
```

Vorher testen:

```sql
SELECT *
FROM customer
WHERE city = 'Berlin';
```

Wenn genau die gewünschten Datensätze erscheinen, können wir anschließend das `UPDATE` durchführen.

### Merksatz

> Unsicher bei `UPDATE`?  
> Erst mit `SELECT` prüfen, was dein `WHERE` findet.

---

# Mehrere Spalten verändern

Mit einem `UPDATE` können mehrere Spalten gleichzeitig geändert werden.

```sql
UPDATE customer
SET
    first_name = 'Max',
    last_name = 'Müller'
WHERE customer_id = 1;
```

Die einzelnen Änderungen werden mit einem Komma getrennt.

---

# Beispiel mit Pokémon

Angenommen Pikachu steigt ein Level auf:

```sql
UPDATE Pokemon
SET level = 16
WHERE name = 'Pikachu';
```

---

# Mit dem alten Wert rechnen

Bei `UPDATE` können wir den bisherigen Wert verwenden.

Pikachu soll ein Level dazubekommen:

```sql
UPDATE Pokemon
SET level = level + 1
WHERE name = 'Pikachu';
```

Angenommen:

```text
level = 15
```

Dann passiert:

```text
15 + 1 = 16
```

Der neue Wert ist:

```text
level = 16
```

---

# Mehrere Werte berechnen

Zum Beispiel Level und KP erhöhen:

```sql
UPDATE Pokemon
SET
    level = level + 1,
    kp = kp + 10
WHERE name = 'Pikachu';
```

---

# Mehrere Datensätze verändern

`WHERE` muss nicht nur einen Datensatz auswählen.

```sql
UPDATE Pokemon
SET level = level + 1
WHERE typ = 'Feuer';
```

Jetzt bekommen **alle Feuer-Pokémon** ein Level dazu.

Das ist völlig in Ordnung, wenn genau das gewollt ist.

---

# UPDATE mit AND

Auch mehrere Bedingungen sind möglich:

```sql
UPDATE Pokemon
SET level = level + 1
WHERE typ = 'Feuer'
AND level < 50;
```

Geändert werden nur Pokémon, die:

```text
Typ = Feuer
UND
Level < 50
```

erfüllen.

---

# UPDATE mit IN

Auch `IN` kann verwendet werden:

```sql
UPDATE Pokemon
SET level = level + 1
WHERE typ IN ('Feuer', 'Elektro');
```

→ Feuer- und Elektro-Pokémon bekommen ein Level dazu.

---

# Einen Wert auf NULL setzen

Wenn die Spalte `NULL` erlaubt:

```sql
UPDATE customer
SET phone = NULL
WHERE customer_id = 1;
```

Damit wird der vorhandene Wert entfernt bzw. auf **keinen Wert** gesetzt.

Wichtig:

```sql
NULL
```

wird nicht in Anführungszeichen geschrieben.

Also nicht:

```sql
SET phone = 'NULL'
```

Denn `'NULL'` wäre einfach der Text **NULL**.

---

# Typische Fehler

## WHERE vergessen

```sql
UPDATE Pokemon
SET level = 100;
```

❌ Alle Pokémon bekommen Level 100.

Wenn nur Pikachu gemeint ist:

```sql
UPDATE Pokemon
SET level = 100
WHERE name = 'Pikachu';
```

---

## Mehrere SET verwenden

Falsch:

```sql
UPDATE customer
SET first_name = 'Max'
SET last_name = 'Müller'
WHERE customer_id = 1;
```

❌

Richtig:

```sql
UPDATE customer
SET
    first_name = 'Max',
    last_name = 'Müller'
WHERE customer_id = 1;
```

Es gibt nur **ein `SET`**.

Mehrere Änderungen werden mit `,` getrennt.

---

## = bei SET und WHERE nicht verwechseln

```sql
UPDATE Pokemon
SET level = 20
WHERE name = 'Pikachu';
```

Hier haben die beiden Teile unterschiedliche Aufgaben:

```text
SET level = 20
        ↓
Was soll geändert werden?

WHERE name = 'Pikachu'
        ↓
Bei wem soll es geändert werden?
```

---

# Typischer Aufbau

```sql
UPDATE tabelle
SET spalte = neuer_wert
WHERE bedingung;
```

Mehrere Spalten:

```sql
UPDATE tabelle
SET
    spalte1 = wert1,
    spalte2 = wert2
WHERE bedingung;
```

---

# Merksätze

> `UPDATE` = vorhandene Daten verändern

> `SET` = Was soll geändert werden?

> `WHERE` = Welche Datensätze sollen geändert werden?

Besonders wichtig:

> ⚠️ **UPDATE ohne WHERE kann alle Datensätze verändern!**

Im Zweifel:

```sql
SELECT *
FROM tabelle
WHERE bedingung;
```

erst prüfen und danach:

```sql
UPDATE tabelle
SET ...
WHERE bedingung;
```

---

## Navigation

⬅️ [[05 INSERT|Zurück zu Kapitel 05 – INSERT]]

➡️ [[07 DELETE|Weiter zu Kapitel 07 – DELETE]]