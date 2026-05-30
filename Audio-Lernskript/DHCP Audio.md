
Hallo.

Heute geht es um **DHCP**.

DHCP steht für  
**Dynamic Host Configuration Protocol**.

Das bedeutet:

DHCP verteilt automatisch Netzwerkeinstellungen an Geräte.

Zum Beispiel:

- IP-Adresse
- Subnetzmaske
- Gateway
- DNS-Server

Ohne DHCP müsste man alles von Hand eintragen.

Das wäre bei vielen Geräten ziemlich nervig.

Zum Beispiel:

Du verbindest dein Handy mit WLAN.

Nach ein paar Sekunden funktioniert Internet.

Du musst keine IP-Adresse eingeben.

Warum?

Weil DHCP das automatisch erledigt.

---

## Der DHCP-Ablauf

Der Ablauf heißt **DORA**.

DORA ist leicht zu merken.

D steht für **Discover**

O steht für **Offer**

R steht für **Request**

A steht für **Acknowledge**

---

### 1. Discover

Ein Gerät kommt neu ins Netzwerk.

Es kennt noch keine IP-Adresse.

Deshalb sendet es:

„Hallo DHCP-Server. Gibt es hier jemanden?“

Das nennt man **DHCP Discover**.

Weil das Gerät noch keine Zieladresse kennt, sendet es als Broadcast.

Broadcast heißt:

Alle im Netzwerk bekommen es.

---

### 2. Offer

Der DHCP-Server antwortet:

„Ja. Ich bin da.“

„Du kannst diese IP bekommen.“

Zum Beispiel:

`192.168.1.25`

Dazu schickt er:

- Subnetzmaske
- Gateway
- DNS

Das nennt man **DHCP Offer**

---

### 3. Request

Das Gerät antwortet:

„Okay. Diese Adresse möchte ich haben.“

Das nennt man **DHCP Request**

---

### 4. Acknowledge

Der Server bestätigt:

„Alles klar.“

„Die Adresse gehört jetzt dir.“

Das nennt man **DHCP Acknowledge**

Jetzt kann das Gerät ins Netzwerk.

---

## Beispiel aus dem Alltag

Du kommst nach Hause.

Handy verbindet sich mit WLAN.

DHCP läuft im Hintergrund:

Discover

Offer

Request

Acknowledge

Danach:

WhatsApp, Browser und Internet funktionieren.

Alles automatisch.

---

## Wichtig

DHCP vergibt IP-Adressen meist nur für eine bestimmte Zeit.

Das nennt man **Lease-Zeit**

Zum Beispiel:

`24 Stunden`

Danach verlängert das Gerät die Adresse.

---

## Prüfungsfragen

**Was bedeutet DHCP?**

Antwort:

Dynamic Host Configuration Protocol.

---

**Wofür wird DHCP benutzt?**

Antwort:

Zum automatischen Verteilen von Netzwerkeinstellungen.

---

**Wie heißt die Reihenfolge?**

Antwort:

DORA.

Discover

Offer

Request

Acknowledge.

---

**Was ist ein Broadcast?**

Antwort:

Eine Nachricht an alle Geräte im Netzwerk.

---

**Warum ist DHCP praktisch?**

Antwort:

Weil Geräte automatisch eine IP-Adresse bekommen.

---

Ende.