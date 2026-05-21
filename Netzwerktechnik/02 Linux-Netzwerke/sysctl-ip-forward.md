
> [!info]
> ## Bedeutung
> `ip_forward`
>
> erlaubt Linux,
> Pakete zwischen Netzwerken weiterzuleiten.

---

# Definition

Standardmäßig arbeitet Linux normalerweise nicht als Router.

Linux empfängt zwar Pakete,
leitet sie aber nicht automatisch weiter.

Mit:

```bash
sysctl -w net.ipv4.ip_forward=1
```

aktiviert man:

```text
IP-Forwarding
```

Dadurch kann Linux Pakete zwischen Netzwerken routen.

---

# Beispiel

```text
Apfel ---- Banane ---- Erdbeere
```

Banane soll als Router arbeiten.

Ohne IP-Forwarding:
- empfängt Banane Pakete
- leitet sie aber nicht weiter

Mit IP-Forwarding:
- routet Banane Pakete zwischen beiden Netzwerken

---

# Aktivieren

## Temporär

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

# Deaktivieren

```bash
sysctl -w net.ipv4.ip_forward=0
```

---

# Prüfen

```bash
cat /proc/sys/net/ipv4/ip_forward
```

---

# Bedeutung der Ausgabe

## Aktiv

```text
1
```

---

## Deaktiviert

```text
0
```

---

# Dauerhaft aktivieren

## Datei bearbeiten

```bash
sudo nano /etc/sysctl.conf
```

---

## Eintrag hinzufügen

```text
net.ipv4.ip_forward=1
```

---

# Änderungen laden

```bash
sudo sysctl -p
```

---

# IPv6

Für IPv6 existiert ebenfalls IP-Forwarding.

---

## Aktivieren

```bash
sysctl -w net.ipv6.conf.all.forwarding=1
```

---

# Typische Einsatzgebiete

- Linux-Router
- NAT
- Container
- Docker
- Kubernetes
- WireGuard
- VPNs
- virtuelle Netzwerke

---

# Beispiel mit NAT

```bash
sysctl -w net.ipv4.ip_forward=1
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

Dadurch kann Linux:
- routen
- NAT durchführen
- Internet weitergeben

---

# Typische Probleme

## Routing funktioniert nicht

Oft fehlt:

```text
IP-Forwarding
```

---

## Container haben kein Internet

Häufig:
- IP-Forwarding deaktiviert
- NAT fehlt

---

## WireGuard funktioniert nicht

Oft fehlt:
- Forwarding
- NAT
- Routing

---

# Unterschied

## Ohne IP-Forwarding

```text
Linux = normales Endgerät
```

---

## Mit IP-Forwarding

```text
Linux = Router
```

---

# Linux-Befehle

## Aktivieren

```bash
sysctl -w net.ipv4.ip_forward=1
```

---

## Deaktivieren

```bash
sysctl -w net.ipv4.ip_forward=0
```

---

## Status prüfen

```bash
cat /proc/sys/net/ipv4/ip_forward
```

---

# Wichtige Merksätze

IP-Forwarding erlaubt Linux das Weiterleiten von Paketen.

Ohne IP-Forwarding arbeitet Linux nicht als Router.

IP-Forwarding wird für Routing und NAT benötigt.

Docker und WireGuard benötigen oft IP-Forwarding.

IP-Forwarding arbeitet auf Layer 3.

---

# Fragen

## Wofür wird IP-Forwarding verwendet?

> [!spoiler]- Lösung anzeigen
> IP-Forwarding erlaubt Linux,
> Pakete zwischen Netzwerken weiterzuleiten.

---

## Wie aktiviert man IP-Forwarding temporär?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> sysctl -w net.ipv4.ip_forward=1
> ```

---

## Wie prüft man,
## ob IP-Forwarding aktiv ist?

> [!spoiler]- Lösung anzeigen
> Mit:
>
> ```bash
> cat /proc/sys/net/ipv4/ip_forward
> ```
>
> Ausgabe:
>
> ```text
> 1 = aktiv
> 0 = deaktiviert
> ```