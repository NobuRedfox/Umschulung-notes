
>[!info]
>## Erklärung
>
>Methoden sind Funktionen innerhalb einer Klasse.
>
>Sie bestimmen, was ein Objekt tun kann.

---

# Definition

Methoden führen Aktionen oder Berechnungen aus.

Sie gehören zu einer Klasse und können auf Attribute zugreifen.

---

# Beispiel

```java
public class Spieler {

    String name;
    int leben;

    public void anzeigen() {
        System.out.println(name);
        System.out.println(leben);
    }
}
```

---

# Erklärung Code

- `public void anzeigen()`
  → Methode namens `anzeigen`

- `void`
  → die Methode gibt keinen Wert zurück

- `System.out.println(...)`
  → gibt Werte auf der Konsole aus

Die Methode greift auf:
- `name`
- `leben`

zu.

---

# Methode aufrufen

```java
Spieler s1 = new Spieler();

s1.name = "Max";
s1.leben = 100;

s1.anzeigen();
```

Die Methode wird mit:
```java
s1.anzeigen();
```

aufgerufen.

---

# Rückgabewerte

Methoden können Werte zurückgeben.

Beispiel:

```java
public int verdoppeln(int zahl) {
    return zahl * 2;
}
```

Hier wird ein `int` zurückgegeben.

---

# Parameter

Methoden können Werte entgegennehmen.

Beispiel:

```java
public void schaden(int dmg) {
    leben = leben - dmg;
}
```

`dmg` ist ein Parameter.

---

# Merksatz

- Attribute = Eigenschaften eines Objekts
- Methoden = Aktionen eines Objekts

---

# Häufige Anfängerfehler

- ❌ Methode nicht aufrufen
- ❌ `()` vergessen
- ❌ Methoden und Konstruktoren verwechseln
- ❌ falschen Rückgabetyp verwenden

---

# Praxisbezug

Methoden nutzt man z. B. für:
- bewegen
- angreifen
- heilen
- speichern
- berechnen

---

# 🔗 Verbindungen

- [[Klasse]]
- [[Objekte]]
- [[Attribute]]
- [[Konstruktoren]]
- [[OOP]]