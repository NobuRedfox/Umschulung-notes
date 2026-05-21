> [!info]
> ## Bedeutung
> BIOS = Basic Input/Output System  
> UEFI = Unified Extensible Firmware Interface

---

# Definition

Das BIOS bzw. UEFI ist die Firmware des Mainboards.

Sie startet direkt nach dem Einschalten des Computers und initialisiert die Hardware.

UEFI ist der moderne Nachfolger des klassischen BIOS.

---

# Aufgaben

Das **BIOS** bzw. **UEFI**:
- überprüft die Hardware
- verwaltet Boot-Geräte
- stellt grundlegende Hardwarefunktionen bereit
- lädt den Bootloader (dieser lädt dann das Betriebssystem)

---

# POST (Power On Self Test)

Beim Start führt das BIOS/UEFI einen Hardwaretest durch.

Dabei werden überprüft:
- CPU
- RAM
- Grafikkarte
- Laufwerke
- Eingabegeräte

Fehler erkennt man häufig an:
- Pieptönen
- Fehlermeldungen
- schwarzem Bildschirm

---

# Unterschiede BIOS und UEFI

| BIOS | UEFI |
|---|---|
| älter | moderner Nachfolger |
| Tastatursteuerung | Maus + Tastatur |
| langsamer | schneller |
| MBR | GPT |
| max. 2 TB | sehr große Festplatten |
| weniger Sicherheitsfunktionen | Secure Boot |

---

# Boot-Reihenfolge

Das BIOS/UEFI bestimmt:
- von welchem Gerät gestartet wird
- in welcher Reihenfolge Geräte geprüft werden

Beispiel:
1. USB-Stick
2. SSD
3. Netzwerk

---

# Secure Boot

[[Secure Boot]] ist eine Sicherheitsfunktion von UEFI.

Sie sorgt dafür, dass nur signierte und vertrauenswürdige Betriebssysteme gestartet werden.

Schützt vor:
- Rootkits
- Bootkits
- manipulierten Bootloadern

---

# TPM

Das [[TPM]] (*Trusted Platform Module*) ist ein Sicherheitschip.

Er wird genutzt für:
- Windows 11
- BitLocker
- Verschlüsselung
- sichere Anmeldung

---

# BIOS-Update

Ein BIOS-/UEFI-Update kann:
- Fehler beheben
- neue CPUs unterstützen
- Stabilität verbessern

Während eines Updates darf der PC nicht ausgeschaltet werden.

---

# Verbindung zur Hardware

Das BIOS/UEFI arbeitet eng mit:
- [[CPU]]
- [[RAM]]
- [[Mainboard]]
- [[SSD]]
- [[TPM]]

zusammen.

---

# Moderne UEFI-Systeme

Moderne UEFI-Systeme bieten:
- grafische Oberfläche
- Maussteuerung
- schnelleren Start
- Sicherheitsfunktionen
- bessere Hardwareunterstützung

---

# Verwandte Themen

- [[CPU]]
- [[RAM]]
- [[Mainboard]]
- [[TPM]]
- [[Secure Boot]]
- [[MBR]]  
- [[GPT]]
- [[Bootloader]]

---

> [!important]
> ## Merksatz
> BIOS bzw. UEFI initialisieren die Hardware und starten das Betriebssystem.

---

# Fragen

- Welche Aufgaben haben BIOS und UEFI?

> [!spoiler]- Lösung anzeigen
> BIOS bzw. UEFI:
> - überprüfen die Hardware
> - starten das Betriebssystem
> - verwalten Boot-Geräte
> - initialisieren Hardwarekomponenten

---

- Was ist der Unterschied zwischen BIOS und UEFI?

> [!spoiler]- Lösung anzeigen
> UEFI ist der moderne Nachfolger des BIOS.
>
> UEFI bietet:
> - grafische Oberfläche
> - schnelleren Start
> - GPT-Unterstützung
> - Secure Boot

---

- Was macht der POST?

> [!spoiler]- Lösung anzeigen
> POST überprüft beim Start die Hardware:
> - CPU
> - RAM
> - Grafikkarte
> - Laufwerke

---

- Wofür wird Secure Boot verwendet?

> [!spoiler]- Lösung anzeigen
> Secure Boot verhindert das Starten manipulierter oder unsicherer Bootloader und schützt vor Malware.

---

- Welche Aufgabe hat TPM?

> [!spoiler]- Lösung anzeigen
> TPM dient der Sicherheit und wird z. B. für:
> - Windows 11
> - BitLocker
> - Verschlüsselung
> genutzt.

---
