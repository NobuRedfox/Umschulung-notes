
> [!info]
> ## Bedeutung
> Secure Boot = Sicherer Startvorgang

---

# Definition

[[Secure Boot]] ist eine Sicherheitsfunktion von [[UEFI]].

Sie überprüft beim Starten des Computers, ob nur vertrauenswürdige Software geladen wird.

---

# Aufgaben

[[Secure Boot]]:
- schützt den Bootvorgang
- verhindert manipulierte Bootloader
- blockiert unsignierte Software
- erhöht die Systemsicherheit

---

# Funktionsweise

Beim Start überprüft Secure Boot:
- Bootloader
- Treiber
- Systemdateien

Nur signierte und vertrauenswürdige Software darf gestartet werden.

---

# Schutz vor Malware

Secure Boot schützt besonders vor:
- Rootkits
- Bootkits
- manipulierten Startdateien

---

# Verbindung zu UEFI

Secure Boot ist Bestandteil von [[UEFI]].

Das klassische BIOS unterstützt Secure Boot normalerweise nicht.

---

# Verbindung zu TPM

[[TPM]] und Secure Boot arbeiten häufig zusammen.

TPM speichert sicherheitsrelevante Informationen, während Secure Boot den Startvorgang überprüft.

---

# Vorteile

Secure Boot bietet:
- höhere Sicherheit
- Schutz vor Malware
- sicheren Systemstart

---

# Nachteile

Mögliche Nachteile:
- manche ältere Systeme funktionieren nicht
- einige Linux-Systeme benötigen Anpassungen
- bestimmte Tools können blockiert werden

---

# Aktivierung

Secure Boot wird meist im [[BIOS]] bzw. [[UEFI]] aktiviert oder deaktiviert.

---

# Verbindung zur Hardware

Secure Boot arbeitet eng mit:
- [[UEFI]]
- [[TPM]]
- [[CPU]]
- [[Mainboard]]

zusammen.

---

# Verwandte Themen

- [[BIOS & UEFI]]
- [[TPM]]
- [[Bootloader]]

---

> [!important]
> ## Merksatz
> Secure Boot schützt den Computer vor manipulierten Startdateien und unsicherer Software beim Bootvorgang.

---

# Fragen

- Welche Aufgabe hat Secure Boot?

> [!spoiler]- Lösung anzeigen
> Secure Boot schützt den Bootvorgang und verhindert das Laden manipulierter Software.

---

- Wovor schützt Secure Boot?

> [!spoiler]- Lösung anzeigen
> Secure Boot schützt besonders vor:
> - Rootkits
> - Bootkits
> - manipulierten Bootloadern

---

- Mit welchem System arbeitet Secure Boot zusammen?

> [!spoiler]- Lösung anzeigen
> Secure Boot arbeitet häufig mit TPM und UEFI zusammen.

---

- Wo wird Secure Boot aktiviert?

> [!spoiler]- Lösung anzeigen
> Secure Boot wird meist im BIOS bzw. UEFI aktiviert oder deaktiviert.