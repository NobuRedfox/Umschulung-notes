### for -Schleife
```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

- wird benutzt, wenn man **weiß wie oft etwas wiederholt wird**  
- alles steht in einer Zeile (Start, Bedingung, Veränderung)

### while-Schleife
```java
int i = 0;
while (i < 5) {
    System.out.println(i);
    i++;
}
```

- wird benutzt, wenn man **nicht genau weiß, wie oft etwas läuft**  
- läuft solange eine Bedingung **true** ist

### Aufbau einer Schleife  
  
Eine Schleife besteht immer aus:  
  
1. **Startwert**  
2. **Bedingung**  
3. **Veränderung**  
  
Beispiel while:  
```java  
int i = 1; // Startwert  
  
while (i <= 10) { // Bedingung  
System.out.println(i);  
i++; // Veränderung  
}
```


### 🧪 Übungen

#### Übung 1
Gib die Zahlen von 1 bis 10 aus.
```java
for (int i = 1; i <= 10; i++) {
	System.out.println(i);
}
```

#### Übung 2
Gib nur gerade Zahlen von 1 bis 20 aus.
```java
for (int i = 2; i  <= 20; i += 2) {
	System.out.println(i);
}
```

#### Übung 3
Zähle von 10 bis 0 rückwärts
```java
for (int i = 10; i >= 0; i--) {
    System.out.println(i);
}
```

#### Übung 4
Gib die Zahlen von 1 bis 10 mit einer **while-Schleife** aus
```java
int i = 1;

while (i <= 10) {
	System.out.println(i);
	i++;
}
