
> [!info]
> ## Erklärung
>
> SSH steht für:
>
> ```text
> Secure Shell
> ```
>
> SSH ermöglicht sichere Verbindungen zu anderen Computern über das Netzwerk.
>
> Mit SSH kann man:
>
> - sich auf Server verbinden
> - Dateien übertragen
> - Remote-Systeme verwalten
> - GitHub mit SSH verwenden

---

# SSH Verbindung

## Erklärung

Mit `ssh` verbindet man sich zu einem anderen Computer.

### Beispiel

```bash
ssh user@server
```

---

## Beispiel mit IP

```bash
ssh max@192.168.0.10
```

---

# Aufbau

| Teil | Bedeutung |
|---|---|
| `ssh` | SSH-Befehl |
| `user` | Benutzername |
| `@` | Trenner |
| `server` | Server oder IP-Adresse |

---

# Erster Verbindungsaufbau

## Erklärung

Beim ersten Login fragt SSH nach einem Fingerprint.

### Beispiel

```text
Are you sure you want to continue connecting?
```

Antwort:

```text
yes
```

---

# SSH-Key

## Erklärung

SSH-Keys ermöglichen Login ohne Passwort.

Ein Key besteht aus:

- Private Key
- Public Key

---

> [!warning]
> ## Wichtig
>
> Der Private Key darf niemals weitergegeben werden.

---

# SSH-Key erstellen

## Beispiel

```bash
ssh-keygen -t ed25519 -C "mail@example.com"
```

---

# Erklärung

| Teil | Bedeutung |
|---|---|
| `ssh-keygen` | erstellt SSH-Key |
| `-t ed25519` | Key-Typ |
| `-C` | Kommentar |

---

# Speicherort

## Standardpfad

```text
~/.ssh/
```

---

# Typische Dateien

| Datei | Bedeutung |
|---|---|
| `id_ed25519` | Private Key |
| `id_ed25519.pub` | Public Key |

---

# Public Key anzeigen

## Beispiel

```bash
cat ~/.ssh/id_ed25519.pub
```

---

# SSH-Agent

## Erklärung

Der SSH-Agent speichert Keys temporär im Speicher.

---

# Agent starten

## Beispiel

```bash
eval "$(ssh-agent -s)"
```

---

# Key hinzufügen

## Beispiel

```bash
ssh-add ~/.ssh/id_ed25519
```

---

# GitHub mit SSH

## Erklärung

GitHub unterstützt SSH-Verbindungen.

---

# SSH testen

## Beispiel

```bash
ssh -T git@github.com
```

---

# Repository mit SSH klonen

## Beispiel

```bash
git clone git@github.com:user/repo.git
```

---

# HTTPS vs SSH

| HTTPS | SSH |
|---|---|
| einfacher Einstieg | komfortabler |
| Passwort/Login nötig | SSH-Key |
| häufig für Anfänger | häufig für Entwickler |

---

# Dateien übertragen

## scp

### Erklärung

`scp` kopiert Dateien über SSH.

### Beispiele

```bash
scp datei.txt user@server:/home/user/

scp user@server:/home/user/datei.txt .
```

---

# Ordner kopieren

## Beispiel

```bash
scp -r projekt/ user@server:/home/user/
```

---

# SSH Config

## Erklärung

Mit einer SSH-Config können Verbindungen vereinfacht werden.

---

# Config-Datei

## Pfad

```text
~/.ssh/config
```

---

# Beispiel

```text
Host meinserver
    HostName 192.168.0.10
    User max
```

---

# Verbindung nutzen

## Beispiel

```bash
ssh meinserver
```

---

# Ports

## Erklärung

SSH verwendet standardmäßig Port `22`.

---

# Anderen Port verwenden

## Beispiel

```bash
ssh -p 2222 user@server
```

---

# Bekannte Hosts

## Erklärung

SSH speichert bekannte Server.

---

# Datei

```text
~/.ssh/known_hosts
```

---

# Fingerprint entfernen

## Beispiel

```bash
ssh-keygen -R server
```

---

# Rechte für SSH-Dateien

## Erklärung

SSH benötigt sichere Dateirechte.

### Beispiele

```bash
chmod 700 ~/.ssh

chmod 600 ~/.ssh/id_ed25519
```

---

# Häufige Probleme

## Permission denied

### Ursache

- falscher Benutzer
- falscher Key
- fehlender SSH-Agent

---

## Connection refused

### Ursache

- SSH läuft nicht
- falscher Port
- Firewall blockiert Verbindung

---

## Host key verification failed

### Ursache

Server-Fingerprint hat sich geändert.

---

# SSH unter Linux

## SSH Server installieren

### Debian/Ubuntu

```bash
sudo apt install openssh-server
```

---

# SSH Dienst starten

## Beispiel

```bash
sudo systemctl start ssh
```

---

# SSH Status prüfen

## Beispiel

```bash
sudo systemctl status ssh
```

---

# Wichtige Dateien

| Datei | Bedeutung |
|---|---|
| `~/.ssh/config` | SSH-Konfiguration |
| `known_hosts` | bekannte Server |
| `authorized_keys` | erlaubte Public Keys |

---

# authorized_keys

## Erklärung

Enthält erlaubte Public Keys für Login.

---

# Beispiel

```text
~/.ssh/authorized_keys
```

---

# Nützliche Befehle

## SSH Verbindung

```bash
ssh user@server
```

---

## Key erzeugen

```bash
ssh-keygen -t ed25519
```

---

## GitHub testen

```bash
ssh -T git@github.com
```

---

## Datei kopieren

```bash
scp file.txt user@server:/home/user/
```

---

# Verwandte Themen

- [[Linux]]
- [[Shell]]
- [[Git]]
- [[GitHub]]
- [[Netzwerk]]
- [[Server]]

---

> [!important]
> ## Merksatz
>
> SSH ermöglicht sichere Remote-Verbindungen und Dateiübertragungen.

---

# Fragen

## Was bedeutet SSH?

> [!spoiler]- Lösung anzeigen
> Secure Shell.

---

## Wofür wird SSH verwendet?

> [!spoiler]- Lösung anzeigen
> Für sichere Verbindungen zu anderen Computern.

---

## Was macht `ssh-keygen`?

> [!spoiler]- Lösung anzeigen
> Erstellt SSH-Keys.

---

## Unterschied zwischen Public und Private Key?

> [!spoiler]- Lösung anzeigen
> Public Key darf geteilt werden.
>
> Private Key muss geheim bleiben.

---

## Was macht `scp`?

> [!spoiler]- Lösung anzeigen
> Kopiert Dateien über SSH.

---

## Was macht `ssh -T git@github.com`?

> [!spoiler]- Lösung anzeigen
> Testet die SSH-Verbindung zu GitHub.