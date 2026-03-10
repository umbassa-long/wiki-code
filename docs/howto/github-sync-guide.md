
---

# 🚀 GitHub Repository Pflege & Fehleranalyse

Dieses How-To beschreibt den sicheren Workflow für die Arbeit mit VS Code und GitHub, besonders wenn das Projekt länger nicht angefasst wurde.

## 1. Der "Wieder-Einstieg" (Nach einer Pause)

Bevor du ein einziges Zeichen änderst: **Immer** den lokalen Stand mit GitHub abgleichen.

```powershell
# 1. Den aktuellen Ordner prüfen
pwd

# 2. Den Status prüfen (Gibt es noch ungespeicherte lokale Reste?)
git status

# 3. Den neuesten Stand von GitHub ziehen
git pull origin main

```

## 2. Der Arbeits-Zyklus (Änderungen hochladen)

Nachdem du deine `.md`-Dateien oder die `mkdocs.yml` bearbeitet hast:

```powershell
# 1. Alle Änderungen für den Versand markieren
git add .

# 2. Den Stand lokal speichern (Commit)
git commit -m "Update: Dokumentation ergänzt (Datum: $(Get-Date -Format 'dd.MM.yyyy'))"

# 3. Zu GitHub schieben
git push origin main

```

## 3. Erfolgskontrolle (Hat der Push funktioniert?)

Woher weißt du, dass alles geklappt hat?

1. **Terminal-Check:** Wenn am Ende steht `To https://github.com/... [new branch] main -> main`, war der Transfer erfolgreich.
2. **GitHub Webseite:** Gehe auf dein Repository -> Klicke oben auf den Reiter **"Actions"**.
* Ein **grüner Haken** bedeutet: Das Wiki wurde erfolgreich neu gebaut.
* Ein **rotes X** bedeutet: Es gibt einen Fehler in der Struktur (meist in der `yml`-Datei).



## 4. Fehleranalyse & Reparatur

### Problem A: "Rejected - Non-fast-forward"

*Ursache:* Du hast auf GitHub (Webseite) etwas geändert, was noch nicht auf deinem PC ist.
*Lösung:*

```powershell
git pull origin main --rebase
git push origin main

```

### Problem B: "Merge Conflicts"

*Ursache:* Du hast dieselbe Zeile lokal UND auf GitHub geändert.
*Lösung:* VS Code markiert die Stellen farbig (Lila/Blau). Wähle "Accept Incoming Change" oder "Accept Current Change", speichere die Datei und wiederhole den "Arbeits-Zyklus" (Schritt 2).

### Problem C: Die Webseite (Wiki) aktualisiert sich nicht

*Ursache:* Fehler in der `mkdocs.yml` oder ein hängender GitHub-Server.
*Lösung:*

* Prüfe die Einrückungen in der `.yml` (Immer 2 Leerzeichen, keine Tabs!).
* Schau unter **"Actions"** auf GitHub nach der Fehlermeldung.

## 5. Was ist noch wichtig? (Profi-Tipps)

1. **Dateinamen:** Verwende keine Umlaute (ä, ö, ü) oder Leerzeichen in Dateinamen. Nutze stattdessen Bindestriche: `vpn-anleitung.md`.
2. **Anonymität:** Bevor du `git add .` machst, öffne die Suche (`Strg + F`) und suche nach deinem Klarnamen oder privaten IPs, um sicherzugehen, dass nichts "rutscht".
3. **Zustand speichern:** Wenn du mittendrin aufhören musst, mach trotzdem einen Commit. Du musst nicht sofort pushen, aber der lokale Stand ist dann gesichert.

---

### Markierung für die Zukunft [2026-03-10]

* **Routine:** Erst `pull`, dann `edit`, dann `push`.
* **Sicherheit:** Private Keys/Passwörter bleiben in der `.gitignore`.
* **Analyse:** GitHub "Actions" Tab ist die erste Anlaufstelle bei Fehlern.

---

 **`mkdocs serve`** ist „das lokale Testlabor“.

 `mkdocs serve` zeigt **sofort** und **live** auf deinem eigenen Rechner an, wie das Wiki aussehen wird.

Hier ist das How-To, wie dieses Werkzeug genutzt wird, um Fehler zu vermeiden, bevor sie im Internet landen.

---

# 🛠️ Lokal Testen mit `mkdocs serve`

Stell dir vor, `mkdocs serve` ist ein kleiner, privater Webserver, der nur auf deinem Laptop läuft.

## 1. Was macht der Befehl genau?

* **Live-Vorschau:** Er baut dein Wiki im Arbeitsspeicher zusammen.
* **Auto-Reload:** Sobald du eine `.md`-Datei oder die `mkdocs.yml` speicherst (`Strg + S`), aktualisiert sich die Ansicht im Browser automatisch.
* **Fehler-Check:** Er warnt dich im Terminal sofort, wenn ein Link kaputt ist oder die `yml`-Datei einen Syntax-Fehler hat.

## 2. So benutzt du es (Schritt für Schritt)

1. Öffne dein Terminal in VS Code im Hauptverzeichnis deines Wikis.
2. Gib den Befehl ein:
```powershell
mkdocs serve

```


3. **Die Adresse:** Im Terminal erscheint nun eine Zeile wie diese:
`[INFO] - Serving on http://127.0.0.1:8000/`
4. Halte `Strg` gedrückt und klicke auf den Link (oder kopiere ihn in deinen Browser).

## 3. Der Workflow ("Sicherheits-Check")

Bevor du deine Daten zu GitHub schickst (`git push`), solltest du diesen Ablauf nutzen:

1. **Start:** `mkdocs serve` im Hintergrund laufen lassen.
2. **Schreiben:** Änderungen in den `.md`-Dateien vornehmen.
3. **Prüfen:** Im Browser schauen: Sieht das Layout gut aus? Funktionieren die Bilder? Ist das Menü in der `mkdocs.yml` richtig eingerückt?
4. **Beenden:** Wenn alles passt, drückst du im Terminal **`Strg + C`**, um den Testserver zu stoppen.
5. **Veröffentlichen:** Erst jetzt machst du `git add`, `commit` und `push`.

---

## 4. Troubleshooting bei `mkdocs serve`

| Fehlermeldung | Bedeutung | Lösung |
| --- | --- | --- |
| `Command not found` | MkDocs ist nicht installiert. | `pip install mkdocs` (oder `mkdocs-material`) |
| `Config file not found` | Du bist im falschen Ordner. | Mit `cd ..` oder `cd docs` zum Ordner mit der `mkdocs.yml` navigieren. |
| `Aborted with 1 errors` | Ein Link ist falsch oder die YAML ist defekt. | Die Fehlermeldung direkt darüber im Terminal lesen – sie nennt meist die Zeilennummer. |

---

### Markierung für die Zukunft [2026-03-10]

* **Lokal:** `mkdocs serve` -> Schnelle Korrektur von Designfehlern.
* **Remote:** `git push` -> Veröffentlichung für die Welt.
* **Wichtig:** `mkdocs serve` zeigt auch private Daten an, die du noch nicht gelöscht hast – perfekt für eine letzte "Zensur-Kontrolle"!

---

