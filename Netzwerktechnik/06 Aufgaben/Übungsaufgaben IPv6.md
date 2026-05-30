# Aufgabe: IPv6 richtig schreiben

> [!question]
> ## Aufgabe
>
> Sind die folgenden IPv6-Adressen korrekt geschrieben?
>
> Falls nicht:
>
> - sagen ob **richtig oder falsch**
> - und korrekt hinschreiben
>
> ---
>
> 1.
>
> ```text
> 2001:db8::1:0:0:5
> ```
>
> ---
>
> 2.
>
> ```text
> 2a01:4f8::abcd::
> ```
>
> ---
>
> 3.
>
> ```text
> fe80:0000:0000:0000:0210:5aff:feaa:1234
> ```
>
> ---
>
> 4.
>
> ```text
> 2001:0db8:0000:0000:0000:0000:0000:0010
> ```
>
> ---
>
> 5.
>
> ```text
> 2001:db8:0:0:1::10
> ```

---

# Aufgabe: IPv6 Standortpräfix und Teilnetz-ID

> [!question]
> ## Aufgabe
>
> Gegeben ist folgende IPv6-Adresse:
>
> ```text
> 2001:ab8:42ff:0012::/64
> ```
>
> Beantworten Sie:
>
> 1. Schreiben Sie die Adresse vollständig aus.
> 2. Nennen Sie das **ungekürzte Standortpräfix (48 Bit)**.
> 3. Nennen Sie die **ungekürzte Teilnetz-ID (16 Bit)**.
> 4. Wie viele Teilnetze können gebildet werden?
> 5. Welche Adresse liegt im **nächsten Teilnetz**?
>
> ```text
> a) 2001:ab8:42ff:0013::/64
> b) 2001:ab8:4300:0012::/64
> c) 2001:ab8:42ff:0020:1::/64
> ```

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Vollständig ausgeschrieben
>
> ```text
> 2001:0ab8:42ff:0012:0000:0000:0000:0000
> ```
>
> ---
>
> ## 2. Standortpräfix (48 Bit)
>
> Die ersten 3 Blöcke:
>
> ```text
> 2001:0ab8:42ff
> ```
>
> ---
>
> ## 3. Teilnetz-ID (16 Bit)
>
> Der 4. Block:
>
> ```text
> 0012
> ```
>
> ---
>
> ## 4. Anzahl möglicher Teilnetze
>
> Teilnetz-ID = 16 Bit
>
> ```text
> 2^16 = 65536
> ```
>
> Antwort:
>
> ```text
> 65536
> ```
>
> ---
>
> ## 5. Nächstes Teilnetz
>
> Aktuell:
>
> ```text
> 0012
> ```
>
> nächster Wert:
>
> ```text
> 0013
> ```
>
> richtige Antwort:
>
> ```text
> a) 2001:ab8:42ff:0013::/64
> ```
>
> ---
>
> ## Merksatz
>
> ```text
> AAAA:BBBB:CCCC:DDDD:EEEE:FFFF:GGGG:HHHH
> |---48 Bit---|16 Bit|------64 Bit------|
> ```
>
> ```text
> Block 1–3 = Standortpräfix
> Block 4   = Teilnetz-ID
> Block 5–8 = Interface-ID
> ```

---
# Aufgabe: IPv6

- In Ihrem Unternehmen soll IPv6 zum Einsatz kommen.  
  Sie verwenden dazu die Notation, dass bei IPv6-Adressen die Interface ID durch die bisherige IPv4-Adresse ersetzt werden soll.

- Bisherige IPv4-Adresse: `192.168.25.12`

- IPv6-Subnet-ID:  
  `2001:0db8:85a3:08d3:1319:8a2e::/96`

- Wandeln Sie die IPv4-Adresse zunächst in Binäre Schreibweise um und anschließend in Hexadezimale Schreibweise.  
  Bilden Sie so die IPv6-Adresse.

---

## Lösung

> [!spoiler]- Musterlösung anzeigen
>
> ### 1. IPv4 in Binär
>
> ```text
> 192 = 11000000
> 168 = 10101000
> 25  = 00011001
> 12  = 00001100
> ```
>
> Gesamt:
>
> ```text
> 11000000 10101000 00011001 00001100
> ```
>
> ---
>
> ### 2. Binär → Hexadezimal
>
> ```text
> 11000000 = C0
> 10101000 = A8
> 00011001 = 19
> 00001100 = 0C
> ```
>
> IPv4 in Hex:
>
> ```text
> C0A8:190C
> ```
>
> ---
>
> ### 3. IPv6-Adresse bilden
>
> Vorgegeben:
>
> ```text
> 2001:0db8:85a3:08d3:1319:8a2e::/96
> ```
>
> Interface-ID ersetzen:
>
> ```text
> 2001:0db8:85a3:08d3:1319:8a2e:C0A8:190C
> ```
>
> ---
>
> ### Endergebnis
>
> ```text
> 2001:0db8:85a3:08d3:1319:8a2e:C0A8:190C
> ```
