
> [!important]
> Die Loss-Funktion misst, wie groß der Fehler eines Modells ist.

## Ziel
Vorhersage möglichst nah an der richtigen Antwort
-> je näher dran -> desto kleiner der Fehler

## Beispiel
Vorhersage: 8
Richtig: 10
Fehler = 2

## Zusammenhang

- Loss → misst Fehler
- Gradient → zeigt Richtung
- Gradientenabstieg → reduziert Fehler

## Warum braucht man das?

Das Modell braucht eine klare Antwort auf:

```
"Wie schlecht bin ich gerade?"
```

Und genau das liefert die Loss-Funktion.

---

## Verbindung zu Gradientenabstieg

Ganz wichtig:

```
Gradientenabstieg minimiert die Loss-Funktion
```

Also:

- Loss sagt → wie schlecht
- Gradient sagt → wohin verbessern
- Gradientenabstieg → macht die Änderung

---

## Andere wichtige Loss-Funktionen

### 🔹 MSE
- für Zahlen (Regression)
### 🔹 Cross Entropy
- für Klassen (z. B. Katze vs Hund)

---

## Verbindungen

-[[Gradientenabstieg]]