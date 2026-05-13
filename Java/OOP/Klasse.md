
>[!info]
>## Erklärung
>
>Eine Klasse ist ein **Bauplan** für Objekte.
>
>Sie beschreibt:
> - welche **Daten** ein Objekt besitzt (**Attribute**)
> - was ein Objekt tun kann (**Methoden**)

---

# Beispiel (Spiel)

Stell dir ein Spiel vor:

Ein Spieler hat:
- einen Namen
- Leben

Genau das beschreibst du in einer Klasse:

```java
public class Spieler {
    String name;
    int leben;
}
```

## Erklärung Code

- `public class Spieler`
  → erstellt eine neue Klasse namens `Spieler`

- `String name`
  → speichert den Namen des Spielers

- `int leben`
  → speichert die Lebenspunkte des Spielers

Das nennt man **Attribute**.

---

# Was ist das Ergebnis?

Die Klasse selbst ist noch **kein echtes Objekt**.

Sie ist nur der Bauplan.

Erst durch das Erstellen eines Objekts wird sie genutzt:

```java
Spieler s1 = new Spieler();
```

Jetzt existiert ein echter Spieler im Programm.

---

# Merksatz

- Klasse = Bauplan
- Objekt = konkrete Instanz der Klasse

---

# Häufige Anfängerfehler

- ❌ Klasse und Objekt verwechseln
- ❌ denken, dass eine Klasse bereits ein fertiges Objekt ist
- ❌ Attribute und Methoden verwechseln

---

# Praxisbezug

Klassen verwendet man z. B. für:
- Spieler
- Gegner
- Autos
- Benutzerkonten
- Tiere
- Waffen

In der OOP wird fast alles als Objekt dargestellt.

---

# 🔗 Verbindungen

- [[Objekte]]
- [[Attribute]]
- [[Methoden]]