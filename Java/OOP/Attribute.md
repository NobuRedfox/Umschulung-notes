
>[!info]
>## Erklärung
>
>Attribute sind die **Eigenschaften** eines Objekts.
>
>Sie speichern Daten innerhalb einer Klasse.

---

# Definition

Attribute beschreiben:
- was ein Objekt besitzt
- welche Daten gespeichert werden

Sie werden in einer Klasse definiert.

---

# Beispiel

```java
public class Spieler {
    String name;
    int leben;
}
```

Die Attribute sind:
- `name`
- `leben`

---

# Erklärung Code

- `String name`
  → speichert den Namen des Spielers

- `int leben`
  → speichert die Lebenspunkte

---

# Was machen Attribute?

Attribute speichern Informationen über ein Objekt.

Beispiel:

Ein Spieler besitzt:
- einen Namen
- Lebenspunkte
- vielleicht Gold oder Erfahrung

Diese Werte werden in Attributen gespeichert.

---

# Zugriff auf Attribute

```java
Spieler s1 = new Spieler();

s1.name = "Max";
s1.leben = 100;
```

Jetzt besitzt das Objekt eigene Werte.

---

# Merksatz

- Attribute = Daten/Eigenschaften eines Objekts
- Methoden = Aktionen/Funktionen eines Objekts

---

# Häufige Anfängerfehler

- ❌ Attribute und Methoden verwechseln
- ❌ denken, dass Attribute nur Zahlen sein können
- ❌ Attribute nicht initialisieren

---

# Praxisbezug

Attribute nutzt man z. B. für:
- Namen
- Alter
- Leben
- Geschwindigkeit
- Farbe
- Positionen

---

# 🔗 Verbindungen

- [[Klasse]]
- [[Objekte]]
- [[Methoden]]
- [[OOP]]