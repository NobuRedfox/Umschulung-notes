## Definition

SSH (Secure Shell) ermöglicht eine verschlüsselte Verbindung zu entfernten Systemen.

SSH wird verwendet für:

- Remote Login
- Dateiübertragung
- Administration von Servern
- Public-Key-Authentifizierung

---

## Begriffe

### Host Key

Identifiziert den Server.

Gespeichert in:

```text
~/.ssh/known_hosts
```

---

### TOFU

**Trust On First Use**

Beim ersten Verbindungsaufbau wird der Host Key akzeptiert und gespeichert.

---

### Public Key Authentication

Anmeldung ohne Passwort.

Der Public Key wird auf dem Server hinterlegt.

Der Private Key bleibt beim Benutzer.

---

### authorized_keys

Datei mit erlaubten Public Keys.

```text
~/.ssh/authorized_keys
```

---

## SSH Schlüssel erzeugen

```bash
ssh-keygen -t ed25519
```

---

## Verbindung herstellen

```bash
ssh tux@192.168.178.51
```

---

## Public Key kopieren

```bash
ssh-copy-id tux@192.168.178.51
```

---

## SSH Server installieren

```bash
sudo apt install openssh-server
```

Status prüfen:

```bash
systemctl status ssh.service
```

---

## Benutzer anlegen

```bash
sudo useradd -m -s /bin/bash tux
sudo passwd tux
```

---

## Rechte für SSH

Das Verzeichnis `.ssh` darf nur vom Besitzer gelesen und geschrieben werden.

Verzeichnis:

```bash
chmod 700 ~/.ssh
```

Datei:

```bash
chmod 600 ~/.ssh/authorized_keys
```

---

## Beispiel authorized_keys

```text
# ~/.ssh/authorized_keys

ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIFAkj6T926MwRwMn5vnDBHk+b6EQWKnvvVDR5FVf0tpu AEROPAG@AEROPAG
```

---

## SSH Server Konfiguration

Datei:

```text
/etc/ssh/sshd_config
```

Wichtige Einstellungen:

```text
PasswordAuthentication no
PermitRootLogin no
AllowUsers tux
Port 2222
```

### Bedeutung

```text
PasswordAuthentication no
```

Passwort-Login deaktivieren.

---

```text
PermitRootLogin no
```

Root-Anmeldung verbieten.

---

```text
AllowUsers tux
```

Nur bestimmte Benutzer erlauben.

---

```text
Port 2222
```

SSH auf anderem Port betreiben.

---

## SSH Client Konfiguration

Datei:

```text
~/.ssh/config
```

Beispiel:

```text
Host foobar
    User tux
    HostName 192.168.178.123
```

Verbindung:

```bash
ssh foobar
```

---

## Dateien kopieren

Datei auf Server kopieren:

```bash
scp datei.txt tux@host:~/datei.txt
```

Datei vom Server herunterladen:

```bash
scp tux@host:~/datei.txt .
```

---

## Dienst deaktivieren

SSH nicht automatisch starten:

```bash
sudo systemctl disable ssh.service
sudo systemctl disable ssh.socket
```

---

## Typischer Ablauf

1. SSH Server installieren

```bash
sudo apt install openssh-server
```

2. Benutzer anlegen

```bash
sudo useradd -m -s /bin/bash tux
sudo passwd tux
```

3. Schlüssel erzeugen

```bash
ssh-keygen -t ed25519
```

4. Public Key kopieren

```bash
ssh-copy-id tux@host
```

5. Verbindung testen

```bash
ssh tux@host
```

6. Passwort-Login deaktivieren

```text
PasswordAuthentication no
```

---

## Merksätze

- SSH überträgt Daten verschlüsselt
- Public Key darf verteilt werden
- Private Key bleibt geheim
- authorized_keys enthält erlaubte Public Keys
- known_hosts enthält bekannte Server
- Passwort-Login und Public-Key-Login sind unabhängige Verfahren
- SSH wird für Remote-Administration und Dateiübertragung verwendet