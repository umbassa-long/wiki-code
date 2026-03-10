Hier ist dein komplettes, strukturiertes **Cheat Sheet** im Markdown-Format. Du kannst diesen Block einfach kopieren und in deine Wissensdatenbank (z. B. Obsidian, Notion oder als `.md` Datei) einfügen.

---

# 🛡️ Cisco Secure Client (v5.1+) Linux Mint Guide

Dieses Cheat Sheet beschreibt die saubere Einrichtung, Wartung und Überwachung des Cisco VPNs unter Linux.

## 1. Zertifikat-Extraktion (.pfx -> .pem)

Cisco benötigt getrennte Dateien für Zertifikat und Schlüssel.

```bash
# 1. Privaten Schlüssel extrahieren (Passwort wird abgefragt)
openssl pkcs12 -in DATEINAME.pfx -nocerts -out vpn_cert.key -nodes

# 2. Zertifikat extrahieren
openssl pkcs12 -in DATEINAME.pfx -clcerts -nokeys -out vpn_cert.pem

# 3. Schlüssel in RSA-Format umwandeln (für Cisco Kompatibilität)
openssl rsa -in vpn_cert.key -out vpn_cert.key

```

## 2. Offizielle Cisco-Struktur (v5.1)

Cisco erwartet in dieser Version eine exakte Unterordner-Struktur im Home-Verzeichnis.

```bash
# Ordner anlegen
mkdir -p ~/.cisco/certificates/client/private
mkdir -p ~/.cisco/certificates/ca

# Dateien kopieren (Zertifikat und Key müssen namensgleich sein!)
cp vpn_cert.pem ~/.cisco/certificates/client/
cp vpn_cert.key ~/.cisco/certificates/client/private/vpn_cert.key

# Vertrauenskette (CAs) vom System verlinken
sudo ln -sf /etc/ssl/certs/* ~/.cisco/certificates/ca/

# Rechte streng setzen (wichtig!)
chmod 700 ~/.cisco/certificates/client/private
chmod 644 ~/.cisco/certificates/client/vpn_cert.pem
chmod 600 ~/.cisco/certificates/client/private/vpn_cert.key

```

## 3. VPN-Profil erstellen (Server-Sperre lösen)

Verhindert den Fehler "Untrusted Server Certificate" und stellt `BlockUntrustedServers` auf `false`.

```bash
sudo nano /opt/cisco/secureclient/vpn/profile/ECKD.xml

```

**Inhalt einfügen:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<AnyConnectProfile xmlns="http://schemas.xmlsoap.org/encoding/">
 <ClientInitialization>
  <BlockUntrustedServers>false</BlockUntrustedServers>
 </ClientInitialization>
 <ServerList>
  <HostEntry>
   <HostName>ECKD VPN</HostName>
   <HostAddress>vpn.eckd.de</HostAddress>
  </HostEntry>
 </ServerList>
</AnyConnectProfile>

```

*Dienst neu starten:* `sudo systemctl restart vpnagentd`

## 4. Komfort-Starter (App + Live-Log)

Erstellt ein Skript, das die App öffnet und gleichzeitig ein Terminal mit Fehlermeldungen zeigt.

1. **Datei erstellen:** `nano ~/vpn_start.sh`
2. **Inhalt:**

```bash
#!/bin/bash
/opt/cisco/secureclient/bin/vpnui &
gnome-terminal --title="VPN Live Log" -- bash -c "journalctl -u vpnagentd -f; exec bash"

```

3. **Ausführbar machen:** `chmod +x ~/vpn_start.sh`
4. **Desktop-Icon:** Neuen Starter anlegen -> Befehl: `/home/DEIN_USER/vpn_start.sh`

## 5. Automatischer Ablauf-Warner (Ablaufdatum)

Erinnert dich 30 Tage vor Ablauf des Zertifikats.

1. **Datei erstellen:** `nano ~/cert_warner.sh`
2. **Inhalt:**

```bash
#!/bin/bash
CERT_FILE="$HOME/.cisco/certificates/client/vpn_cert.pem"
if [ -f "$CERT_FILE" ]; then
    EXPIRY_DATE=$(openssl x509 -enddate -noout -in "$CERT_FILE" | cut -d= -f2)
    EXPIRY_SECONDS=$(date -d "$EXPIRY_DATE" +%s)
    DIFF_DAYS=$(( (EXPIRY_SECONDS - $(date +%s)) / 86400 ))
    if [ "$DIFF_DAYS" -lt 30 ]; then
        notify-send -u critical "VPN Zertifikat Warnung" "Das Zertifikat läuft in $DIFF_DAYS Tagen ab!"
    fi
fi

```

3. **Ausführbar machen:** `chmod +x ~/cert_warner.sh`
4. **Cronjob einrichten:** `crontab -e` eingeben und unten anfügen:

```cron
00 09 * * 1 /home/DEIN_USER/cert_warner.sh

```

*(Prüft jeden Montag um 09:00 Uhr)*

## 6. Diagnose-Kommandos

| Befehl | Zweck |
| --- | --- |
| `journalctl -u vpnagentd -f` | Live-Fehlersuche (Zertifikate, Verbindung) |
| `vnstat -l -i cscotun0` | Live-Traffic innerhalb des Tunnels prüfen |
| `openssl x509 -enddate -noout -in [PFAD]` | Exaktes Ablaufdatum anzeigen |

---

**Notiz [2026-03-01]:** Bei Zertifikatswechsel nur Schritt 1 & 2 wiederholen. Dateinamen beibehalten!