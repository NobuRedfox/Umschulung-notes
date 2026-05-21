
> [!info]
> ## Bedeutung
> VLAN = Virtual Local Area Network

---

# Definition

Ein VLAN teilt ein physisches Netzwerk
in mehrere virtuelle Netzwerke auf.

Dadurch können Geräte logisch getrennt werden,
obwohl sie denselben Switch verwenden.

---

# Beispiel

## Ohne VLAN

```text
PC1 ----\
PC2 ----- Switch
PC3 ----/
```

Alle Geräte befinden sich im selben Netzwerk.

---

## Mit VLAN

```text
VLAN 10:
PC1
PC2

VLAN 20:
PC3
```

Obwohl alle Geräte am selben Switch hängen,
sind die Netzwerke getrennt.

---

# Zweck von VLANs

VLANs werden verwendet für:

- Sicherheit
- Netzwerktrennung
- bessere Organisation
- weniger Broadcasts

---

# Beispiel aus einer Firma

## VLAN 10

```text
Buchhaltung
```

---

## VLAN 20

```text
Entwicklung
```

---

## VLAN 30

```text
Gast-WLAN
```

Die Gruppen sind voneinander getrennt.

---

# Vorteile von VLANs

- Mehr Sicherheit
- Weniger Netzwerkverkehr
- Bessere Struktur
- Mehr Kontrolle

---

# VLAN-ID

Jedes VLAN besitzt eine Nummer.

Beispiel:

```text
VLAN 10
VLAN 20
VLAN 30
```

Mögliche IDs:

```text
1 - 4094
```

---

# Kommunikation zwischen VLANs

Geräte aus unterschiedlichen VLANs
können normalerweise nicht direkt miteinander kommunizieren.

Dafür benötigt man:
- einen Router
- Layer-3-Switch
- Routing

---

# Access Port

Ein Access-Port gehört zu genau einem VLAN.

Beispiel:

```text
PC -> VLAN 10
```

---

# Trunk Port

Ein Trunk transportiert mehrere VLANs gleichzeitig.

Wird oft verwendet zwischen:
- Switches
- Routern
- Servern

---

# VLAN-Tagging

Damit Geräte wissen,
zu welchem VLAN ein Paket gehört,
werden VLAN-Tags verwendet.

Das Standardprotokoll heißt:

```text
IEEE 802.1Q
```

---

# VLAN unter Linux

Linux unterstützt VLANs direkt.

---

# VLAN-Interface erstellen

## Beispiel

```bash
ip link add link eth0 name eth0.10 type vlan id 10
```

Bedeutung:

```text
Erstelle VLAN 10 auf eth0
```

---

# VLAN aktivieren

```bash
ip link set eth0.10 up
```

---

# IP-Adresse vergeben

```bash
ip addr add 192.168.10.5/24 dev eth0.10
```

---

# VLANs anzeigen

```bash
ip link
```

---

# Beispielaufbau

```text
                VLAN 10
PC1 --------\
             \ 
              Switch
             /
PC2 --------/

                VLAN 20
PC3 --------\
             \
              Switch
             /
PC4 --------/
```

---

# VLAN und Switches

Switches verwalten VLANs.

Der Switch entscheidet:
- welches Paket
- zu welchem VLAN gehört

---

# Typische Probleme

## Falsches VLAN

Geräte können nicht kommunizieren.

---

## Trunk falsch konfiguriert

VLANs funktionieren zwischen Switches nicht.

---

## VLAN-Interface nicht aktiv

Dann funktioniert die Verbindung nicht.

---

# VLAN vs Physisches Netzwerk

## Ohne VLAN

```text
Ein großes Netzwerk
```

---

## Mit VLAN

```text
Mehrere getrennte virtuelle Netzwerke
```

---

# Wichtige Merksätze

VLANs teilen Netzwerke logisch auf.

VLANs erhöhen Sicherheit und Ordnung.

Ein VLAN besitzt eine VLAN-ID.

VLANs werden oft auf Switches verwendet.

Zur Kommunikation zwischen VLANs braucht man Routing.

IEEE 802.1Q wird für VLAN-Tagging verwendet.

---

# Fragen

## Wofür wird ein VLAN verwendet?

> [!spoiler]- Lösung anzeigen
> Ein VLAN trennt ein Netzwerk logisch in mehrere virtuelle Netzwerke.

---

## Was ist ein Trunk-Port?

> [!spoiler]- Lösung anzeigen
> Ein Trunk-Port transportiert mehrere VLANs gleichzeitig.

---

## Welches Protokoll wird für VLAN-Tagging verwendet?

> [!spoiler]- Lösung anzeigen
> ```text
> IEEE 802.1Q
> ```