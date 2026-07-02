## Erklärung

Mit **if**  kannst du Entscheidungen im Code treffen.

#### Beispiel (if)
```java
int zahl = 10;

if (zahl > 5) {
    System.out.println("Größer als 5");
}
```
Code wird nur ausgeführt, wenn die Bedingung **true** ist

#### if - else
```java
int zahl = 3;

if (zahl > 5) {
    System.out.println("Größer als 5");
} else {
    System.out.println("Kleiner oder gleich 5");
}
```
entweder **if** oder **else**

#### else if
```java
int zahl = 5;

if (zahl > 5) {
    System.out.println("Größer als 5");
} else if (zahl == 5) {
    System.out.println("Genau 5");
} else {
    System.out.println("Kleiner als 5");
}
```

#### Vergleichsoperatoren
```java
>   größer als
<   kleiner als
>=  größer gleich
<=  kleiner gleich
==  gleich
!=  ungleich
```

#### Logische Operatoren
```java
&&   und
||   oder
!    nicht
```


### Übungen
#### Übung 1
Erstelle eine Variable **zahl = 10**. Gib aus, ob sie größer als **5** ist.
```java
int zahl = 10;

if (zahl > 5) {
    System.out.println("Größer als 5");
}
```

#### Übung 2
Erstelle eine Variante **zahl**. Gib aus, ob sie gerade oder ungerade ist.
```java
int zahl = 4;

if (zahl % 2 == 0) {
    System.out.println("Gerade");
} else {
    System.out.println("Ungerade");
}
```

#### Übung 3
Erstelle eine Variable **alter**. Wenn alter >= 18 ist, dann "Volljährig", sonst "Minderjährig".
```java
int alter = 20;

if (alter >= 18) {
    System.out.println("Volljährig");
} else {
    System.out.println("Minderjährig");
}
```
