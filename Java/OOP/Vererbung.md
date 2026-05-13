
>[!info]
>## Erklärung
>
>Vererbung bedeutet, dass eine Klasse Eigenschaften und Methoden einer anderen Klasse übernimmt.

---

# Definition

Mit Vererbung kann eine Klasse auf einer anderen Klasse aufbauen.

Die neue Klasse übernimmt:
- Attribute
- Methoden

der bestehenden Klasse.

---

# Grundidee

Beispiel:

- `Tier` → allgemeine Klasse
- `Hund` → spezielle Klasse

Ein Hund ist ein Tier und übernimmt daher Eigenschaften des Tiers.

---

# Beispiel

```java
public class Tier {

    String name;

    public void essen() {
        System.out.println("Das Tier frisst.");
    }
}
```

```java
public class Hund extends Tier {

    public void bellen() {
        System.out.println("Wuff!");
    }
}
```

---

# Erklärung Code

- `extends Tier`
  → `Hund` erbt von `Tier`

Die Klasse `Hund` besitzt jetzt:
- `name`
- `essen()`
- `bellen()`

---

# Objekt verwenden

```java
Hund h1 = new Hund();

h1.name = "Bello";

h1.essen();
h1.bellen();
```

Das Objekt kann:
- geerbte Methoden nutzen
- eigene Methoden nutzen

---

# Vorteile

Vererbung sorgt für:
- weniger doppelten Code
- bessere Struktur
- Wiederverwendbarkeit

---

# Oberklasse und Unterklasse

## Oberklasse
Die allgemeine Klasse.

Beispiel:
```java
Tier
```

## Unterklasse
Die spezialisierte Klasse.

Beispiel:
```java
Hund
```

---

# Überschreiben von Methoden

Methoden können in der Unterklasse angepasst werden.

```java
@Override
public void essen() {
    System.out.println("Der Hund frisst.");
}
```

Das nennt man:
- Methoden überschreiben
- Override

---

# Merksatz

- Vererbung = Eigenschaften und Methoden übernehmen

---

# Häufige Anfängerfehler

- ❌ denken, dass alles automatisch kopiert wird
- ❌ `extends` vergessen
- ❌ Oberklasse und Unterklasse verwechseln

---

# Praxisbezug

Vererbung nutzt man z. B. für:
- Tiere → Hund, Katze
- Fahrzeuge → Auto, Motorrad
- Gegner → Bossgegner

---

# 🔗 Verbindungen

- [[OOP]]
- [[Klasse]]
- [[Objekte]]
- [[Methoden]]
- [[Polymorphie]]