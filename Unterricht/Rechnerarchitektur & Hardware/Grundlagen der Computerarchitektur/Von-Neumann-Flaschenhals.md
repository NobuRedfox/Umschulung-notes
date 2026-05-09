
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

## Problem

Die CPU muss häufig:
- auf Daten warten
- auf Befehle warten

Das verlangsamt das gesamte System.

---

## Auswirkungen

- geringere Geschwindigkeit
- langsamere Speicherzugriffe
- ungenutzte CPU-Leistung

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