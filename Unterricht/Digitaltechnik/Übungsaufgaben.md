# Übungen zu Energie, Speicher und Datenübertragung

---

## Aufgabe 1: Stromkosten eines Servers

Ein Server hat eine Leistungsaufnahme von **300 W**.  
Er wird rund um die Uhr betrieben.

Eine kWh Strom kostet **30 ct**.

Wie teuer ist der Strom für den Betrieb aufs ganze Jahr gerechnet?

> [!spoiler]- Lösung anzeigen
>
> ### 1. Watt in Kilowatt umrechnen
>
> ```text
> 300 W = 0,300 kW
> ```
>
> ---
>
> ### 2. Betriebsstunden pro Jahr berechnen
>
> ```text
> 24 × 365 = 8760 Stunden
> ```
>
> ---
>
> ### 3. Stromverbrauch berechnen
>
> ```text
> 0,300 kW × 8760 h = 2628 kWh
> ```
>
> ---
>
> ### 4. Kosten berechnen
>
> ```text
> 2628 × 0,30 €
> = 788,40 €
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> 788,40 €
> ```

---

## Aufgabe 2: Maximale Leistungsaufnahme

Eine Firma hat ein Jahresstrombudget von **1.000 €**.

Eine kWh Strom kostet **30 ct**.

Wie viel Watt darf ein Server, der ganzjährig durchgehend betrieben werden soll, höchstens ziehen?

> [!spoiler]- Lösung anzeigen
>
> ### 1. Maximale Strommenge berechnen
>
> ```text
> 1000 € / 0,30 €
> = 3333,33 kWh
> ```
>
> ---
>
> ### 2. Leistung berechnen
>
> ```text
> 3333,33 kWh / (24 × 365)
> = 0,3805 kW
> ```
>
> ---
>
> ### 3. In Watt umrechnen
>
> ```text
> 0,3805 kW = 380,5 W
> ```
>
> Konservativ gerundet:
>
> ```text
> 380 W
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> maximal 380 W
> ```

---

## Aufgabe 3: Fotos auf einer SD-Karte

Alice möchte den Sternenhimmel fotografieren.

Jedes Foto ist **5 MiB** groß.

Wie viele Fotos passen auf ihre **40 GB** große SD-Karte?

> [!spoiler]- Lösung anzeigen
>
> ### 1. Kartengröße in Byte umrechnen
>
> ```text
> 40 GB = 40 × 1000 × 1000 × 1000 B
> = 40.000.000.000 B
> ```
>
> ---
>
> ### 2. Fotogröße berechnen
>
> ```text
> 5 MiB = 5 × 1024 × 1024 B
> = 5.242.880 B
> ```
>
> ---
>
> ### 3. Anzahl Fotos berechnen
>
> ```text
> 40.000.000.000 / 5.242.880
> = 7629,39
> ```
>
> Konservativ gerundet:
>
> ```text
> 7629 Fotos
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> 7629 Fotos
> ```

---

## Aufgabe 4: Upload einer Datei

Mustafa möchte eine **10 GiB** große Datei in eine Cloud hochladen.

Seine Uploadgeschwindigkeit beträgt durchschnittlich **20 Mbps**.

Wie lange dauert der Upload?  
(Antwort in Minuten und Sekunden.)

> [!spoiler]- Lösung anzeigen
>
> ### 1. Datenmenge in Bit umrechnen
>
> ```text
> 10 GiB
> = 10 × 1024 × 1024 × 1024 Byte
> ```
>
> ```text
> × 8
> = 85.899.345.920 Bit
> ```
>
> ---
>
> ### 2. Dauer berechnen
>
> ```text
> 85.899.345.920 Bit / 20.000.000 Bit/s
> = 4294,97 Sekunden
> ```
>
> ---
>
> ### 3. In Minuten umrechnen
>
> ```text
> 4294,97 / 60
> = 71 Minuten Rest 34,97 Sekunden
> ```
>
> Gerundet:
>
> ```text
> 71 min 35 s
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> 71 Minuten 35 Sekunden
> ```

---

## Aufgabe 5: Mobile Daten beim Streaming

Jenny schaut ein **30-minütiges** Video mit einer durchschnittlichen Bitrate von **6 Mbps**.

