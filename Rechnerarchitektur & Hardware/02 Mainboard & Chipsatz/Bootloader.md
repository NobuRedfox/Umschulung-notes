
> [!info]
> ## Bedeutung
> Bootloader = Startprogramm des Betriebssystems

---

# Definition

Der [[Bootloader]] ist ein kleines Programm, das das Betriebssystem startet.

Er wird nach dem **BIOS** bzw. **UEFI** geladen.

---

# Aufgaben

Der [[Bootloader]]:
- startet das Betriebssystem
- lädt wichtige Systemdateien
- übergibt die Kontrolle an das Betriebssystem
- ermöglicht die Auswahl verschiedener Betriebssysteme

---

# Bootvorgang

Der vereinfachte Startablauf:

1. BIOS / UEFI
2. Bootloader
3. Betriebssystem

---

# Beispiele

Bekannte Bootloader:
- Windows Boot Manager
- GRUB
- systemd-boot

---

# Multi-Boot

Ein Bootloader kann mehrere Betriebssysteme verwalten.

Beispiel:
- Windows
- Linux

Beim Start kann das gewünschte System ausgewählt werden.

---

# Verbindung zu Secure Boot

[[Secure Boot]] überprüft den Bootloader beim Start.

Manipulierte oder unsignierte Bootloader werden blockiert.

---

# Fehler

Probleme mit dem Bootloader können dazu führen, dass:
- das Betriebssystem nicht startet
- Fehlermeldungen erscheinen
- der PC in einer Bootschleife hängen bleibt

---

# Verbindung zur Hardware

Der Bootloader arbeitet eng mit:
- [[BIOS & UEFI]]
- [[SSD]]
- [[Secure Boot]]

zusammen.

---

# Verwandte Themen

- [[BIOS & UEFI]]
- [[Secure Boot]]
- [[SSD]]

---

> [!important]
> ## Merksatz
> Der Bootloader startet das Betriebssystem nach BIOS bzw. UEFI.

---

# Fragen

- Welche Aufgabe hat der Bootloader?

> [!spoiler]- Lösung anzeigen
> Der Bootloader startet das Betriebssystem und lädt wichtige Systemdateien.

---

- Wann wird der Bootloader geladen?

> [!spoiler]- Lösung anzeigen
> Der Bootloader wird nach BIOS bzw. UEFI geladen.

---

- Welche bekannten Bootloader gibt es?

> [!spoiler]- Lösung anzeigen
> Beispiele:
> - Windows Boot Manager
> - GRUB
> - systemd-boot

---

- Warum überprüft Secure Boot den Bootloader?

> [!spoiler]- Lösung anzeigen
> Damit manipulierte oder unsichere Startprogramme blockiert werden können.