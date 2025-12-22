# Internet gelöscht

## Suche nach öffentlicher Ordnerauflistung (Directory Listing):

 site:(Name der Seite ohne https://) intitle:"Index of /"

-  Lektion: Wenn diese Suche Ergebnisse liefert, bedeutet dies, dass der Server bei Eingabe eines falschen Pfades eine Liste aller Dateien und Unterordner anzeigt.

## Suche nach bestimmten Dateitypen im öffentlichen Bereich:

site:example.com filetype:xls

-  Lektion: alle Dateien mit einer bestimmten Endung im öffentlichen Bereich der Webseite


3. wget -r -np -k -p https://example.com
 - -r = rekursiv
 - -np = nicht zum Elternverzeichnis hochgehen
 - -k = Links anpassen, sodass sie lokal funktionieren
 - -p = alle benötigten Ressourcen(Bilder, CSS, JS) mitnehmen

# 🧭 Google Dorks – Top 20 Cheat Sheet

Google Dorks (auch „Site Hacks“) nutzen erweiterte Suchoperatoren,
um öffentlich zugängliche, aber oft unbeabsichtigt exponierte Inhalte zu finden.

---

## 🔎 Grundlegende Operatoren

| Operator | Beschreibung | Beispiel |
|--------|--------------|----------|
| `site:` | Suche auf einer Domain | `site:example.com` |
| `intitle:` | Suchbegriff im Titel | `intitle:"index of"` |
| `inurl:` | Suchbegriff in URL | `inurl:admin` |
| `filetype:` | Dateityp suchen | `filetype:pdf` |
| `cache:` | Google-Cache anzeigen | `cache:example.com` |

---

## 🧭 Top 20 Google Dorks

### 1️⃣ Offene Verzeichnisse
```text
intitle:"index of"
```

### 2️⃣ Admin-Logins finden
```text
inurl:admin login
```

### 3️⃣ Öffentliche Konfigurationsdateien
```text
filetype:env
```
### 4️⃣ Backup-Dateien
```text
filetype:bak OR filetype:backup
```

### 5️⃣ Datenbanken (SQL Dumps)
```text
filetype:sql
```

### 6️⃣ Öffentliche Log-Dateien
```text
filetype:log
```

### 7️⃣ Passwort-Dateien
```text
intext:"password" filetype:txt
```

### 8️⃣ Git-Repositories
```text
inurl:.git
```

### 9️⃣ Apache Status Pages
```text
inurl:server-status
```
### 🔟 Kameras & IoT-Geräte
```text
intitle:"Live View" inurl:view
```

### 1️⃣1️⃣ PHP-Info-Seiten
```text
intitle:"phpinfo()"
```

### 1️⃣2️⃣ Admin-Panels (generisch)
```text
inurl:admin OR inurl:login
```

### 1️⃣3️⃣ Öffentliche Dokumente
```text
filetype:doc OR filetype:xls OR filetype:pdf
```

### 1️⃣4️⃣ Konfigurationsdateien
```text
filetype:xml OR filetype:conf
```

### 1️⃣5️⃣ Fehler- & Debug-Seiten
```text
intext:"Fatal error" filetype:php
```

### 1️⃣6️⃣ VPN / Zugangsdaten
```text
intext:"vpn" filetype:txt
```

### 1️⃣7️⃣ Exposed APIs
```text
inurl:api filetype:json
```

### 1️⃣8️⃣ WordPress Admin
```text
inurl:/wp-admin
```

### 1️⃣9️⃣ WordPress Backups
```text
inurl:wp-content filetype:zip
```

### 2️⃣0️⃣ Öffentliche Jenkins-Dashboards
```text
intitle:"Dashboard [Jenkins]"
```

