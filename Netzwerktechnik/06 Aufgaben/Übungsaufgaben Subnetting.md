# Aufgabe: Vorletzte mögliche IP-Adresse im Netz

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 192.168.100.0/26
> ```
>
> Die letzte mögliche IP-Adresse im Netz wird für das Gateway genutzt.
>
> Die vorletzte mögliche IP-Adresse soll für **Druckstation 1** verwendet werden.
>
> PC 1:
>
> ```text
> 192.168.100.21
> ```
>
> PC 2:
>
> ```text
> 192.168.100.42
> ```
>
> **Welche IP-Adresse bekommt Druckstation 1?**

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Subnetzmaske bestimmen
>
> `/26` bedeutet:
>
> ```text
> 255.255.255.192
> ```
>
> Blockgröße:
>
> ```text
> 256 - 192 = 64
> ```
>
> ---
>
> ## 2. Bereich des ersten Subnetzes
>
> ```text
> 192.168.100.0 - 192.168.100.63
> ```
>
> ---
>
> ## 3. Netzadresse und Broadcast
>
> Netzadresse:
>
> ```text
> 192.168.100.0
> ```
>
> Broadcast:
>
> ```text
> 192.168.100.63
> ```
>
> ---
>
> ## 4. Nutzbare Hosts
>
> ```text
> 192.168.100.1 - 192.168.100.62
> ```
>
> Letzte mögliche Host-IP (Gateway):
>
> ```text
> 192.168.100.62
> ```
>
> Vorletzte mögliche Host-IP:
>
> ```text
> 192.168.100.61
> ```
>
> ---
>
> ## Antwort
>
> Druckstation 1 bekommt:
>
> ```text
> 192.168.100.61
> ```
>
> ---
>
> ## Kontrolle
>
> Alle Geräte liegen im selben Netz:
>
> ```text
> PC 1         192.168.100.21
> PC 2         192.168.100.42
> Druckstation 192.168.100.61
> Gateway      192.168.100.62
> ```
>
> Broadcast:
>
> ```text
> 192.168.100.63
> ```

---

# Aufgabe: Subnetting in 8 gleich große Subnetze

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 192.168.12.0/24
> ```
>
> Beantworten Sie folgende Fragen:
>
> 1. Wie viele Hosts können in diesem Netzwerk adressiert werden?
> 2. Nennen Sie die Subnetzmaske dieses Netzwerks in Dezimalschreibweise.
> 3. Das Netzwerk soll in **8 gleich große Subnetze** unterteilt werden.  
>    Nennen Sie die neue Subnetzmaske in Dezimalschreibweise.

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Anzahl nutzbarer Hosts
>
> `/24` bedeutet:
>
> ```text
> 32 - 24 = 8 Host-Bits
> ```
>
> ```text
> 2^8 = 256 Adressen
> ```
>
> Davon sind 2 nicht nutzbar:
>
> ```text
> Netzadresse
> Broadcastadresse
> ```
>
> Also:
>
> ```text
> 256 - 2 = 254 nutzbare Hosts
> ```
>
> Antwort:
>
> ```text
> 254
> ```
>
> ---
>
> ## 2. Subnetzmaske von /24
>
> `/24` bedeutet binär:
>
> ```text
> 11111111.11111111.11111111.00000000
> ```
>
> Dezimal:
>
> ```text
> 255.255.255.0
> ```
>
> Antwort:
>
> ```text
> 255.255.255.0
> ```
>
> ---
>
> ## 3. In 8 gleich große Subnetze aufteilen
>
> Gesucht sind 8 Subnetze.
>
> ```text
> 2^1 = 2
> 2^2 = 4
> 2^3 = 8
> ```
>
> Also werden **3 Bits** zusätzlich für Subnetze benötigt.
>
> Ausgang:
>
> ```text
> /24
> ```
>
> Neue Präfixlänge:
>
> ```text
> /24 + 3 = /27
> ```
>
> `/27` bedeutet binär:
>
> ```text
> 11111111.11111111.11111111.11100000
> ```
>
> Letztes Oktett:
>
> ```text
> 11100000
> ```
>
> Rechnung:
>
> ```text
> 128 + 64 + 32 = 224
> ```
>
> Neue Subnetzmaske:
>
> ```text
> 255.255.255.224
> ```
>
> Antwort:
>
> ```text
> 255.255.255.224
> ```
>
> ---
>
> ## Kontrolle: 8 Subnetze
>
> Blockgröße:
>
> ```text
> 256 - 224 = 32
> ```
>
> Die Subnetze sind:
>
> ```text
> 192.168.12.0   - 192.168.12.31
> 192.168.12.32  - 192.168.12.63
> 192.168.12.64  - 192.168.12.95
> 192.168.12.96  - 192.168.12.127
> 192.168.12.128 - 192.168.12.159
> 192.168.12.160 - 192.168.12.191
> 192.168.12.192 - 192.168.12.223
> 192.168.12.224 - 192.168.12.255
> ```

