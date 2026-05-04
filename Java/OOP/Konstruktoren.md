## 🧠 Erklärung  
Ein Konstruktor wird benutzt, um ein Objekt **direkt beim Erstellen zu setzen**  
  
---  
  
## 🎮 Beispiel  
  
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
## Nutzung

```java
Spieler s1 = new Spieler("Nobu", 100);
```
Werte werden direkt gesetzt

---
## 💡 Merksatz

👉 Konstruktor = Startwerte setzen

---
## ⚠️ Fehler

- ❌ Name nicht gleich Klassenname
- ❌ `void` davor schreiben

---
## 🔗 Verbindungen

- [[Klassen]]
- [[Objekte]]