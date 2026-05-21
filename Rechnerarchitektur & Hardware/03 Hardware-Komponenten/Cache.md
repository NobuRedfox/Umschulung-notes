> [!info]
> ## Bedeutung
> Cache = schneller Zwischenspeicher zwischen CPU und RAM

---

# Definition

Der [[Cache]] ist ein besonders schneller Zwischenspeicher im Computer.

Er speichert Daten und Befehle, die die [[CPU]] wahrscheinlich bald wieder benötigt.

Dadurch muss die CPU nicht jedes Mal auf den langsameren [[RAM]] zugreifen.

---

# Aufgabe

Der [[Cache]]:
- beschleunigt den Zugriff auf häufig genutzte Daten
- reduziert Wartezeiten der CPU
- entlastet den RAM
- verbessert die Leistung des Computers
- hilft gegen den [[Von-Neumann-Flaschenhals]]

---

# Warum braucht man Cache?

Die [[CPU]] arbeitet sehr schnell.

Der [[RAM]] ist im Vergleich dazu deutlich langsamer.

Ohne Cache müsste die CPU oft auf Daten aus dem RAM warten.

Der Cache speichert deshalb häufig benötigte Daten näher an der CPU.

---

# Speicherhierarchie

Speicher im Computer ist unterschiedlich schnell.

Von schnell nach langsam:

```text
Register
↓
L1-Cache
↓
L2-Cache
↓
L3-Cache
↓
RAM
↓
SSD / HDD
```

Je schneller der Speicher ist, desto kleiner und teurer ist er meistens.

---

# Cache Hit

Ein **Cache Hit** bedeutet:

Die benötigten Daten befinden sich bereits im Cache.

Die CPU kann direkt darauf zugreifen.

Das ist schnell.

---

# Cache Miss

Ein **Cache Miss** bedeutet:

Die benötigten Daten befinden sich nicht im Cache.

Die Daten müssen erst aus dem langsameren RAM geladen werden.

Das dauert länger.

---

# Arten von Cache

## L1-Cache

Der L1-Cache ist der schnellste Cache.

Er befindet sich direkt im CPU-Kern.

Eigenschaften:
- sehr schnell
- sehr klein
- pro CPU-Kern vorhanden

---

## L2-Cache

Der L2-Cache ist größer als der L1-Cache.

Er ist etwas langsamer als L1.

Eigenschaften:
- größer als L1
- langsamer als L1
- meist pro CPU-Kern vorhanden

---

## L3-Cache

Der L3-Cache ist größer als L1 und L2.

Er ist langsamer als L1 und L2, aber immer noch schneller als RAM.

Eigenschaften:
- relativ groß
- meist von mehreren CPU-Kernen gemeinsam genutzt
- schneller als RAM

---

# Vergleich L1, L2 und L3

| Cache | Geschwindigkeit | Größe | Nähe zur CPU |
|---|---|---|---|
| L1 | sehr schnell | sehr klein | direkt im Kern |
| L2 | schnell | mittel | nahe am Kern |
| L3 | langsamer als L1/L2 | größer | oft gemeinsam genutzt |

---

# Typische Größen

| Cache | Typische Größe |
|---|---|
| L1 | wenige KB |
| L2 | einige hundert KB bis wenige MB |
| L3 | mehrere MB bis viele MB |

---

# Beispiel

Ein Programm braucht bestimmte Daten aus dem RAM.

Beim ersten Zugriff sind die Daten noch nicht im Cache.

Das ist ein Cache Miss.

Die Daten werden aus dem RAM geladen und zusätzlich im Cache gespeichert.

Wenn die CPU die gleichen Daten kurz danach wieder braucht, liegen sie bereits im Cache.

Das ist ein Cache Hit.

---

# Zusammenhang mit der CPU

Der Cache sitzt sehr nah an der [[CPU]] oder direkt in ihr.

Je besser der Cache genutzt wird, desto weniger muss die CPU warten.

Dadurch können Programme schneller ausgeführt werden.

---

# Zusammenhang mit RAM

Der [[RAM]] speichert laufende Programme und Daten.

Der Cache speichert nur einen kleinen Teil davon.

Er enthält meistens Daten, die häufig oder bald wieder gebraucht werden.

---

# Vorteile

Der Cache bietet:
- schnelleren Datenzugriff
- bessere CPU-Auslastung
- weniger Wartezeit
- höhere Leistung
- weniger direkte RAM-Zugriffe

---

# Nachteile

Cache hat auch Nachteile:
- sehr teuer im Vergleich zu RAM
- nur sehr wenig Speicherplatz
- komplexe Verwaltung
- nicht alle Daten können gleichzeitig gespeichert werden

---

# Wichtig für Prüfungen

Wichtige Begriffe:
- Cache
- L1-Cache
- L2-Cache
- L3-Cache
- Cache Hit
- Cache Miss
- Speicherhierarchie

---

# Verwandte Themen

- [[CPU]]
- [[RAM]]
- [[Register]]
- [[Von-Neumann-Architektur]]
- [[Von-Neumann-Flaschenhals]]
- [[Fetch-Execute-Cycle]]
- [[Speicherhierarchie]]

---

> [!important]
> ## Merksatz
> Der Cache ist ein schneller Zwischenspeicher, der Daten nahe an der CPU bereithält, damit die CPU weniger auf den langsameren RAM warten muss.

---

# Fragen

- Was ist ein Cache?

> [!spoiler]- Lösung anzeigen
> Ein Cache ist ein schneller Zwischenspeicher.
>
> Er speichert häufig benötigte Daten, damit die CPU schneller darauf zugreifen kann.

---

- Warum braucht die CPU einen Cache?

> [!spoiler]- Lösung anzeigen
> Die CPU ist sehr schnell, der RAM aber deutlich langsamer.
>
> Der Cache verhindert, dass die CPU ständig auf den RAM warten muss.

---

- Was bedeutet Cache Hit?

> [!spoiler]- Lösung anzeigen
> Ein Cache Hit bedeutet:
>
> Die benötigten Daten befinden sich bereits im Cache.

---

- Was bedeutet Cache Miss?

> [!spoiler]- Lösung anzeigen
> Ein Cache Miss bedeutet:
>
> Die benötigten Daten befinden sich nicht im Cache und müssen aus dem RAM geladen werden.

---

- Welche Cache-Arten gibt es in der CPU?

> [!spoiler]- Lösung anzeigen
> Es gibt hauptsächlich:
> - L1-Cache
> - L2-Cache
> - L3-Cache

---

- Welcher Cache ist am schnellsten?

> [!spoiler]- Lösung anzeigen
> Der L1-Cache ist am schnellsten.
>
> Er ist aber auch der kleinste Cache.

---

- Welcher Cache ist meist am größten?

> [!spoiler]- Lösung anzeigen
> Der L3-Cache ist meist am größten.
>
> Er ist langsamer als L1 und L2, aber schneller als RAM.

---

- Was ist die Speicherhierarchie?

> [!spoiler]- Lösung anzeigen
> Die Speicherhierarchie beschreibt die Reihenfolge von schnellen zu langsamen Speichern:
>
> Register → L1-Cache → L2-Cache → L3-Cache → RAM → SSD/HDD

---

- Was ist der Zusammenhang zwischen Cache und Von-Neumann-Flaschenhals?

> [!spoiler]- Lösung anzeigen
> Der Von-Neumann-Flaschenhals entsteht, weil CPU und Speicher über begrenzte Verbindungen kommunizieren.
>
> Der Cache reduziert dieses Problem, weil häufig benötigte Daten näher an der CPU gespeichert werden.