---
# Aufgabe: Subnetting mit /19 und 9 Subnetzen

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 192.168.224.0/19
> ```
>
> Beantworten Sie folgende Fragen:
>
> 1. Wie viele Hosts können in diesem Netzwerk adressiert werden?
> 2. Nennen Sie die Subnetzmaske dieses Netzwerks in Dezimalschreibweise.
> 3. Das Netzwerk soll in **9 gleich große Subnetze** unterteilt werden.  
>    Nennen Sie die neue Subnetzmaske in Dezimalschreibweise.
> 4. Nennen Sie die Netzwerkadresse und Broadcastadresse des **3. Subnetzes**.

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Anzahl nutzbarer Hosts
>
> `/19` bedeutet:
>
> ```text
> 32 - 19 = 13 Host-Bits
> ```
>
> ```text
> 2^13 = 8192 Adressen
> ```
>
> Davon sind 2 nicht nutzbar:
>
> ```text
> Netzadresse
> Broadcastadresse
> ```
>
> Also:
>
> ```text
> 8192 - 2 = 8190 nutzbare Hosts
> ```
>
> Antwort:
>
> ```text
> 8190
> ```
>
> ---
>
> ## 2. Subnetzmaske von /19
>
> `/19` bedeutet binär:
>
> ```text
> 11111111.11111111.11100000.00000000
> ```
>
> Das dritte Oktett ist:
>
> ```text
> 11100000
> ```
>
> Rechnung:
>
> ```text
> 128 + 64 + 32 = 224
> ```
>
> Dezimal:
>
> ```text
> 255.255.224.0
> ```
>
> Antwort:
>
> ```text
> 255.255.224.0
> ```
>
> ---
>
> ## 3. In 9 gleich große Subnetze aufteilen
>
> Gesucht sind 9 Subnetze.
>
> ```text
> 2^3 = 8
> 2^4 = 16
> ```
>
> 8 reicht nicht, also werden **4 Bits** zusätzlich benötigt.
>
> Ausgang:
>
> ```text
> /19
> ```
>
> Neue Präfixlänge:
>
> ```text
> /19 + 4 = /23
> ```
>
> `/23` bedeutet binär:
>
> ```text
> 11111111.11111111.11111110.00000000
> ```
>
> Das dritte Oktett ist:
>
> ```text
> 11111110
> ```
>
> Rechnung:
>
> ```text
> 128 + 64 + 32 + 16 + 8 + 4 + 2 = 254
> ```
>
> Neue Subnetzmaske:
>
> ```text
> 255.255.254.0
> ```
>
> Antwort:
>
> ```text
> 255.255.254.0
> ```
>
> ---
>
> ## 4. Netzwerkadresse und Broadcastadresse des 3. Subnetzes
>
> Bei `/23` ist die Maske:
>
> ```text
> 255.255.254.0
> ```
>
> Blockgröße im dritten Oktett:
>
> ```text
> 256 - 254 = 2
> ```
>
> Die Subnetze springen also im dritten Oktett immer um 2:
>
> ```text
> 1. Subnetz: 192.168.224.0 - 192.168.225.255
> 2. Subnetz: 192.168.226.0 - 192.168.227.255
> 3. Subnetz: 192.168.228.0 - 192.168.229.255
> ```
>
> Netzwerkadresse des 3. Subnetzes:
>
> ```text
> 192.168.228.0
> ```
>
> Broadcastadresse des 3. Subnetzes:
>
> ```text
> 192.168.229.255
> ```
>
> Antwort:
>
> ```text
> Netzwerkadresse: 192.168.228.0
> Broadcastadresse: 192.168.229.255
> ```
>
> ---
>
> ## Kontrolle: Hosts pro neuem Subnetz
>
> `/23` bedeutet:
>
> ```text
> 32 - 23 = 9 Host-Bits
> ```
>
> ```text
> 2^9 = 512 Adressen
> ```
>
> Nutzbar:
>
> ```text
> 512 - 2 = 510 Hosts
> ```

---
# Aufgabe: VLSM mit 4 Abteilungen

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 200.1.1.0/24
> ```
>
> Der Adressbereich soll für 4 Abteilungen aufgeteilt werden.
>
> Mindestbedarf:
>
> ```text
> Abteilung A: 72 Hosts
> Abteilung B: 35 Hosts
> Abteilung C: 20 Hosts
> Abteilung D: 18 Hosts
> ```
>
> Füllen Sie für jede Abteilung aus:
>
> - Größe des Subnetzes
> - Anzahl nutzbarer Adressen
> - Präfixnotation (CIDR)
> - Subnetzmaske
> - Netzadresse
> - Broadcastadresse

