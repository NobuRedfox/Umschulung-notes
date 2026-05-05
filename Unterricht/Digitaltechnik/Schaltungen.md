##  Erklärung

Logikgatter sind die Grundlage von Computern.

Sie arbeiten mit:
- 0 = AUS
- 1 = AN

genau wie im Binärsystem

---

##  NOT (NICHT)

```text
Eingang → Ausgang
0       → 1
1       → 0
```

---

## AND (UND)

```
A B → Ausgang
0 0 → 0
0 1 → 0
1 0 → 0
1 1 → 1
```

nur TRUE wenn beide 1 sind

---

## OR (ODER)

```
A B → Ausgang
0 0 → 0
0 1 → 1
1 0 → 1
1 1 → 1
```

TRUE wenn mindestens eins 1 ist

---

## ❌ XOR (exklusiv ODER)

```
A B → Ausgang0 0 → 00 1 → 11 0 → 11 1 → 0
```

TRUE wenn genau eins 1 ist

---

## NAND

```
A B → Ausgang0 0 → 10 1 → 11 0 → 11 1 → 0
```

Gegenteil von AND

---

## NOR

```
A B → Ausgang0 0 → 10 1 → 01 0 → 01 1 → 0
```

Gegenteil von OR