Wie viele mobile Daten fallen dafür an?  
(Antwort in MB.)

> [!spoiler]- Lösung anzeigen
>
> ### 1. Dauer in Sekunden
>
> ```text
> 30 × 60 = 1800 Sekunden
> ```
>
> ---
>
> ### 2. Datenmenge berechnen
>
> ```text
> 6 MBit/s × 1800 s
> = 10800 MBit
> ```
>
> ---
>
> ### 3. In Megabyte umrechnen
>
> ```text
> 10800 / 8
> = 1350 MB
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> 1350 MB
> ```

---

## Aufgabe 6: Speicherbedarf eines RAW-Fotos

Herberts Kamera nimmt ein **1024 × 768** großes Foto im RAW-Format auf.

Die Farbtiefe pro Farbkanal (rot, grün, blau) beträgt **8 Bit**.

Wie viel Platz nimmt so ein Foto ein?  
(Antwort in MiB.)

> [!spoiler]- Lösung anzeigen
>
> ### 1. Farbtiefe berechnen
>
> ```text
> 8 Bit × 3 Farben
> = 24 Bit pro Pixel
> ```
>
> ---
>
> ### 2. Gesamtgröße berechnen
>
> ```text
> 1024 × 768 × 24 Bit
> = 18.874.368 Bit
> ```
>
> ---
>
> ### 3. In MiB umrechnen
>
> ```text
> 18.874.368 / 8
> = 2.359.296 Byte
> ```
>
> ```text
> 2.359.296 / 1024 / 1024
> = 2,25 MiB
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> 2,25 MiB
> ```

---

## Aufgabe 7: Wirkungsgrad eines Netzteils

Ein Netzteil zieht **330 W** aus der Steckdose und stellt den PC-Komponenten **300 W** zur Verfügung.

Was ist der Wirkungsgrad vom Netzteil?

> [!spoiler]- Lösung anzeigen
>
> ### 1. Formel
>
> ```text
> Wirkungsgrad = Nutzleistung / Eingangsleistung
> ```
>
> ---
>
> ### 2. Berechnung
>
> ```text
> 300 / 330
> = 0,9090909
> ```
>
> ---
>
> ### 3. In Prozent umrechnen
>
> ```text
> 0,9090909 × 100
> = 90,9 %
> ```
>
> Gerundet:
>
> ```text
> 91 %
> ```
>
> ---
>
> ## Zusatzinfo
>
> ```text
> Der Wirkungsgrad liegt immer zwischen 0 % und 100 %.
> ```
>
> ```text
> 100 % = perfekte Nutzung der Energie
> 0 % = gesamte Energie geht verloren
> ```
>
> Ein Wirkungsgrad über 100 % ist physikalisch unmöglich.
>
> ---
>
> ## Endergebnis
>
> ```text
> 91 %
> ```
---

 - Alice kauft eine Festplatte, die mit 500 GB Größe beworben wird.
   Wie viele Gibibyte passen auf diese Platte?

> [!spoiler]- Musterlösung anzeigen
> 500 × 1000 × 1000 ×1000 / 1024 /1024 /1024 GiB = 465.661287 GiB = 466 GiB (gerundet)
> Antwort: Es passt 466 GiB auf die Platte.

---
## Aufgabe 8: USV für 300-W-Server

Eine USV soll bei Stromausfällen den kurzzeitigen Weiterbetrieb eines **300-W-Servers** ermöglichen.

Als Batteriekapazität ist angegeben:

```text
4 × 12 V, 9 Ah
```

Die USV packt bis zu **3000 VA**.

Wie lange kann diese USV rein rechnerisch den Server versorgen?

> [!spoiler]- Lösung anzeigen
>
> ### 1. Batteriekapazität berechnen
>
> ```text
> Energie = Spannung × Stromstärke × Anzahl
> ```
>
> ```text
> 12 V × 9 Ah × 4 = 432 Wh
> ```
>
> ---
>
> ### 2. Laufzeit berechnen
>
> ```text
> Laufzeit = Energie / Leistung
> ```
>
> ```text
> 432 Wh / 300 W = 1,44 h
> ```
>
> ---
>
> ### 3. In Minuten umrechnen
>
> ```text
> 1,44 × 60 = 86,4 Minuten
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> ca. 86 Minuten
> ```
>
> Hinweis:
>
> ```text
> Rein rechnerisch, ohne Verluste.
> In der Praxis ist die Laufzeit geringer.
> ```

