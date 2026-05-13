
> [!important]
> Backpropagation ist der Prozess, bei dem der Fehler **vom Output zurück durch das Netzwerk geschickt wird**, um die Gewichte zu verbessern.

## Ablauf

1. Forward Pass (Vorhersage)
	- Input -> Netzwerk -> Output
2.  Fehler berechnen ([[Loss-Funktion]])
3. Fehler zurück zurückschicken (Backpropagation)
	- vom Output -> zurück durch alle Layer
4. Gewichte anpassen ([[Gradientenabstieg]])
## Bild im Kopf

```
Vorwärts:  Input → Output
Rückwärts: Output → Fehler → zurück
```

---
## Was passiert genau?

 Für jedes Gewicht wird berechnet:

```
Wie stark habe ich den Fehler verursacht?
```

Dann:

- wichtige Gewichte → stärker angepasst
- unwichtige → kaum verändert

---
## Ziel

Fehler auf alle Gewichte verteilen und verbessern

---
## Einfach merken

```
Backpropagation = Fehler zurück durchs Netzwerk schicken
```

## Verlinkungen

- [[Loss-Funktion]]
- [[Gradientenabstieg]]