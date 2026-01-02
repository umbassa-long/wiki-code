# ss vs netstat – Markdown Cheat Sheet

## Kurzfassung

* **ss** = moderner Ersatz für **netstat**
* Schneller, detaillierter, besser filterbar
* Standard auf modernen Linux-Systemen

---

## Grundlegende Befehle

| Zweck             | netstat          | ss          |
| ----------------- | ---------------- | ----------- |
| Alle Verbindungen | `netstat -a`     | `ss -a`     |
| Listening Sockets | `netstat -l`     | `ss -l`     |
| TCP               | `netstat -t`     | `ss -t`     |
| UDP               | `netstat -u`     | `ss -u`     |
| Numerisch         | `netstat -n`     | `ss -n`     |
| Prozesse anzeigen | `netstat -p`     | `ss -p`     |
| Alles kombiniert  | `netstat -tulnp` | `ss -tulnp` |

---

## Häufige Use-Cases

### Welcher Prozess hört auf einem Port?

```bash
ss -tulnp | grep :80
```

### Alle aktiven TCP-Verbindungen

```bash
ss -t state established
```

### HTTPS-Verbindungen (Port 443)

```bash
ss state established '( dport = :443 or sport = :443 )'
```

### IPv4 / IPv6

```bash
ss -4 -tuln   # IPv4
ss -6 -tuln   # IPv6
```

---

## Performance & Debugging

### Verbindungsstatus zählen

```bash
ss -ant | awk '{print $1}' | sort | uniq -c
```

### Hohe Queues erkennen

```bash
ss -lnt
```

Achte auf hohe Werte in **Recv-Q** / **Send-Q**

---

## Ersatz für weitere netstat-Befehle

| netstat      | moderner Ersatz |
| ------------ | --------------- |
| `netstat -r` | `ip route`      |
| `netstat -i` | `ip -s link`    |
| `ifconfig`   | `ip addr`       |

---

## Merkhilfe

* `ss` = **Socket Statistics**
* Nutzt Netlink → schneller als `/proc`
* Ideal für Server, Container, Cloud

---

# grep

🔁 Rekursiv in allen Dateien suchen
```bash
grep -r "THM{" .
```

🔡 Groß-/Kleinschreibung ignorieren
```bash
grep -i "thm{" file.txt
```

🔗 grep + Pipes (sehr wichtig!)
Kombiniert mit cat
```bash
cat notes.txt | grep "THM{"
```

Nur Textdateien durchsuchen
```bash
grep -r "THM{" /var/log --include="*.txt"
```

Ausschließen bestimmter Dateien
```bash
grep -r "THM{" . --exclude="*.bin"
```

📦 In Archiven suchen
unzip archive.zip
```bash
grep -r "THM{" .
```

🔎 Dateien nach Inhalt finden
```bash
find . -type f -exec grep "THM{" {} \;
```

| Befehl | Beschreibung |
| :--- | :--- |
| **ls** | Listet den Inhalt eines Verzeichnisses auf (oft mit `-la` genutzt). |
| **cd** | Wechselt das aktuelle Arbeitsverzeichnis (Change Directory). |
| **cat** | Zeigt den Inhalt einer Datei vollständig im Terminal an. |
| **grep** | Durchsucht Dateien oder Ausgaben nach bestimmten Textmustern. |
| **chmod** | Ändert die Zugriffsrechte (Read, Write, Execute) einer Datei. |
| **chown** | Ändert den Besitzer und die Gruppe einer Datei oder eines Ordners. |
| **cp** | Kopiert Dateien oder ganze Verzeichnisse. |
| **mv** | Verschiebt oder benennt Dateien und Verzeichnisse um. |
| **rm** | Löscht Dateien (mit `-r` auch Verzeichnisse). |
| **mkdir** | Erstellt ein neues Verzeichnis. |
| **touch** | Erstellt eine neue, leere Datei oder aktualisiert den Zeitstempel. |
| **head** / **tail** | Zeigt die ersten bzw. letzten Zeilen einer Datei an (ideal für Logs). |
| **nano** / **vi** | Einfache Texteditoren direkt für die Konsole. |
| **find** | Sucht im Dateisystem nach Dateien basierend auf Namen oder Typ. |
| **df** | Zeigt den verfügbaren Speicherplatz auf den Dateisystemen an. |
| **du** | Schätzt den Speicherverbrauch von Dateien oder Verzeichnissen. |