![[Subnetzmaske.png]]

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## Grundregel
>
> Es wird immer mit der größten Abteilung begonnen.
>
> ```text
> A = 72 Hosts
> B = 35 Hosts
> C = 20 Hosts
> D = 18 Hosts
> ```
>
> ---
>
> ## Abteilung A
>
> Bedarf:
>
> ```text
> 72 Hosts
> ```
>
> Nächstgrößeres passendes Subnetz:
>
> ```text
> 128 Adressen
> ```
>
> Nutzbar:
>
> ```text
> 128 - 2 = 126 Hosts
> ```
>
> Präfix:
>
> ```text
> /25
> ```
>
> Subnetzmaske:
>
> ```text
> 255.255.255.128
> ```
>
> Netzadresse:
>
> ```text
> 200.1.1.0
> ```
>
> Broadcast:
>
> ```text
> 200.1.1.127
> ```
>
> ---
>
> ## Abteilung B
>
> Bedarf:
>
> ```text
> 35 Hosts
> ```
>
> Nächstgrößeres passendes Subnetz:
>
> ```text
> 64 Adressen
> ```
>
> Nutzbar:
>
> ```text
> 64 - 2 = 62 Hosts
> ```
>
> Präfix:
>
> ```text
> /26
> ```
>
> Subnetzmaske:
>
> ```text
> 255.255.255.192
> ```
>
> Netzadresse:
>
> ```text
> 200.1.1.128
> ```
>
> Broadcast:
>
> ```text
> 200.1.1.191
> ```
>
> ---
>
> ## Abteilung C
>
> Bedarf:
>
> ```text
> 20 Hosts
> ```
>
> Nächstgrößeres passendes Subnetz:
>
> ```text
> 32 Adressen
> ```
>
> Nutzbar:
>
> ```text
> 32 - 2 = 30 Hosts
> ```
>
> Präfix:
>
> ```text
> /27
> ```
>
> Subnetzmaske:
>
> ```text
> 255.255.255.224
> ```
>
> Netzadresse:
>
> ```text
> 200.1.1.192
> ```
>
> Broadcast:
>
> ```text
> 200.1.1.223
> ```
>
> ---
>
> ## Abteilung D
>
> Bedarf:
>
> ```text
> 18 Hosts
> ```
>
> `/28` wäre zu klein:
>
> ```text
> /28 = 16 Adressen
> 16 - 2 = 14 nutzbare Hosts
> ```
>
> Deshalb wird `/27` benötigt:
>
> ```text
> /27 = 32 Adressen
> 32 - 2 = 30 nutzbare Hosts
> ```
>
> Präfix:
>
> ```text
> /27
> ```
>
> Subnetzmaske:
>
> ```text
> 255.255.255.224
> ```
>
> Netzadresse:
>
> ```text
> 200.1.1.224
> ```
>
> Broadcast:
>
> ```text
> 200.1.1.255
> ```
>
> ---
>
> # Fertige Tabelle
>
> | Subnetz | Abteilung A | Abteilung B | Abteilung C | Abteilung D |
> |---|---:|---:|---:|---:|
> | Bedarf | 72 | 35 | 20 | 18 |
> | Größe des Subnetzes | 128 | 64 | 32 | 32 |
> | Anzahl nutzbarer Adressen | 126 | 62 | 30 | 30 |
> | Präfixnotation | /25 | /26 | /27 | /27 |
> | Subnetzmaske | 255.255.255.128 | 255.255.255.192 | 255.255.255.224 | 255.255.255.224 |
> | Netzadresse | 200.1.1.0 | 200.1.1.128 | 200.1.1.192 | 200.1.1.224 |
> | Broadcast | 200.1.1.127 | 200.1.1.191 | 200.1.1.223 | 200.1.1.255 |
>
> ---
>
> ## Merksatz
>
> ```text
> Erst die größte Abteilung einteilen.
> Dann immer die nächstgrößere passende Zweierpotenz nehmen.
> ```
>
> ```text
> 72 Hosts → 128 Adressen → /25
> 35 Hosts → 64 Adressen  → /26
> 20 Hosts → 32 Adressen  → /27
> 18 Hosts → 32 Adressen  → /27
> ```

