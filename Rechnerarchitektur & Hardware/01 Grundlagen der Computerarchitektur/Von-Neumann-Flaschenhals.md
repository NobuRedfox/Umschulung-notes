
> [!info]
> ## Bedeutung
> Engpass zwischen CPU und Arbeitsspeicher.

---

## Definition

Der Von-Neumann-Flaschenhals beschreibt das Problem, dass
die [[CPU]] und der [[RAM]] denselben Datenbus verwenden.

Dadurch kann die CPU oft nicht schnell genug auf Daten zugreifen.

---

## Ursache

Programme und Daten liegen bei der
[[Von-Neumann-Architektur]]
im selben Speicher.

Die Übertragung läuft über denselben Bus.

Dadurch entsteht ein Engpass.

---

## Auswirkungen

Die CPU muss häufig:
- auf Daten warten
- auf Befehle warten

Dadurch:
- sinkt die Geschwindigkeit
- bleibt Rechenleistung ungenutzt

---

## Lösungsmöglichkeiten

Moderne Computer reduzieren den Flaschenhals durch:
- Cache-Speicher
- schnelleren RAM
- mehrere Busse
- parallele Verarbeitung

---

## Vergleich zur Harvard-Architektur

Bei der [[Harvard-Architektur]]
sind Daten- und Programmspeicher getrennt.

Dadurch können beide gleichzeitig gelesen werden.

---

## Verwandte Themen

- [[Von-Neumann-Architektur]]
- [[CPU]]
- [[RAM]]
- [[Harvard-Architektur]]
- [[Fetch-Execute-Cycle]]

---

> [!important]
> ## Merksatz
> Die CPU ist oft schneller als die Datenübertragung zum Arbeitsspeicher.

---

# Fragen

- Was beschreibt der Von-Neumann-Flaschenhals?

> [!spoiler]- Lösung anzeigen
> Der Von-Neumann-Flaschenhals beschreibt den Engpass zwischen
> [[CPU]]
> und [[RAM]].
>
> Beide verwenden denselben Datenbus für Programme und Daten.

---

- Warum muss die CPU oft warten?

> [!spoiler]- Lösung anzeigen
> Die CPU muss warten, weil Daten und Befehle über denselben Bus übertragen werden.
>
> Dadurch entstehen Verzögerungen beim Speicherzugriff.

---

- Wie kann der Flaschenhals reduziert werden?

> [!spoiler]- Lösung anzeigen
> Der Flaschenhals kann reduziert werden durch:
> - Cache-Speicher
> - schnelleren RAM
> - mehrere Busse
> - parallele Verarbeitung