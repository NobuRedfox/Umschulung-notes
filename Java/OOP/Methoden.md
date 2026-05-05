##  Erklärung
Methoden sind **Funktionen innerhalb einer Klasse**.

-> Sie bestimmen, was ein Objekt **tun kann**

---

## Beispiel

```java
public class Spieler {
    String name;
    int leben;

    void heilen() {
        leben = leben + 10;
    }
}
```

#### Erklärung Code
- `void heilen()` → Methode
- erhöht Leben

---
##  Nutzung

```java
s1.heilen();
```

 führt die Methode aus

---
## Merksatz

--> Methoden = Verhalten

---
## Fehler

- ❌ Methode nicht aufrufen
- ❌ denken, dass sie automatisch läuft

---
## 🔗 Verbindungen

- [[Klassen]]
- [[Objekte]]