# SQL

## Regeln zum SELECT Befehl

```SQL
SELECT Spaltennamen |2. * FROM Tabellenname
[WHERE Suchbedingung]
[GROUP BY Spaltennamen]
[HAVING Gruppenbedingung]
[ORDER BY Spaltennamen [ASC | DESC]];
```

### Wichtige Regeln und Reihenfolge der Klauseln

!!! note
    Die Reihenfolge der wichtigsten Klauseln ist streng festgelegt:
    
---

1. SELECT: 🔎 Wählt die Spalten aus, die in der Ergebnisliste erscheinen sollen. Syntax: SELECT Spalte1, Spalte2, ... oder SELECT * (für alle Spalten).

2. FROM: 📚 Gibt an, aus welcher Tabelle oder welchen Tabellen die Daten stammen. Syntax: FROM Tabellenname (oder Verknüpfungen/Joins von Tabellen).

3. WHERE: ⚙️ Filtert die einzelnen Zeilen basierend auf einer oder mehreren Bedingungen. Dies geschieht bevor die Gruppierung (falls vorhanden) stattfindet. Syntax: WHERE Bedingung (z. B. Alter > 18 AND Stadt = 'Berlin').

4. GROUP BY: 📊 Gruppiert Zeilen mit denselben Werten in den angegebenen Spalten. Wird typischerweise mit Aggregatfunktionen (wie SUM(), COUNT(), AVG()) verwendet. Syntax: GROUP BY Spalte1, Spalte2.

5. HAVING: 🛡️ Filtert die Gruppen, die durch GROUP BY erstellt wurden, basierend auf einer Bedingung. Syntax: HAVING Aggregatbedingung (z. B. HAVING COUNT(*) > 10).

6. ORDER BY: 🗃️ Sortiert die Ergebniszeilen in aufsteigender (ASC, Standard) oder absteigender (DESC) Reihenfolge.
Syntax: ORDER BY Spalte [DESC].

### ✨ Zusätzliche wichtige Syntax-Regeln
Schlüsselwörter: SQL-Schlüsselwörter wie SELECT, FROM, WHERE können in Groß- oder Kleinschreibung geschrieben werden (SQL ist nicht case-sensitiv bei Schlüsselwörtern), aber Großschreibung wird aus Gründen der Lesbarkeit oft empfohlen.

Aliase: Sie können Spalten oder Tabellen einen Alias (einen temporären, neuen Namen) mit dem Schlüsselwort AS geben.

Beispiel: SELECT Name AS Kundenname FROM Kunden AS K.

Eindeutige Werte: Das Schlüsselwort DISTINCT wird unmittelbar nach SELECT platziert, um nur eindeutige (doppelte Zeilen werden entfernt) Ergebnisse zurückzugeben.

Beispiel: SELECT DISTINCT Stadt FROM Kunden.

Zeilenende: SQL-Anweisungen werden in den meisten Systemen mit einem Semikolon (;) abgeschlossen, obwohl dies oft nur für das Trennen mehrerer Befehle erforderlich ist. Es ist aber eine Best Practice.

Kommas: Spalten in der SELECT-Liste und in der GROUP BY- oder ORDER BY-Liste werden durch Kommas getrennt.