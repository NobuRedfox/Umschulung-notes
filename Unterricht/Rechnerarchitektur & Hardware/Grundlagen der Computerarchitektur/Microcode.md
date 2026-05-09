
> [!info]
> ## Bedeutung
> Interne Steuerbefehle innerhalb einer CPU.

---

## Definition

Microcode sind kleine interne Befehle innerhalb einer
[[CPU]].

Sie steuern, wie komplexe Maschinenbefehle ausgeführt werden.

---

## Funktionsweise

Ein komplexer Maschinenbefehl wird:
- in mehrere kleine Schritte zerlegt
- nacheinander abgearbeitet

Diese kleinen Schritte nennt man:
> Mikrooperationen

---

## Aufgabe

Microcode verbindet:
- Maschinenbefehle
- interne Hardware-Steuerung der CPU

Dadurch kann die CPU komplexe Befehle einfacher verarbeiten.

---

## Verwendung

Microcode wird besonders häufig bei
[[CISC]]
-Prozessoren verwendet.

Dort bestehen viele komplexe Befehle aus mehreren internen Einzelschritten.

---

## Vorteile

- flexible CPU-Steuerung
- komplexe Befehle einfacher umsetzbar
- Fehler können teilweise per Microcode-Update behoben werden

---

## Nachteile

- zusätzliche Verarbeitungsschritte
- teilweise geringere Geschwindigkeit

---

## Zusammenhang mit dem Fetch-Execute-Cycle

Während des
[[Fetch-Execute-Cycle]]
nutzt die CPU den Microcode, um Befehle intern auszuführen.

---

## Verwandte Themen

- [[CPU]]
- [[CISC]]
- [[RISC]]
- [[Fetch-Execute-Cycle]]

---

> [!important]
> ## Merksatz
> Microcode zerlegt komplexe Befehle in kleine interne Arbeitsschritte.