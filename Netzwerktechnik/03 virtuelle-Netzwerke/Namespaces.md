
> [!info]
> ## Bedeutung
> Namespaces trennen Ressourcen voneinander.
>
> Dadurch entstehen isolierte Bereiche innerhalb desselben Linux-Systems.

---

# Definition

Ein Namespace erstellt eine isolierte Umgebung.

Programme innerhalb eines Namespaces sehen:
- eigene Netzwerkinterfaces
- eigene Prozesse
- eigene Hostnamen
- eigene Mountpoints

Dadurch wirken Namespaces wie kleine virtuelle Computer oder Container.

---

# Zweck

Namespaces werden verwendet für:
- Container
- Docker
- Kubernetes
- virtuelle Netzwerke
- Sicherheit
- Isolation

---

# Network Namespace

Der wichtigste Namespace für Netzwerke ist:

```text
Network Namespace
```

Er besitzt:
- eigene IP-Adressen
- eigene Routingtabellen
- eigene Interfaces
- eigene Firewallregeln

---

# Beispiel

## Hostsystem

```text
eth0
192.168.0.10
```

---

## Namespace

```text
veth0
10.0.0.2
```

Beide Netzwerke sind voneinander getrennt.

---

# Namespace erstellen

```bash
ip netns add Apfel
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

Danach arbeitet man direkt innerhalb des Namespaces.

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

# Loopback aktivieren

Der Loopback-Adapter ist standardmäßig deaktiviert.

---

## Aktivieren

```bash
ip netns exec Apfel ip link set lo up
```

---

# Netzwerkinterface verschieben

Ein Interface kann in einen Namespace verschoben werden.

---

## Beispiel

```bash
ip link set veth0 netns Apfel
```

Danach gehört das Interface dem Namespace `Apfel`.

---

# Virtuelle Kabel

Namespaces werden oft mit `veth` verbunden.

---

## Beispiel

```bash
ip link add veth-A type veth peer name veth-B
```

---

# Aufbau

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

# Unterschied zu virtuellen Maschinen

## Namespace

- gemeinsamer Linux-Kernel
- leichtgewichtig
- schnell
- wenig Ressourcen

---

## Virtuelle Maschine

- eigener Kernel
- vollständiges Betriebssystem
- mehr Ressourcen

---

# Namespace-Arten

Linux besitzt mehrere Namespace-Typen.

---

## Network Namespace

```text
Netzwerke trennen
```

---

## PID Namespace

```text
Prozesse trennen
```

---

## Mount Namespace

```text
Dateisysteme trennen
```

---

## UTS Namespace

```text
Hostnamen trennen
```

---

## User Namespace

```text
Benutzerrechte trennen
```

---

# Container-Technologien

Viele Container-Systeme verwenden Namespaces:

- Docker
- Podman
- Kubernetes
- LXC

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

## Namespace betreten

```bash
ip netns exec Apfel bash
```

---

## Namespace löschen

```bash
ip netns del Apfel
```

---

## Interfaces anzeigen

```bash
ip netns exec Apfel ip addr
```

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

# Wichtige Merksätze

Namespaces erzeugen isolierte Bereiche unter Linux.

Network Namespaces besitzen eigene Netzwerkeinstellungen.

Namespaces verhalten sich ähnlich wie kleine Container.

Docker und Kubernetes verwenden Namespaces.

Namespaces teilen sich denselben Linux-Kernel.

---

# Fragen

## Wofür werden Namespaces verwendet?

> [!spoiler]- Lösung anzeigen
> Namespaces trennen Ressourcen voneinander und erzeugen isolierte Bereiche.

---

## Wie erstellt man einen Network Namespace?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> ip netns add Apfel
> ```

---

## Welche bekannte Container-Technologie verwendet Namespaces?

> [!spoiler]- Lösung anzeigen
> Beispiele:
>
> - Docker
> - Kubernetes
> - Podman
> - LXC