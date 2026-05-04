## Erklärung
Eine Klasse ist ein **Bauplan** für Objekte.

-> Sie beschreibt:
- welche **Daten** ein Objekt hat (Attribute)
- was ein Objekt **kann** (Methoden)

---

## 🎮 Beispiel (Spiel)

Stell dir ein Spiel vor:

Ein Spieler hat:
- einen Namen
- Leben

-> Genau das beschreibst du in einer Klasse:

```java
public class Spieler {
    String name;
    int leben;
}
```

#### Erklärung Code
- `public class Spieler` -> erstellt eine neue Klasse namens Spieler
- `String name` -> Text (Name des Spielers)
- `int leben` -> Ganzzahl (zb. 100 Leben)
-> Das nennt man **Attribute**

---
##  Was ist das Ergebnis?

Die Klasse selbst ist **noch nichts Greifbares**

**Sie ist nur der Bauplan**
Erst mit Objekten wird sie benutzt:

```java
Spieler s1 = new Spieler();
```

---
## 💡 Merksatz

- Klasse = Bauplan  
- Objekt = echtes Ding

---
## ⚠️ Häufige Anfängerfehler

- ❌ Klasse = Objekt verwechseln
- ❌ denken, dass die Klasse schon „läuft“
- ❌ keine Verbindung zu echten Beispielen

---
##  Praxisbezug

Klassen nutzt du z.B. für:

- Spieler in einem Spiel
- Gegner
- Autos
- Benutzer (Login-System)

-> ALLES wird als Objekt gedacht

---
## 🔗 Verbindungen

- [[Objekte]]
- [[Attribute]]
- [[Methoden]]