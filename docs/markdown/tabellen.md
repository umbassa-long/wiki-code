---
title: Tabellen
---

# Tabellen
---

## 📝 Grundlegende Syntax

Du benötigst **vertikale Striche** (`|`) um Spalten zu trennen, 
und eine **Trennlinie** aus drei oder mehr **Bindestrichen** (`---`) unter der Kopfzeile.
Vor und nach der Tabelle jeweils eine leere Zeile.

Hier ist das Grundschema:

### "Aufbau"

=== "Aussehen 1"

    ```markdown
    | Kopfzeile 1 | Kopfzeile 2 | Kopfzeile 3 |
    |-------------|-------------|-------------|
    | Zelle A1    | Zelle B1    | Zelle C1    |
    | Zelle A2    | Zelle B2    | Zelle C2    |
```

=== "Aussehen 2"

    | Kopfzeile 1 | Kopfzeile 2 | Kopfzeile 3 |
    |-------------|-------------|-------------|
    | Zelle A1    | Zelle B1    | Zelle C1    |
    | Zelle A2    | Zelle B2    | Zelle C2    |

=== "Syntax"

    ```markdown
    | Docker-Befehl | Erklärung | Status |
    | :--- | :--- | :--- |
    | docker run | Container starten | :material-check-circle: Aktiv |
    | docker stop | Container stoppen | :material-close-circle: Inaktiv |
    | docker rm | Container löschen | :material-alert-circle: Vorsicht |
    ```

## Bunte Bildchen in Tabellen

Hier siehst du die vollständig aktualisierte Tabelle mit Twemoji-Häkchen und Kontrollkästchen.  
Alle Icons werden farblich korrekt dargestellt und passen sich dem hellen bzw. dunklen Schema an.  
Die Schriftgröße ist einheitlich mit dem Fließtext (1.2 em).

| Icon-Code | Darstellung (Symbol) | Bedeutung & Verwendung |
|-----------|--------------------|-----------------------|
| `:material-check:` | <span class="twemoji icon-success">✅</span> | Das einfachste, grundlegendste Häkchen. |
| `:material-check-circle:` | <span class="twemoji icon-success">✔️</span> | Häufig verwendetes Icon: Häkchen in solidem Kreis (Aktiv / Erledigt). |
| `:material-check-circle-outline:` | <span class="twemoji icon-success">✔️</span> | Häkchen in einem Kreis-Umriss (subtiler). |
| `:material-check-all:` | <span class="twemoji icon-success">✔✔</span> | Zwei Häkchen (Alle bestätigt / Gelesen). |
| `:material-check-bold:` | <span class="twemoji icon-success">✔️</span> | Dickeres, prominenteres Häkchen (stärkere Betonung). |
| `:material-checkbox-marked:` | <span class="twemoji icon-success">☑️</span> | Klassisches, ausgefülltes Kontrollkästchen. |
| `:material-checkbox-blank-outline:` | <span class="twemoji icon-pending">⬜</span> | Leeres Kontrollkästchen (Ausstehend). |
| `:material-close:` | <span class="twemoji icon-error">❌</span> | Rotes X für Fehler oder Ablehnung. |
| `:material-alert:` | <span class="twemoji icon-error">⚠️</span> | Warnung / Achtung. |
| `:material-info:` | <span class="twemoji icon-success">ℹ️</span> | Informationssymbol. |

## Markdown-Tabellen

Hier eine Beispiel-Tabelle, die den Card-Look und die einheitliche Schriftgröße verwendet:

| Name | Funktion | Status |
|------|----------|--------|
| Projekt1 | Testphase | <span class="twemoji icon-success">✅</span> |
| Projekt2 | In Arbeit | <span class="twemoji icon-pending">⬜</span> |
| Projekt3 | Fehler | <span class="twemoji icon-error">❌</span> |

## Weitere Tabellen

Weitere Tabellen können analog erstellt werden, indem du die Twemoji-Icons `<span class="twemoji icon-...">Emoji</span>` einsetzt, um Farben und Status korrekt darzustellen.  
Alle Tabellen übernehmen automatisch **schriftgröße, Farben und Card-Look** aus `extra.css`.


