## Erklärung
Computer arbeiten mit verschiedenen Zahlensystemen:
- Dezimal (Basis 10)
- Binär (Basis 2)
- Hexadezimal (Basis 16)

---

## Binärsystem

nur 0 und 1

 +--- Achter
    |
    | +--- Zweier
    | |
    v v
   11011 = 1 16er + 1 8er + 1 2er + 1 1er = 16 + 8 + 2 + 1 = 27
   ^ | ^
   | | |
   | | +--- Einer
   | |
   | +--- Vierer
   |
   +--- 16er


Stellenwerte:
1, 2, 4, 8, 16, 32, 64, 128 ...

---

## Binär → Dezimal

1010 = 10  
111 = 7
11000 = 24


---

## Dezimal → Binär

109 = 1101101 (gerade = 0, ungerade = 1)
1. 109 ist ungerade, geteilt durch 2: 54
2. 54 ist gerade, geteilt durch 2: 27
3. 27 ist ungerade, geteilt durch 2: 13
4. 13 ist ungerade, geteilt durch 2: 6
5. 6 ist gerade, geteilt durch 2: 3
6. 3 ist ungerade, geteilt durch 2: 1
7. 1 ist ungerade, geteilt durch 2: 0; fertig.
**oder**
109 = 1101101
109 - 64 = 45
45  - 32 = 13
13  -  8 = 5
5   -  4 = 1

---

## Hexadezimalsystem

a = 10
b = 11
c = 12
d = 13
e = 14
f = 15

   +-- 16er
   |
   v
  1a3 = 3 1er + a 16er + 1 256er = 3 + 10*16 + 256 = 419
  ^ ^
  | |
  | +--- Einer
  |
  +--- 256er

  ff = f 1er + f 16er = 15 + 15*16 = 255

Immer mal 16: 1er, 16er, 256er, 4096er, ...


---

## Hex <-> Binär

1 Hex-Ziffer = 4 Bits

0 = 0000   8 = 1000
1 = 0001   9 = 1001
2 = 0010   a = 1010
3 = 0011   b = 1011
4 = 0100   c = 1100
5 = 0101   d = 1101
6 = 0110   e = 1110
7 = 0111   f = 1111

## Merksatz

Binär = Basis 2  
Hex = Basis 16  
1 Hex = 4 Bit