---
# Aufgabe: Netz in 4 gleich große Subnetze teilen

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 192.168.44.0/24
> ```
>
> Teilen Sie das Netz in **vier gleich große Netze**.
>
> Geben Sie jeweils an:
>
> - Netzadresse
> - Broadcastadresse
> - Subnetzmaske

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Neue Subnetzmaske bestimmen
>
> 4 Subnetze werden benötigt:
>
> ```text
> 2^2 = 4
> ```
>
> Also werden 2 zusätzliche Bits benötigt.
>
> Ausgang:
>
> ```text
> /24
> ```
>
> Neue Präfixlänge:
>
> ```text
> /24 + 2 = /26
> ```
>
> Subnetzmaske:
>
> ```text
> 255.255.255.192
> ```
>
> Blockgröße:
>
> ```text
> 256 - 192 = 64
> ```
>
> ---
>
> ## 2. Die 4 Subnetze
>
> | Subnetz | Netzadresse | Broadcastadresse | Subnetzmaske |
> |---:|---|---|---|
> | 1 | 192.168.44.0 | 192.168.44.63 | 255.255.255.192 |
> | 2 | 192.168.44.64 | 192.168.44.127 | 255.255.255.192 |
> | 3 | 192.168.44.128 | 192.168.44.191 | 255.255.255.192 |
> | 4 | 192.168.44.192 | 192.168.44.255 | 255.255.255.192 |

---
# Aufgabe: Hosts und 3. Subnetz bei 8 Subnetzen

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 192.168.12.0/24
> ```
>
> Das Netzwerk soll in **8 gleich große Subnetze** eingeteilt werden.
>
> Beantworten Sie:
>
> 1. Wie viele Hosts können in einem der neuen Subnetze adressiert werden?
> 2. Nennen Sie die Netz-ID des dritten Subnetzes.
> 3. Nennen Sie den Broadcast des dritten Subnetzes.

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Neue Subnetzmaske bestimmen
>
> 8 Subnetze:
>
> ```text
> 2^3 = 8
> ```
>
> Also werden 3 Bits zusätzlich benötigt.
>
> ```text
> /24 + 3 = /27
> ```
>
> Neue Subnetzmaske:
>
> ```text
> 255.255.255.224
> ```
>
> Blockgröße:
>
> ```text
> 256 - 224 = 32
> ```
>
> ---
>
> ## 2. Hosts pro neuem Subnetz
>
> Bei `/27` bleiben:
>
> ```text
> 32 - 27 = 5 Host-Bits
> ```
>
> ```text
> 2^5 = 32 Adressen
> ```
>
> Davon sind 2 nicht nutzbar:
>
> ```text
> Netzadresse
> Broadcastadresse
> ```
>
> Nutzbare Hosts:
>
> ```text
> 32 - 2 = 30
> ```
>
> Antwort:
>
> ```text
> 30
> ```
>
> ---
>
> ## 3. Subnetze auflisten
>
> Die Blockgröße ist:
>
> ```text
> 32
> ```
>
> Deshalb springen die Subnetze im letzten Oktett immer um 32:
>
> ```text
> 1. Subnetz: 192.168.12.0  - 192.168.12.31
> 2. Subnetz: 192.168.12.32 - 192.168.12.63
> 3. Subnetz: 192.168.12.64 - 192.168.12.95
> ```
>
> Netz-ID des dritten Subnetzes:
>
> ```text
> 192.168.12.64
> ```
>
> Broadcast des dritten Subnetzes:
>
> ```text
> 192.168.12.95
> ```
>
> ---
>
> ## Antworten
>
> ```text
> 4. 30 Hosts
> 5. 192.168.12.64
> 6. 192.168.12.95
> ```

