# oder Use Case Diagram

> [!info]
> Beschreibt die Funktionen eines Systems aus Sicht der Benutzer.

---
![[Anwendungsfalldiagramm.png]]
# Definition

Ein Anwendungsfalldiagramm (Use Case Diagram) zeigt:

- welche Akteure mit dem System arbeiten
- welche Funktionen das System bietet
- welche Akteure welche Funktionen nutzen

Es beschreibt **was** ein System können soll, nicht **wie** es umgesetzt wird.

---

# Bestandteile

## Akteur (Actor)

Ein Akteur ist eine Person oder ein anderes System, das mit dem System interagiert.

Beispiele:

- Kunde
- Mitarbeiter
- Administrator
- Externes System

Darstellung:

```text
   O
  /|\
  / \
```

---

## Anwendungsfall (Use Case)

Ein Anwendungsfall beschreibt eine Funktion des Systems.

Beispiele:

- Login
- Registrieren
- Bestellung aufgeben
- Passwort ändern

Darstellung:

```text
(Login)
```

---

## Systemgrenze

Die Systemgrenze zeigt, welche Funktionen zum System gehören.

```text
+----------------------+
|      Shop-System     |
|                      |
|      (Login)         |
|      (Bestellen)     |
|                      |
+----------------------+
```

---

## Assoziation

Eine Linie verbindet Akteur und Anwendungsfall und wird offiziell meist Assoziation genannt.

```text
Kunde -------- (Login)
```

Bedeutung:

Der Kunde nutzt die Funktion Login.

---

# Include-Beziehung

Ein Anwendungsfall benötigt immer einen anderen Anwendungsfall.

Darstellung:

```text
(Bestellen)
     |
<<include>>
     |
    \ /
(Bezahlen)
```

Bedeutung:

Zum Bestellen gehört immer das Bezahlen.

---

# Extend-Beziehung

Ein Anwendungsfall erweitert einen anderen optional.

Darstellung:

```text
(2FA)
   ^
   |
<<extend>>
   |
(Login)
```

Bedeutung:

Die Zwei-Faktor-Authentifizierung ist optional.

---

# Generalisierung

Vererbung zwischen Akteuren.

```text
          Benutzer
          /      \
         /        \
     Kunde    Administrator
```

Beide sind Benutzer.

Der Administrator besitzt zusätzliche Rechte.

---

# Beispiel

Online-Shop:

```text
           Kunde
             |
             |
   +------------------+
   |   Shop-System    |
   |                  |
   | (Registrieren)   |
   | (Login)          |
   | (Bestellen)      |
   +------------------+
```

Der Kunde kann:

- sich registrieren
- anmelden
- bestellen

---

# Vorteile

- leicht verständlich
- gute Kommunikation mit Kunden
- zeigt Anforderungen übersichtlich
- dient als Grundlage für die Planung

---

# Merksatz

> Das Anwendungsfalldiagramm beschreibt die Funktionen eines Systems aus Sicht der Benutzer.

Es beantwortet die Frage:

**Wer nutzt das System und was kann er damit tun?**

Nicht:

- Wie der Code aussieht
- Welche Klassen existieren
- Wie Daten gespeichert werden

Dafür werden andere UML-Diagramme verwendet, z. B. Klassendiagramme oder Sequenzdiagramme.

---

# Fragen

## Was beschreibt ein Anwendungsfalldiagramm?

> [!spoiler]- Lösung anzeigen
> Die Funktionen eines Systems aus Sicht der Benutzer.

---

## Was ist ein Akteur?

> [!spoiler]- Lösung anzeigen
> Eine Person oder ein anderes System, das mit dem System interagiert.

---

## Was ist ein Anwendungsfall?

> [!spoiler]- Lösung anzeigen
> Eine Funktion, die das System bereitstellt.

---

## Wofür wird <<include>> verwendet?

> [!spoiler]- Lösung anzeigen
> Wenn ein Anwendungsfall immer einen anderen benötigt.

---

## Wofür wird <<extend>> verwendet?

> [!spoiler]- Lösung anzeigen
> Für optionale Erweiterungen eines Anwendungsfalls.