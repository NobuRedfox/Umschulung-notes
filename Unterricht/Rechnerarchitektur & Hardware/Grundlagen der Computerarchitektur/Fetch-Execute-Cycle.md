
> [!info]
> ## Bedeutung
> Grundlegender Arbeitsablauf einer CPU.

---

## Definition

Der Fetch-Execute-Cycle beschreibt den Ablauf, mit dem eine
[[CPU]] Befehle verarbeitet.

Die CPU:
1. holt einen Befehl
2. entschlüsselt ihn
3. führt ihn aus
4. speichert ggf. das Ergebnis

Dieser Zyklus läuft permanent während der Programmausführung.

---

## Ablauf

## 1. Fetch

Die CPU lädt den nächsten Befehl aus dem [[RAM]].

---

## 2. Decode

Der Befehl wird entschlüsselt.

Die CPU erkennt:
- welche Operation ausgeführt werden soll
- welche Daten benötigt werden

---

## 3. Execute

Die CPU führt den Befehl aus.

Beispiele:
- rechnen
- vergleichen
- Daten verschieben

---

## 4. Store

Das Ergebnis wird gespeichert.

Zum Beispiel:
- im Register
- im [[RAM]]

---

## Eigenschaften

- läuft Milliarden Male pro Sekunde
- verarbeitet Befehle Schritt für Schritt
- Grundlage jeder Programmausführung

---

## Verbindung zur Von-Neumann-Architektur

Bei der [[Von-Neumann-Architektur]]
werden Befehle und Daten aus demselben Speicher geladen.

Dadurch kann der
[[Von-Neumann-Flaschenhals]]
entstehen.

---

## Verwandte Themen

- [[CPU]]
- [[RAM]]
- [[Von-Neumann-Architektur]]
- [[Von-Neumann-Flaschenhals]]
- [[Microcode]]

---

> [!important]
> ## Merksatz
> Holen → Entschlüsseln → Ausführen → Speichern