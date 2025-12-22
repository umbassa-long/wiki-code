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