```markdown
| Icon-Code | Darstellung (Symbol) | Bedeutung & Verwendung |
|-----------|--------------------|-----------------------|
| `:material-check:` | <span class="twemoji icon-success">✅</span> | Das einfachste, grundlegendste Häkchen. |
| `:material-check-circle:` | <span class="twemoji icon-success">✔️</span> | Häufig verwendetes Icon: Häkchen in solidem Kreis (Aktiv / Erledigt). |
| `:material-check-circle-outline:` | <span class="twemoji icon-success">✔️</span> | Häkchen in einem Kreis-Umriss (subtiler). |
| `:material-check-all:` | <span class="twemoji icon-success">✔✔</span> | Zwei Häkchen (Alle bestätigt / Gelesen). |
| `:material-check-bold:` | <span class="twemoji icon-success">✔️</span> | Dickeres, prominenteres Häkchen (stärkere Betonung). |
| `:material-checkbox-marked:` | <span class="twemoji icon-success">☑️</span> | Klassisches, ausgefülltes Kontrollkästchen. |
| `:material-checkbox-blank-outline:` | <span class="twemoji icon-pending">⬜</span> | Leeres Kontrollkästchen (Ausstehend). |
| `:material-check-circle-alt:` | <span class="twemoji icon-success">✅</span> | Alternative Variante eines Kreishäkchens. |
| `:material-checkbox-indeterminate:` | <span class="twemoji icon-pending">➖</span> | Teilweise markiertes Kontrollkästchen (Indeterminate). |
| `:material-close:` | <span class="twemoji icon-error">❌</span> | Rotes X für Fehler, Ablehnung oder Schließen. |
| `:material-alert:` | <span class="twemoji icon-error">⚠️</span> | Warnung / Achtung. |
| `:material-info:` | <span class="twemoji icon-success">ℹ️</span> | Informationssymbol. |
```



### Textausrichtung

Du kannst die Textausrichtung in jeder Spalte mithilfe von Doppelpunkten (:) in der Trennlinie steuern:

- Links ausgerichtet: Doppelpunkt links vom Bindestrich (:---)
- Rechts ausgerichtet: Doppelpunkt rechts vom Bindestrich (---:)
- Zentriert: Doppelpunkte links und rechts vom Bindestrich (:---:)
- Standard (meist links): Nur Bindestriche (---)

```markdown
| Links | Zentriert | Rechts |
| :--- | :---: | ---: |
| Apfel | Banane | Zitrone |
| Auto | Fahrrad | Roller |
```

#### Ergebnis

| Links | Zentriert | Rechts |
| :--- | :---: | ---: |
| Apfel | Banane | Zitrone |
| Auto | Fahrrad | Roller |

### Formatierung im Tabelleninhalt

 Du kannst grundlegende Formatierungen wie fett, kursiv und Inline-Code auch innerhalb der
 Zellen verwenden:

```markdown
| Produkt | Preis | Status |
|---|---|---|
| **Laptop** | 1200 € | *Auf Lager* |
| `Maus` | **25 €** | Nicht verfügbar |
Ergebnis:ProduktPreisStatusLaptop1200 €Auf LagerMaus25 €Nicht verfügbar
```
#### Ergebnis: 

| Produkt | Preis | Status |
|---|---|---|
| **Laptop** | 1200 € | *Auf Lager* |
| `Maus` | **25 €** | Nicht verfügbar |




### Nützliche Werkzeuge

<a href="https://www.tablesgenerator.com/markdown_tables" target="_blank">Markdown Tables Generator: </a>Ein Editor, mit dem du Tabellen grafisch erstellen und dann 
den Markdown-Code exportieren kannst.

<a href="https://tabletomarkdown.com/convert-spreadsheet-to-markdown/" target="_blank">Table to Markdown: </a>Konvertiert Daten, die du aus einem Tabellenkalkulationsprogramm 
(wie Excel oder Google Sheets) kopierst, direkt in eine Markdown-Tabelle.
