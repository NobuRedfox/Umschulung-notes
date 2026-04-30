##  Erklärung

Ein Array speichert **mehrere Werte in einer Variable**.

👉 Beispiel:
```java
int[] zahlen = {1, 2, 3, 4};
```
statt 4 einzelne Variablen -> ein **Array**


### Zugriff auf Werte
```java
int[] zahlen = {1, 2, 3, 4};

System.out.println(zahlen[0]); // 1
System.out.println(zahlen[1]); // 2
```
**Wichtig**
- Index startet bei 0
- erstes Element = [0]

### Länge eines Arrays
```java
int[] zahlen = {1, 2, 3, 4};

System.out.println(zahlen.length); // 4
```

### Mit Schleife durchgehen
```java
int[] zahlen = {1, 2, 3, 4};

for (int i = 0; i < zahlen.length; i++) {
    System.out.println(zahlen[i]);
}
```


### Übungen
#### Übung 1
Erstelle ein Array mit den Zahlen 1 bis 5 und gib das erste Element aus.
```java
int[] zahlen = {1, 2, 3, 4, 5};

System.out.println(zahlen[0]);
```

#### Übung 2
Gib alle Elemente eines Arrays mit einer Schleife aus.
```java
int[] zahlen = {1, 2, 3, 4, 5};

for (int i = 0; i < zahlen.length; i++) {
    System.out.println(zahlen[i]);
}
```

#### Übung 3
Berechne die Summe aller Zahlen im Array.
```java
int[] zahlen = {1, 2, 3, 4, 5};

int summe = 0;

for (int i = 0; i < zahlen.length; i++) {
    summe += zahlen[i];
}

System.out.println(summe);
```

#### Übung 4
Gib nur die geraden Zahlen aus dem Array aus.
```java
int[] zahlen = {1, 2, 3, 4, 5};

for (int i = 0; i < zahlen.length; i++) {
    if (zahlen[i] % 2 == 0) {
        System.out.println(zahlen[i]);
    }
}
```
