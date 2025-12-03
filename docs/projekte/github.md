# Github 

## **GitHub-Account einrichten**

1. **Registrieren:** Gehe auf die GitHub-Website und klicke auf 
<a href="https://github.com/signup" target="_blank">Sign Up</a>

2. **Daten eingeben:** Folge den Anweisungen, gib deine E-Mail-Adresse ein, wähle ein starkes Passwort und einen **Benutzernamen**.

3. **Verifizieren:** Bestätige deine E-Mail-Adresse über den Link, den du erhältst.

## **Neues Projekt (Repository) erstellen**

1. **Repository erstellen:** Logge dich bei GitHub ein. Klicke oben rechts auf das **Pluszeichen** (+) und wähle **"New repository"** (Neues Repository).

2. **Namen wählen:** Gib einen kurzen, prägnanten **Repository-Namen** ein (z. B. mein-erstes-projekt).

3. **Beschreibung** (optional): Füge eine kurze Beschreibung deines Projekts hinzu.

4.  **Sichtbarkeit:** Wähle zwischen **"Public"** (öffentlich, jeder kann es sehen) und **"Private"** (privat, nur du und eingeladene Mitarbeiter können es sehen).

5.  **Initialisierung** (optinal): Aktiviere das Kästchen **"Add a README file"** (README-Datei hinzufügen). Das ist eine gute Praxis, da die README-Datei oft eine Projektbeschreibung enthält.

6. **Erstellen:** Klicke auf **"Create repository"**.

## **Codespaces**
### **Einrichten**

Du musst nichts manuell verlinken, da Codespaces immer direkt mit einem deiner GitHub-Repositorys verbunden sind.

1. **Navigiere zum Repository:** Gehe auf GitHub zu dem Repository, das du verwalten möchtest (das, welches du im ersten Schritt eingerichtet hast, z. B. `mein-erstes-projekt`)


<div class="hover-container">
    <!-- Der Text/Link, über den man hovern soll -->
    <a href="/wiki-code/bilder/github-navrepository.png" class="mein-link">Fahren Sie mit der Maus hier rüber</a>
    
    <!-- Das Bild, das beim Hovern erscheinen soll -->
    <img=src"../bilder/github-navrepository.png" alt="Hover-Bild" class="hover-bild">
</div>


2. **Codespace starten:** Klicke auf den grünen Button 
`< > Code`.
![CodeButton](../bilder/github-codespace-button.png)


3. **Wähle Codespaces:** Wechsle zum Tab "Codespaces".

4. **Neuen Codespace erstellen:** Klicke auf **"Create codespace on main"** (oder auf dem Branch, den du verwenden möchtest).

### **Mit dem Team zusammenarbeiten**

Codespaces sind ideal für die Zusammenarbeit, da die Umgebung für jeden Mitarbeiter exakt gleich ist.

- **Pullen von Partner-Änderungen:** Wenn dein Partner Änderungen in das Repository hochgeladen hat, klicke im Codespace auf das Quellcodeverwaltung-Symbol und dann auf den "Pull"-Button (Pfeil nach unten) oder "Änderungen synchronisieren". Dadurch werden die neuesten Änderungen in deinen Codespace geholt.

- **Branches:** Du kannst Branches direkt im Codespace verwalten. Unten links in der Statusleiste von VS Code siehst du den aktuellen Branch (main). Klicke darauf, um einen **neuen Branch zu erstellen** oder zu einem **bestehenden Branch zu wechseln.**

- **Pull Request:** Nachdem du deine Änderungen in einem Feature-Branch gepusht hast, kannst du den **Pull Request** weiterhin über die **GitHub-Website** erstellen, um den Code von deinen Kollegen überprüfen zu lassen.

### **Codespace schließen und fortsetzen**

Da Codespaces in der Cloud laufen, sind sie nicht an deinen lokalen Computer gebunden.

- **Beenden:** Schließe einfach deinen Browser-Tab. Der Codespace wird nach einer gewissen Inaktivität (meist 30 Minuten, je nach Einstellung) automatisch gestoppt, um Kosten zu sparen.

- **Fortsetzen:** Wenn du auf github.com/codespaces oder den Code-Button deines Repositorys zurückkehrst, wird dein letzter Codespace angezeigt. Klicke auf ihn, um ihn innerhalb weniger Sekunden wieder zu starten, genau an dem Punkt, wo du aufgehört hast (inklusive aller geöffneten Dateien und des Terminalverlaufs).

### Standard Arbeitsablauf
1. lokales Testen

```bash
python -m mkdocs build --site-dir site --clean # erste Fehler werden sichtbar

mkdocs serve # lokaler Server wird gestartet
```
- Seiten Aufruf erfolgt über 127.0.0.1:8000

- Wenn alles passt, dann folgt ...
```bash
git add . # Änderungen markieren
git commit -m "KURZE BESCHREIBUNG" # Änderung speichern
git push # Änderung zu Github hochladen
```

### Github-Branch aktueller als lokale Version***

```bash
git pull # Neueste Änderungen von Github holen
```

### Einrichten eines lokalen Editor (VSCode)


```bash
git remote add origin https://github.com/DEINNAME/DEINREPO.git
git branch -M main
git push -u origin main

git clone https://github.com/DEINNAME/DEINREPO.git # laden der vollständigen github copie
```

### Weitere Befehle

![Befehle](../bilder/git-cheatsheet.jpg)

### Optionen im Merge Editor

***In VS Code hast du oben vier Buttons:***

 - Accept Current Change → lokale Datei behalten

 - Accept Incoming Change → GitHub-Version übernehmen

 - Accept Both Changes → beide Versionen zusammenführen

 - Compare Changes → Unterschiede anzeigen