---

# Aufgabe: Subnetting - 2

> [!question]
> ## Aufgabe
>
> Gegeben ist das Netzwerk:
>
> ```text
> 172.18.0.0/16
> ```
>
> Beantworten Sie:
>
> 1. Wie viele Hosts können in diesem Netzwerk adressiert werden?
> 2. Das Netzwerk soll in **12 gleich große Subnetze** unterteilt werden.  
>    Nennen Sie die neue Subnetzmaske in Dezimalschreibweise.
> 3. Wie viele Hosts können in einem der neuen Subnetze adressiert werden?
> 4. Nennen Sie die Netz-ID des zweiten Subnetzes.
> 5. Nennen Sie den Broadcast des zweiten Subnetzes.

---

# Lösung

> [!spoiler]- Lösung anzeigen
>
> ## 1. Hosts im ursprünglichen Netzwerk
>
> `/16` bedeutet:
>
> ```text
> 32 - 16 = 16 Host-Bits
> ```
>
> ```text
> 2^16 = 65536 Adressen
> ```
>
> Davon sind 2 nicht nutzbar:
>
> ```text
> Netzadresse
> Broadcastadresse
> ```
>
> Nutzbare Hosts:
>
> ```text
> 65536 - 2 = 65534
> ```
>
> Antwort:
>
> ```text
> 65534
> ```
>
> ---
>
> ## 2. Neue Subnetzmaske bei 12 Subnetzen
>
> Gesucht sind 12 Subnetze.
>
> ```text
> 2^3 = 8
> 2^4 = 16
> ```
>
> 8 reicht nicht, also werden **4 Bits** benötigt.
>
> ```text
> /16 + 4 = /20
> ```
>
> `/20` bedeutet binär:
>
> ```text
> 11111111.11111111.11110000.00000000
> ```
>
> Das dritte Oktett ist:
>
> ```text
> 11110000
> ```
>
> Rechnung:
>
> ```text
> 128 + 64 + 32 + 16 = 240
> ```
>
> Neue Subnetzmaske:
>
> ```text
> 255.255.240.0
> ```
>
> Antwort:
>
> ```text
> 255.255.240.0
> ```
>
> ---
>
> ## 3. Hosts pro neuem Subnetz
>
> Neue Präfixlänge:
>
> ```text
> /20
> ```
>
> Host-Bits:
>
> ```text
> 32 - 20 = 12
> ```
>
> ```text
> 2^12 = 4096 Adressen
> ```
>
> Nutzbare Hosts:
>
> ```text
> 4096 - 2 = 4094
> ```
>
> Antwort:
>
> ```text
> 4094
> ```
>
> ---
>
> ## 4. Netz-ID des zweiten Subnetzes
>
> Neue Maske:
>
> ```text
> 255.255.240.0
> ```
>
> Blockgröße im dritten Oktett:
>
> ```text
> 256 - 240 = 16
> ```
>
> Die Subnetze springen also im dritten Oktett immer um 16:
>
> ```text
> 1. Subnetz: 172.18.0.0  - 172.18.15.255
> 2. Subnetz: 172.18.16.0 - 172.18.31.255
> ```
>
> Netz-ID des zweiten Subnetzes:
>
> ```text
> 172.18.16.0
> ```
>
> ---
>
> ## 5. Broadcast des zweiten Subnetzes
>
> Das zweite Subnetz geht von:
>
> ```text
> 172.18.16.0
> ```
>
> bis:
>
> ```text
> 172.18.31.255
> ```
>
> Broadcast des zweiten Subnetzes:
>
> ```text
> 172.18.31.255
> ```
>
> ---
>
> ## Antworten
>
> ```text
> 22. 65534
> 23. 255.255.240.0
> 24. 4094
> 25. 172.18.16.0
> 26. 172.18.31.255
> ```