---

## Aufgabe 9: Foto für Printmedium

Ein Printmedium erwartet von seiner Fotografin ein Foto mit **300 DPI** Auflösung.

Das Foto soll **10 cm × 5 cm** groß sein.

Aus wie vielen Pixeln besteht so ein Foto?

Wie viel Speicherplatz in **MiB** nimmt es ein, wenn es im RAW-Format im RGB-Farbraum mit **10 Bit pro Farbkanal** gespeichert wird?

> [!spoiler]- Lösung anzeigen
>
> ### 1. Zentimeter in Inch umrechnen
>
> ```text
> 1 Inch = 2,54 cm
> ```
>
> ```text
> 10 cm / 2,54 = 3,94 Inch
> 5 cm / 2,54 = 1,97 Inch
> ```
>
> ---
>
> ### 2. Pixel berechnen
>
> ```text
> 3,94 × 300 = ca. 1181 Pixel
> ```
>
> ```text
> 1,97 × 300 = ca. 591 Pixel
> ```
>
> Also ungefähr:
>
> ```text
> 1181 × 591 Pixel
> ```
>
> Gesamt:
>
> ```text
> 1181 × 591 = 697971 Pixel
> ```
>
> ---
>
> ### 3. Speicherbedarf pro Pixel
>
> RGB hat 3 Farbkanäle:
>
> ```text
> Rot + Grün + Blau
> ```
>
> Pro Kanal:
>
> ```text
> 10 Bit
> ```
>
> Also:
>
> ```text
> 3 × 10 Bit = 30 Bit pro Pixel
> ```
>
> ---
>
> ### 4. Gesamtspeicher berechnen
>
> ```text
> 697971 × 30 Bit = 20939130 Bit
> ```
>
> In Byte:
>
> ```text
> 20939130 / 8 = 2617391,25 Byte
> ```
>
> In MiB:
>
> ```text
> 2617391,25 / 1024 / 1024 = 2,50 MiB
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> ca. 1181 × 591 Pixel
> ```
>
> ```text
> ca. 2,50 MiB
> ```

---

## Aufgabe 10:

Sie wollen einen Film in die Cloud sichern.

Berechnen Sie die Zeit in Minuten, die für die Übertragung der 4,8 GiB großen Datei bei einer VDSL-Leitung mit 50 MBit/s Download und 20 MBit/s Upload benötigt wird.

Das Ergebnis ist auf volle Minuten aufzurunden.

Der Rechenweg ist anzugeben.

> [!spoiler]- Musterlösung anzeigen
>
> ### 1. Richtige Geschwindigkeit wählen
>
> Für das Hochladen in die Cloud ist die **Upload-Geschwindigkeit** relevant:
>
> ```text
> 20 MBit/s
> ```
>
> ---
>
> ### 2. Dateigröße umrechnen
>
> ```text
> 4,8 GiB
> ```
>
> 1 GiB = 1024 MiB
>
> ```text
> 4,8 × 1024 = 4915,2 MiB
> ```
>
> 1 Byte = 8 Bit
>
> ```text
> 4915,2 × 8 = 39321,6 MBit
> ```
>
> ---
>
> ### 3. Übertragungszeit berechnen
>
> Formel:
>
> ```text
> Zeit = Datenmenge / Geschwindigkeit
> ```
>
> ```text
> 39321,6 MBit / 20 MBit/s
> = 1966,08 Sekunden
> ```
>
> ---
>
> ### 4. Sekunden in Minuten umrechnen
>
> ```text
> 1966,08 / 60
> = 32,77 Minuten
> ```
>
> Aufrunden:
>
> ```text
> = 33 Minuten
> ```
>
> ---
>
> ## Endergebnis
>
> ```text
> Der Upload dauert 33 Minuten.
> ```

---

## Aufgabe 11: Upload eines Urlaubsalbums

