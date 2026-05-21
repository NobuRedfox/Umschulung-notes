
> [!info]
> ## Bedeutung
> `ip netns`
>
> verwaltet Netzwerk-Namespaces unter Linux.

---

# Definition

Ein Network Namespace ist ein eigener virtueller Netzwerkbereich.

Jeder Namespace besitzt:
- eigene Netzwerkinterfaces
- eigene IP-Adressen
- eigene Routingtabellen
- eigene Firewall-Regeln

Dadurch wirken Namespaces wie kleine virtuelle Computer.

---

# Einsatzgebiete

`ip netns` wird häufig verwendet für:
- Container
- virtuelle Netzwerke
- Netzwerktests
- Docker
- Kubernetes
- Routing-Labs

---

# Namespace erstellen

```bash
ip netns add Apfel
```

Erstellt einen neuen Namespace namens:

```text
Apfel
```

---

# Namespaces anzeigen

```bash
ip netns list
```

---

# In Namespace wechseln

```bash
ip netns exec Apfel bash
```

Öffnet eine Shell innerhalb des Namespaces.

Danach arbeitet man direkt im Container.

---

# Namespace verlassen

```bash
exit
```

oder:

```text
Strg + D
```

---

# Namespace löschen

```bash
ip netns del Apfel
```

---

# Beispiel

## Namespace erstellen

```bash
ip netns add Apfel
```

---

## Loopback aktivieren

```bash
ip netns exec Apfel ip link set lo up
```

---

## IP-Adressen anzeigen

```bash
ip netns exec Apfel ip addr
```

---

# Warum Loopback aktivieren?

Das Interface:

```text
lo
```

ist standardmäßig deaktiviert.

Viele Programme funktionieren ohne Loopback nicht richtig.

---

# Befehle im Namespace ausführen

```bash
ip netns exec Apfel ping 127.0.0.1
```

---

# Netzwerkinterfaces verschieben

Ein Interface kann in einen Namespace verschoben werden.

---

## Beispiel

```bash
ip link set veth0 netns Apfel
```

Danach gehört das Interface dem Namespace `Apfel`.

---

# Virtuelle Kabel

Mit `veth` kann man Namespaces verbinden.

---

## Beispiel

```bash
ip link add veth-A type veth peer name veth-B
```

---

## Aufbau

```text
Namespace A ---- veth ---- Namespace B
```

---

# Beispiel mit Routing

```text
Apfel ---- Banane ---- Erdbeere
```

Banane kann als Router arbeiten.

---

# Namespace besitzt eigenes Netzwerk

Innerhalb eines Namespaces funktionieren:
- eigene IP-Adressen
- eigenes Routing
- eigene Interfaces

unabhängig vom Hostsystem.

---

# Vergleich

## Hostsystem

```text
Eigenes Netzwerk
```

---

## Namespace

```text
Separater virtueller Netzwerkbereich
```

---

# Typische Einsatzgebiete

- Container simulieren
- Routing testen
- VLANs testen
- NAT testen
- virtuelle Netzwerke aufbauen

---

# Typische Probleme

## Loopback nicht aktiv

Dann funktionieren viele Programme nicht.

---

## Kein Interface vorhanden

Dann besitzt der Namespace keine Netzwerkverbindung.

---

## Interface DOWN

Dann funktioniert die Verbindung nicht.

---

# Linux-Befehle

## Namespace erstellen

```bash
ip netns add Apfel
```

---

## Namespaces anzeigen

```bash
ip netns list
```

---

## Befehl im Namespace ausführen

```bash
ip netns exec Apfel ip addr
```

---

## Namespace löschen

```bash
ip netns del Apfel
```

---

# Unterschied zu virtuellen Maschinen

## Namespace

- nutzt denselben Linux-Kernel
- sehr leichtgewichtig
- schnell

---

## Virtuelle Maschine

- eigener Kernel
- mehr Ressourcen
- vollständiges Betriebssystem

---

# Wichtige Merksätze

`ip netns` verwaltet Netzwerk-Namespaces.

Namespaces besitzen eigene Netzwerkinterfaces und Routingtabellen.

Namespaces verhalten sich ähnlich wie kleine Container.

`ip netns exec` führt Befehle innerhalb eines Namespaces aus.

Network Namespaces werden häufig für Container verwendet.

---

# Fragen

## Wofür wird `ip netns` verwendet?

> [!spoiler]- Lösung anzeigen
> `ip netns` verwaltet virtuelle Netzwerk-Namespaces unter Linux.

---

## Wie erstellt man einen Namespace?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip netns add Apfel
> ```

---

## Wie führt man einen Befehl innerhalb eines Namespaces aus?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip netns exec Apfel <Befehl>
> ```