
> [!info]
> ## Ziel
> Ein virtueller Container soll Internetzugriff erhalten.
>
> Das Hostsystem arbeitet dabei als Router.

---

# Definition

Ein Container besitzt standardmäßig keine Internetverbindung.

Damit ein Container ins Internet kommt,
muss das Hostsystem:
- Routing durchführen
- NAT/Masquerading verwenden

---

# Aufbau

```text
Container ---- Host ---- Internet
```

---

# Beispiel

```text
Container:
10.0.0.2
```

```text
Host:
10.0.0.1
```

Der Host leitet die Pakete ins Internet weiter.

---

# Begriffe

## Router

Der Host arbeitet als Router.

---

## NAT

Der Host übersetzt:
- private IP-Adressen
- in öffentliche IP-Adressen

---

## Masquerading

Linux-Funktion für einfaches NAT.

---

# Virtuelles Kabel erstellen

```bash
ip link add veth-host type veth peer name veth-container
```

---

# Aufbau

```text
veth-host <----> veth-container
```

---

# Container erstellen

```bash
ip netns add Apfel
```

---

# Kabel in Container verschieben

```bash
ip link set veth-container netns Apfel
```

---

# IP-Adressen vergeben

## Host

```bash
ip addr add 10.0.0.1/24 dev veth-host
```

---

## Container

```bash
ip netns exec Apfel ip addr add 10.0.0.2/24 dev veth-container
```

---

# Interfaces aktivieren

## Host

```bash
ip link set veth-host up
```

---

## Container

```bash
ip netns exec Apfel ip link set lo up
ip netns exec Apfel ip link set veth-container up
```

---

# Default Route setzen

```bash
ip netns exec Apfel ip route add default via 10.0.0.1
```

Bedeutung:

```text
Unbekannte Ziele an den Host schicken
```

---

# IP-Forwarding aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

Dadurch darf Linux Pakete weiterleiten.

---

# NAT aktivieren

```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

---

# Bedeutung

```text
Private Container-IP in öffentliche Host-IP übersetzen
```

---

# DNS konfigurieren

Damit Domainnamen funktionieren:

```bash
mkdir -p /etc/netns/Apfel
```

---

## DNS setzen

```bash
echo "nameserver 8.8.8.8" > /etc/netns/Apfel/resolv.conf
```

---

# Komplettes Script

```bash
set -ex

# Internet-Interface automatisch erkennen
INTERNET_IF=$(ip route | grep default | awk '{print $5}' | head -1)

# Alte Sachen löschen
ip netns del Apfel 2>/dev/null || true
ip link del veth-host 2>/dev/null || true

# Container erstellen
ip netns add Apfel

# Virtuelles Kabel erstellen
ip link add veth-host type veth peer name veth-container

# Kabel in Container verschieben
ip link set veth-container netns Apfel

# IP-Adressen vergeben
ip addr add 10.0.0.1/24 dev veth-host
ip netns exec Apfel ip addr add 10.0.0.2/24 dev veth-container

# Interfaces aktivieren
ip link set veth-host up

ip netns exec Apfel ip link set lo up
ip netns exec Apfel ip link set veth-container up

# Default Route setzen
ip netns exec Apfel ip route add default via 10.0.0.1

# IP-Forwarding aktivieren
sysctl -w net.ipv4.ip_forward=1

# NAT aktivieren
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -o $INTERNET_IF -j MASQUERADE

# DNS konfigurieren
mkdir -p /etc/netns/Apfel
echo "nameserver 8.8.8.8" > /etc/netns/Apfel/resolv.conf

# Verbindung testen
ip netns exec Apfel ping -c3 10.0.0.1
ip netns exec Apfel ping -c3 8.8.8.8
ip netns exec Apfel ping -c3 google.com

# Shell öffnen
ip netns exec Apfel bash
```

---

# Verbindung testen

## Host erreichbar?

```bash
ip netns exec Apfel ping 10.0.0.1
```

---

## Internet erreichbar?

```bash
ip netns exec Apfel ping 8.8.8.8
```

---

## DNS funktioniert?

```bash
ip netns exec Apfel ping google.com
```

---

# Typische Probleme

## Kein Internet

Oft fehlt:
- NAT
- IP-Forwarding
- Default Route

---

## DNS funktioniert nicht

Dann geht oft:

```bash
ping 8.8.8.8
```

aber:

```bash
ping google.com
```

nicht.

---

## Interface DOWN

Dann funktioniert die Verbindung nicht.

---

# Wichtige Merksätze

Container benötigen Routing für Internetzugriff.

Das Hostsystem arbeitet als Router.

Masquerading ermöglicht NAT unter Linux.

IP-Forwarding erlaubt Linux das Weiterleiten von Paketen.

Ohne DNS funktionieren Domainnamen nicht.

---

# Fragen

## Warum braucht der Container eine Default Route?

> [!spoiler]- Lösung anzeigen
> Damit unbekannte Netzwerke an den Host-Router geschickt werden.

---

## Wofür wird Masquerading verwendet?

> [!spoiler]- Lösung anzeigen
> Masquerading führt NAT durch und übersetzt private IP-Adressen in öffentliche IP-Adressen.

---

## Warum wird IP-Forwarding benötigt?

> [!spoiler]- Lösung anzeigen
> Damit Linux Pakete zwischen Netzwerken weiterleiten darf.