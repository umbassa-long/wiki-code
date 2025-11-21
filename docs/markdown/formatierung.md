
# Formatierung


### 🅰️ Text-Basisformatierung (Inline)
Hier sehen Sie die Syntax und das gerenderte Ergebnis.

| Ziel | Syntax (So schreiben Sie es) | Ergebnis (So sieht es aus) |
| :--- | :--- | :--- |
| **Kursiv** | `*Text*` oder `_Text_` | *Text* |
| **Fett** | `**Text**` oder `__Text__` | **Text** |
| **Fett & Kursiv** | `***Text***` oder `___Text___` | ***Text*** |
| **Hervorhebung (Highlight)** | `==Text==` | ==Text== |
| **Durchgestrichen** | `~~Text~~` | ~~Text~~ |
| **Tiefgestellt** | `H~2~O` | H~2~O |
| **Hochgestellt** | `X^2^` | X^2^ |
| **Unterstreichen** | `---` oder `***` | siehe unten  **eigene Zeile** |
| **Wörter grau hinterlegt** | \``Wörter grau hinterlegt`\` | `Wörter grau hinterlegt` |

***

---

### Überschriften
=== "Darstellung"

    # Überschrift 1
    ## Überschrift 2
    ### Überschrift 3
    #### Überschrift 4
    ##### Überschrift 5
    ###### Überschrift 6

=== "Syntax"

    ```markdown
    # Überschrift 1
    ## Überschrift 2
    ### Überschrift 3
    #### Überschrift 4
    ##### Überschrift 5
    ###### Überschrift 6
    ```

### Listen
=== "Unsortiert"

    - Listenpunkt 1
    - Listenpunkt 2
    - Listenpunkt 3

=== "Syntax"

    ```markdown
    - Listenpunkt 1
    - Listenpunkt 2
    - Listenpunkt 3
    ```

=== "Sortiert"

    1. Listenpunkt 1
    2. Listenpunkt 2
    3. Listenpunkt 3

=== "Syntax"

    ```markdown
    1. Listenpunkt 1
    2. Listenpunkt 2
    3. Listenpunkt 3
    ```

**Checkliste**

- Markdown gibt Ihnen zusätzlich die Möglichkeit, Checklisten zu erstellen. Diese erscheinen mit einem Kästchen.
Sie können auch beim erstellen der Liste Häkchen setzen. 
Nutzen Sie hierfür eckige Klammern und ein X.

```markdown
- [ ] A
- [x] B
- [ ] C
```

- [ ] A
- [x] B
- [ ] C

**Checkliste in Tabellenform**

```markdown
| Aufgabe | Status |
|----------|--------|
| A | [x] |
| B | [ ] |
| C | [ ] |
```

| Aufgabe | Status |
|----------|--------|
| A | [x] |
| B | [ ] |
| C | [ ] |

### Darstellung von Code
 - Apostroph vor und nach dem Wort siehe `code`.
 - ``Zwei Apostrophe an Anfang und Ende hebt jeweils ein Apostroph auf, siehe `code`.``
 - Drei Apostrophe Anfang und Ende, sowie der Name der Programmiersprache. 
   Damit wird highlighting aktiviert

### Links
**Links ins Internet**
- Optionaler Tooltip: Fügen Sie einen Titel in Anführungszeichen nach der URL ein, 
  der angezeigt wird, wenn man mit der Maus über den Link fährt.

```markdown

- [Emojis](https://gist.github.com/rxaviers/7360908"Text beim Maus gleiten")


```

- Links ins Internet 
	    - Es wird ein neuer Tab geöffnet.

```html
<a href="https://qualidy.github.io/wiki-docker" target="_blank">Docker</a>
```

### Emojis
- [Emojis](https://gist.github.com/rxaviers/7360908)


### Sonderzeichen
- Asterisk: *
- Bindestrich: \-
- Unterstrich: _
- Runde Klammern: ()
- Eckige Klammern: []
- Geschweifte Klammern: {}
- Punkt: .
- Ausrufezeichen: !
- Raute: #
- Gravis: `
- Backslash: \\

!!! info 
 - Backslash hebt die Bedeutung des folgenden Sonderzeichen auf.

 
 
 
 
 ### Abkürzungserweiterung

Den Mauszeiger über großgeschriebenen Begriff bewegen.


```markdown
*[WINNETOU]: Er ist der Chief-Influencer der Apachen. Reitet meistens auf seinem Pferd Iltschi durch die Prärie, hat nie einen Bad Hair Day, egal wie stürmisch es wird.
*[APACHEN]: Sie reiten schneller, schießen besser und sind insgesamt viel zu ehrenhaft für die fiesen Tricks ihrer Gegenspieler. Sie sind die, die am Ende das Lagerfeuer löschen und dafür sorgen, dass der Sonnenuntergang auch morgen noch schön rot ist.
*[ÖLPRINZ]: Das ist der Typ, der sich dachte: "Ich bau' hier mal eine Fake-Tankstelle auf und verkaufe den Leuten wertlosen Dreck 
```

*[APACHEN]: Sie reiten schneller, schießen besser und sind insgesamt viel zu ehrenhaft für die fiesen Tricks ihrer Gegenspieler. Sie sind die, die am Ende das Lagerfeuer löschen und dafür sorgen, dass der Sonnenuntergang auch morgen noch schön rot ist. unter ihrem edlen Häuptling

*[WINNETOU]: Er ist der Chief-Influencer der Apachen. Reitet meistens auf seinem Pferd Iltschi durch die Prärie, hat nie einen Bad Hair Day, egal wie stürmisch es wird.

*[ÖLPRINZ]: Das ist der Typ, der sich dachte: "Ich bau' hier mal eine Fake-Tankstelle auf und verkaufe den Leuten wertlosen Dreck und seiner skrupellosen Gehilfen zu beenden.

Die **APACHEN** unter ihrem edlen Häuptling **WINNETOU** ritten entschlossen in den Kampf, um die Machenschaften des **ÖLPRINZ** 
**Winnetou** Angriff zielte darauf ab, die von den Handlangern des **Ölprinz** durchgeführte Zerstörung des Landes und die Bedrohung ihres Stammes zu stoppen.

### Verlinkung von Bilder

| Beschreibung | Markdown-Syntax |
| --- | --- |
| Bild von einer externen URL | `![Winnetou reitet](https://example.com/winnetou.jpg)` |
| Bild aus dem gleichen Ordner | `![Blick auf die Prärie](praerie.png)` |
| Bild aus einem Unterordner | `![Der Ölprinz](bilder/oelprinz.gif)` |