
> [!important]
> Embeddings sind Zahlenvektoren, die die Bedeutung von Wörtern darstellen.

## Warum braucht man das?

Computer verstehen keine Wörter wie:
```
"Katze", "Hund", "Auto"
```

-> Sie brauchen Zahlen:
```
[0.2, -1.3, 0.8, ...]
```

---
## Idee dahinter

Ähnliche Wörter → ähnliche Vektoren

---
## Ablauf

1. Text -> [[Tokens]] 
2. Tokens -> Embeddings (Vektoren)
3. Verarbeitung (Netzwerk arbeitet mit Zahlen)

## Warum ist das so wichtig?

Das ist der Moment, wo KI „versteht“:
```
Bedeutung statt nur Text
```

---
## Beispiel

„König - Mann + Frau ≈ Königin“

-> funktioniert nur wegen Embeddings

---

## Verbindungen

- [[Token]]