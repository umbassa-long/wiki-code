

# 📝 Markdown-Tabellen erstellen

Markdown verwendet eine relativ einfache Syntax, um Tabellen zu formatieren. 
Man spricht hier oft vom **Github Flavored Markdown (GFM)**, 
da es eine häufig verwendete Erweiterung ist, die Tabellen unterstützt.

---

## 📝 Grundlegende Syntax

Du benötigst **vertikale Striche** (`|`) um Spalten zu trennen, 
und eine **Trennlinie** aus drei oder mehr **Bindestrichen** (`---`) unter der Kopfzeile.
Vor und nach der Tabelle jeweils eine leere Zeile.

Hier ist das Grundschema:

```markdown
| Kopfzeile 1 | Kopfzeile 2 | Kopfzeile 3 |
|-------------|-------------|-------------|
| Zelle A1    | Zelle B1    | Zelle C1    |
| Zelle A2    | Zelle B2    | Zelle C2    |
```
#### Ergebnis

| Kopfzeile 1 | Kopfzeile 2 | Kopfzeile 3 |
|-------------|-------------|-------------|
| Zelle A1    | Zelle B1    | Zelle C1    |
| Zelle A2    | Zelle B2    | Zelle C2    |


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