Sie möchten Ihre Urlaubsfotos in die Cloud hochladen.  
Die Fotos haben eine Gesamtgröße von **2,5 GiB**.

Ihre Internetverbindung hat eine Upload-Geschwindigkeit von **10 Mbit/s**.

Berechnen Sie, wie lange der Upload dauert.  
Runden Sie das Ergebnis auf volle Minuten und zeigen Sie den Rechenweg.

> [!spoiler]- Lösung anzeigen
>
> ```text
> 2,5 GiB × 1024 = 2560 MiB
> 2560 MiB × 8 = 20480 Mbit
> ```
>
> ```text
> 20480 Mbit / 10 Mbit/s = 2048 Sekunden
> ```
>
> ```text
> 2048 / 60 = 34,13 Minuten
> ```
>
> Aufgerundet:
>
> ```text
> 35 Minuten
> ```

---

## Aufgabe 12: Download eines Videospiels

Sie laden ein Videospiel mit einer Größe von **30 GiB** herunter.

Ihre Internetverbindung hat eine Download-Geschwindigkeit von **100 Mbit/s**.

Wie lange dauert der Download?  
Geben Sie das Ergebnis in Minuten an und zeigen Sie den Rechenweg.

> [!spoiler]- Lösung anzeigen
>
> ```text
> 30 GiB × 1024 = 30720 MiB
> 30720 MiB × 8 = 245760 Mbit
> ```
>
> ```text
> 245760 Mbit / 100 Mbit/s = 2457,6 Sekunden
> ```
>
> ```text
> 2457,6 / 60 = 40,96 Minuten
> ```
>
> Aufgerundet:
>
> ```text
> 41 Minuten
> ```

---

## Aufgabe 13: Streaming eines Films

Ein Streamingdienst verwendet für hochauflösende Filme eine durchschnittliche Bitrate von **8 Mbit/s**.

Ein Film dauert **2 Stunden**.

Berechnen Sie, wie viele Gibibyte (**GiB**) während des Streamings heruntergeladen werden.  
Zeigen Sie den Rechenweg.

> [!spoiler]- Lösung anzeigen
>
> ```text
> 2 Stunden = 120 Minuten = 7200 Sekunden
> ```
>
> ```text
> 8 Mbit/s × 7200 s = 57600 Mbit
> ```
>
> ```text
> 57600 Mbit / 8 = 7200 MiB
> ```
>
> ```text
> 7200 MiB / 1024 = 7,03 GiB
> ```
>
> Ergebnis:
>
> ```text
> ca. 7,03 GiB
> ```

---

## Aufgabe 14: Sicherung einer Festplatte in der Cloud

Sie möchten eine Sicherung Ihrer **500 GiB** großen Festplatte in der Cloud speichern.

Ihre Upload-Geschwindigkeit beträgt **50 Mbit/s**.

Wie lange dauert dieser Upload in Stunden?  
Zeigen Sie den Rechenweg.

> [!spoiler]- Lösung anzeigen
>
> ```text
> 500 GiB × 1024 = 512000 MiB
> 512000 MiB × 8 = 4096000 Mbit
> ```
>
> ```text
> 4096000 Mbit / 50 Mbit/s = 81920 Sekunden
> ```
>
> ```text
> 81920 / 3600 = 22,76 Stunden
> ```
>
> Ergebnis:
>
> ```text
> ca. 22,76 Stunden
> ```

---

## Aufgabe 15: Download eines Software-Updates

Ein großes Software-Update hat eine Größe von **15 GiB**.

Ihr Internetanschluss erlaubt eine maximale Downloadgeschwindigkeit von **250 Mbit/s**.

Wie lange dauert der Download des Updates?  
Zeigen Sie den Rechenweg und runden Sie auf volle Minuten.

> [!spoiler]- Lösung anzeigen
>
> ```text
> 15 GiB × 1024 = 15360 MiB
> 15360 MiB × 8 = 122880 Mbit
> ```
>
> ```text
> 122880 Mbit / 250 Mbit/s = 491,52 Sekunden
> ```
>
> ```text
> 491,52 / 60 = 8,19 Minuten
> ```
>
> Aufgerundet:
>
> ```text
> 9 Minuten
> ```