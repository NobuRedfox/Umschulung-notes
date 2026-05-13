
>[!info]
>## Erklärung
>
>Ein Objekt ist eine konkrete Instanz einer Klasse.
>
>Es wird aus einer Klasse erzeugt.

---

# Definition

Ein Objekt ist ein „echtes“ Element im Programm, das auf einem Bauplan basiert.

Die Klasse beschreibt den Aufbau, das Objekt ist die konkrete Umsetzung.

---

# Beispiel

```java
public class Spieler {

    String name;
    int leben;
}
```

Aus dieser Klasse können Objekte erstellt werden.

---

# Objekt erstellen

```java
Spieler s1 = new Spieler();
```

- `Spieler`
  → Datentyp/Klasse

- `s1`
  → Name der Variable

- `new Spieler()`
  → erstellt ein neues Objekt

---

# Werte speichern

```java
s1.name = "Max";
s1.leben = 100;
```

Jetzt besitzt das Objekt eigene Werte.

---

# Mehrere Objekte

```java
Spieler s1 = new Spieler();
Spieler s2 = new Spieler();
```

Beide Objekte sind unabhängig voneinander.

Jedes Objekt besitzt eigene Daten.

---

# Zusammenhang Klasse und Objekt

- Klasse = Bauplan
- Objekt = konkrete Instanz

Beispiel:
- Klasse → Auto
- Objekt → ein bestimmtes Auto

---

# Zugriff auf Methoden

Objekte können Methoden ausführen.

```java
s1.anzeigen();
```

Die Methode gehört zur Klasse, wird aber vom Objekt genutzt.

---

# Merksatz

- Klassen beschreiben Objekte
- Objekte enthalten echte Daten

---

# Häufige Anfängerfehler

- ❌ Klasse und Objekt verwechseln
- ❌ denken, dass mehrere Objekte dieselben Werte besitzen
- ❌ `new` vergessen

---

# Praxisbezug

Objekte nutzt man z. B. für:
- Spieler
- Gegner
- Autos
- Benutzer
- Tiere
- Waffen

---

# 🔗 Verbindungen

- [[Klasse]]
- [[Attribute]]
- [[Methoden]]
- [[Konstruktoren]]
- [[OOP]]