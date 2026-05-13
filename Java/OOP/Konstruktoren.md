
>[!info]
>## Erklärung
>
>Ein Konstruktor erstellt und initialisiert ein Objekt.
>
>Er wird automatisch beim Erzeugen eines Objekts aufgerufen.

---

# Definition

Ein Konstruktor ist eine spezielle Methode einer Klasse.

Er sorgt dafür, dass ein Objekt beim Erstellen Anfangswerte erhält.

---

# Beispiel

```java
public class Spieler {

    String name;
    int leben;

    public Spieler(String n, int l) {
        name = n;
        leben = l;
    }
}
```

---

# Erklärung Code

- `public Spieler(...)`
  → Konstruktor der Klasse `Spieler`

- `String n`
  → übergebener Name

- `int l`
  → übergebene Lebenspunkte

- `name = n`
  → speichert den Namen im Objekt

- `leben = l`
  → speichert die Lebenspunkte im Objekt

---

# Objekt erstellen

```java
Spieler s1 = new Spieler("Max", 100);
```

Jetzt besitzt das Objekt:
- den Namen `"Max"`
- `100` Lebenspunkte

---

# Eigenschaften

Ein Konstruktor:
- hat keinen Rückgabewert
- besitzt denselben Namen wie die Klasse
- wird automatisch aufgerufen

---

# Warum benutzt man Konstruktoren?

Konstruktoren sorgen dafür, dass Objekte direkt mit sinnvollen Werten erstellt werden.

Dadurch:
- wird Code sauberer
- entstehen weniger Fehler

---

# Standardkonstruktor

Wird kein Konstruktor geschrieben, erstellt Java automatisch einen Standardkonstruktor.

```java
Spieler s1 = new Spieler();
```

---

# Merksatz

- Konstruktor = erstellt und initialisiert Objekte

---

# Häufige Anfängerfehler

- ❌ Konstruktor mit Methode verwechseln
- ❌ Rückgabetyp schreiben (`void`)
- ❌ Klassenname falsch schreiben

---

# Praxisbezug

Konstruktoren nutzt man z. B. für:
- Spieler
- Gegner
- Autos
- Benutzerkonten

mit Startwerten.

---

# 🔗 Verbindungen

- [[Klasse]]
- [[Objekte]]
- [[Attribute]]
- [[Methoden]]
- [[OOP]]