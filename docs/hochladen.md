# Code


## Werkzeuge der Seite
```powershell

git commit -m "Kurze Beschreibung der Aenderung" # 1. Beschreibung des Brunch in ""eintragen

git push origin main                             # 2. Sichert den Quellcode (index.md, mkdocs.yml, etc.) im Haupt-Branch (main) auf GitHub

python -m mkdocs gh-deploy --force               # 3. Generiert die statische HTML-Website und laedt Sie zu gh-pages-Branch hoch, um die Online-Seite zu aktualisieren.

```