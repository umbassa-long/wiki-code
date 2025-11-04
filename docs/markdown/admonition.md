
## Admonition-Typen

1. __Standard-Hinweise__ (Grau, Blau, Grün)
Diese sind ideal für allgemeine Informationen, Hintergrundwissen oder Tipps.

| Typ | Farbe / Icon | Typischer Zweck |
| --- | --- | --- |
note | 🔵 Blau | "Allgemeine Information, Standardhinweis."
abstract / summary / info | 🔵 Blau | "Zusammenfassungen, Hintergrundinformationen."
tip / hint | 🟢 Grün | "Nützliche Tipps, Abkürzungen oder gute Praktiken."
success | 🟢 Grün | "Bestätigung einer erfolgreichen Aktion, positives Ergebnis."
question | 🟣 Lila | "Fragen oder Punkte, die zur Diskussion anregen sollen."

2. __Warnungen und Dringlichkeit__ (Gelb, Rot)
Diese lenken die Aufmerksamkeit des Benutzers auf kritische Punkte.

|Typ | Farbe / Icon | Typischer Zweck|
| --- | --- | --- |
warning | 🟡 Gelb | "Wichtiger Hinweis, auf den man achten muss (wie in Ihrem Bild)."
caution / attention | 🟡 Gelb | "Vorsichtshinweise, die möglicherweise zu Problemen führen."
failure | 🔴 Rot | "Negative Ergebnisse, Fehlschläge."
danger / error | 🔴 Rot | "Kritische Warnung, Dinge, die nicht getan werden dürfen (führt zu Datenverlust, etc.)."

3. __Spezielle Typen__
Diese Typen sind nützlich für organisatorische Inhalte

| Typ | Farbe / Icon | Typischer Zweck | 
|---|---|---|
bug | 🪲 Orange | Hinweise auf bekannte Fehler oder Bugs.
example | 🟢 Grün/Blau | Hervorhebung eines Code-Beispiels oder Anwendungsfalls.
quote / cite | 🔵 Blau | Zitate oder Referenzen.

## __Syntax__

Basis Syntax


!!! tip
    Mögliche Arten von **TYP** siehe oben. 
    Richtige Anzahl der Leerzeichen beachten


```markdown
!!! TYP ["Optionaler Titel"]
    Hier steht der Inhalt der Admonition.
    Der gesamte Text muss mit vier Leerzeichen eingerückt sein.
```
1. Standard-Admonition (Typ = Titel)
- Wenn Sie keinen eigenen Titel angeben, 
  verwendet die Box den Typ als Titel (z.B. "Note" oder "Warning").

```markdown 
!!! note
    Dies ist ein allgemeiner Hinweis für den Leser.
    Sie müssen hier nichts Besonderes beachten.
```
!!! note 
    Dies ist ein allgemeiner Hinweis für den Leser.
    Sie müssen hier nichts Besonderes beachten.

 __Faltbare Fenster__

- Faltbare Admonitions:
Sie können jede Admonition faltbar machen, 
indem Sie ?? statt !! verwenden. Dies ist nützlich für lange Abschnitte, die nicht sofort sichtbar sein sollen.

Voraussetzung: **pymdownx.details** muss in Ihrer **mkdocs.yml** unter markdown_extensions: aktiviert sein.

??? tip
    Mögliche Arten von **TYP** siehe oben. 
    Richtige Anzahl der Leerzeichen beachten

--Fenster mit Icon__
Sie können das Standard-Icon eines Admonition-Typs überschreiben, 
indem Sie das gewünschte Icon direkt nach dem Typ angeben:

```markdown
!!! success icon:material-check "Fertig!"
    Die Installation ist abgeschlossen.
```
- Ergebnis

!!! success icon:material-check "Fertig!"
    Die Installation ist abgeschlossen.

__Links für Icons__
- [Material Design](https://pictogrammers.com/library/mdi/)
- [FontAwesome](https://fontawesome.com/search?m=free)
- [Octicons](https://primer.style/octicons/)
- [Simple Icons](https://simpleicons.org/)
