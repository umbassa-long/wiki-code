
# Formatierung

## Fett & Kursiv & Highlighting & und mehr

```markdown
*Kursiver Text*
_Kursiver Text_
**Fetter Text**
__Fetter Text__
***Kursiver und fetter Text***
___Kursiver und fetter Text___
Highlighting ==very important words==.
H~2~O
X^2^
```

- *Kursiver Text*
- _Kursiver Text_
- **Fetter Text**
- __Fetter Text__
- ***Kursiver und fetter Text***
- ___Kursiver und fetter Text___
- Highlighting ==very important words== .
- H~2~O
- X^2^

## Unterstreichen

Eine horizontale Linie wird durch drei oder mehr Bindestriche, 
Sternchen oder Unterstriche in einer eigenen Zeile erstellt.

```markdown
- ---
- ***
```

## Durchstreichen

```markdown
~~Dieser Text ist durchgestrichen.~~ Dieser aber nicht.
```

## Überschriften

```markdown
# Überschrift 1
## Überschrift 2
### Überschrift 3
#### Überschrift 4
##### Überschrift 5
###### Überschrift 6
```

## Zitate

```markdown
>Dies ist ein **eingerückter Bereich**.
>Der Bereich geht hier weiter.
>Dies ist ein weiterer **eingerückter Bereich**.
Auch dieser Bereich geht in der nächsten Zeile weiter.
Diese Zeile ist allerdings nicht mehr eingerückt.
```

- >Dies ist ein **eingerückter Bereich**. 
- >Der Bereich geht hier weiter. 
- >Dies ist ein weiterer **eingerückter Bereich**. 
- Auch dieser Bereich geht in der nächsten Zeile weiter. 
- Diese Zeile ist allerdings nicht mehr eingerückt. 

## Listen

**Unsortiert**

```markdown

- Listenpunkt 1
- Listenpunkt 2
- Listenpunkt 3
```
**Sortiert**

Eine sortierte Liste hingegen erzeugt man durch eine Zahl 
mit einem direkt darauffolgenden Punkt.

```markdown
1. Listenpunkt 1
2. Listenpunkt 2
3. Listenpunkt 3
```

**Checkliste**

Markdown gibt Ihnen zusätzlich die Möglichkeit, Checklisten zu erstellen. 
Diese erscheinen mit einem Kästchen, das per Knopfdruck aktiviert werden kann. 
Sie können auch bereits beim Erstellen der Liste Häkchen setzen. 
Nutzen Sie hierfür eckige Klammern und ein X. Zwischen den eckigen Klammern ein Leerzeichen.

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

## Darstellung von Code

 - Apostroph vor und nach dem Wort siehe `code`.
 - ``Zwei Apostrophe an Anfang und Ende hebt jeweils ein Apostroph auf, siehe `code`.``
 - Drei Apostrophe Anfang und Ende, sowie der Name der Programmiersprache. 
   Damit wird highlighting aktiviert

## Links

**Links ins Internet**
- Optionaler Tooltip: Fügen Sie einen Titel in Anführungszeichen nach der URL ein, 
  der angezeigt wird, wenn man mit der Maus über den Link fährt. 

```markdown

- [Emojis](https://gist.github.com/rxaviers/7360908"Text beim Maus gleiten")


```

- Links ins Internet 
	    - Es wird ein neuer Tab geöffnet.

```markdown

<a href="https://qualidy.github.io/wiki-docker" target="_blank">Docker</a>


```

## Emojis

- [Emojis](https://gist.github.com/rxaviers/7360908)


## Sonderzeichen

- Asterisk: *
- Bindestrich:
- Unterstrich: _
- Runde Klammern: ()
- Eckige Klammern: []
- Geschweifte Klammern: {}
- Punkt: .
- Ausrufezeichen: !
- Raute: #
- Gravis: `
- Backslash: \

- Mit dem Backslash löst man die Bedeutung der Sonderzeichen auf.

Die ist ein \*Beispiel mit Sternchen\*.

Die ist ein *Beispiel mit Sternchen und ohne backslash*.