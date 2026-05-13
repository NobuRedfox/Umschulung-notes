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